---
title: "HELP! My wireless card has suddenly died!"
date: 2010-12-13
forum: Networking &amp; Wireless
---

### Post by ve4cib on 2010-12-13
I'm the owner of an HP dv6000-series laptop with a Broadcom b43xx wireless card that -- up until this evening -- was working just fine under 10.04.  Everything is up-to-date as of about 2pm CST today.

I shut down my computer sometime this afternoon, turned it back on this evening, and I cannot connect to any wireless networks at all.  nm-applet doesn't list any wireless networks and the "Hardware Drivers" utility doesn't even list my wireless card.  I've tried reinstalling the broadcom drivers, but to no avail.

I know the problem is not with the router, as my smartphone connects to it just fine.

Here's the output from a few standard commands:

```

$ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1b:24:70:80:cc  
          inet addr:192.168.1.107  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:24ff:fe70:80cc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1669 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2230 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1259085 (1.2 MB)  TX bytes:293603 (293.6 KB)
          Interrupt:20 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3261 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3261 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:304766 (304.7 KB)  TX bytes:304766 (304.7 KB)

vboxnet0  Link encap:Ethernet  HWaddr 0a:00:27:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

```

$iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

vboxnet0  no wireless extensions.

```

```

$lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 [Geforce Go 6150] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
07:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

```

```

$lsusb
Bus 002 Device 002: ID 046d:c045 Logitech, Inc. Optical Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

My wireless card used to be wlan0, but that's not even listed as an option.  lspci does not seem to register the device at all.

I tried booting off a 10.10 live disc, and got the same results as above; the hardware simply does not appear to be detected.  I also tried a bootable USB stick with a stripped-down 10.04 installed on it (that previously worked fine with the wireless) in case it was a recent update issue.  Same problem.

So am I looking at a hardware failure?  Or is there something (anything) else I can try to resolve this?  I'm an exceptionally busy -- and VERY stressed-out -- computer science graduate student with three assignments and two research projects on-the-go right now, so getting my wireless up and running ASAP is very important.

I appreciate any help anyone can offer.  If you need any additional diagnostic information please let me know and I'll edit this first post to include the relevant details.


EDIT:
I'll also mention that the wired connection works just fine (I'm using it right now).  Also, I did make sure that the hardware switch to turn the wireless card on and off is in the "On" position.

---

### Post by chili555 on 2010-12-13
> So am I looking at a hardware failure?That's my first guess. Have you had any unusual events such as lockups, hard resets or dropped the laptop? It there a little door on the bottom of your HP that you can open and see if the wireless card can be reseated (using all recommended precautions, of course)? I suggest you do:```
dmesg | less
```See if there are any interesting messages, especially errors or warnings.

---

### Post by ve4cib on 2010-12-14
> **chili555 said:**
> That's my first guess. Have you had any unusual events such as lockups, hard resets or dropped the laptop? It there a little door on the bottom of your HP that you can open and see if the wireless card can be reseated (using all recommended precautions, of course)? I suggest you do:```
dmesg | less
```See if there are any interesting messages, especially errors or warnings.

I checked dmesg, and there weren't any error messages or anything that I could see.

Out of desperation I whipped out the Vista factory recovery DVDs and reset the machine to its original state.  The wireless card was still not detected.  So it's off to the shop now.  And naturally the warranty expired six months ago.  $350 + taxes + two weeks = I should have a working computer again.

Thanks anyway.

---

### Post by plux on 2010-12-14
The HP DV6000 has overheating issues that can destroy the wireless card. 
It not unlikely that the next defect will be the gpu. Be sure that there is no dust in the air vents.

[http://en.wikipedia.org/wiki/HP_Pavilion_(computer)#Overheating_issue](http://en.wikipedia.org/wiki/HP_Pavilion_(computer)#Overheating_issue)

---

