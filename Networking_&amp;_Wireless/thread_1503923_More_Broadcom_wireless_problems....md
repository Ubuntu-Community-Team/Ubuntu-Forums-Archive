---
title: "More Broadcom wireless problems..."
date: 2010-06-07
forum: Networking &amp; Wireless
---

### Post by jpeery on 2010-06-07
Frustrating, I've read through several of the posts here, and don't seem to be making much headway, basically my wireless up and quit working a week or so ago, can't seem to figure it out.  Have tried the NDIS stuff to no avail, etc.  Thing is, if I remove and re-install the Broadcom sta driver it still never works.  In Hardware Drivers it says it's "Activated, but not currently in use"  ????

Help???

Some info:

~$ lspci
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
03:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
07:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

~$ lshw -c network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:b6000000-b6003fff

~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

Thanks in advance!
Jason

---

### Post by jpeery on 2010-06-07
Ok, installed NDIS wrapper, and it looks CLOSE to working, but network manager still isn't showing in the panel...  And after I reboot everything goes screwy, this is REALLY starting to **** me off, actually thinking about going back to Windows, dare I say it, because compared to this is, just works.  Which is what I USED to say about Ubunutu, and that it was easier to figure stuff out on Ubuntu.  Not the case anymore!  ANY HELP appreciated.

---

### Post by purelinuxuser on 2010-06-07
EDIT: You may want to consider disabling or uninstalling ndiswrapper before trying my solution.

The problem is the Broadcom STA driver doesn't support the BCM4311 wireless card (why it shows up under Hardware Drivers with your configuration, I have no idea).  You'll have to use the native b43 driver instead.  The only reason why this native driver doesn't work out of the box is the firmware, which must be installed AFTER installation:

[LIST=1]
[*]Plug into Ethernet for an Internet connection
[*]Open Synaptic
[*]Install "b43-fwcutter"
[*]During the installation you will get a popup with a checkbox that reads, "Automatically download and install firmware?"  Make sure it is **checked**.
[*]Reboot.
[/LIST]
If wireless works, yay!  Otherwise, post
```
lshw -c network
```again.  Good luck :)

---

### Post by Captain Carrot on 2010-06-07
I have been having problems with my wireless as well, but broadcom STA seems to be (most of the time) working with my bcm4311 card. Would b43fwcutter be the better choice? It's stresses me out when it doesn't work right. Although, curiously, it will still connect to other unsecured networks. This is kind of driving me nuts, any idea what might be happening?

---

### Post by purelinuxuser on 2010-06-07
> **Captain Carrot said:**
> I have been having problems with my wireless as well, but broadcom STA seems to be (most of the time) working with my bcm4311 card. Would b43fwcutter be the better choice? It's stresses me out when it doesn't work right. Although, curiously, it will still connect to other unsecured networks. This is kind of driving me nuts, any idea what might be happening?

Basically, the STA driver is the proprietary driver supplied by Broadcom (which is "ok") while b43-fwcutter is a tool that installs firmware for the native b43 driver supplied by the Linux kernel.  b43 is native and provides more features, and might even be more stable.  However, being open-source and completely built on reverse engineering, it may be buggy.  I suggest b43 since it's native.

---

### Post by jpeery on 2010-06-08
Well, it appears to work, however the network manager isn't showing in the panel...  It apparently picked up my previous conf and was able to connect to my wireless at home, but not sure what it'll do once I am away from here...  Would be nice to have that panel so I can see what else is out there when I need to connect to something else...  Is it me, or is this release pretty buggy?

---

### Post by jpeery on 2010-06-08
Ok, so restarted NetworkManager, didn't solve it, etc.  Reboot, and now it's not working again!  ARG!!!!  Am about to use this laptop for a hockey puck!  Is there ANOTHER Linux distro that's NOT having such wireless issues?  Oh, and I'm still not seeing the b43 driver available in System -> Administration -> Hardware Drivers only the STA...  Is there some command I can run that would get around this GUI?

---

### Post by purelinuxuser on 2010-06-08
As for the Network Manager applet not appearing, you can press Alt+F2, type
```
nm-applet
```and click "Run" to (hopefully) solve this issue.

The b43 driver (usually) does not appear under Hardware Drivers, just the STA driver since it's proprietary.

Post the output of
```
lshw -c network
```

---

### Post by pdc on 2010-06-09
> *Is there ANOTHER Linux distro that's NOT having such wireless issues?*

download the .iso for opensuse

have a look; has very good wireless support

---

