---
title: "Apple Airpods as microphone in Ubuntu 20.04"
date: 2020-05-24
forum: Multimedia Software
---

### Post by nxdcalap on 2020-05-24
[COLOR=#242729][FONT=Arial]I've just acquired **Apple Airpods** (2nd gen) to use it as my main sound setup in **Ubuntu 20.04** since I'm WFH in order to use them in Zoom meetings and so on but is not possible.
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Ubuntu 20.04 is not able to detect the microphone and there's **no way to use them as a microphone**.
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Any idea how to fix that? If they are not gonna work I'll return them since they are pretty expensive.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]
Thanks in advance![/FONT][/COLOR]

---

### Post by marcio-munhoz on 2020-06-16
Same problem with Ubuntu 20.04 + JBL TUNE 120TWS

---

### Post by Holger_Gehrke on 2020-06-18
Bluetooth defines so called 'profiles' for various devices which define what capabilities devices have and how to access those capabilities. Headsets can be accessed through two different profiles. One is headset profile (hsp) or handsfree profile (hfp), which gives access to low quality audio output **and** input. The other is  a2dp (advanced audio distribution profile) which provides high quality audio **output only**. Often the devices also have some buttons and those are accessed as separate, additional devices of type HID (human interface device).  So to access the microphone you'll have to change the profile used to connect to the device.

Disclaimer: I've never actually managed to make it work, but that's probably down to some peculiarities of my system and my OS-installation. When I try to switch to HSP/HFP I always get an error.

Holger

---

