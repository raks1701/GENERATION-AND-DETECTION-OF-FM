# GENERATION-AND-DETECTION-OF-FM
## AIM:
To write a program for Frequency Modulation and Demodulation using SCILAB and to observe and measure the frequency deviation and the modulation index of FM.

## EQUIPMENTS REQUIRED

•	Computer with i3 Processor

•	SCI LAB

## THEORY
  Frequency modulation is a type of modulation in which the frequency of the high frequency (carrier) is varied in accordance with the instantaneous value of the modulating signal.
  
  #### FREQUENCY DEVIATION Δf  and MODULATION INDEX m f :
  
  The frequency deviation Δf represents the maximum shift between the  modulated signal
  frequency, over and under the frequency of the carrier.
  
  We define modulation index m f the ratio between Δf and the modulating frequency
  m= Δf / fm


#### FREQUENCY MODULATION GENERATION:
  The circuits used to generate a frequency modulation must vary the frequency of a high frequency signal (carrier) as function of the amplitude of a low frequency signal (modulating signal). In practice there are two main methods used to generate FM.

## ALGORITHM
  1.	Define Parameters:
     
      •	Fs: Sampling frequency.
      •	T: Duration of the signal.
      •	Fc: Carrier frequency.
      •	Fm: Frequency of the modulating signal.
      •	Beta: Modulation index, which controls the extent of frequency deviation.
  2.	Generate Signals:
     
      •	modulating_signal: Sinusoidal signal used for modulation.
      •	carrier_signal: The high-frequency carrier signal.
      •	modulated_signal: FM modulated signal calculated by varying the carrier frequency according to the modulating signal.
      
  3.	FM Modulation:
     
      •	Modulated_signal is obtained by modulating the carrier signal with the modulating signal.
 
  4.	FM Demodulation:
     
      •	Differentiation: Computes the derivative of the modulated signal to extract frequency variations.
      •	Envelope Detection: Takes the absolute value to retrieve the envelope of the signal.
      •	Low-pass Filtering: Applies a Butterworth low-pass filter to smooth the envelope and recover the original modulating signal.
      
  5.	Visualization:
      
      •	Plots the modulating signal, carrier signal, FM modulated signal, and demodulated signal for analysis.


## PROCEDURE

    •	Refer Algorithms and write code for the experiment.
    •	Open SCILAB in System
    •	Type your code in New Editor
    •	Save the file
    •	Execute the code
    •	If any Error, correct it in code and execute again
    Verify the generated waveform using Tabulation and Model Waveform

## MODEL GRAPH:
<img width="512" height="365" alt="image" src="https://github.com/user-attachments/assets/dfe6bc64-2b6f-4afa-ae79-95391859ab04" />

## PROGRAM
```
clc; clear; close;
function p = pdf(t)
    p = 3 .* (1 - t).^2;
endfunction
function y = integrand_mean(t)
    y = t .* pdf(t);
endfunction
function y = integrand_x2(t)
    y = t.^2 .* pdf(t);
endfunction
a = 0; b = 1;
EX  = intg(a, b, integrand_mean);
EX2 = intg(a, b, integrand_x2);
vX  = EX2 - EX^2;
EY  = intg(a, b, integrand_mean);
EY2 = intg(a, b, integrand_x2);
vY  = EY2 - EY^2;
mprintf("Mean of X   = %g\n", EX);
mprintf("Var(X)      = %g\n\n", vX);
mprintf("Mean of Y   = %g\n", EY);
mprintf("Var(Y)      = %g\n\n", vY);
function r = crosscorr_seq(x, y)
    nx = length(x);
    ny = length(y);
    lags = -(ny-1):(nx-1);
    r = zeros(1, nx + ny - 1);
    idx = 1;
    for lag = lags
        s = 0;
        for n = 1:nx
            m = n - lag;
            if m >= 1 & m <= ny then
                s = s + x(n) * y(m);
            end
        end
        r(idx) = s;
        idx = idx + 1;
    end
endfunction
x = input("Enter reference sequence (e.g. [1 2 3 4]): ");
y = input("Enter second sequence    (e.g. [2 3 4 5]): ");
x = x(:)'; y = y(:)';
r = crosscorr_seq(x, y);
lags = -(length(y)-1):(length(x)-1);
scf(1);
plot2d3(lags, r);
xtitle("Cross-correlation (stem plot)","Lag","r_{xy}(lag)");
```

## TABULATION

## CALCULATION
![ac 4](https://github.com/user-attachments/assets/d9a17bbe-d8bf-400e-a2bd-1bc740fed045)

## OUTPUT
![ac 4](https://github.com/user-attachments/assets/11f5b1c7-3a8e-4883-84ef-ca55b8d0fcdf)
![4 out](https://github.com/user-attachments/assets/3568c54e-4cbb-422f-b836-702c8b042ac5)

## RESULT
Thus the mean , variance and cross correlation are executed in Scilab and output is verified.

