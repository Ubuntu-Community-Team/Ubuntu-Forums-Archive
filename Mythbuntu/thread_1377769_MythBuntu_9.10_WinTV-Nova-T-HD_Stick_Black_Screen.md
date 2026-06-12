---
title: "MythBuntu 9.10 WinTV-Nova-T-HD Stick Black Screen"
date: 2010-01-10
forum: Mythbuntu
---

### Post by eclipse2009 on 2010-01-10
[LEFT]Hi all, 

First post in these forums. Been a windows users since uni and have been playing / learning to use Mythbuntu over the last week or so. I am living in spain where they have DVB (TDT digital Terrestrial). 
I have installed Mythbuntu 9.10 with a  a Hauppauge WinTV-Nova-T-HD Stick (USB) model 351 on a compaq laptop with 498MB RAM and a Pentium Celron Processor. 30GB Harddrive.

Current Problem: Getting a black screen when trying to view LiveTV with the OSD saying :
Signal 72% BE 0 (LMs) Partial lock when viewing using MythTVFrontend on the primary backend.

Any ideas? Should I try a different USB tuner, any recommendations?

Notes:
--------
Getting the channels to detect only worked after manually creating all the Transports and doing a scan of them. Doing a full scan never found them.

I have tried the USB stick on a windows box and it locks and watches the channels without any problem.

I tried earlier this week to install Mythbunto with Myth .21 and had the same problem.
Getting the WinTV Stick to register took adding:

options dvb_usb_dib0700 force_lna_activation=1

In /etc/modprobe.d/options

(the file was empty before i added that line is that correct?)

Any help would be greatly appreciated. Thank you in advance.


[/LEFT]

---

### Post by SiHa on 2010-01-11
In 9.10, the modprobe options file now needs a **.conf**, so it would now be **/etc/modprobe.d/options.conf**.

Does that help?

Although at 72%, signal strength is probbaly not the issue.

---

### Post by eclipse2009 on 2010-01-13
I've got it working. Turns out my amplifier on in the roof for the TV signal was on the fritz, the television worked correctly 90% of the time and on the odd occasion wouldn't find a channel. Had the electrician review the signal and we found the cause. So now it is working on the mythtv frontend. 

Thank you for your help.

---

### Post by deflagmator on 2010-03-31
Hello Eclypse,

Good work, can you confirm that the WinTV-Nova-T-HD Stick works out of the box?

I found that the WinTV-Nova-T Stick **(NO HD)** is supported but nothing except your thread about the **HD version**.

I have to recommend it to a new linux user ;). I your confirmation will be very appreciated.


As a note:
 I have one Hauppauge Nova-T 500 and works perfectly since Karmic, remote and everything.


(I only had to add the options dvb_usb_dib0700 force_lna_activation=1 on the modprobe options)

Thanks in advace for your reply.

---

### Post by eclipse2009 on 2010-04-01
Hi, Yep worked out of the box.

---

### Post by deflagmator on 2010-04-01
Thanks

---

