---
title: "Dell Wireless 1395 - Not detected"
date: 2009-10-29
forum: Networking &amp; Wireless
---

### Post by elusive_night on 2009-10-29
Hello,

First of all, WOW! Ubuntu 9.10, fantastic! Much better than I expected!

But of course, I wouldnt be here to only post that would I? No, I'm having a little bit of a problem with my wireless card; of which the main problem is that Ubuntu seems unable to actually detect it.  
Ok so I have no properity drivers running, eth0 (wired) is recognised but any instance of eth1 is not there.
It works on W7, Kubuntu, Ubuntu 9.04 and Sabayon; only since the upgrade has the problem started.  
I'm using a Dell Vostro 1000 with an intergrated Dell Wireless 1395.

If any more information is needed I will happily give it!

Thanks,

EN

---

### Post by elusive_night on 2009-10-29
outpost of command: lspci:

d00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200]
05:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
08:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
08:01.0 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
08:01.1 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)

the network controller is listed, but however it is not used by the system.

Do I have to manually configure it or is there any other way of getting the system to utilise the controller?

Thanks,

EN

---

### Post by elusive_night on 2009-10-29
Tried to install bcmwl-kernel-source package, brought up drive in 'hardware drivers' but activating it fails, just stays grayed out and doesnt do anything!

Any ideas?

EN

---

### Post by bkratz on 2009-10-29
> **elusive_night said:**
> Tried to install bcmwl-kernel-source package, brought up drive in 'hardware drivers' but activating it fails, just stays grayed out and doesnt do anything!

Any ideas?

EN

Here is a recent thread about this card

[http://ubuntuforums.org/showthread.php?t=1266620&highlight=BCM4312](http://ubuntuforums.org/showthread.php?t=1266620&highlight=BCM4312)

---

### Post by elusive_night on 2009-10-30
Hello,

Thank you for the reply, I followed the instructions in that thread, to which there was no effect on my wireless card; the device still cannot be found (when I loaded the driver I recieved an output from the terminal saying the driver was loaded, but nothing about the device being found).  Once I had completed those instructions, my wired connection controller also dissapared, so I had to do a full-reinstall.  I then tried again, but am greeted with the error 'FATAL: Module ssb is in use' when I try to run the command 'make unload'
I've had a look at other threads and it seems ndiswrapper could be using the module, but does this mean that ndiswrapper has perhaps loaded the wrong driver?

Many thanks,

James

---

### Post by Ayuthia on 2009-10-30
Can you try the following:
```
sudo modprobe -r b43 b44 ssb ndiswrapper wl
sudo modprobe wl
sudo modprobe b44
sudo iwlist scan
```

The b44 module (the wired card) needs to have the ssb module so we need to remove all the wireless and wired modules and then reload them in the right order.

---

### Post by elusive_night on 2009-10-30
Hello,

Thank you for the reply, I tried using the first command you stated but it brought up the error 'FATAL: *Module wl not found*'.

Earlier today I noticed ndiswrapper was not installed upon my system, so after booting into windows and downloading the ndiswrapper-common & ndiswrapper-utils I installed both packages.

Many thanks,

EN

---

