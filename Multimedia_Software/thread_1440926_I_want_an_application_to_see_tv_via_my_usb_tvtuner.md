---
title: "I want an application to see tv via my usb tvtuner or Pci internal tvtuner Please hlp"
date: 2010-03-28
forum: Multimedia Software
---

### Post by xrhstaras on 2010-03-28
I want an application to see tv via my usb tvtuner or Pci internal tvtuner Please hlp
I tried "Tv time television viewer" & "Me TV"  software on the new ubuntu 10 beta but nothing works ! Can't even recognise my tvtuners.
Please tell me what software to download to see tv !

I've installed on my ssd hdd the Ubuntu 10 beta and it boots in 1 second guys this is great !  I have installed also windows 7 and have no problem at all. If Linux had more serious applications i would remove it

---

### Post by realzippy on 2010-03-28
...specify your tuners!

e.g. run in terminal:

```
lsusb
```

when USB tuner is plugged in,for pci:

```
lspci
```

..and post output.
And,welcome!!

---

### Post by xrhstaras on 2011-03-14
Bus 004 Device 003: ID 05ac:8215 Apple, Inc. Bluetooth USB Host Controller
Bus 004 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 05ac:8242 Apple, Inc. IR Receiver [built-in]
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 014: ID 046d:0a0b Logitech, Inc. ClearChat Pro USB
Bus 002 Device 013: ID 058f:6254 Alcor Micro Corp. USB Hub
Bus 002 Device 012: ID 0603:00f2 Novatek Microelectronics Corp. 
Bus 002 Device 011: ID 059f:101a LaCie, Ltd 
Bus 002 Device 010: ID 0458:003a KYE Systems Corp. (Mouse Systems) NetScroll+ Mini Traveler
Bus 002 Device 009: ID 058f:6254 Alcor Micro Corp. USB Hub
Bus 002 Device 005: ID 05ac:8403 Apple, Inc. 
Bus 002 Device 003: ID 1bcf:0c31 Sunplus Innovation Technology Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 05ac:8502 Apple, Inc. Built-in iSight
Bus 001 Device 002: ID eb1a:2881 eMPIA Technology, Inc. EM2881 Video Controller
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub



I have a Pinnacle Hybrid Pctv 320 usb tv tuner recognisable my ubuntu but.....

Also the mythtv is so hard to configure ! seems impossible to use it !

Also i can't use my imac's line input and i want it like crazy cause i want to plugin my guitar.

Anyway Please help me if you can with these two issues.

---

### Post by xrhstaras on 2011-03-15
hello ?

---

### Post by BicyclerBoy on 2011-03-15
The composite capture tuner eb1a:2881 device has worked for some people for last year..but was broken after..may be the device has multiple hardware versions.
You may need the latest v4l-dvb (LinuxTV) packages (compiled).

Have you installed the non-free firmware package ? This is required for USB & internal tuners..

Output of 
lspci
for the internal PCI tuner card.
lsmod 
(after firmware install & reboot)

Search the output of 
dmesg 
for messages about tuner firmware loading, cold start warm state etc..

---

### Post by xrhstaras on 2011-03-16
lets face the truth im not gonna use my tv tuner am i?
nor my soundcard's linein.
Also i got no sound on tuxguitar a good app.
Why there arent many software for linux?, anyway
thank you for your help.

---

### Post by BicyclerBoy on 2011-03-17
The problem is this..

TV tuners (& most PC peripherals) are made (software/firmware) for windows cos it is a big market.
The firmware is not open source/free & without firmware TV tuners, wifi devices etc are just junk.
There is a lot of cheap stuff made with huge variation.

The Linux support comes from reverse engineering and/or very clever expting.
So linux will never support all hardware.
You need to pick your brands especially with TV tuner cards/webcam.
Check the lists on MythTV & LinuxTV websites.

Audio line in

Have you installed/run 
pavucontrol
try different inputs ?
The Ubuntu sound preferences has a vu meter..
alsamixer   checked for muted inputs ?

---

### Post by Chronon on 2011-03-17
I tried, without success, to get MythTV running when I was using Hardy.  These days I use Kaffeine (or sometimes SMplayer) to watch TV.

Make sure you have the non-free-firmware package that BicyclerBoy mentioned.

---

### Post by xrhstaras on 2011-03-18
i think on linutv there are some firmware.
Tell me if i can do something , if you can help with this situation.
Also i have another tv tuner anti crypto tvtuner i dont know if this can work?

---

### Post by BicyclerBoy on 2011-03-19
Install the package
linux-firmware-nonfree

You can download firmware from other sources & manually install/copy into the right folder..

If you study the 
dmesg
std output you can see if firmware is loaded etc..

If a TV tuner card is** not** listed/mentioned/discussed on LinuxTV or MythTV sites/forums, it will **not** work..

---

