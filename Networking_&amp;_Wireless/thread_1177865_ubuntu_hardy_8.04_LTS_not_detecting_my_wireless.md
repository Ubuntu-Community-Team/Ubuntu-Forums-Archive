---
title: "ubuntu hardy 8.04 LTS not detecting my wireless"
date: 2009-06-03
forum: Networking &amp; Wireless
---

### Post by YCW on 2009-06-03
Hi all
Pls help me. I had already google this topic and had done the following steps which is
1) sudo apt-get update
2) sudo apt-get install build-essential
3) wget [http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz)

At this point, i got this error

Resolving snapshots.madwifi.org... failed: Name or service not known.

Please help me, coz i m very far behind in my work already and i m soooo fed up with window coz it's so slow and am really hoping ubuntu can be of help. PLS PLS PLEASSSEEEEEEEEEEeeeeeeeeee

---

### Post by YCW on 2009-06-03
Hi all
I m enclosing more infor pertaining my problems.

ricky@ricky-laptop:~$ uname -rm
2.6.24-24-generic i686
ricky@ricky-laptop:~$ lsusb
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 09da:000a A4 Tech Co., Ltd 
Bus 001 Device 001: ID 0000:0000  
ricky@ricky-laptop:~$ lshw -C Network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 2
       bus info: pci@0000:08:02.0
       logical name: eth0
       version: 10
       serial: 00:16:36:d2:28:96
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.2.102 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network:1 UNCLAIMED
       description: Ethernet controller
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 4
       bus info: pci@0000:08:04.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=168 maxlatency=28 mingnt=10
