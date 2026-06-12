---
title: "mic doesn't want to work on HP pavillion dv1000"
date: 2012-01-18
forum: Multimedia Software
---

### Post by silverfilling on 2012-01-18
Hi all,
I'm new to ubuntu, I think it's great but if I'm not able to fix the problem with the microphone I won't be able to use skype and therefore I will need to go back to windows, and I really don't want to do that! 
I've installed ubuntu 11.04 on my machine, a laptop HP Pavillion dv1000. I've bought a brand new webcam kinobo 5, the video works but the mic not. I've also tried using a pair of headphones with microphone, but mic doesn't want to work. Sound in output is ok, put nothing in input. I've opened alsamixer from the terminal and checked that the mic is not mute and its level is at its maximum. I don't have anything in input, neither in Sound recording nor in Skype. I've tried uninstalling pulseaudio as I read that pulse audio could have some conflict with alsamixer, but nothing. I've just reinstall ubuntu 11.04 so I will be able to follow your suggestion restarting from scracth (I think I messed up a few things). Thanks in advance

---

### Post by wolfen69 on 2012-01-18
> **silverfilling said:**
> I've bought a brand new webcam kinobo 5, the video works but the mic not.

Before buying new hardware, it's important to check for linux compatibility. 

Ubuntu 11.10 has a better chance of detecting your hardware, since newer versions have more drivers included. Plus, 11.10 has a more polished version of Unity. You can try the live cd to see if it is detected.

But I'm sure an alsa guru will stop by and give some good advice.

---

### Post by silverfilling on 2012-01-18
Thanks wolfen69,
the problem is that kinobo 5 should work for ubuntu 'out of the box', as it is said on the Technical details. You can imagine how surpise I was when I discovered that the video works but the mic doesn't. I think though that the problem is with my audio card, but unfortunately as I said I'm not an expert. Thanks anyway, I can try again with ubuntu 11.10, I switched to ubuntu 11.04 because 11.10 gave me troubles with the internet wireless connection.

---

### Post by silverfilling on 2012-01-21
Hi there,
as suggested I've installed ubuntu 11.10, but I've still got the same problem, the microphone doesn't work.

---

### Post by silverfilling on 2012-01-24
[LIST=1]
[*]I've checked alsamixer, mic is not mute
[*]I'installed 'pulse audio volume control'
[*]Internal audio is set to 'Analog stereo Duplex'
[*]I opened the terminal and I wrote:

 	Code:
 	gstreamer-properties 
both are now to ALSA
[*]Then I typed
 	Code:
 	lspci 
And this is the result:
[/LIST]
ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
05:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)
05:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
05:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
05:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
05:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)


I don't know what else I can try. Please help me

---

### Post by madvinegar on 2012-01-25
In pulse audio volume control (4th tab - input) have you tried switching off completely one of the two channels (i.e. the left one)?

(You should first click on the button that shows a little lock on it so as to de-activate the two bars from moving together).

Let me know if that worked.

---

### Post by silverfilling on 2012-01-25
Hi madvinegar,
I really do appreciate your help. I've tried switching off the left channel of the input, leaving the right one to its maximum. I've also tried doing the other way around. I also have two options in input, input analog or input microphone. I've tried all these combinations but it is still not working.

---

### Post by MoreOrLess on 2012-01-25
I'm not good with input issues, but hopefully this will help someone help you: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by silverfilling on 2012-01-25
Done it, 
I've got my ALSA info uploaded and I have the http address to point you there if you want. Cheers

---

### Post by silverfilling on 2012-01-26
Sorry,
this is the ALSA output:
[http://www.alsa-project.org/db/?f=bc2734f067496953e27566e37e6218098baa5abd](http://www.alsa-project.org/db/?f=bc2734f067496953e27566e37e6218098baa5abd)

---

### Post by MoreOrLess on 2012-01-26
The only suggestion I have is playing with hdaanalyzer: [http://www.alsa-project.org/main/index.php/HDA_Analyzer](http://www.alsa-project.org/main/index.php/HDA_Analyzer)

---

### Post by neu5eeCh on 2012-05-22
Any more developments on this? 

I also have the HP Pavillion dv1000 and in all the years I've used Ubuntu, I've never gotten the internal mic to work. I can hear my voice very, very faintly (beneath lots of static) but none of the ALSA or pulse-audio tricks seem to work. The mic works just fine when I'm in the XP partition.

---

### Post by aimwin on 2012-07-01
[SIZE="3"][B][U][COLOR="Red"]I fixed the mic for dv1000 now please see the below link.

[http://ubuntuforums.org/showthread.php?t=2018599](http://ubuntuforums.org/showthread.php?t=2018599)[/COLOR][/U][/B][/SIZE]

Please help

mic, my dv1729tu, HP pavillion dv1000,
only have jack mic for external mic,

Mic work perfect under XP

doesn't work under Ubuntu any versions, 10.04, 10.10, 11.04,
including 12.04 flesh installed.

But I used 10.04 due to stability and temp sensor functions.
I run
sudo wget [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) -O alsa-info.sh && bash alsa-info.sh

and got
[http://www.alsa-project.org/db/?f=d43bed6d8faa481e0c59df0e69727d9e71b7535c](http://www.alsa-project.org/db/?f=d43bed6d8faa481e0c59df0e69727d9e71b7535c)

I have spent many hours and days, can't work out.
Try to do what is in 
[http://ubuntuforums.org/showthread.php?t=1467307&highlight=CX20551&page=3](http://ubuntuforums.org/showthread.php?t=1467307&highlight=CX20551&page=3)

changing to different setting in
gksu gedit /etc/modprobe.d/alsa-base.conf

laptop
laptop-hp
thinkpad
toshiba
hp
hp-dv5
generic
----many others ---- 
[http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568)
not all of them but many other... no luck

Which one should I used ?
===================\\
I use both skype and sound recorder to test mic.

I have installed Gnome-Alsamixer , and mic volume is at max and not mute.
I have check in Alsamixer and mic was MM, so I do press key "m" to unmute the mic, from one of libex 's tutoring.

I hope libex will be answering our problems soon.

Thank you in advance.

---

### Post by aimwin on 2012-07-06
I combind this post to the previous one.
I cannot edit the previous post any longer.

I left my mic problems as reference for my problems.

those dv1000 user who solved the mic sucessfully,
please leave comment, so we all know if it works or just luck for my machine only.
Thanks

---

