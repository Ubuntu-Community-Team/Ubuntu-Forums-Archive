---
title: "connect to and remote into home network.."
date: 2011-02-08
forum: Networking &amp; Wireless
---

### Post by gettinit on 2011-02-08
I am some what of a novice so excuse the ignorance. I have an older laptop that I could not get ubuntu 10 installed onto for whatever reason it just wouldn't load. So I installed xubuntu with no problem. It's missing some of the icons I am used to for locating and seeing my home network etc. ( I run a dual boot on my windows machine of ubuntu 10) Anyway, my ultimate goal here is to connect this machine to the network to be able to remote in from my windows machine. I have enabled "allow others to control this machine" but still cannot see it from any of my win 7 machines. I'm sure I'm missing something simple any help would be greatly appreciated thanks!

---

### Post by espressobeanie on 2011-02-08
Type into a terminal, "sudo ufw status". If you have moblock installed, disable it. Also, type "lspci" and show me what comes up.

---

### Post by gettinit on 2011-02-08
tereo@stereo-laptop:~$ sudo ufw status
[sudo] password for stereo: 
Status: inactive
stereo@stereo-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 11)
00:01.0 PCI bridge: Intel Corporation 82815 815 Chipset AGP Bridge (rev 11)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801BAM ISA Bridge (LPC) (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801BAM IDE U100 Controller (rev 03)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 03)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 03)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 03)
00:1f.6 Modem: Intel Corporation 82801BA/BAM AC'97 Modem Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 Go] (rev b2)
02:00.0 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
02:00.1 CardBus bridge: Texas Instruments PCI1420 PC card Cardbus Controller
02:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:0a.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)

---

### Post by espressobeanie on 2011-02-08
Okay, so it's not hardware related. Windows usually makes it's own WORKGROUP subdomain that Ubuntu by default has no clue how to see or connect. It's a bit more techy than that. So, what you would need to do is to install Samba from synaptic manager.  

Samba info: 
[https://help.ubuntu.com/community/Samba](https://help.ubuntu.com/community/Samba)
 Samba setup:  
[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

---

