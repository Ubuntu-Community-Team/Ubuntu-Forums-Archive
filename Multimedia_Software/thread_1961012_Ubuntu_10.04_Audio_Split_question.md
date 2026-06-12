---
title: "Ubuntu 10.04 Audio Split question"
date: 2012-04-18
forum: Multimedia Software
---

### Post by neuman1812 on 2012-04-18
Is it possable to set the audio output specific to the program?

What I would like to do is set Totem to output to my analogue speakers ..watching movies, but have other applications like Skype to output to my USB Headset/Mic

---

### Post by papibe on 2012-04-18
Hi neuman1812.

Indeed, it is possible.

Doing it manual, it's pretty simple: you just change the default output on 'Sound Preferences' before opening a program.

To design a more permanent solution, I would recommend studying the command 'pacmd'. Also take a look at this [thread]("http://ubuntuforums.org/showthread.php?t=1845855&highlight=pacmd") with solutions to a similar concern.

I hope that point you in the right direction. Tell us how it goes.
Regards.

---

### Post by neuman1812 on 2012-04-18
> **papibe said:**
> Hi neuman1812.

Indeed, it is possible.

Doing it manual, it's pretty simple: you just change the default output on 'Sound Preferences' before opening a program.

To design a more permanent solution, I would recommend studying the command 'pacmd'. Also take a look at this [thread]("http://ubuntuforums.org/showthread.php?t=1845855&highlight=pacmd") with solutions to a similar concern.

I hope that point you in the right direction. Tell us how it goes.
Regards.

Would you happen to know if totem has the Sound preferences option?  I found after starting it that i can change the type...analogue 4 channel 5 channel....etc   but nothing to change the hardware used.

---

### Post by papibe on 2012-04-18
I don't know, but VLC does. 

Anyway, I meant the system's Sound Preferences. For example: I have two mics, an integrated-webcam-mic, and the motherboard's. Before I initiate a Skype chat, I can set on Sound Preferences what mic to use.

Regards.

---

### Post by BicyclerBoy on 2012-04-18
I think that pulse audio can save/re-apply audio setups per application..

Install/run pavucontrol
run your audio apps.
select each audio app (running) in pavucontrol & set the (input &) output device.

Apps that can go direct to any audio device (VLC, mplayer mythtc XBMC) can be setup internally to do anything..

Totem & skype most like just use the default pulse audio devices..

---

