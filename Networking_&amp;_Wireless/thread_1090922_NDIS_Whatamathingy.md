---
title: "NDIS Whatamathingy?"
date: 2009-03-08
forum: Networking &amp; Wireless
---

### Post by el canadiano on 2009-03-08
Yeah, I have just installed Ubuntu for the second time on a second computer. This time, I have a PC Card installed into this one, and I have no clue how to configure the wireless connection using NDISWrapper. I need help installing it and I have been getting numerous errors (currently I have the computer at the other side of the house on a wired connection =/).

- I'm on Hardy Heron. 
- I have downloaded NDISWrapper to my desktop (/home/awpoon/Desktop). I also have an extracted version in the desktop folder.
- These are my results from lspci
> 00:00.0 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:08.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
00:0a.0 Communication controller: Conexant HSF 56k Data/Fax Modem
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter (rev 01)

- I try this method [here](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper), with no luck. This is what happened when I tried the first time.
> awpoon@awpoon-desktop:~$ sudo apt-get install ndisgtk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ndisgtk


I'm kinda new to the Wireless section, a little help would be nice, you guys have got me out once by going LTS. :) I'm so used to downloading an exe and installing it like that *rolleyes*

---

### Post by Ayuthia on 2009-03-08
If you have a working internet connection, you will need to update the repository list:
```
sudo apt-get update
```

If you do not have a working internet connection, you can use the live CD to install ndisgtk:
```
sudo apt-cdrom add
```It will ask you for the live CD.  Once complete:
```
sudo apt-get update
sudo apt-get install ndisgtk
```
That should get you started with ndiswrapper.  As for how to configure ndiswrapper to work with the Atheros card, I am not for sure because I have not had a chance to work with one yet.

---

### Post by dmizer on 2009-03-09
You should be able to use native drivers for that card instead of ndiswrapper. Take a look at this thread: [http://ubuntuforums.org/showthread.php?t=1026972](http://ubuntuforums.org/showthread.php?t=1026972)

---

