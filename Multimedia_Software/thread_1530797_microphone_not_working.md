---
title: "microphone not working"
date: 2010-07-14
forum: Multimedia Software
---

### Post by gothicboy on 2010-07-14
Hello, I have a hda-intel soundcard which is working perfectly with alsa on Kubuntu 10.4.
The only problem is the microphone.

Apparently I am not able to make it capture any sound or the sound is horrible:
- it works only in QArecord after I check the "Capture" checkbox.
-it doesn't work at all for Flash even if I Allow Flsh to use my mic
-it doesn't work at all for vmware player (I have a winxp guest os)
-in Skype for Linux it works only if I set Microphone boost to 100%, but the sound is  too weak and distorted.

In alsa mixer I have enabled all 3 Capture sliders to 100%, the Mic is at 100%, Input sources are all 3 set up as Mic.

The microphone doesn't work at all for any application if I use FrontMic instead of Mic.

Being able to use the microphone in Skype and VMware player is very important to me and it's the only thing keeping me from using linux as my main OS.

Any ideas? Thank you.

Note: I have tried Slackware and I have the same issues there too.

---

### Post by lidex on 2010-07-17
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

