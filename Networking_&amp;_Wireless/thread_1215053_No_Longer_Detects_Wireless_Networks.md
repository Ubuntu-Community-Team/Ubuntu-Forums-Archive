---
title: "No Longer Detects Wireless Networks"
date: 2009-07-16
forum: Networking &amp; Wireless
---

### Post by EmptySkies on 2009-07-16
I'm quite new to using Ubuntu or any type of Linux, so try to explain things in simple terms, if you can.  

I have Ubuntu 9.04 installed on my netbook, and it was working fine until I literally one day turned it on, with it being fine the previous day, and it said no networks were detected.  All the obvious things have been checked, such as making sure the wireless is on and that the security keys were entered properly.  

Also, prior to today I was still able to connect using Windows, but now again no networks are found.  I assume this means there's something wrong with the wireless card or something.  I'm using a Lenovo s10.

What should I do to find/solve the problem?

---

### Post by dimeotane on 2009-07-18
I'm assuming rebooting didn't help.   That's what I needed to do. 
Does the card still work in windows?

My netbook is so finicky in ubuntu still I'm thinking I need a dual boot (as much as I hate windows).  I'm still only testing ubuntu off a USB drive.

I'm getting dropped connections with the Atheros AR9285.

---

### Post by EmptySkies on 2009-07-18
Correct, rebooting did not work.

The card did work in windows when the problem first appeared in Ubuntu, but now I'm afraid it's not working in Windows either.  I'm not sure what to do, is there a way to like...detect if the computer knows the card is there?  Or can I reset the car or something?

---

### Post by Crafty Kisses on 2009-07-18
What are the results of the following?
```
lspci
```

---

### Post by RedSingularity on 2009-07-18
You may not have the drivers installed in ubuntu.  I doubt it had an effect on your windows install at all.

As said above....post the output of lspci.

---

### Post by EmptySkies on 2009-07-18
result of lspci:

   00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
  
  00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
  
  00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
  
  00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
  
  00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
  
  00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
  
  00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
  
  00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
  
  00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
  
  00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
  
  00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
  
  00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
  
  00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
  
  00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
  
  00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
  
  00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
  
  00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
  
  02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
  
  05:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

---

### Post by RedSingularity on 2009-07-19
Ok, before we do anything else did you look in System>Admin>Hardware drivers, to see if you can activate the drivers for the card?

---

### Post by EmptySkies on 2009-07-19
> **Shadow121 said:**
> Ok, before we do anything else did you look in System>Admin>Hardware drivers, to see if you can activate the drivers for the card?

Broadcom STA wireless driver is "activated and currently in use."

---

### Post by RedSingularity on 2009-07-19
Ok good you have Drivers then.  Is your wireless card turned on?  There is usually a key combo or a switch to turn the card on.  When it is _on_ there will be a light that will glow on the netbook itself.

---

### Post by EmptySkies on 2009-07-19
Oh wow I feel dumb now; I think that's it.  I was preoccupied with the idea of there being a little physical switch without realizing there could be a key combination for it.  And there is a light off that typically is on.

It seems like I need to press Fn+F5, but it's not working; do I have to do it at a certain time like during startup or something?

---

### Post by RedSingularity on 2009-07-19
The light is not changing?  Try pressing it and reboot.  If nothing press it again and reboot again.  See what happens.

---

### Post by EmptySkies on 2009-07-19
Thanks a bunch, Shadow; I've got it.  There was a button next to the power button that I had to press before doing Fn+F5.

It's all working now.  It was a pretty simple problem, actually; I'm just not great at this stuff haha.
[]("http://ubuntuforums.org/member.php?u=677095")

---

### Post by RedSingularity on 2009-07-19
No problem :)

---

### Post by Lelouch Yagami on 2010-05-29
im having the same problem heres what mine has 

[FONT=monospace]00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller (rev 10)
08:05.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
08:07.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
08:0e.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 80)[/FONT]

---

### Post by Lelouch Yagami on 2010-05-29
nvm i got it to work:guitar:

---

