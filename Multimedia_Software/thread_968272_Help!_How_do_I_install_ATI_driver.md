---
title: "Help! How do I install ATI driver?"
date: 2008-11-02
forum: Multimedia Software
---

### Post by Blakeman on 2008-11-02
PC guy that is clueless on Linux but trying to learn.  I have an ATI FIREGL V5600 and have downloaded the driver: ati-driver-installer-8.523.1.1-x86.x86_64.run

I have tried running this thing to install the driver, but have not succeeded.  How do I install this thing?  The downloaded file from ATI/AMD's website is on my desktop.  Thanks

---

### Post by Knoal on 2008-11-16
I'm having the same problem(ish).

I'm not sitting at my lunix box, but I downloated the auto installer from ATI (AMD)

I ran it, it opened the terminal stated to unpack and then told me I needed to have superuser access.  I had already opened a terminal and typed in sude and my password.

I've tried several varaitions of this install and nothing works for me  :-(

OH, the whole reason I'm doing this is my screen has all kind of green artifacts and a can't properly see ~15% of my screen.


TIA,

Knoal

---

### Post by MonGol on 2008-11-16
hey guys,

open a terminal, change the directory to Desktop (if the ati-driver file is saved on the Desktop) and type:
```
sudo ./ati*
``` (Yeah, we need to run the graphical installer ;-))
Just click "Continue", "I Agree" (or Accept, i dunno^^) and again "Contine" (i guess the caption of the button are these, but if not just follow the installer by continueing and agreeing anything). After a while the installer is finished and after a reboot the fglrx-driver is working fine ;-)

greez,
marcel

---

### Post by Knoal on 2008-11-16
I'll try it.

I already tried it with sudo ./entiredrivername  and that didn't work.

Maybe this will...

Will know in an hour.

Knoal

---

### Post by WWSmith36 on 2008-11-16
Please check out these useful guides for installing the proprietary ATI drivers

For Hardy
[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

For Intrepid
[http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide)

---

### Post by sirthorn on 2008-11-17
> **WWSmith36 said:**
> Please check out these useful guides for installing the proprietary ATI drivers

For Hardy
[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

For Intrepid
[http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide)

Is this still the preferred way for Catalyst 8.11? I read this in the announcement of 8.11:

> KNOWN ISSUE: (1) Installing the driver on Ubuntu systems using the community-supported Ubuntu packaging mechanism leads to a failure to load the kernel module resulting in 3D acceleration being disabled. Please install this driver release using the interactive installer instead.

But I don't find it in the PDF that's linked from the [Driver Update Notification feed]("http://ati.amd.com/online/rss/atilinuxdriver.rss?OTC-rssfeedlinux"); it's only in the announcement itself. :confused: Can anyone confirm or deny the accuracy of this?

---

### Post by Knoal on 2008-11-20
What one really needs to install ATI Catalyst in ENVY, auto installer.

Find it here

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

Worked fer me.....


knoal

---

### Post by LaserCobra on 2008-11-26
I've been having a lot of driver trouble overall with Ubuntu. My latest challenge is the new box I built with an ati X800 card. The fresh install resulting in perfect resolution but video playback was pegging the 2GHz P4 it's running. Things like YouTube and standard def DVD's were choppy most of the time. I've searched and see there are some known issues with YouTube playback but the cpu spike lead me to believe my default drivers were not allowning this card to step in and take the burden off the cpu. I tried ATI's drivers which resulted in low res options. I tried the restricted driver available under the hardware driver section within administration. I tried envy but think I missunderstood it's use. I also tried the tutorial here for the open source ati drivers. Since my first "try" the system will boot and prompt low graphics mode with the option to fix. No matter what I do, I can't get a good res back.

I, like most here, am relatively new at Linux so I need some guidance if possible.

Question:

Is there a way to cleanly undo everything so I'm sure there are no conflicts as a result of my exploring?

Am I correct in expecting better graphic performance from a system that works fine under Windows? P4 2.0GHz, 512MB mem, and ati X800. I mearly want a decent standard def HTPC.

Where should I go from here? Restricted drivers, open drivers, other drivers, etc?

---

### Post by Bablefish on 2008-11-26
Reinstall your OS

---

