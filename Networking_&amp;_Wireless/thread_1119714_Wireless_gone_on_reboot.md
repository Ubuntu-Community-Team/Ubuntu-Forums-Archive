---
title: "Wireless gone on reboot"
date: 2009-04-08
forum: Networking &amp; Wireless
---

### Post by stim on 2009-04-08
I have two identical laptops with 8.10.  Both Dell Vostro 1000's.  I just installed 8.10 yesterday on the second one, and have been using 8.10 on the first one for a few months now(with zero problems). 

After installation on the second machine, the wireless was detected as proprietary and I was prompted to activate the proprietary driver and restart.  At this pointmy wireless was working well.  I then proceeded to download the several hundred megabytes of updates that naturally are required or a new install. 


 I finished updating and shut down last night, restarted this morning and when I click on the network manager icon(the two computers).... no wifi. Just vpn and auto eth0.

How can one machine work just fine and the other lose wireless after reboot?
The working computer detects the hardware as:

Broadcom Wireless STA Driver

Does anyone know how to force re-detection of hardware drivers?

I have been using Ubuntu for a few years and have experience getting wireless to work since 6.06.I don't doubt that I can do it in a few minutes with ndiswrapper, but I would prefer it to 'just work', as I am giving this computer to someone else. I just dont understand why it worked and then stopped......any input is valuable and appreciated!!:mad:

---

### Post by Sam Lars on 2009-04-09
Have you tried more reboots?
If it still doesn't work, try
```
sudo modprobe wl
```
in a terminal.

---

### Post by superprash2003 on 2009-04-09
have you tried disabling and enabling it again?"

---

### Post by stim on 2009-04-09
I would if I could..... the problem is that it no longer shows up in  the  restricted drivers/hardware drivers window.

The computer was one I was prepping for someone else.  They already have it so I will get the opportunity to work on it tonight.  I will let you know what comes of it.  Thank you all for your help!!!

---

