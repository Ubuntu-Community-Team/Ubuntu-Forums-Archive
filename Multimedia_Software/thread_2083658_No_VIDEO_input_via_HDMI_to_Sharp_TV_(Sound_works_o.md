---
title: "No VIDEO input via HDMI to Sharp TV (Sound works ok)"
date: 2012-11-13
forum: Multimedia Software
---

### Post by WiReIs on 2012-11-13
Hello, 

I am currently trying to connect my Dell Inspiron laptop to my Sharp Aquos TV via HDMI, i am able to hear Audio through the TV ok, however i am unable to get any Video signal through the HDMI, i have a LG Plasma downstairs and everything works ok on that TV, i have tried adjusting settings on the Sharp TV HDMI settings but with no luck nothing seems to change.  I have also tried adjusting settings in System > Preferences > Monitors, the laptop is picking up the Sharp Corporation 42" monitor but again no Video only Audio, any help or ideas would be very much appreciated guys, thanks :)

---

### Post by ercherramon on 2012-11-13
what version of ubuntu are you? and what video chip you have?

---

### Post by WiReIs on 2012-11-13
Hi im using Ubuntu 11.04, i have an Intel chip

```
ireis@wireis-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 18)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 06)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
12:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g LP-PHY (rev 01)
13:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
```

---

### Post by WiReIs on 2012-11-13
Anyone any ideas what might be (not) happening?

Really stuck, i have searched all over the net with no luck, everybody seems to have Audio not working rather than Video issues but Audio fine

---

### Post by Halbblutplins on 2012-11-13
I had the same problem ... but I could fix it by checking the hdmi cable ... it hasn't been fully in the connector :P


Peter

---

### Post by ercherramon on 2012-11-13
Well, I think in your case it would be appropriate to create a new configuration to your xorg.conf

enter the test option in ubuntu rescue mode and as administrator to access the console.

our TV may have a display resolution that is not compatible with the HDMI and the xorg.conf perhaps find some configuration that if the supports.

reboot the notebook and enter in mode rescue.

```
Xorg -configure

sudo mv xorg.conf.new /etc/X11/xorg.conf

reboot
```

if the video does not work with that, try to follow the thread of this case that is very similar to yours on the problem of screen resolutions that do not let you run the video input of your monitor:


[http://ubuntuforums.org/archive/index.php/t-1744465.html](http://ubuntuforums.org/archive/index.php/t-1744465.html)

---

