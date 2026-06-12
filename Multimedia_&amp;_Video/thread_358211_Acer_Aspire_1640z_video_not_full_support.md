---
title: "Acer Aspire 1640z video not full support"
date: 2007-02-10
forum: Multimedia &amp; Video
---

### Post by yurukov on 2007-02-10
Hi all,

I have an Acer Aspire 1640z. I installed Kubuntu 6.10 a.k.a. Edgy. Before I have also installed Kubuntu (5.x) and I have problems with sound, video and wlan. Then I didn't have time to dig deeper. Now all is fixed except the video. It works, but I cannot get a better resolution. This laptop has a widescreen and can support 1366×768 or any 16:9. The most I can get now is 1024×768. I figure that it is a driver problem. I've got some drivers from acer for windows, so I installed ndiswrapper, but it did not work. Here is what came from lspci:

```
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
06:01.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
06:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
06:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

```

Does anyone has any idea how to get it to work?

---

### Post by banditti on 2007-02-10
```
sudo apt-get install 915resolution
```

or you can do it from the Synaptic manager

---

### Post by banditti on 2007-02-11
forgot, in case you didn't know already.

sorry, you need to:


```
sudo gedit /etc/apt/sources.list
```



In there, there are a couple of lines that talk to "universe" Remove the # in front of those universe lines that start with deb.

Then from a terminal window:

```
sudo apt-get update sudo apt-get install 915resolution
```

---

### Post by yurukov on 2007-02-16
Ok that worked 10x a lot. It set the resolution to widescreen. Do you know how can I get it even higher. I tried to edit the options in xorg.conf, but nothing happened.

---

### Post by southpaw13 on 2008-07-07
Will this work for Hardy version? I can't get copmiz to run. Says that I have the wrong driver. When I installed the versa driver was installed. I can't find the driver specifically for my video card. This is what compiz-check says:

Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
 Driver in use:         vesa
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: vesa driver in use 

Would you like to know more? (Y/n) y

 The vesa driver is not capable of running Compiz, you need to install the
 proper driver for your graphics card. 

Thanks,

Caleb

---

