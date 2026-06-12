---
title: "No Sound in Dual boot Ubuntu 14.04 after windows upgrade"
date: 2014-08-07
forum: Multimedia Software
---

### Post by Puneet_Agarwal on 2014-08-07
I have HP ZBook 14, configured as dual boot with Windows 7 and Ubuntu 14.04.
Speakers used to work fine in Ubuntu. 


Yesterday I booted through Windows, and installed MS Office 2010.
Later microsoft upgrade came, I installed the upgrades also.


After that when I booted through Ubuntu the sound is not working.
again booted through Windows and found that speakers work fine through windows.


But not through Ubuntu.


Please suggest, what can I do to get Speakers working again.




-Puneet

---

### Post by slooksterpsv on 2014-08-08
Do you have HDMI on your system? If so, check your sound settings on Ubuntu and make sure HDMI is not the default and or that the sound isn't muted. And make sure nothing's plugged into the audio jack.

---

### Post by Puneet_Agarwal on 2014-08-08
Thanks for the reply.

How to check that? usnig "aplay -l"
No output of this command, the terminal hangs...

---

### Post by Puneet_Agarwal on 2014-08-08
aplay -l worked

**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA Intel HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 0: 92HD91BXX Analog [92HD91BXX Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: HDMI_1 [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: HDMI_1 [HDA ATI HDMI], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


Following is what I have understood / observed

1.  if I run vls once aplay -l stops working

2.  Output of pacmd --> Daemon not responding

3.  output of pulseaudio:

E: [pulseaudio] pid.c: Daemon already running.
E: [pulseaudio] main.c: pa_pid_file_create() failed.


4.  I tried pulseaudio --kill and then pulseaudio --start - below is what I got

pulseaudio --start
N: [pulseaudio] main.c: User-configured server at {dd4f877cced7ab34d4280f0f53d187aa}unix:/run/user/1000/pulse/native, which appears to be local. Probing deeper.



My OS: Ubuntu 14.04 (with dual boot for Windows 7)


Please help me in resolving this.

---

### Post by Puneet_Agarwal on 2014-08-08
My Alsa-Info.sh output is here - [http://www.alsa-project.org/db/?f=d92a8b39a24a7c4900b7ad5d59b5829f4ade784d](http://www.alsa-project.org/db/?f=d92a8b39a24a7c4900b7ad5d59b5829f4ade784d)

please help

---

### Post by Puneet_Agarwal on 2014-08-11
I have no other choice...I have formatted my machine

Hope this time it works fine. Too bad could not find any solution.

---

### Post by Puneet_Agarwal on 2014-08-12
I re-installed the OS

Youtube was working fine.

then I installed SMPlayer  - it worked fine.

then I opened settings tab the SMPLayer got hung. Ever since then even the youtube in browser is not working and also the videos on local machine through SMPlayer

Someone please help.

---

### Post by JDorfler on 2014-08-12
When you are going from Windows to Ubuntu are you just rebooting or are you shutting all the way down, then turning it on?  Your best bet, due to firmware issues is always shut all the way down before picking another OS.  Firmware seems to stick in there on some pieces of hardware when using restart.

---

### Post by Puneet_Agarwal on 2014-08-13
Yes, I have always been shutting down the OS.

I re-installed Ubuntu 14.04, and problem persisted.
Next - I re-installed Ubuntu 14.04.1 - problem seem to have gone. So far its working.

If it does not work, I will come back here.

---

### Post by n.chatzi on 2015-03-04
I have the same computer: HP zBook14 and the same issue, with the same outputs.
I was using Ubuntu, latest version, and now I'm on Ubuntu Studio.
The audio works on certain boots but most of the time does not.
Any suggestions?

---

