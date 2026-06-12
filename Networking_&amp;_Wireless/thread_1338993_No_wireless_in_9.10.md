---
title: "No wireless in 9.10"
date: 2009-11-27
forum: Networking &amp; Wireless
---

### Post by scoopy on 2009-11-27
Hey there friends. I'm having issues too with my Compaq v6000. The Broadcom drivers isn't showing up in "Hardware Drivers". It used to work in 9.04 but no longer.

I've install fwcutter, modaliases, bcmwl-kernel-source restarted still nothing in "Hardware Drivers"

Some more info:

luke@luke-laptop:~$ lspci
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


luke@luke-laptop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 03f0:171d Hewlett-Packard Wireless (Bluetooth + WLAN) Interface [Integrated Module]
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


lshw -class network
I get nothing for this?

luke@luke-laptop:~$ iwconfig
lo no wireless extensions.

eth0 no wireless extensions.

pan0 no wireless extensions.




I'm pretty new to all this so please dumb down your advice for a dummy.

Thanks

---

### Post by scoopy on 2009-11-29
Bump

---

### Post by j2bv16 on 2009-11-29
Try using ndiswrapper  > sudo apt-get install ndiswrapper-common and the windows drivers

---

### Post by scoopy on 2009-11-29
Thanks dude.  

I have been able to download ndiswrapper and install and download and installed the broadcom drivers for my Compaq V6000 without an issue. however, now I get this message:  "Hardware present: No".  

This would suggest that my system is not even recognizing that the wireless is present or that it is broken.

Any other thoughts anyone out there in Ubuntu land?

Thanks

Scoop

---

### Post by j2bv16 on 2009-11-29
> **scoopy said:**
> Thanks dude.  

I have been able to download ndiswrapper and install and download and installed the broadcom drivers for my Compaq V6000 without an issue. however, now I get this message:  "Hardware present: No".  

This would suggest that my system is not even recognizing that the wireless is present or that it is broken.

Any other thoughts anyone out there in Ubuntu land?

Thanks

Scoop

Dont worry for the mensaje it will work, if is this the case mark at solved

---

### Post by scoopy on 2009-11-29
Thanks for getting back again.  Much appreciated :)

Sorry I don't understand what this means?

"Dont worry for the mensaje it will work, if is this the case mark at solved"

Thanks

Scoopy

---

### Post by j2bv16 on 2009-11-29
well i dont speack much englis , ndiswrapper will say "Hardware present: No".  but it will work, you try to connect?

---

### Post by scoopy on 2009-11-29
> **j2bv16 said:**
> well i dont speack much englis , ndiswrapper will say "Hardware present: No".  but it will work, you try to connect?

No, still can't connect.  Thanks for you help!!!

Scoopy.

---

### Post by scoopy on 2009-11-29
just found a usb wireless dongle and plugged it in and it work straight away.  Hmmmm.  Would be cool if i could get the internal wireless to work!!!!

---

### Post by gdesilva on 2009-11-29
I have had a very similar problem...mine is with a usb bluetooth dongle. Was working fine in 9.04 but with the upgrade to 9.10, Ubuntu claims that there are no bluetooth devices. So far haven't had any success with posts to forums such as this.

---

