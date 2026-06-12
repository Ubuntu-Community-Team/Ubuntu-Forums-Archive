---
title: "Wireless card is on but is showing as &quot;Disabled&quot;"
date: 2009-01-21
forum: Networking &amp; Wireless
---

### Post by Budd Manlove on 2009-01-21
I tried to follow the instructions shown inside of the help section on Ubuntu. I'm completely new at this and I've never even tried a different OS other than Windows before now. 

In the help sections it says: 
[I]
3.3.1. Check that the device is on[/I]

So I check that it's on, even go back to Windows to double check. Yep all gravy, going to step two.

*3.3.2. Check for device recognition*

I type in the command and find:

Network:0 DISABLED
Network:1 DISABLED

The first is my wireless and the second is the Ethernet interface. 

I check back on the troubleshooting to find:
[I]
4. Disabled - see Section 3.3.1 -- Check that the device is on. [/I]

Sorry if I sound super newb but I'm lost here. I tried to dig through the forums but can't find anything pertaining to my situation.

---

### Post by damis648 on 2009-01-21
What model wireless chipset do you have? Post the output of
```
lspci
```

---

### Post by Budd Manlove on 2009-01-21
Took me a minute to figure out how to get the information from the other computer to this one. Here we go:

budd@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc M52 [Mobility Radeon X1300]
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
0b:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
budd@ubuntu:~$

---

### Post by damis648 on 2009-01-21
```
0b:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
```
There is our little bugger. :popcorn:

If you can connect to a wired network, all you have to do is visit System>Administration>Hardware Drivers and enable the Broadcom STA Wireless Driver.

---

### Post by Budd Manlove on 2009-01-21
Well I hooked up my computer to a wired network (I guess that is what you meant) and went to the menu you instructed. However, it just states:

"Proprietary drivers are being used to make this computer work properly"

I don't even see my network card in this section, only some weird "w|" thing and my video card.

---

### Post by damis648 on 2009-01-21
Okay, try first clicking the NM-Applet in the upper right hand corner of your screen (by the volume applet) and make sure you see no wireless networks when you do so. If no wireless networks are visible, then try this:
Open System>Administration>Software Sources and make sure all the boxes are check on the first tab, as well as the 'Third Party' tab. Click close and then let it reload (you will need to be connected to wired network). Now see if anything shows up in the drivers menu.

---

### Post by Budd Manlove on 2009-01-21
Dear damis648,

I regret to inform you that I have run away. After you fixed my disgusting situation with my wireless network card, I fell in love with you. For that, I know that we can never be as one. I have gathered my belongings, cusp my Ubuntu laptop w/ wireless network, and fled into the night. You will forever have my heart my little Einstein.

With love,
Budd Manlove

---

### Post by Budd Manlove on 2009-01-21
No really, thanks a lot. I really appreciate your help.

---

### Post by JBonzo on 2009-01-22
Hello.  I'm in the process of switching over from XP and very happy so far, except that I have no networking in Ubuntu yet.  I'm running Intrepid on a Dell Vostro 1500 (with Broadcom).

I have the same problem with my wireless card, and my output from lspci contains the exact same Broadcom line mentioned above.  Unfortunately, my wired networking does not work either (lshw -C network shows it as DISABLED also).  In XP, wired & wireless both work.  I have been looking through the forums for a while and I have tried several things, but so far no change at all.

I have noticed (among other things) that ifdown returns "interface <interface> not configured" for every interface I've tried.  (Similarly, ifup returns "Ignoring unknown interface <interface>=<interface>" for everything).  I'm guessing that /etc/network/interfaces should have more than two lines, but I don't know enough to configure the interfaces manually if that's how I would have do it.

Any suggestions?  Thanks.

---

