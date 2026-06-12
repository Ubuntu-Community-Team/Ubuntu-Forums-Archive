---
title: "Realtek RTL8188CE"
date: 2013-02-02
forum: Networking &amp; Wireless
---

### Post by Marcus13345 on 2013-02-02
so I've got Ubuntu fully installed and everything seems to be going quite nicely so far except for one thing. My wireless internet occasionally stops working. it still shows the "bars" in the top left saying that its connected to the router but when i open firefox i am unable to connect. this usually happens about every 20 minutes or so. the only way i have found to fix it (temporarily) is to disable network connection (or just wireless), then re enable them, or just to restart the computer. This problem is specific to linux. i have two hard drives i use, one with ubuntu and the other with windows 7 and fedora. this same error occurs on fedora but not windows 7. when the connection goes out, other computers on the network are still able to connect to the internet. i tried to fix the problem by adding "options iwlwifi 11n_disable=1" to /etc/modprobe.d/iwlwifi.conf

---

### Post by Bucky Ball on 2013-02-02
*Thread moved to **Networking & Wireless**.*

Welcome to the forums. You might have more luck here. ;)

---

### Post by Marcus13345 on 2013-02-02
I would just like to make a point that the problem is getting progressively worse to the point where I can't keep a connection long enough to open one page and click a link. Naturally, I am now posting from an iPod.

---

### Post by ahallubuntu on 2013-02-02
~

---

### Post by Marcus13345 on 2013-02-02
```
marcus@Marcus-Ubuntu:~$ sudo lshw -C network
[sudo] password for marcus: 
PCI (sysfs)  
  *-network               
       description: Ethernet interface
       product: AR8152 v2.0 Fast Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: c1
       serial: e8:9a:8f:84:69:bb
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI duplex=full latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:43 memory:f0100000-f013ffff ioport:3000(size=128)
  *-network
       description: Wireless interface
       product: RTL8188CE 802.11b/g/n WiFi Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: d0:df:9a:75:73:3b
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192ce driverversion=3.5.0-23-generic firmware=N/A ip=10.0.0.14 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 ioport:2000(size=256) memory:f0000000-f0003fff
marcus@Marcus-Ubuntu:~$ 
marcus@Marcus-Ubuntu:~$ iwconfig
eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"august"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 30:46:9A:03:C3:BB   
          Bit Rate=150 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=53/70  Signal level=-57 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:38   Missed beacon:0

marcus@Marcus-Ubuntu:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] Family 12h Processor Root Complex
00:01.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI BeaverCreek [Radeon HD 6520G]
00:01.1 Audio device: Advanced Micro Devices [AMD] nee ATI BeaverCreek HDMI Audio [Radeon HD 6500D and 6400G-6600G series]
00:04.0 PCI bridge: Advanced Micro Devices [AMD] Family 12h Processor Root Port
00:05.0 PCI bridge: Advanced Micro Devices [AMD] Family 12h Processor Root Port
00:11.0 SATA controller: Advanced Micro Devices [AMD] Hudson SATA Controller [AHCI mode]
00:12.0 USB controller: Advanced Micro Devices [AMD] Hudson USB OHCI Controller (rev 11)
00:12.2 USB controller: Advanced Micro Devices [AMD] Hudson USB EHCI Controller (rev 11)
00:13.0 USB controller: Advanced Micro Devices [AMD] Hudson USB OHCI Controller (rev 11)
00:13.2 USB controller: Advanced Micro Devices [AMD] Hudson USB EHCI Controller (rev 11)
00:14.0 SMBus: Advanced Micro Devices [AMD] Hudson SMBus Controller (rev 13)
00:14.2 Audio device: Advanced Micro Devices [AMD] Hudson Azalia Controller (rev 01)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] Hudson LPC Bridge (rev 11)
00:14.4 PCI bridge: Advanced Micro Devices [AMD] Hudson PCI Bridge (rev 40)
00:14.5 USB controller: Advanced Micro Devices [AMD] Hudson USB OHCI Controller (rev 11)
00:16.0 USB controller: Advanced Micro Devices [AMD] Hudson USB OHCI Controller (rev 11)
00:16.2 USB controller: Advanced Micro Devices [AMD] Hudson USB EHCI Controller (rev 11)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 0 (rev 43)
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 6
00:18.6 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 5
00:18.7 Host bridge: Advanced Micro Devices [AMD] Family 12h/14h Processor Function 7
01:00.0 Ethernet controller: Atheros Communications Inc. AR8152 v2.0 Fast Ethernet (rev c1)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
marcus@Marcus-Ubuntu:~$ lsusb
Bus 001 Device 003: ID 0480:b001 Toshiba America Info. Systems, Inc. 
Bus 001 Device 004: ID 1a40:0101 Terminus Technology Inc. 4-Port HUB
Bus 004 Device 002: ID 046d:0a38 Logitech, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 046d:c52f Logitech, Inc. Wireless Mouse M305
Bus 001 Device 006: ID 046d:c31c Logitech, Inc. Keyboard K120 for Business
Bus 001 Device 007: ID 046d:08af Logitech, Inc. QuickCam Easy/Cool
marcus@Marcus-Ubuntu:~$
```

