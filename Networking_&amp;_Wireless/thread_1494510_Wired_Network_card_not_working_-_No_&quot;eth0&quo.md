---
title: "Wired Network card not working - No &quot;eth0&quot;"
date: 2010-05-27
forum: Networking &amp; Wireless
---

### Post by rollin77 on 2010-05-27
I recently installed Ubuntu 10.04 on an older PC and I'm having problems with the network card built into the motherboard.  When I connect an ethernet cable into the ethernet port I get a solid amber light, and I can't connect to my router, (which is being directly connected).  Nothing is shown in Network Connections, but on another PC with the same version of Ubuntu it shows "Auto eth0", and it works just fine connecting with the router.

How do I fix this?  I'm an Ubuntu noob so I'm not really sure what to do here.

The network card is an **Intel 82547EI Gigabit LAN controller**, and Intel's website offered a driver available for my kernel version of Linux.  However I was typing everything it told me to do in terminal, (which half the time I have no clue what I'm typing actually means), but I ended up getting some errors towards the end of the install process.  I'm not sure if I messed something up or the driver just isn't going to work.  

I'm hoping there is an easier fix for this, I've been searching the net all night trying to find someone with a similar problem and I haven't found any.  I think I have another ethernet card which I might pop in and see if that works....but I figure I'll most likely run into the same problem because I know for sure the motherboards network card works - has on Windows, I just can't get it working in Ubuntu.

---

### Post by v1ad on 2010-05-27
can you show us the installation manual and on what steps you are getting the error on.

---

### Post by rollin77 on 2010-05-28
I don't know what you mean by installation manual.  This was a full  install by the way, no other OS is installed on the computer.

---

### Post by chili555 on 2010-05-28
This is supposed to use the module *e1000* which is already built in. If it isn't loading, something else may be wrong. Let's try to load it and ask the kernel what's wrong. Open a terminal and do:```
sudo modprobe e1000
dmesg | grep e100
```Please post the result.

---

### Post by rollin77 on 2010-05-28
> **chili555 said:**
> This is supposed to use the module *e1000* which is already built in. If it isn't loading, something else may be wrong. Let's try to load it and ask the kernel what's wrong. Open a terminal and do:```
sudo modprobe e1000
dmesg | grep e100
```Please post the result.
Nothing happens when I entered those in the terminal.  I might do another install of Ubuntu and see if it works, it took 3 tries to get it to install with other random problems occurring, so maybe I need to cross more fingers this time lol

I do believe I had the same networking error message during the installation during the 2nd install, so I don't think re-installing  will solve this problem.  But if I can't find a fix by tonight it wouldn't hurt either.

---

### Post by rollin77 on 2010-05-28
Ok I just ran from the install disc and went to "recover a broken PC", which basically goes through the install process again.  Here is the exact error message I received when it tries to detect a network interface:

> No network interface detected
No network interfaces were found.  The installation system was unable to find a network device.
[LEFT] 
You may need to load a specific module for your card, if you have one.  For this, go back to the network hardware detection step.[/LEFT]


By module does it mean it needs Linux drivers?

---

### Post by Joe Awsome on 2010-05-28
Yes module does mean driver in ubuntu, I'm also having a similar problem with an old gateway solo 9300. I've got no integrated network card on the darn thing so I have to use PCMIA ethernet cards for the netwrok connection (I'm running lubuntu 10.04 beta 10), but none of the cards i try work when put in, I even tried a usb-ehternet adapter just to make sure I didn't bend a pin or something. They also worked fone before i lent it to the school IT guy, who didn't even have the password to log-on I think (i left him a note, don't think he got it though). Any sugestions?

---

### Post by chili555 on 2010-05-28
> By module does it mean it needs Linux drivers?Yes, in this case, e1000.

---

### Post by rollin77 on 2010-05-28
So what do I do when it says "go back to the network hardware detection step".  I have already downloaded the driver, but this step doesn't have any option to let me load my own drivers.

Any idea on how to install the driver?  I already tried doing it via the readme file included with the driver, but it had me punching in a bunch of commands in terminal and ultimately it didn't work.

Is there an easy way to do this?

---

### Post by chili555 on 2010-05-28
Please run:```
lspci -nn
```Post only the part relevant to your Intel 82547EI and we'll troubleshoot.

---

### Post by rollin77 on 2010-05-29
> **chili555 said:**
> Please run:```
lspci -nn
```Post only the  part relevant to your Intel 82547EI and we'll troubleshoot.

^ This is what I get:
```
00:00.0 Host bridge [0600]: Intel Corporation 82875P/E7210 Memory Controller Hub [8086:2578] (rev 02)
00:01.0 PCI bridge [0604]: Intel Corporation 82875P Processor to AGP Controller [8086:2579] (rev 02)
00:06.0 System peripheral [0880]: Intel Corporation 82875P/E7210 Processor to I/O Memory Interface [8086:257e] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 [8086:24d2] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 [8086:24d4] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 [8086:24d7] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 [8086:24de] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller [8086:24dd] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev c2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge [8086:24d0] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller [8086:24db] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller [8086:24d3] (rev 02)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller [8086:24d5] (rev 02)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV350 AR [Radeon 9600] [1002:4152]
01:00.1 Display controller [0380]: ATI Technologies Inc RV350 AR [Radeon 9600] (Secondary) [1002:4172]
02:03.0 FireWire (IEEE 1394) [0c00]: VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller [1106:3044] (rev 80)
02:0a.0 Multimedia audio controller [0401]: VIA Technologies Inc. ICE1712 [Envy24] PCI Multi-Channel I/O Controller [1412:1712] (rev 02)
```It doesn't even show the LAN controller.  I've never had problems with it under Windows either, Ubuntu just doesn't seem to be able to see it for some reason.

---

### Post by chili555 on 2010-05-29
> It doesn't even show the LAN controller.Quite correct. Please post:```
dmesg | grep -i warn
dmesg | grep -i error
```You might also look around in the BIOS to see if there is a setting you can change to get the LAN recognized.

---

### Post by rollin77 on 2010-05-30
God I feel stupid...for some idiotic reason I must have turned the LAN controller off in BIOS, because that was all it was!  It's working perfectly fine now...pebkac strikes (me) again again...8-[

Thanks a ton for your patience and help chili555!

---

### Post by bobd27 on 2010-05-30
Hi, I'm having a similar problem. My old HP pavilion ze1110 works fine with everything up to Lucid. Once I reboot after install the net drops out. I'm using a belkin F5D5050 USB adapter which was working fine. I've tried to check the BIOS but all I can see are a date and time control, processor and memory info, noting else. I don't have a disk to reinstall from yet. This is the second time this has happened. I also got the "No network device detected" warning. what's going on? Is my machine just too old?
Thanks

---

### Post by chili555 on 2010-05-30
> **bobd27 said:**
> Hi, I'm having a similar problem. My old HP pavilion ze1110 works fine with everything up to Lucid. Once I reboot after install the net drops out. I'm using a belkin F5D5050 USB adapter which was working fine. I've tried to check the BIOS but all I can see are a date and time control, processor and memory info, noting else. I don't have a disk to reinstall from yet. This is the second time this has happened. I also got the "No network device detected" warning. what's going on? Is my machine just too old?
ThanksAs this has nothing to do with an Intel wired ethernet card, I'd suggest you start a new thread. Please post:```
lsusb
```Thanks.

---

