# -Amplitude-Modulation-and-Demodulation-using-NumPy-and-Matplotlib

__Aim__: 

To implement and analyze amplitude modulation (AM) using Python's NumPy and Matplotlib libraries. 

__Apparatus Required__: 

Software: Python with NumPy and Matplotlib libraries 
Hardware: Personal Computer 

__Theory__: 

Amplitude Modulation (AM) is a technique used in electronic communication, primarily for transmitting 
information via a radio carrier wave. In AM, the amplitude of the carrier wave is varied in proportion to that of 
the message signal. The general form of an AM signal is: 


__Algorithm__:
1. Initialize Parameters: Set the values for carrier frequency, message frequency, and sampling frequency. 
2. Generate Time Axis: Create a time vector for the signal duration. 
3. Generate Message Signal: Define the message signal as a cosine wave. 
4. Generate Carrier Signal: Define the carrier signal as a cosine wave. 
5. Modulate Signal: Apply the AM formula to obtain the modulated signal. 
6. Plot the Signals: Use Matplotlib to plot the message signal, carrier signal, and modulated signal


__Program__ :
```
import numpy as np
import matplotlib.pyplot as plt
from scipy.signal import hilbert

# Parameters (from your photo)
A_c =6.2      # Carrier amplitude
f_c = 6100      # Carrier frequency (Hz)
A_m = 3.1        # Message amplitude
f_m = 610        # Message frequency (Hz)

sampling_frequency = 100000   # VERY IMPORTANT for proper waveform
duration = 0.015              # show only 15ms like your picture

# Time axis
t = np.linspace(0, duration, int(sampling_frequency * duration))

# Message Signal
m_t = A_m * np.cos(2 * np.pi * f_m * t)

# Carrier Signal
c_t = A_c * np.cos(2 * np.pi * f_c * t)

# Amplitude Modulated (AM) Signal
s_t = (1 + (m_t / A_c)) * c_t   # normalized so waveform looks correct

# Demodulation using Hilbert Transform
analytic_signal = hilbert(s_t)
envelope = np.abs(analytic_signal)
demodulated_message = envelope - A_c

# Plot results
plt.figure(figsize=(12, 10))

plt.subplot(4, 1, 1)
plt.plot(t, m_t)
plt.title('Original Message Signal')
plt.grid(True)

plt.subplot(4, 1, 2)
plt.plot(t, c_t)
plt.title('Carrier Signal')
plt.grid(True)

plt.subplot(4, 1, 3)
plt.plot(t, s_t)
plt.title('Amplitude Modulated (AM) Signal')
plt.grid(True)

plt.subplot(4, 1, 4)
plt.plot(t, demodulated_message)
plt.title('Demodulated Signal')
plt.grid(True)

plt.tight_layout()
plt.show()
```
__Tabulation__:
![WhatsApp Image 2025-12-03 at 01 07 52_b25e111e](https://github.com/user-attachments/assets/850b6470-3ef5-4ed4-adc6-e7d7c3969958)

 __Output__:
![WhatsApp Image 2025-12-03 at 01 07 52_5800c26d](https://github.com/user-attachments/assets/3b15e653-0e7e-4ae1-80d6-6fb6fb3ae4f4)


 __Result__:
![WhatsApp Image 2025-12-03 at 01 07 53_c7355141](https://github.com/user-attachments/assets/79f9c704-e619-456e-830d-bd90f585b4fd)


