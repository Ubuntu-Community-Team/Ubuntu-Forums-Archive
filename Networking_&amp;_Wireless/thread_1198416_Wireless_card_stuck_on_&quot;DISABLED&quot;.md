---
title: "Wireless card stuck on &quot;DISABLED&quot;"
date: 2009-06-27
forum: Networking &amp; Wireless
---

### Post by icbolsh on 2009-06-27
I'm somewhat of a noob. Okay I am a noob. I just got an Dell D610 from someone and downloaded and installed the latest version of ubuntu. I have a problem with the internal wireless card. I looked around and tried a few different solutions but to no avail. When I boot up in windows it works but not ubuntu. Here is what I expect is the problem, it has a power on and off using the fn+F2 keys on the keyboard but nothing seems to happen when I do it in ubuntu(again works in windows). I ran this code and here is the result.

Code:
lspci -nn
lshw -C Network
dmesg | grep -e ath -e wlan
uname -rm
sudo iwlist scan

Here is what I got.


pete@pete-laptop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller [8086:2590] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2592] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller [8086:2792] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 [8086:2660] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 [8086:2658] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 [8086:2659] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 [8086:265a] (rev 03)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 [8086:265b] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller [8086:265c] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev d3)
00:1e.2 Multimedia audio controller [0401]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller [8086:266e] (rev 03)
00:1e.3 Modem [0703]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller [8086:266d] (rev 03)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge [8086:2641] (rev 03)
00:1f.2 IDE interface [0101]: Intel Corporation 82801FBM (ICH6M) SATA Controller [8086:2653] (rev 03)
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express [14e4:1677] (rev 01)
03:01.0 CardBus bridge [0607]: Texas Instruments PCI6515 Cardbus Controller [104c:8036]
03:01.5 Communication controller [0780]: Texas Instruments PCI6515 SmartCard Controller [104c:8038]
03:03.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
pete@pete-laptop:~$ lshw -C Network
WARNING: you should run this program as super-user.
*-network
description: Ethernet interface
product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:02:00.0
logical name: eth0
version: 01
serial: 00:12:3f:15:79:14
width: 64 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical
configuration: broadcast=yes driver=tg3 driverversion=3.94 firmware=5751-v3.29a ip=192.168.1.164 latency=0 module=tg3 multicast=yes
*-network
description: Network controller
product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
vendor: Broadcom Corporation
physical id: 3
bus info: pci@0000:03:03.0
version: 02
width: 32 bits
clock: 33MHz
capabilities: bus_master
configuration: driver=b43-pci-bridge latency=64 module=ssb
*-network:0 DISABLED
description: Wireless interface
physical id: 1
logical name: wlan0
serial: 00:14:a5:00:e2:8a
capabilities: ethernet physical wireless
configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
*-network:1 DISABLED
description: Ethernet interface
physical id: 2
logical name: pan0
serial: 3e:1d:3d:a5:f6:86
capabilities: ethernet physical
configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
pete@pete-laptop:~$ dmesg | grep -e ath -e wlan
[ 3.086942] device-mapper: multipath: version 1.0.5 loaded
[ 3.086945] device-mapper: multipath round-robin: version 1.0.0 loaded
pete@pete-laptop:~$ uname -rm
2.6.28-13-generic i686
pete@pete-laptop:~$ sudo iwlist scan

I hope someone can help. Please (I am using the same laptop with a LAN, should I disconnect it before running the command?)

---

### Post by Ayuthia on 2009-06-27
Can you try installing b43-fwcutter from Synaptic or:
```
sudo apt-get update
sudo apt-get install b43-fwcutter
```

Just in case you are not sure, keep the LAN connected for those steps.

---

### Post by icbolsh on 2009-06-27
> **Ayuthia said:**
> Can you try installing b43-fwcutter from Synaptic or:
```
sudo apt-get update
sudo apt-get install b43-fwcutter
```

Just in case you are not sure, keep the LAN connected for those steps.

I ran that and here is what I got:

pete@pete-laptop:~$ sudo apt-get update
[sudo] password for pete: 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release.gpg                            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Translation-en_US                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Translation-en_US   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Translation-en_US 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release.gpg          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty Release                      
Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release.gpg [197B]
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates Release                        
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Translation-en_US            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages                   
Get:2 [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release [11.7kB]          
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Packages            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages     
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/free Packages               
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/universe Sources             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Packages  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/main Sources         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/restricted Sources   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources    
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/universe Sources     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) jaunty-updates/multiverse Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty/non-free Packages
Fetched 198B in 1s (101B/s)
Reading package lists... Done
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems
pete@pete-laptop:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)

---

### Post by Ayuthia on 2009-06-27
> **icbolsh said:**
> 
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) jaunty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems
pete@pete-laptop:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
For the first error do the following:
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```It looks like you were missing the key was not there for the medibuntu site.

For the second part, you left out the sudo so it would not let you execute the command.  However, the command should have been:
```
sudo apt-get install b43-fwcutter
```

---

### Post by icbolsh on 2009-06-27
SUCCESS!!! Thank you for all the help. I am not able to use the fn+F2 to turn the wireless on and off. But as of now that is okay. As long as I can use the wireless at all. If some knows off the top of their heads how I I can still use that, that would be great, otherwise nevermind.
 Thanks again everyone. 
PS: I LOVE UBUNTU!!! Windows is not that great and Mac it too restrictive and costly.

---

