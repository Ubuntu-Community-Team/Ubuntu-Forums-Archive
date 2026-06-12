---
title: "Realtek Wifi USB drivers"
date: 2013-07-30
forum: Networking &amp; Wireless
---

### Post by sE7DNzA on 2013-07-30
Hello! I've seen several forums regarding the drivers for realtek devices, but they all seem to be old or outdated and none of their solutions have really worked for me. I basically want to get my Wifi USB stick working. 
Here's what I get when using the lsusb command to check all of my devices:

```
$ lsusbBus
001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 2001:3301 D-Link Corp. DWA-130 802.11n Wireless N Adapter(rev.C1) [Realtek RTL8192U]
Bus 001 Device 004: ID 0461:4dcb Primax Electronics, Ltd 
Bus 001 Device 005: ID 0461:4d64 Primax Electronics, Ltd 
Bus 002 Device 003: ID 058f:6361 Alcor Micro Corp. Multimedia Card Reader
$
```

I assumed I needed the Realtek RTL8192U driver so I tried following the solution presented in here: [http://ubuntuforums.org/showthread.php?t=1582673&p=10505710#post10505710](http://ubuntuforums.org/showthread.php?t=1582673&p=10505710#post10505710) and in some other forums. 

At first, I attempted to do like in that forum and search by using: 
```
wget http://ftp.at.debian.org/debian-backports//pool/non-free/f/firmware-nonfree/firmware-realtek_0.27~bpo50+1_all.deb
```

But since the link wasn't found, I edited to match the firmware-realtek_0.36+wheezy.1~bpo60+1_all.deb file in the [http://ftp.at.debian.org/debian-backports//pool/non-free/f/firmware-nonfree/](http://ftp.at.debian.org/debian-backports//pool/non-free/f/firmware-nonfree/) website and was able to download it. When I attempted to download it using Ubuntu Software Center, I had the exact same issue that the final poster in the [http://ubuntuforums.org/showthread.php?t=1582673&p=10505710#post10505710](http://ubuntuforums.org/showthread.php?t=1582673&p=10505710#post10505710) thread had. 

Are there any new solutions to this problem? I'm using Ubuntu 12.04 64-bit

---

### Post by wildmanne39 on 2013-07-30
*Thread moved to **Networking & Wireless**.*

---

### Post by kurt18947 on 2013-07-30
It's too bad you don't have a DWA-131 ver. A; they use an 819**2**SU chipset and is one of my favorite adapters.  Plug it in and it works.  I checked your adapter here:

[http://wikidevi.com/wiki/D-Link_DWA-130_rev_E1](http://wikidevi.com/wiki/D-Link_DWA-130_rev_E1)

If this is correct, your adapter uses a Realtek RTL819**1**SU but according to that site your chipset uses the same driver, r8712u that the RTL8192SU chipset uses.  Do you see any signs of life when you simply plug the adapter in without loading any extra drivers or anything?  If you run the command 'lsmod', does the module r8712u appear on the list?

It looks like D-link changes chip suppliers with the phases of the moon:).  

Rev. A1 uses **Marvell** 88W8362 
Rev. B1 uses **Ralink** RT2870 
Rev. C1 uses **Realtek** RTL8192U (This one would be plug-n-play)
Rev. D   uses **Atheros** AR9170  (This one would likely be plug-n-play as well)

---

### Post by Bucky Ball on 2013-07-30
Welcome to the forums.

As mentioned, did you just plug it in and try it? Did you actually check that it *wasn't* working before doing any of this??? That dongle should work 'out of the box' and the drivers are already in the kernel, so best to plug it in and tell us exactly what is happening. More helpful as you don't even know if you need those drivers and they could now conflict with what is already there and prevent the dongle working.

Switch off the machine and unplug the dongle. Switch on the machine, get to a desktop, plug the dongle in, open a terminal and:

```
dmesg

```
Do you see it there? Do an update via update manager or terminal:

```
sudo apt-get update
```

Then run these two, one after the other:

```
iwconfig
sudo lshw -C network
```

Post the results of these two commands back here.

---

### Post by Bucky Ball on 2013-07-30
Welcome to the forums.

That should work 'out of the box'. Switch off the machine and unplug it. Switch on the machine, get to a desktop, plug it in, open a terminal and:

```
dmesg

```
Do you see it there? Do an update via update manager or terminal:

```
sudo apt-get update
```

Then run these two, one after the other:

```
iwconfig
sudo lshw -C network
```

Post the results of these two commands back here.

---

### Post by sE7DNzA on 2013-07-31
Here are the terminal results: 

dmesg (It was the first result)
```
Module                  Size  Used byr8192u_usb            275951  0
```

sudo apt-get update (only the end since it was long, it was also the only part I saw that referenced the Wifi USB)
```
[   49.281934] usb 1-1.1: New USB device found, idVendor=2001, idProduct=3301
[   49.281940] usb 1-1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[   49.281943] usb 1-1.1: Product: 802.11n WLAN Adapter
[   49.281946] usb 1-1.1: Manufacturer: Realtek
[   49.281949] usb 1-1.1: SerialNumber: 00e04c000001
[   49.289320] r8192u_usb: module is from the staging directory, the quality is unknown, you have been warned.
[   49.290338] ieee80211_crypt: registered algorithm 'NULL'
[   49.290340] ieee80211_crypt: registered algorithm 'TKIP'
[   49.290342] ieee80211_crypt: registered algorithm 'CCMP'
[   49.290343] ieee80211_crypt: registered algorithm 'WEP'
[   49.290344] 
[   49.290344] Linux kernel driver for RTL8192 based WLAN cards
[   49.290346] Copyright (c) 2007-2008, Realsil Wlan
[   49.926811] Dot11d_Init()
[   49.926818] End of initendpoints
[   49.927220] usbcore: registered new interface driver rtl819xU
[   50.156399] rtl819xU:request firmware fail!
[   50.156399] 
[   50.156404] rtl819xU:ERR in init_firmware()
[   50.156404] 
[   50.156406] rtl819xU:ERR!!! rtl8192_adapter_start(): Firmware download is failed
[   50.156406] 
[   50.156408] rtl819xU:ERR!!! _rtl8192_up(): initialization failed!
[   50.156408] 
[   50.156564] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   50.386667] rtl819xU:request firmware fail!
[   50.386667] 
[   50.386671] rtl819xU:ERR in init_firmware()
[   50.386671] 
[   50.386674] rtl819xU:ERR!!! rtl8192_adapter_start(): Firmware download is failed
[   50.386674] 
[   50.386676] rtl819xU:ERR!!! _rtl8192_up(): initialization failed!
[   50.386676]
```
several scary failures here :/

iwconfig
```
Get:38 http://pr.archive.ubuntu.com precise-backports/universe amd64 Packages [36.2 kB]
Get:39 http://pr.archivGet:1 http://security.ubuntu.com precise-security Release.gpg [198 B]
Get:2 http://security.ubuntu.com precise-security Release [49.6 kB]       
Get:3 http://extras.ubuntu.com precise Release.gpg [72 B]                 
Hit http://pr.archive.ubuntu.com precise Release.gpg                      
Get:4 http://pr.archive.ubuntu.com precise-updates Release.gpg [198 B]    
Get:5 http://pr.archive.ubuntu.com precise-backports Release.gpg [198 B]  
Hit http://ppa.launchpad.net precise Release.gpg                          
Hit http://extras.ubuntu.com precise Release                              
Hit http://pr.archive.ubuntu.com precise Release                          
Hit http://ppa.launchpad.net precise Release                              
Get:6 http://pr.archive.ubuntu.com precise-updates Release [49.6 kB]      
Get:7 http://security.ubuntu.com precise-security/main Sources [83.7 kB]  
Hit http://extras.ubuntu.com precise/main Sources                         
Hit http://ppa.launchpad.net precise/main Sources                         
Hit http://extras.ubuntu.com precise/main amd64 Packages                  
Hit http://extras.ubuntu.com precise/main i386 Packages                   
Ign http://extras.ubuntu.com precise/main TranslationIndex                
Hit http://ppa.launchpad.net precise/main amd64 Packages                  
Hit http://ppa.launchpad.net precise/main i386 Packages                   
Ign http://ppa.launchpad.net precise/main TranslationIndex                
Get:8 http://pr.archive.ubuntu.com precise-backports Release [49.6 kB]    
Get:9 http://security.ubuntu.com precise-security/restricted Sources [2,494 B]
Get:10 http://security.ubuntu.com precise-security/universe Sources [27.6 kB]
Get:11 http://security.ubuntu.com precise-security/multiverse Sources [1,383 B]
Get:12 http://security.ubuntu.com precise-security/main amd64 Packages [301 kB]
Hit http://pr.archive.ubuntu.com precise/main Sources                     
Hit http://pr.archive.ubuntu.com precise/restricted Sources               
Hit http://pr.archive.ubuntu.com precise/universe Sources                 
Hit http://pr.archive.ubuntu.com precise/multiverse Sources               
Hit http://pr.archive.ubuntu.com precise/main amd64 Packages              
Hit http://pr.archive.ubuntu.com precise/restricted amd64 Packages        
Hit http://pr.archive.ubuntu.com precise/universe amd64 Packages          
Hit http://pr.archive.ubuntu.com precise/multiverse amd64 Packages        
Hit http://pr.archive.ubuntu.com precise/main i386 Packages               
Hit http://pr.archive.ubuntu.com precise/restricted i386 Packages         
Hit http://pr.archive.ubuntu.com precise/universe i386 Packages           
Hit http://pr.archive.ubuntu.com precise/multiverse i386 Packages         
Hit http://pr.archive.ubuntu.com precise/main TranslationIndex            
Hit http://pr.archive.ubuntu.com precise/multiverse TranslationIndex      
Hit http://pr.archive.ubuntu.com precise/restricted TranslationIndex      
Hit http://pr.archive.ubuntu.com precise/universe TranslationIndex        
Get:13 http://pr.archive.ubuntu.com precise-updates/main Sources [411 kB] 
Get:14 http://security.ubuntu.com precise-security/restricted amd64 Packages [4,627 B]
Get:15 http://security.ubuntu.com precise-security/universe amd64 Packages [80.2 kB]
Get:16 http://security.ubuntu.com precise-security/multiverse amd64 Packages [2,186 B]
Get:17 http://security.ubuntu.com precise-security/main i386 Packages [316 kB]
Ign http://extras.ubuntu.com precise/main Translation-en_US               
Ign http://ppa.launchpad.net precise/main Translation-en_US               
Ign http://extras.ubuntu.com precise/main Translation-en                  
Ign http://ppa.launchpad.net precise/main Translation-en                  
Get:18 http://pr.archive.ubuntu.com precise-updates/restricted Sources [5,467 B]
Get:19 http://pr.archive.ubuntu.com precise-updates/universe Sources [93.4 kB]
Get:20 http://pr.archive.ubuntu.com precise-updates/multiverse Sources [6,582 B]
Get:21 http://pr.archive.ubuntu.com precise-updates/main amd64 Packages [668 kB]
Get:22 http://security.ubuntu.com precise-security/restricted i386 Packages [4,620 B]
Get:23 http://security.ubuntu.com precise-security/universe i386 Packages [83.1 kB]
Get:24 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,371 B]
Hit http://security.ubuntu.com precise-security/main TranslationIndex     
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex
Hit http://security.ubuntu.com precise-security/universe TranslationIndex 
Hit http://security.ubuntu.com precise-security/main Translation-en       
Hit http://security.ubuntu.com precise-security/multiverse Translation-en 
Get:25 http://pr.archive.ubuntu.com precise-updates/restricted amd64 Packages [10.1 kB]
Hit http://security.ubuntu.com precise-security/restricted Translation-en 
Get:26 http://pr.archive.ubuntu.com precise-updates/universe amd64 Packages [211 kB]
Hit http://security.ubuntu.com precise-security/universe Translation-en   
Get:27 http://pr.archive.ubuntu.com precise-updates/multiverse amd64 Packages [13.6 kB]
Get:28 http://pr.archive.ubuntu.com precise-updates/main i386 Packages [689 kB]
Get:29 http://pr.archive.ubuntu.com precise-updates/restricted i386 Packages [10.0 kB]
Get:30 http://pr.archive.ubuntu.com precise-updates/universe i386 Packages [214 kB]
Get:31 http://pr.archive.ubuntu.com precise-updates/multiverse i386 Packages [13.8 kB]
Hit http://pr.archive.ubuntu.com precise-updates/main TranslationIndex    
Hit http://pr.archive.ubuntu.com precise-updates/multiverse TranslationIndex
Hit http://pr.archive.ubuntu.com precise-updates/restricted TranslationIndex
Hit http://pr.archive.ubuntu.com precise-updates/universe TranslationIndex
Get:32 http://pr.archive.ubuntu.com precise-backports/main Sources [2,935 B]
Get:33 http://pr.archive.ubuntu.com precise-backports/restricted Sources [14 B]
Get:34 http://pr.archive.ubuntu.com precise-backports/universe Sources [35.2 kB]
Get:35 http://pr.archive.ubuntu.com precise-backports/multiverse Sources [5,311 B]
Get:36 http://pr.archive.ubuntu.com precise-backports/main amd64 Packages [2,378 B]
Get:37 http://pr.archive.ubuntu.com precise-backports/restricted amd64 Packages [14 B]e.ubuntu.com precise-backports/multiverse amd64 Packages [5,206 B]
Get:40 http://pr.archive.ubuntu.com precise-backports/main i386 Packages [2,390 B]
Get:41 http://pr.archive.ubuntu.com precise-backports/restricted i386 Packages [14 B]
Get:42 http://pr.archive.ubuntu.com precise-backports/universe i386 Packages [36.1 kB]
Get:43 http://pr.archive.ubuntu.com precise-backports/multiverse i386 Packages [5,178 B]
Get:44 http://pr.archive.ubuntu.com precise-backports/main TranslationIndex [72 B]
Get:45 http://pr.archive.ubuntu.com precise-backports/multiverse TranslationIndex [72 B]
Get:46 http://pr.archive.ubuntu.com precise-backports/restricted TranslationIndex [70 B]
Get:47 http://pr.archive.ubuntu.com precise-backports/universe TranslationIndex [73 B]
Hit http://pr.archive.ubuntu.com precise/main Translation-en              
Hit http://pr.archive.ubuntu.com precise/multiverse Translation-en        
Hit http://pr.archive.ubuntu.com precise/restricted Translation-en        
Hit http://pr.archive.ubuntu.com precise/universe Translation-en          
Hit http://pr.archive.ubuntu.com precise-updates/main Translation-en      
Hit http://pr.archive.ubuntu.com precise-updates/multiverse Translation-en
Hit http://pr.archive.ubuntu.com precise-updates/restricted Translation-en
Hit http://pr.archive.ubuntu.com precise-updates/universe Translation-en  
Hit http://pr.archive.ubuntu.com precise-backports/main Translation-en    
Hit http://pr.archive.ubuntu.com precise-backports/multiverse Translation-en
Hit http://pr.archive.ubuntu.com precise-backports/restricted Translation-en
Get:48 http://pr.archive.ubuntu.com precise-backports/universe Translation-en [26.5 kB]
Fetched 3,562 kB in 16s (210 kB/s)                                        
Reading package lists... Done
gustavo@TheGagModule:~$ iwconfig
eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     802.11b/g/n  Mode:Managed  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

sudo lshw -C network
```
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 06
       serial: d0:27:88:9d:b2:16
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168e-2.fw ip=10.0.0.66 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:40 ioport:e800(size=256) memory:fafff000-faffffff memory:faff8000-faffbfff
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       bus info: usb@1:1.1
       logical name: wlan0
       serial: 00:24:01:a4:14:1f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=rtl819xU multicast=yes wireless=802.11b/g/n
```

Since the device is found, I assume that this has an obvious solution that my simplistic Windows mind doesn't seem to know? Most of the things I find online assume that Ubuntu has all the Wireless networks on the drop down list at the top of the desktop, or they're mostly about driver installation. I attempted to add a wireless connection in the "edit connections" by adding the connection but that didn't do anything.

---

### Post by Bucky Ball on 2013-07-31
Right click the network icon, is enable networking and enable wireless ticked? If they are, unclick and retick them. If they aren't let us know. 

That card is fine and good to go, just disabled. The driver is in the kernel and installed. After that last upgrade you might want to try restarting. Leave the dongle in through the restart and see what pops up. 

Yes, this should be a short road to a fix. The card may be disabled by previous tweaking but we'll find out. ;)

* Just for clarity, how exactly are you connecting to the internet? Are you connecting to a wireless router/modem and is it sending you an IP address or are you setting static ones at the local machine? You might want to click the network icon and see if you access point/router is listed.

---

### Post by m86 on 2013-07-31
You do indeed need the driver (and firmware) for RTL8192U installed to use the thing.

AFAIK, the driver is in staging - it should be (and is, per your logs) included by default. I don't think the firmware is currently packaged (your logs show it fails to load).. although it may have been at some point.

[The driver set provided by D-Link on their FTP server should have what you need.]("http://aptosid.com/index.php?name=PNphpBB2&file=viewtopic&p=10544") A quick download of [that]("ftp://ftp.dlink.com/Wireless/dwa130_revC/Drivers/dwa130_revC_drivers_linux_006.zip") and a movement of the '*RTL8192U*' directory located under the root folder in '*Firmware*' to your distro's firmware directory (presumably */lib/firmware*) should hopefully get the device up and running.

---

### Post by praseodym on 2013-07-31
Check this one:

[http://ubuntuforums.org/showthread.php?t=1707785](http://ubuntuforums.org/showthread.php?t=1707785)

starting with #8

---

### Post by sE7DNzA on 2013-07-31
Thank you all! I got it all working by following the instructions in that link. Being bad at ubuntu is kinda fun :P

---

