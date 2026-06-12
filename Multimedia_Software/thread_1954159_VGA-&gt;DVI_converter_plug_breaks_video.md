---
title: "VGA-&gt;DVI converter plug breaks video?"
date: 2012-04-07
forum: Multimedia Software
---

### Post by hiro24 on 2012-04-07
I've got an NVIDIA GeForce 9800 GT which has 2 DVI ports.  Up until now, I've been running a DVI cable from it to my monitor, which is fine.  But I'm throwing a KVM in the mix.

Long story short, I need to use the KVM cable, which is a VGA cable.  So I have a VGA to DVI converter plug so it will attach.  POST and bootup shows video fine, but once I get to the login screen... nothing.  No video source.  Does anybody know what I could do to fix this?

---

### Post by BicyclerBoy on 2012-04-07
You have a DVI-A-->VGA adapter..The opposite is not a passive plug adapter..

The 2 DVI outputs on your video card might not be the same..One may be DVI-D & the other DVI-I. This is common on the older cards as it saves a RAMDAC.
DVI-D has no VGA output..& the connector pin pattern is different.

The nVidia X server only runs/loads as X starts not at boot/greeter screens.

Other possibility:
If the driver can not detect the monitor it will not activate the output.
It is most likely the KVM switch that's causing the problem.

With nVidia driver you can force any display output on by xorg.conf entries etc..

---

### Post by hiro24 on 2012-04-07
So how am I supposed to make this work then?  And how do I know if something is DVI-A, D or I?  I tried plugging it into the other port on the video card but the same thing happened.  There's nothing wrong w/ the KVM btw, I've got another linux box hooked up no problems, but it has a VGA output, not DVI.

---

### Post by BicyclerBoy on 2012-04-07
Use the internet to find pic of DVI. Wikipedia's a great start..

Can you try console login:
- when your login screen does not appear..
- <ctrl>+<alt>+<F1>
- login wuth username password..
- cp /var/log/Xorg.0.log ~/Desktop/Xorg-log.txt
- post the log file..

---

