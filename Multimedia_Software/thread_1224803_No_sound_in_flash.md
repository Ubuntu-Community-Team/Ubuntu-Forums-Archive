---
title: "No sound in flash"
date: 2009-07-27
forum: Multimedia Software
---

### Post by TEH BE3F on 2009-07-27
Hello,

Ive recently installed Ubuntu onto 3 of my home computers, an IBM laptop, a Compaq desktop and my Packard Bell desktop, at first, none were playing sound on youtube and other flash apps but after some messing around with them, i managed to get it to work on the first 2 computers mentioned but not on mine, i have spent 12 hours today (no joke) searching for a way to fix that on mine. Ive tried everything, searching the web for fixes, switched between comps to find any differences but no luck. The only difference between my computer and the others that i think could matter is that it is an AMD while the others are all Intel computers.

I have tried almost all the approaches shown on the web, ive reinstalled adobe over and over again trying different methods of installing and different files, rebooting my computer and trying again.

And what bugs me the most is that i think i had it working when i was running Ubuntu alongside windows.

Is there anything that you think could help me to get this to work?
I've an AMD Athlon XP 2000+ 
running Ubuntu 9.04 (Jaunty Jackalope)
Firefox 3.0.12
Flash Player 10
And my audio card is a C-Media CMI8738

---

### Post by igorzwx on 2009-07-27
I solved all such problems with OSS4
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

check if you hardware is supported by OSS4
**Does OSS Support My Hardware?**

 Check the list [here]("http://mercurial.opensound.com/?file/6bf18b4a87d6/devlists/Linux"). Some devices may not have full functionality (e.g. the X-fi module is limited to stereo output at the time of this writing, and jack sensing may not work on Azalia-compliant "High-Definition" devices, which are very common on motherboards and laptops today). If you're in doubt, consult the "Additional Support" sources found towards the end of this document.

---

### Post by TEH BE3F on 2009-07-27
doesn't support my sound card :(

---

### Post by igorzwx on 2009-07-27
try these commands

aplay -l

lspci > hardwareinfo.txt

---

### Post by TDurden1937 on 2009-07-27
Yo - Just for the heck of it I typed the commands you suggested into a terminal . . . 

00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GT (rev a1)
02:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GT (rev a1)
05:0b.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
05:0c.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)

and under Multimedia audio controller it lists "nVidia Corporation CK804" and "AC'97 Audio Controller (rev a2)." So is that "nVidia Corporation CK804" the bus that "AC'97 Audio Controller (rev a2)," is on? Just wondering 'cause when I was trying to get sound to work with quake3 linux edition this terminology came up. 'Cause I definitely know I'm using the AC'97 audio as any other device is disabled in the bios.

---

### Post by TEH BE3F on 2009-07-27
there wasnt my exact card number but i did see one which turned up in one of my earlier attempts so i used that and now it works :D

thanks for the help

---

### Post by TDurden1937 on 2009-07-27
> **TEH BE3F said:**
> there wasnt my exact card number but i did see one which turned up in one of my earlier attempts so i used that and now it works :D

thanks for the help

Good . . . not having sound sucks big time!

---