---

### Post by ahallubuntu on 2013-02-03
OK - first of all, in your original post you said you tried the fix "options iwlwifi 11n_disable=1" which is for Intel wireless cards.  But you don't have an Intel wireless card; you have a Realtek card, an RTL8188CE.  The fix you tried for the Intel card will have no effect on a Realtek card.

You seem to be on Ubuntu 12.10.  People have complained about issues with RTL8188CE in Ubuntu 12.04/12.10.  The good news is: Realtek provides updated Linux drivers on their website:

[http://www.realtek.com.tw/downloads/](http://www.realtek.com.tw/downloads/)

The bad news: people have had trouble building the RTL8188CE driver in Ubuntu.  They get a "make" error probably due to some missing packages.  I have managed to build this driver but I have installed many development packages - can't tell you which ones would allow an error-free build.  And I don't even have this card to test the driver on - I don't even know if the new driver works better but I suspect it does.

---

### Post by Marcus13345 on 2013-02-03
How would i go about trying to get this new driver to work on my computer? I've got the new driver's sources, though i'm unsure where to go from there.

---

### Post by Bucky Ball on 2013-02-03
There should be step by step instructions downloaded as part of that driver. Go in the folder where you've extracted/saved it and look for 'ReadMe' file.

---

### Post by Marcus13345 on 2013-02-03
I read the readme file and proceeded to do what it asked of me. it all went smoothly until it told me that i was missing some files. i did a quick google search of the directory it was trying to access and found the package to get for it. after install said package, i then went back and retried "make install". And again, i got the same error, claiming there is no such directory /lib/modules/3.5.0-23-generic/build

```
marcus@Marcus-Ubuntu:~/Desktop/RTL$ ls
base.c                              core.c    pci.c   release_note
base.h                              core.h    pci.h   rtl8188ee
cam.c                               debug.c   ps.c    rtl8192ce
cam.h                               debug.h   ps.h    rtl8192de
compat                              efuse.c   rc.c    rtl8192se
compat.h                            efuse.h   rc.h    rtl8723e
compat-wireless-3.0-2-mesh.tar.bz2  firmware  readme  stats.c
compat-wireless-3.0-2.tar.bz2       Kconfig   regd.c  stats.h
compat-wireless-3.2.5-1.tar.bz2     Makefile  regd.h  wifi.h
marcus@Marcus-Ubuntu:~/Desktop/RTL$ make
make -C /lib/modules/3.5.0-23-generic/build M=/home/marcus/Desktop/RTL modules
make: *** /lib/modules/3.5.0-23-generic/build: No such file or directory.  Stop.
make: *** [all] Error 2
marcus@Marcus-Ubuntu:~/Desktop/RTL$
```

---

### Post by Bucky Ball on 2013-02-03
sudo make
sudo make install

Make sure you have cd 'ed to the correct directory. It will be a directory inside the extracted directory, NOT just the extracted directory.

---

### Post by Marcus13345 on 2013-02-03
The readme told me to "make" in the root of the extracted directory. Also I checked for the folder it says is missing and all of them exist except for the build directory. Also, "make" didn't do anything different when I tried as a super user.

---

### Post by ahallubuntu on 2013-02-03
~

---

