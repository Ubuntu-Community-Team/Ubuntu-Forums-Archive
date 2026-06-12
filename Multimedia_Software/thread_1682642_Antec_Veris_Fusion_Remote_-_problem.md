---
title: "Antec Veris Fusion Remote - problem"
date: 2011-02-06
forum: Multimedia Software
---

### Post by bnilsson on 2011-02-06
Hi!

I got a Antec Fusion Remote computer case, with iMon remote and LCD, and Maverick 10.10.

I test the iMON part by

    sudo evtest /dev/input/event4

The volume knob works fine, and the remote mousepad also. All other buttons create an endless stream of events, sometimes stoppable by rocking the volume knob CW/CCW. Other times it hangs the computer completely. Pressing the volume up/down button makes the volume desktop symbol progress bar race to top and then flashing wildly.

I have not installed lirc(yet).

Have anybody else seen this, and is there any cure?


BN

---

### Post by bnilsson on 2011-02-08
Dumping Ubuntu 10.10 and installing Ubuntu 10.04 solved the issue.
Now everything (afaics) works as described in the different web sources I have found. I have adapted XBMC so that it responds to remote control commands.

I will just have to wait until the imon kernel driver is fixed in 10.10.

BN

---

### Post by bnilsson on 2011-05-21
Upgrading to Natty and replacing the hardware solved my problem.

---

### Post by MikeDK on 2012-04-15
Which hardware did you change? and does everything work under 11.04 or have you upgraded to 11.10 since?

kind regards mikedk

---

