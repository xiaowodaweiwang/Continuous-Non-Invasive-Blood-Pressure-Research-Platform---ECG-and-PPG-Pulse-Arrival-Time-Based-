# Continuous Non-Invasive Blood Pressure Research Platform - ECG and PPG Pulse Arrival Time Based
This project is cuffless cNIBP research platform with ECG(two-electrode, without Right Leg Drive(RLD) ) and PPG(MAX3010x),  the Pulse Arrival Time (PAT) using ECG and PPG signal, measure the time delay(∆t) between QRS-Complex of the ECG signal and any one systolic peak of the PPG signal.

<p align="center">
 <img src="https://github.com/GCY/Continuous-Non-Invasive-Blood-Pressure-Research-Platform---ECG-and-PPG-Pulse-Arrival-Time-Based-/blob/master/res/v3%20demo.gif">
</p>

## Hardware

### V4

coming soon...

- STM32F405
- ECG : INA333+AD8669(without RLD)
- Electrode : PCB Pads and NeuroSky EEG dry 6mm electrode(Pinhole PAD1 & PAD2) [NeuroSky](http://neurosky.com)
- PPG : LArm
- LCM : 128x64 SSD1306
- OUTPUT : USB-FS VCP
- Charger : BQ24014

### V3

- STM32F405
- ECG : INA827+LM324PWR(without RLD)
- Electrode : PCB Pads and NeuroSky EEG dry 6mm electrode(Pinhole PAD1 & PAD2) [NeuroSky](http://neurosky.com)
- PPG : LArm
- LCM : 128x64 SSD1306
- OUTPUT : USB-FS VCP
- Charger : TP4056*

#### Note
- TP4056 have mV level peak-to-peak noise... so, jump VBUS to switch... ![alt text](https://github.com/GCY/Continuous-Non-Invasive-Blood-Pressure-Research-Platform---ECG-and-PPG-Pulse-Arrival-Time-Based-/blob/master/res/without%20charger.png?raw=true)
- Replace D1 to 0R resistor, reduce LDO VDDA noise.
- Unplug the NB AC adapter.

</br>

![alt text](https://github.com/GCY/Continuous-Non-Invasive-Blood-Pressure-Research-Platform---ECG-and-PPG-Pulse-Arrival-Time-Based-/blob/master/res/v3%20pic.jpg?raw=true)

### V1
- STM32F407
- ECG : INA827+LM324PWR(without RLD)
- Electrode : PCB Pads
- PPG : LArm and RArm
- LCM : 128x64 SSD1306
- OUTPUT : UART

## Firmware
This firmware only for testing, includes USB-FS VCP, Max3010x Spo2 algorithm, PPG and ECG signal oscilloscope display.</br>

 - cd ./firmware/stm32f405/src/
 - make
 - load elf file
 - run
## Software
[wxECGAnalyzer](https://github.com/GCY/wxECGAnalyzer) is a QRS-Complex ECG signal process tool and QRS-Complex detection algorithm validation tools, [Pulse Oximeter MAX3010X](https://github.com/GCY/Pulse-Oximeter-with-MAX3010X) is a Spo2 signal process and r-ratio finetune tool, combining the two tools, could implement the PAT-BP regression algorithm.


</br>

![alt text](https://github.com/GCY/Continuous-Non-Invasive-Blood-Pressure-Research-Platform---ECG-and-PPG-Pulse-Arrival-Time-Based-/blob/master/res/example.png?raw=true)

## Pulse Arrival Time Calculate

![](https://github.com/GCY/Continuous-Non-Invasive-Blood-Pressure-Research-Platform---ECG-and-PPG-Pulse-Arrival-Time-Based-/blob/master/res/PAT%20Calculate.png)

## What's cuff-less blood pressure monitor and difference between Pulse Arrival Time(PAT) and Pulse Transit Time(PTT)
In cuffless non-invasive blood pressure monitor field, we with the accurate calibration of PAT to BP, beat-to-beat BP can be estimated from PAT. On the basis of the theoretical relationship between PAT and BP and their experimental or empirical relationship, various models that correlate PAT with BP have been established.</br>
</br>
PAT and BP with Regression: </br>
![alt text](https://github.com/GCY/Continuous-Non-Invasive-Blood-Pressure-Research-Platform---ECG-and-PPG-Pulse-Arrival-Time-Based-/blob/master/res/PAT%20and%20Regression.png?raw=true)

</br>
</br>
Pulse transit time (PTT) is the time it takes for the pressure or flow wave to propagate between two arterial sites.
PTT measured as the time delay between invasive proximal and distal blood pressure or flow, and PTT(propagate time) can be converted to Pulse Wave Velocity(PWV is speed unit).

the most used is the R-wave(QRS Complex) in the electrocardiogram (ECG) and combine pulsemeter(piezo or PPG), leading to the so called pulse arrival time (PAT). 
PAT is not exactly the PTT, as it includes the time interval between ventricular depolarization and the opening of the aortic valve which is known as pre-ejection period (PEP) and it varies beat-to-beat.

Most efforts have employed the time delay between ECG and finger photoplethysmography (PPG) waveforms as a convenient surrogate of PTT. 

However, these conventional pulse arrival time (PAT) measurements include the pre-ejection period (PEP) and the time delay through small,
muscular arteries and may thus be an unreliable marker of BP.


Shortcoming is that PAT includes the pre-ejection period (PEP) in addition to PTT. 
Since the PEP component depends on the electromechanical functioning of the heart, it can change independently of PTT and thus BP. 

Because the ECG QRS-Complex is not the starting point for blood to actually enter the radial artery, it is a biopotential to depolarization of the sinus node

</br>

## This project only for research

</br>

[![](http://img.youtube.com/vi/RtydQm8okKk/0.jpg)](https://www.youtube.com/watch?v=RtydQm8okKk)


</br>

## Reference :
- [1] Continuous Blood Pressure Measurement from Invasive to Unobtrusive: Celebration of 200th Birth Anniversary of Carl Ludwig</br>
- [2] Cuff-Less and Continuous Blood Pressure Monitoring: A Methodological Review</br>
- [3] https://www.egr.msu.edu/classes/ece480/capstone/spring13/group03/documents.html
- [4] Cho, J., & Baek, H. J. (2020). A Comparative Study of Brachial–Ankle Pulse Wave Velocity and Heart–Finger Pulse Wave Velocity in Korean Adults. Sensors, 20(7), 2073.
 
LICENSE
-------

MIT License

Copyright (c) 2020 Tony Guo

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.

OSHW Certification
-------

https://certification.oshwa.org/tw000003.html

![alt text](https://github.com/GCY/Continuous-Non-Invasive-Blood-Pressure-Research-Platform---ECG-and-PPG-Pulse-Arrival-Time-Based-/blob/master/res/OSHW_mark_TW000003.png?raw=true) 
