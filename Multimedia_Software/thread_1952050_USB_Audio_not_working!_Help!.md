---
title: "USB Audio not working! Help!"
date: 2012-04-03
forum: Multimedia Software
---

### Post by lJ9%3MR&gt;sa on 2012-04-03
I have a cheap USB audio card I bought from amazon. It works fine in Windows and plays music and youtube audio great. But in Xubuntu, nothing plays at all! Please help! :confused::confused::confused:

---

### Post by megabuffen on 2012-04-03
What version of Ubuntu are you using? What's the name and brand of the audio card?

You might want to try System -> Administration -> Additional drivers.

---

### Post by lJ9%3MR&gt;sa on 2012-04-03
> **megabuffen said:**
> What version of Ubuntu are you using? What's the name and brand of the audio card?
 
You might want to try System -> Administration -> Additional drivers.
 
I'm not currently at the computer I'm having problems with, but it is running Xubuntu 11.10. It's a generic "3D Sound" USB card. Link to it: [http://www.amazon.com/Virtual-5-1-surround-External-Sound-Card/dp/B000N35A0Y/ref=sr_1_1?ie=UTF8&qid=1333491442&sr=8-1](http://www.amazon.com/Virtual-5-1-surround-External-Sound-Card/dp/B000N35A0Y/ref=sr_1_1?ie=UTF8&qid=1333491442&sr=8-1)
 
It's not that great, but it's great for watching YouTube. On Windows, it had some static in it sometimes but not all the time. I may not be at the computer next time you post. But I'll try to reply when possible.
EDIT:
Also, there is no driver available in "Additional Drivers" for any audio device.

---

### Post by Rodney9 on 2012-04-03
Pavucontrol will help you select whatever sound your using

> sudo apt-get install pavucontrol

PulseAudio, previously known as Polypaudio, is a sound server for POSIX and WIN32 systems. It is a drop in replacement for the ESD sound server with much better latency, mixing/re-sampling quality and overall architecture.

PulseAudio Volume Control (pavucontrol) is a simple GTK+ based volume control tool (mixer) for the PulseAudio sound server. In contrast to classic mixer tools this one allows you to control both the volume of hardware devices and of each playback stream separately. It also allows you to redirect a playback stream to another output device without interrupting playback.

Rodney

---

### Post by lJ9%3MR&gt;sa on 2012-04-06
> **Rodney9 said:**
> Pavucontrol will help you select whatever sound your using



PulseAudio, previously known as Polypaudio, is a sound server for POSIX and WIN32 systems. It is a drop in replacement for the ESD sound server with much better latency, mixing/re-sampling quality and overall architecture.

PulseAudio Volume Control (pavucontrol) is a simple GTK+ based volume control tool (mixer) for the PulseAudio sound server. In contrast to classic mixer tools this one allows you to control both the volume of hardware devices and of each playback stream separately. It also allows you to redirect a playback stream to another output device without interrupting playback.

Rodney
Thank you! Thank you!! Thank you!!! I downloaded that and opened it with ALT+F2 and typed in pavucontrol. It opened and I just messed around with it and with the controls under the volume icon on the menu bar! THX again!

---

### Post by ldcdc on 2012-04-15
> **Rodney9 said:**
> Pavucontrol will help you select whatever sound your using

Just wanted to say a big THANK YOU! My USB card was running as 2.1, even though it's a 7.1. Pavucontrol made it real easy to change this.

---