ricky@ricky-laptop:~$ 
[http://ubuntuforums.org/images/smilies/icon_biggrin.gif](http://ubuntuforums.org/images/smilies/icon_biggrin.gif)

---

### Post by albinootje on 2009-06-03
Please post also the output of this :
```

lspci

```
And can you follow this howto first ?
[http://madwifi-project.org/wiki/Compatibility/Atheros/AR5005G](http://madwifi-project.org/wiki/Compatibility/Atheros/AR5005G)
(Found here : [https://answers.launchpad.net/ubuntu/+question/56938](https://answers.launchpad.net/ubuntu/+question/56938))

---

### Post by YCW on 2009-06-03
Hi there
ricky@ricky-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:07.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]
08:01.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
08:01.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
08:01.2 SD Host controller: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
08:01.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
08:01.4 FLASH memory: ENE Technology Inc SD/MMC Card Reader Controller (rev 01)
08:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
08:04.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
ricky@ricky-laptop:~$ 
ricky@ricky-laptop:~$ 

Hope this is of help to u..[http://ubuntuforums.org/images/smilies/icon_biggrin.gif](http://ubuntuforums.org/images/smilies/icon_biggrin.gif)

---

### Post by YCW on 2009-06-03
Hi
I m adding more infor ( got this step from the link previously advise.. hopefully this is helpful to any1 of u that can help me out. Many thks )

ricky@ricky-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:05.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:07.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 83)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc RS485 [Radeon Xpress 1100 IGP]
08:01.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
08:01.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
08:01.2 SD Host controller: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
08:01.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
08:01.4 FLASH memory: ENE Technology Inc SD/MMC Card Reader Controller (rev 01)
08:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
08:04.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
ricky@ricky-laptop:~$ 
ricky@ricky-laptop:~$

---

### Post by albinootje on 2009-06-03
> **YCW said:**
> 
08:04.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)

Okay, thanks for the information.

I just found that the broken link mentioned in the howto here :
[http://ubuntuforums.org/showpost.php?p=4791500&postcount=7](http://ubuntuforums.org/showpost.php?p=4791500&postcount=7)

should be :
wget [http://snapshots.madwifi-project.org/special/madwifi-ng-r2756+ar5007.tar.gz](http://snapshots.madwifi-project.org/special/madwifi-ng-r2756+ar5007.tar.gz)

If that doesn't work, then please try the suggestions in this link : [https://answers.launchpad.net/ubuntu/+question/56938](https://answers.launchpad.net/ubuntu/+question/56938)

GL!

---

### Post by YCW on 2009-06-04
Hi there fren
This is the output...Pls have a look. TQ

ricky@ricky-laptop:~$ sudo apt-get update
[sudo] password for ricky: 
Hit [http://ftp.twaren.net](http://ftp.twaren.net) hardy Release.gpg
Ign [http://ftp.twaren.net](http://ftp.twaren.net) hardy/main Translation-en_US
Ign [http://ftp.twaren.net](http://ftp.twaren.net) hardy/restricted Translation-en_US
Ign [http://ftp.twaren.net](http://ftp.twaren.net) hardy/universe Translation-en_US
Ign [http://ftp.twaren.net](http://ftp.twaren.net) hardy/multiverse Translation-en_US
Hit [http://ftp.twaren.net](http://ftp.twaren.net) hardy-updates Release.gpg
Ign [http://ftp.twaren.net](http://ftp.twaren.net) hardy-updates/main Translation-en_US
Ign [http://ftp.twaren.net](http://ftp.twaren.net) hardy-updates/restricted Translation-en_US
Ign [http://ftp.twaren.net](http://ftp.twaren.net) hardy-updates/universe Translation-en_US
Ign [http://ftp.twaren.net](http://ftp.twaren.net) hardy-updates/multiverse Translation-en_US
Hit [http://ftp.twaren.net](http://ftp.twaren.net) hardy-security Release.gpg
Ign [http://ftp.twaren.net](http://ftp.twaren.net) hardy-security/main Translation-en_US
Ign [http://ftp.twaren.net](http://ftp.twaren.net) hardy-security/restricted Translation-en_US
Ign [http://ftp.twaren.net](http://ftp.twaren.net) hardy-security/universe Translation-en_US
Ign [http://ftp.twaren.net](http://ftp.twaren.net) hardy-security/multiverse Translation-en_US
Hit [http://ftp.twaren.net](http://ftp.twaren.net) hardy Release
Hit [http://ftp.twaren.net](http://ftp.twaren.net) hardy-updates Release
Hit [http://ftp.twaren.net](http://ftp.twaren.net) hardy-security Release
Hit [http://ftp.twaren.net](http://ftp.twaren.net) hardy/main Packages 
Hit [http://ftp.twaren.net](http://ftp.twaren.net) hardy/restricted Packages
Hit [http://ftp.twaren.net](http://ftp.twaren.net) hardy/restricted Sources
Hit [http://ftp.twaren.net](http://ftp.twaren.net) hardy/main Sources
Hit [http://ftp.twaren.net](http://ftp.twaren.net) hardy/multiverse Sources
Hit [http://ftp.twaren.net](http://ftp.twaren.net) hardy/universe Sources
Hit [http://ftp.twaren.net](http://ftp.twaren.net) hardy/universe Packages
Hit [http://ftp.twaren.net](http://ftp.twaren.net) hardy/multiverse Packages
Hit [http://ftp.twaren.net](http://ftp.twaren.net) hardy-updates/main Packages
Hit [http://ftp.twaren.net](http://ftp.twaren.net) hardy-updates/restricted Packages
Hit [http://ftp.twaren.net](http://ftp.twaren.net) hardy-updates/restricted Sources
Hit [http://ftp.twaren.net](http://ftp.twaren.net) hardy-updates/main Sources
Hit [http://ftp.twaren.net](http://ftp.twaren.net) hardy-updates/multiverse Sources
Hit [http://ftp.twaren.net](http://ftp.twaren.net) hardy-updates/universe Sources
Hit [http://ftp.twaren.net](http://ftp.twaren.net) hardy-updates/universe Packages
Hit [http://ftp.twaren.net](http://ftp.twaren.net) hardy-updates/multiverse Packages
Hit [http://ftp.twaren.net](http://ftp.twaren.net) hardy-security/main Packages
Hit [http://ftp.twaren.net](http://ftp.twaren.net) hardy-security/restricted Packages
Hit [http://ftp.twaren.net](http://ftp.twaren.net) hardy-security/restricted Sources
Hit [http://ftp.twaren.net](http://ftp.twaren.net) hardy-security/main Sources
Hit [http://ftp.twaren.net](http://ftp.twaren.net) hardy-security/multiverse Sources
Hit [http://ftp.twaren.net](http://ftp.twaren.net) hardy-security/universe Sources
Hit [http://ftp.twaren.net](http://ftp.twaren.net) hardy-security/universe Packages
Hit [http://ftp.twaren.net](http://ftp.twaren.net) hardy-security/multiverse Packages
Reading package lists... Done
ricky@ricky-laptop:~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree        
Reading state information... Done
build-essential is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.24-19-generic linux-headers-2.6.24-19
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ricky@ricky-laptop:~$ wget [http://snapshots.madwifi-project.org/special/madwifi-ng-r2756+ar5007.tar.gz](http://snapshots.madwifi-project.org/special/madwifi-ng-r2756+ar5007.tar.gz)
--12:48:27--  [http://snapshots.madwifi-project.org/special/madwifi-ng-r2756+ar5007.tar.gz](http://snapshots.madwifi-project.org/special/madwifi-ng-r2756+ar5007.tar.gz)
           => `madwifi-ng-r2756+ar5007.tar.gz'
Resolving snapshots.madwifi-project.org... 217.24.1.134
Connecting to snapshots.madwifi-project.org|217.24.1.134|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 485 [application/x-gzip]

100%[====================================>] 485           --.--K/s             

12:48:31 (35.24 MB/s) - `madwifi-ng-r2756+ar5007.tar.gz' saved [485/485]

ricky@ricky-laptop:~$ tar xfz madwifi-ng-r2756+ar5007.tar.gz
ricky@ricky-laptop:~$ cd madwifi-ng-r2756+ar5007
ricky@ricky-laptop:~/madwifi-ng-r2756+ar5007$ make
make: *** No targets specified and no makefile found.  Stop.
ricky@ricky-laptop:~/madwifi-ng-r2756+ar5007$ sudo make install
make: *** No rule to make target `install'.  Stop.
ricky@ricky-laptop:~/madwifi-ng-r2756+ar5007$ 
ricky@ricky-laptop:~/madwifi-ng-r2756+ar5007$ 

Pls help. TQ

---

### Post by YCW on 2009-06-04
Hi all
Just like to add 1 more thing. I noticed that my wireless switch is alway "ON" even when i toggle it also no effect. BTW, does any1 know whether ubuntu 8.10 have any wireless problem? Because i m thinking of downloading it and install it and hopefully it is just like gutsy where wireless work out of box. Any1 PLS???[http://ubuntuforums.org/images/smilies/icon_sad.gif](http://ubuntuforums.org/images/smilies/icon_sad.gif)

---

### Post by albinootje on 2009-06-04
> **YCW said:**
> 
ricky@ricky-laptop:~$ tar xfz madwifi-ng-r2756+ar5007.tar.gz
ricky@ricky-laptop:~$ cd madwifi-ng-r2756+ar5007
ricky@ricky-laptop:~/madwifi-ng-r2756+ar5007$ make
make: *** No targets specified and no makefile found.  Stop.


That .tar.gz file had only one file called README, saying :
> 
You most likely downloaded this tarball since you are looking for a version of MadWifi which supports the AR5007 chipset family, which is for example used in the EeePC.

However, since you've downloaded this tarball, you've followed outdated instructions. The code that this tarball once contained is now obsolete.
Please follow these instructions to enable your AR5007-based WLAN device: [http://madwifi.org/ticket/1192](http://madwifi.org/ticket/1192)

If you have any questions about it, please contact our regular support channels: [http://madwifi.org/wiki/Support](http://madwifi.org/wiki/Support)

Thanks.


---

### Post by YCW on 2009-06-04
Haizzzzz

I clicked on d link and i c this

Not Found

The requested URL /ticket/1192 was not found on this server.
Apache/2.0.55 (Unix) Server at madwifi.org Port 80

Pls oh...pls...will some good soul point me 2 d correct way...tqtqtqtqtqtqtqtqtqtqtqtqtqtqtqtqtqtqtqtqqtTQTQTQTQTQTQTQQT

Haizzzzzzzzzz

---

### Post by albinootje on 2009-06-04
> **YCW said:**
> 
Not Found


Sorry, I should have checked those links :(
Here's the support page : [http://madwifi-project.org/wiki/Support](http://madwifi-project.org/wiki/Support)

---

