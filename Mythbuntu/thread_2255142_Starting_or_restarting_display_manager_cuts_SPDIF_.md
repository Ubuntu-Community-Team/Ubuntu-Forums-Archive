---
title: "Starting or restarting display manager cuts SPDIF optical audio out"
date: 2014-12-02
forum: Mythbuntu
---

### Post by brianwc on 2014-12-02
Hi,

New to Mythbuntu but have used LinHes, Knoppmyth, and Ubuntu for years. I had this same hardware working fine under LinHes, but prefer Ubuntu to Arch and so recently made the switch. First problem:

Every time I boot Mythbuntu, the audio (I use SPDIF optical audio out) is muted / not working, but all I have to do is go to the Setup|Audio screen and do anything there (I don't even change the settings from ALSA:default) and it starts working again. I've learned that simply restarting the display manager, lightdm, also recreates this problem, and I have to again go back into Setup|Audio to get audio working again. Any ideas what could be causing this? I had a lot of trouble getting audio working at all because it seems like it wants to use HDMI out or detects my two tuner cards as audio devices as well. Now it works, it just requires jumping through this weird hoop on every boot. Thanks for any advice.

From lshw:

```
          description: Multimedia audio controller
          product: CK804 AC'97 Audio Controller
          vendor: NVIDIA Corporation
```

---

### Post by Lester_Burnham on 2014-12-03
Hi,
Try going into the frontend setup>audio and instead of ALSA:default select the other options and look at the bottom of the screen to see if it says connected device blah blah. 
First I'd try the iec958 one.
Lester

---

### Post by brianwc on 2014-12-11
Yeah, the only ones that produce any sound are the ALSA:default and the ALSA:sysdefault:CARD=CK804 ones. I switched to sysdefault and still lose sound any time the display manager is restarted or on reboot.

---

