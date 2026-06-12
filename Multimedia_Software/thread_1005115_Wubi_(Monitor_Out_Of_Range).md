---
title: "Wubi (Monitor Out Of Range)"
date: 2008-12-07
forum: Multimedia Software
---

### Post by EncryptedFile on 2008-12-07
I have been lurking these forums for the past hour, and 27 minutes looking for an answer to my problem, and all I've found is unanswered posts that have done nothing, but made those users who wanted to try out, and possibly switch to Ubuntu do the exact opposite.
Hopefully this is not one of those posts.

I'm trying out Kubuntu through the Wubi installer, but after the first reboot my 19" widescreen Hanns-G (HW191D) goes out of range.
In winblowze xpee it runs smoothly at 1440x900@75Hz.
Someone please help me get it running correctly so I can use Kubuntu on my desktop as I already run it on my laptop with no problems other then the monitor going out of spec for a few minutes the first time I tried installing it.

The following links are to my current system hardware.
[http://www.newegg.com/Product/Product.aspx?Item=N82E16824254005](http://www.newegg.com/Product/Product.aspx?Item=N82E16824254005) (monitor)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16813131339](http://www.newegg.com/Product/Product.aspx?Item=N82E16813131339) (motherboard)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16820145197](http://www.newegg.com/Product/Product.aspx?Item=N82E16820145197) (ram)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16819103249](http://www.newegg.com/Product/Product.aspx?Item=N82E16819103249) (cpu)

---

### Post by EncryptedFile on 2008-12-08
tried ```
$ sudo dpkg-reconfigure kserver-xorg
``` and it said xorg was not installed.

---

### Post by EncryptedFile on 2008-12-08
i have also tried
```
cd .config
sudo pico monitors.xml
```
it was blank, or didn't exist.
tried ```
gksudo displayconfig-gtk
``` gave me an error/did nothing

---

### Post by Vista1330 on 2008-12-17
I installed Ubuntu on my 17" widescreen laptop and I had the same problem>Screen being out of range. I corrected this problem by doing kind of 'twisting and turning' work...On my laptop I needid to install and download the linux 'drivers' for my Nvidia video card. When the 'drivers' where installed I restarted my laptop and there I began doing some 'twisting and turning'. 
U just need to find the monitor settings in teh main menu and TRY to change the settings to the smallest size and from there on change it to the size u like.
That solved my problem of screen being out of range

---

### Post by EncryptedFile on 2008-12-17
my problem is that as soon as Kubuntu loads up the screen immediately goes into out of range mode.
the only thing I can do is get into text only mode.
if you can tell me how to install my ATI drivers, or change my screen res. from a command line then that would probably solve my problem.

---

### Post by Willberg on 2008-12-18
Amigo, try going into text prompt (Ctrl+Alt+f1), log in, and try:

sudo apt-get install xorg-driver-fglrx

That should install the driver. Someone more knowledgeable than me might overlook your horrifically rude sense of entitlement and know what to add to your xorg config file to make it work instead of doing this/if this doesn't work.

Good luck, I guess.

Edit:

Also make sure you only have one monitor plugged in.

And also tell us what the contents of /etc/X11/xorg.conf is

sudo nano /etc/X11/xorg.conf

Ctrl+X is how you exit that program

---

### Post by EncryptedFile on 2008-12-18
finally someone who took the time to look at my post, and reply with some sort of a helpful answer.
when i get home I will try that, and reply with my results.

---

### Post by Willberg on 2008-12-18
I'm about to go to bed (New Zealand), so you're on your own for 12 hours or so (heavy sleeper). Post your xorg.conf file, and hopefully someone will be able to suggest changes. For giggles, I'm attaching mine so you can compare and contrast. G'luck.

---

### Post by EncryptedFile on 2008-12-18
> **Willberg said:**
> Amigo, try going into text prompt (Ctrl+Alt+f1), log in, and try:

sudo apt-get install xorg-driver-fglrx

That should install the driver. Someone more knowledgeable than me might overlook your horrifically rude sense of entitlement and know what to add to your xorg config file to make it work instead of doing this/if this doesn't work.

Good luck, I guess.

Edit:

Also make sure you only have one monitor plugged in.

And also tell us what the contents of /etc/X11/xorg.conf is

sudo nano /etc/X11/xorg.conf

Ctrl+X is how you exit that program

unfortunatly that didn't work.
i even tried plugging in an old 4:3 1024x768 dell lcd to see if that would work, and it still said out of range...

---

### Post by Willberg on 2008-12-18
Could ye please tell us what's in your xorg.conf file? My previous post has instructions on this.

---

### Post by EncryptedFile on 2008-12-19
> **Willberg said:**
> Could ye please tell us what's in your xorg.conf file? My previous post has instructions on this.

i don't quite know how to give it to you because I'm using the Wubi version of Kubuntu, and i cannot access the files stored in the virtual hard drive that Kubuntu runs from though windows, and Kubuntu will not give me a GUI to work with.

perhaps if there is a way to connect to an ftp, and upload my xorg.conf file through the command line i could do so as my internet is working because i can run sudo apt-get update/upgrade commands without problems.

worst case scenario i could always take a picture, and upload it.

---

### Post by Willberg on 2008-12-19
To get it across to windows...

Ctrl-Alt-F1 to get a linux terminal, no matter how pwnt your screen is.

login

cp /etc/X11/xorg.conf /host/

(You see, /host is the folder containing the drive that windows is on, it will just be in the root of C (or D or whatever) when you log on to windows again).

Or you can

sudo nano /etc/X11/xorg.conf    

To see/edit the file in linux on the terminal, and write it down/whatever.

---

### Post by EncryptedFile on 2008-12-19
ok i'll do that as soon as i get home.
hopefully once i post the xorg.conf file someone can tell me what i'm doing wrong because i already have kubuntu set up on my laptop*, and custom built secondary desktop** without any problems, and i'd really like to see how it performs on my recently built main PC***.

*
Gateway MT6452
AMD Turion 64 X2 Mobile TL-52
1596.1 MHz/1600 MHz
DDR2, PC2-5300 (333 MHz), 2048 MBytes, Nanya Technology

**
AMD Athlon 64 X2 Dual Core Processor 4800+ 1MB L2 Cache (per core 2MB total) Socket 939 Processor (2437.14 MHz)
ASRock 939Dual-SATA2 Socket 939 ULi M1695 ATX AMD Motherboard
Corsair PC-3200 DDR400 ram 2048 MB/2 Gigs
ATI Radeon x1800XT 512mb GDDR3 core:625mhz mem:1500mhz


***
AMD Phenom x4 9850 BLACK EDITION 2.5GHz 4 x 512KB L2 Cache 2MB L3 Cache Socket AM2+ 125W Quad-Core Processor
ASUS M3A79-T Deluxe AM2+/AM2 AMD 790FX ATX AMD Motherboard
CORSAIR DOMINATOR 4GB (2 x 2GB) 240-Pin DDR2 SDRAM DDR2 1066 (PC2 8500) Dual Channel Kit Desktop Memory
ATI Radeon x1800XT 512mb GDDR3 core:625mhz mem:1500mhz (going to upgrade someday, and crossfire the secondary pc)

---

### Post by EncryptedFile on 2008-12-22
```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

---

### Post by EncryptedFile on 2008-12-22
> **Willberg said:**
> I'm about to go to bed (New Zealand), so you're on your own for 12 hours or so (heavy sleeper). Post your xorg.conf file, and hopefully someone will be able to suggest changes. For giggles, I'm attaching mine so you can compare and contrast. G'luck.

what kind of video card do you have?

---

### Post by SlidingHorn on 2008-12-22
Stop bumping the thread.  Threads should only be bumped if they've not been answered within 24-48 hours.  People are trying...have patience.

---

### Post by EncryptedFile on 2008-12-22
> **SlidingHorn said:**
> Stop bumping the thread.  Threads should only be bumped if they've not been answered within 24-48 hours.  People are trying...have patience.

Thanks for the free bump.
=D>

---

### Post by EncryptedFile on 2008-12-22
[IMG]http://www.offtopic.me/uploads/1217868847312.jpg[/IMG]

---

