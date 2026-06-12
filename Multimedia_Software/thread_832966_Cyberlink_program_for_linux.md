---
title: "Cyberlink program for linux"
date: 2008-06-18
forum: Multimedia Software
---

### Post by Milardo on 2008-06-18
Does anyone know how to compile this program?


[http://www.cyberlink.com/english/products/powercinema/pcm-linux/pcmlinuxgpl.jsp](http://www.cyberlink.com/english/products/powercinema/pcm-linux/pcmlinuxgpl.jsp)

---

### Post by cozmicharlie on 2008-06-18
I don't beleive this is a program.  Looks to me that this is integrated into a Linux operating systems for OEM (original equipment manufacturers).  So a company like Dell could sell a Linux computer with this integrated into the operating system.  You might try contacting the company to see if they are releasing a version for individual users.  In the meantime, you can do all this with other packages available in Linux.  If you are interested let me know what specifically you want to do and I can recommend packages that will work for you.

From the Cyberlink web site:
[COLOR="Blue"]"CyberLink Corp. (5203.TW), a world leader and pioneer in providing integrated solutions for the Digital Home, announced today that the all-in-one entertainment center PowerCinema is now available in a Linux version for OEM customers." [/COLOR]

---

### Post by xc3RnbFO8P on 2008-06-18
It is installed from Windows, it is a media center.
Works with my computer Medion 8808.
> Usage:
let's say C: is the first partition on the first harddisk hence (hd0,0) is the GRUB name of this partition and C:\boot\stage1 is the NT name of the boot file

* To make the files stage1 and stage2 bootable from NTLDR:
C:\> grubinstall -d (hd0,0) -1 C:\boot\stage1 -2 C:\boot\stage2

When stage1, stage2, menu.lst are in C:\, use the following
C:\> grubinstall -d C:

* To make the installer detect the install location itself:
C:\> grubinstall -a -1 C:\boot\stage1 -2 C:\boot\stage2

* To make a boot floppy in A: (B: is not supported)
C:\> grubinstall -b -1 C:\boot\stage1 -2 C:\boot\stage2 
I can start Linux Media Center by special button on my rig
and controlling  it with RF remote:

> Multimedia at the press of a button
This PC is supplied with an additional multimedia function that will enable you to play photo slideshows, video DVDs, audio CDs or MP3 files by pressing a key, without having to start the Windows® operating system. Read how you can use this &#8216;Linux Power Cinema&#8217; program in the following section.&#8727;

SWITCH POWER CINEMA ON
You will start the Linux Power Cinema application with the multimedia button (N2) when the PC is switched off. The user interface, which you will be able to operate with the aid of the remote of the multimedia keys, will appear after a short time.

It is possible to leave the application in three ways: 1. Press the On/Off switch (N1) of the PC briefly. or or 3. Select the &#8216;Switch Off&#8217; menu point. 2. Press the On/Off button on the remote control.

---

### Post by aeiah on 2008-06-18
i think its only going to be prevelant in the new media centres that will start coming out. one of the big drawbacks was that anyone selling pre-built linux media centres couldnt enable dvd playback.


edit: this post became rather redundant once ringi posted ;)

---

### Post by Milardo on 2008-06-20
How do you install the program via windows exactly? Can't you just start the program from linux by just clicking  on it? This would help out many linux users I think.

---

