---
title: "Wireless on Acer Aspire One ZG5"
date: 2010-03-05
forum: Networking &amp; Wireless
---

### Post by gohargod on 2010-03-05
Ok, although I'm new to Ubuntu, I do have some unix experience. I've installed Ubuntu 9.1 on my Acer Aspire One ZG5 that was previously running Win XP with the wireless working fine. 

In ubuntu,though, i can't get the wireless to work at all and I don't really even know how to troubleshoot it. I've opened a terminal and used sudo to update various packages, but still nothing. It does appear as though the system recognizes the card since I can configure it, but I'm not keen on playing wi8th the BSSID and MAC address stuff because I just don't have any confidence that it will change my situation. Has anyone had any success with this setup (ubuntu 9.1 and acer one)? Is there a step-by-step wireless troubleshooting/configuration process that's generic to ubuntu? 

All I can seem to find are various postings that worked for one person but I can't seem to get to work for me.

---

### Post by bkratz on 2010-03-06
> **gohargod said:**
> Ok, although I'm new to Ubuntu, I do have some unix experience. I've installed Ubuntu 9.1 on my Acer Aspire One ZG5 that was previously running Win XP with the wireless working fine. 

In ubuntu,though, i can't get the wireless to work at all and I don't really even know how to troubleshoot it. I've opened a terminal and used sudo to update various packages, but still nothing. It does appear as though the system recognizes the card since I can configure it, but I'm not keen on playing wi8th the BSSID and MAC address stuff because I just don't have any confidence that it will change my situation. Has anyone had any success with this setup (ubuntu 9.1 and acer one)? Is there a step-by-step wireless troubleshooting/configuration process that's generic to ubuntu? 

All I can seem to find are various postings that worked for one person but I can't seem to get to work for me.

No, don't have one, but here is some interesting reading

[https://help.ubuntu.com/community/AspireOne/Ubuntu9.10](https://help.ubuntu.com/community/AspireOne/Ubuntu9.10)

Your's is about 1/2 down.  You might go to the terminal (Applications>>Accessories>>Terminal) and type in:

lspci
(that is LSPCI in lowercase) and either read the output or copy/paste it back here so someone can decode and find out details of your wireless card.


Also here is a link to the community wireless troubleshooting guide you asked about.

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

There is plenty of help available here!

---

### Post by gohargod on 2010-03-06
bkratz, thanks for the info. i think one of the issues is that there is so much info, it's hard to find something specific to my situation. I did see the first link that you posted before and it provides some good background. I hadn't seen the troubleshooting link you posted - I'm going to try that now.

In the mean time, I've posted the results of my lspci command. Thank you for your help!

$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
03:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)

$ iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

---

### Post by atomizer on 2010-03-06
is there no driver available with System=>Administration=>Hardware Drivers?


I thought Atheros was supported that way....

---

### Post by gohargod on 2010-03-06
Ok, quick update:

1. System->admin->hardware drivers shows no proprietary drivers.
2. additional inspection work: 
   a. I downloaded the linux-backports-modules-karmic (I think that's what it was - who names these things?)
   b. I realized my previous troubleshooting efforts had led to a blacklist ath5k in the modprobe.d file. I removed that and things seem to be progressing - I now have a logical name for the device wlan0 and the wireless config in the network panel shows the device as disabled (not quite sure what that's about...though enabling/disabling the hard-wired switch on the front of the laptop doesn't seem to be working).

---

### Post by gohargod on 2010-03-06
Ok, after further screwing around, I actually can see available wireless networks. and it appears that I'm actually trying to connect. However, if I remove my cat5, i lose my connection. hovering over the wireless in the panel says something like 2WIRE222 active 100% (2WIRE222 is my SSID), but I still can't browse. ifconfig shows a 10... address rather than a 192...-style dhcp that I would expect.

---

### Post by vprajapati on 2010-03-06
> **gohargod said:**
> Ok, although I'm new to Ubuntu, I do have some unix experience. I've installed Ubuntu 9.1 on my Acer Aspire One ZG5 that was previously running Win XP with the wireless working fine. 

In ubuntu,though, i can't get the wireless to work at all and I don't really even know how to troubleshoot it. I've opened a terminal and used sudo to update various packages, but still nothing. It does appear as though the system recognizes the card since I can configure it, but I'm not keen on playing wi8th the BSSID and MAC address stuff because I just don't have any confidence that it will change my situation. Has anyone had any success with this setup (ubuntu 9.1 and acer one)? Is there a step-by-step wireless troubleshooting/configuration process that's generic to ubuntu? 

All I can seem to find are various postings that worked for one person but I can't seem to get to work for me.



Hi,
solution for athros wireless card
u might need to install linux-backport-modulres-karmic
in terminal type sudo inux-backport-modulres-karmic
it should work
[IMG]http://ubuntuforums.org/images/icons/icon13.gif[/IMG]
Vijay Prajapati
Ubuntu 9.10
Acer Gemstone, 3GB RAM, 2 GHZ

---

### Post by gohargod on 2010-03-06
ok, thanks all for your help, pokes, and prodding - i am now wireless on my acer one aspire running ubuntu 9.1. I'm not entirely sure how i got here, but I did!

---

### Post by Arkymedes on 2010-07-26
Hello,

Care to share your solution step by step?

For the life of me I cannot make this work and I have the same computer as you. :(

Thanks

---

