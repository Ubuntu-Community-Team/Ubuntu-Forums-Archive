---
title: "Using satellite without powering LNB"
date: 2009-03-09
forum: Mythbuntu
---

### Post by amphibem on 2009-03-09
Simple question: I would like to receive a satellite signal that has been looped through a set top box which is providing the LNB power. 

So how do I stop mythtv from providing power to the LNB? In the LNB setup it shows up as a greyed out option [Standard (Voltage)].

---

### Post by AlecJ on 2009-04-22
> **amphibem said:**
> Simple question: I would like to receive a satellite signal that has been looped through a set top box which is providing the LNB power. 

So how do I stop mythtv from providing power to the LNB? In the LNB setup it shows up as a greyed out option [Standard (Voltage)].

                                 LNB (low noise block) used to collect RF (Radio Frequency) bounced and focused from a parabolic dish reflector.


Rf signal passes though a electro magnetic polarized feed horn powered vertical/horizontal (in old money) by the receiver tuner as to the frequency/polarization of each channel. Which is then filtered via an air capacitor tuned to a particular LO ( Local oscillator). Giving the LNB a particular ban of GHz it is able to receive in.( C band, K band) etc., but tri-band lnb's are now common place in Europe.


 Once the signal have been received and converted to a UHF frequency it is able to travel down and within the confines of a coax cable, and pluged into the back of a receiver that further de-modulates the signal in to video and sound to be displayed.
 

 From this information, you can see that interfering with the LNB output is not possible, as it's one LNB, one channel received. Even if it one of 4 inside one enclosed LNB ( i'm not clear how you polarise these units independently, the old Voltage swicthing unit's gave way the current swicthing unit's. I never owned a multi unit)

 You can only take the video/sound composite signal out of the STB.
 For this you would only require a comp/svideo capture card, not dvb-s card.

---

