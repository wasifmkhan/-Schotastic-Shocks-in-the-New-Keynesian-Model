# -MATLAB-Schotastic-Shocks-in-the-New-Keynesian-Model

## Technical Skills - MATLAB (Dynare Library)

This project was done as an assignment for my SFU Undergraduate Class ECON 483.

This project simulates stochastic shocks on macro variables of the New-Keynesian DSGE 
model which includes Demand, Supply and Inflation. It assumes rational expectations to 
evaluate how the economy converges back into its steady state. 

The paper also looks into how the convergence is affected when we change the degree of 
stochastic shock and how aggressively the government reacts to changes in macro variables for its steady state.

![image](https://user-images.githubusercontent.com/122067802/213050615-3ddf1108-1732-4288-807e-ed439ccb3bfc.png)

![image](https://user-images.githubusercontent.com/122067802/213050695-bf8e1474-4671-4d99-8175-d18c6e183dc4.png)

![image](https://user-images.githubusercontent.com/122067802/213050780-f48e0023-2a92-44b4-96ba-154ed121837f.png)

![image](https://user-images.githubusercontent.com/122067802/213050847-5cd8ada1-79af-4b3f-8c7e-3603628a9a2d.png)

![image](https://user-images.githubusercontent.com/122067802/213050908-ea8959f0-67e7-47ab-9eda-147944691bd5.png)

![image](https://user-images.githubusercontent.com/122067802/213050972-2eb8cd39-2832-4f4c-bc88-baf18dab72ca.png)

Appendix: Code used for model Simulations: 

%Block 1

var x pi i u Ex Epi; 

varexo epsilon;

parameters beta kappa sigma rhou phipi phix;

%Block 2 

%Values changed in this block for part (c) and 
(d)% beta=0.99;

kappa=0.3;

sigma=1;

rhou=0.9;

phipi=1.5;

phix=0.5;

%Block 3

model(linear);

Ex = x(+1);

Epi = pi(+1);

x = Ex - (1/sigma)*(i-Epi)+u;

%x = Ex - (1/sigma)*(i-Epi);->without demand shock%

pi = beta*Epi + kappa*x;

%pi = beta*Epi + kappa*x+u;-> with inflation shock%

i = phipi*pi + phix*x;

%i = phipi*pi + phix*x+u;-> Rule 1 with shock%

%i = phipi*Epi; -> Rule 3%

%i = phipi*Epi+u; -> Rule 3 with shock%

u = rhou*u(-1) + epsilon;

end;
shocks;
var epsilon;
stderr 1;
end;
steady;
stoch_simul;

