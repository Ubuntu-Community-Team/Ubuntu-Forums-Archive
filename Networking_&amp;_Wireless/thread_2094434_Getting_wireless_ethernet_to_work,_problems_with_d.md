---
title: "Getting wireless ethernet to work, problems with drivers."
date: 2012-12-13
forum: Networking &amp; Wireless
---

### Post by Buruk on 2012-12-13
A few things you need to know. I'm new to linux. I'm actually using mint 14, but figured it was close enough to ubuntu that there wouldn't be much difference when it comes to this. I'd go to the mint forums but people here seem to be much more knowledgeable. I'm completely new to any wireless networking with linux, so there may be some stupid step I'm not getting.



I have WICD installed and it doesn't detect any wireless networks. My windows vista installation connects fine so it can't be a hardware problem. The wired connection works. I assumed it was the driver at fault so went to the marvell website and installed the fedora 2.6 driver. I know fedora's not the same as ubuntu, and 2.6 isn't 3.5.0 (my kernel) but the driver has worked for others, and it's the newest one they have. I went through the install process and at the end got an error on compiling the kernel.

Here's what I did

paula@paula-Inspiron-1545 ~ $ cd /home/paula/Downloads
paula@paula-Inspiron-1545 ~/Downloads $ tar xfvj install_v10.92.1.3.tar.bz2
DriverInstall/
DriverInstall/sk98lin.tar.bz2
DriverInstall/functions
DriverInstall/install.sh
DriverInstall/sk98lin.4
DriverInstall/README
paula@paula-Inspiron-1545 ~/Downloads $ cd DriverInstall
paula@paula-Inspiron-1545 ~/Downloads/DriverInstall $ sudo bash ./install.sh
[sudo] password for paula: 


Installation script for sk98lin driver.
Version 10.92.1.3 (Jan-26-2012)
(C)Copyright 2003-2011 Marvell(R).
====================================================
Add to your trouble-report the logfile install.log
which is located in the  DriverInstall directory.
====================================================


1) installation          3) generate makefile
2) generate patch     4) exit
Choose your favorite installation method: 1











Please read this carefully!

This script will automatically compile and load the sk98lin
driver on your host system. Before performing both compilation
and loading, it is necessary to shutdown any device using the
sk98lin kernel module and to unload the old sk98lin kernel 
module. This script will do this automatically per default.
 
Please plug a card into your machine. Without a card we aren't
able to check the full driver functionality.

Do you want proceed? (y/N) y




































IMPORTANT INFORMATION!

We found an alternative driver for your Marvell product on this system.
The alternative driver is _NOT_ directly supported by Marvell and does not
include all features provided by your device. If you want to use the
sk98lin driver developed by Marvell, you may choose either to deactivate
or remove the alternative driver.

[PRESS ANY KEY FOR FURTHER INSTRUCTIONS]
 














Do nothing:
  - The sk98lin will be installed
  NOTE: It may happen that the alternative driver will be loaded on 
  the next boot process. In this case the Marvell driver _WON'T_ be
  loaded.

Deactivate driver:
  - The alternative driver will be renamed to _skge.ko or _sky2.ko
  - All references in the /etc/modprobe.conf file will be changed to
    the sk98lin driver
  - The alternative driver will be unloaded
  - The sk98lin driver will be installed

Remove driver (recommended):
  - The alternative driver will be removed from your system
  - All references in the /etc/modprobe.conf file will be changed to
    the sk98lin driver
  - The alternative driver will be unloaded
  - The sk98lin driver will be installed


1) Do nothing
2) Deactivate diver
3) Remove driver
Action: 3

Disconnect alternative devices:  (done)                              [   OK   ]
Unload alternative driver (done)                                     [   OK   ]
Create tmp dir (/tmp/Sk98IoNfbJANaPPIGiLDaJfaE)                      [   OK   ]
Check user id (0)                                                    [   OK   ]
Check kernel version (3.5.0-17-generic)                              [   OK   ]
Check kernel symbol file (/proc/kallsyms)                            [   OK   ]
Check kernel type (SMP)                                              [   OK   ]
Check number of CPUs (2)                                             [   OK   ]
Check architecture (found)                                           [   OK   ]
Set architecture (x86_64)                                            [   OK   ]
Check compiler (/usr/bin/gcc)                                        [   OK   ]
Check mcmodel flags (kernel)                                         [   OK   ]
Check module support (/sbin/insmod)                                  [   OK   ]
Check make (/usr/bin/make)                                           [   OK   ]
Check kernel gcc version (4.7.2) (Kernel:4.7.2 == gcc:4.7.2)         [   OK   ]
Check sk98lin driver availability (not loaded)                       [   OK   ]
Check kernel header files (/lib/modules/3.5.0-17-generic/build)      [   OK   ]
Check driver location (/lib/modules/3.5.0-17-generic/build/drivers/net/ethernet/marvell)                                                             [   OK   ]
Check sources for .config file (/lib/modules/3.5.0-17-generic/build/.[   OK   ]
Copy and check .config file (done)                                   [   OK   ]
Check the mem address space (lowmem)                                 [   OK   ]
Change IOMMU (enabled)                                               [   OK   ]
Create new .config file (done)                                       [   OK   ]
Execute: make oldconfig (done)                                       [   OK   ]
Check modpost availability (available)                               [   OK   ]
Unpack the sources (done)                                            [   OK   ]
Check firmware availability (done)                                   [   OK   ]
Check kernel header version (not recognized)                         [  warn  ]
Check kernel functions (Changed: nothing)                            [   OK   ]
Compile the kernel (error)                                           [ failed ]

An error has occurred during the compile proces which prevented 
the installation from completing.                              
Take a look at the log file install.log for more informations.  
Installation of package failed.
paula@paula-Inspiron-1545 ~/Downloads/DriverInstall $ 

Then I decided just to try the windows driver.
I downloaded the windows driver

I opened Windows Wireless Drivers driver instillation tool, tried to install the driver and got FATAL: Module ndiswrapper not found.
I tried the steps outlined in the following threads and still got the same error.
[http://askubuntu.com/questions/132894/how-to-fix-ndiswrapper-not-found](http://askubuntu.com/questions/132894/how-to-fix-ndiswrapper-not-found)
[https://forums.virtualbox.org/viewtopic.php?t=1493](https://forums.virtualbox.org/viewtopic.php?t=1493)
The only thing different I did was in the last thread I didn't install virtualbox, but tried to install ndiswrapper again with no results.
Also there is a problem where things like ndiswrapper-util or something like that aren't installed by default, I installed all things related to ndiswrapper but still got the error. 



I don't really know where to go from here, any help would be appreciated  greatly.

---

### Post by ahallubuntu on 2012-12-13
This isn't the answer you were looking for but...if you have an Inspiron 1545 as it appears you do, I suggest you spend $10 or less on a new wireless card that works automatically in all recent versions of Linux.  I have a 1545, and the wireless card is extremely easy to get to from the bottom.  Unscrew the panel, the one screw (I think) to remove the wireless card itself.  Remove the two antenna wires carefully (they pop off), remove card and replace.  Look on YouTube for lots of examples of replacing an internal wireless card on a laptop.  If you can get to the card easily, replacing it is simple.

Your existing card is probably a Broadcom G card anyway - I think my original was.  You can get an Intel WiFi Link 5100 card instead that is 802.11n.  You want a HALF-height card (not a full-height card), and you want one that is *NOT* an HP or Lenovo version.  Get one for Dell or Toshiba or Sony or Acer (or generic).  If you are in North America, I recommend getting a used card off eBay and avoiding the "new" ones from Asia that I've personally had bad luck with (versions often don't match what was advertised).

FYI, my 1545 shows a Marvell WIRED ethernet controller (88E8040).  I think you have a Broadcom card, not a Marvell wireless card.  Look at your lspci again.

---

### Post by chili555 on 2012-12-13
Aside from the multitude of issues here, Mint with a Fedora driver; a driver designed for kernel version 2.6 on a 3.5 kernel and the probable lack of kernel headers needed to compile from source, *sky2* and it's great-grandfather *sk98lin* (I wonder if '98' refers to 1998 or maybe even 1898) are ethernet drivers, not wireless.> $ modinfo sky2
filename:       /lib/modules/3.5.0-19-generic/kernel/drivers/net/ethernet/marvell/sky2.ko
version:        1.30
license:        GPL
author:         Stephen Hemminger <shemminger@linux-foundation.org>
description:    Marvell Yukon 2 Gigabit Ethernet driver
Now let's try to see what wireless driver you really need. Please run and post:```
lspci -nn | grep 0280
rfkill list all
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by Buruk on 2012-12-13
Here's what I get. 

paula@paula-Inspiron-1545 ~ $ lspci -nn | grep 0280
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
paula@paula-Inspiron-1545 ~ $ rfkill list all
paula@paula-Inspiron-1545 ~ $

---

### Post by chili555 on 2012-12-13
Please hook up the ethernet temporarily and do:```
sudo apt-get install linux-headers-generic
sudo apt-get install --reinstall bcmwl-kernel-source
sudo modprobe wl
```Detach the ethernet cable and tell us if the wireless is working.

This is a controversial little device and there are two theories on the right way to drive it. As Sinatra says, I did it my way.

---

### Post by Buruk on 2012-12-13
I stupidly forgot to save the output from the terminal before shutting down the computer. 

There was some about 6 errors about some file not being there, unfortunately I can't remember what exactly it said. There were still no networks found.

---

### Post by chili555 on 2012-12-13
> There was some about 6 errors about some file not being there, unfortunately I can't remember what exactly it said. It will be difficult to propose a solution without the exact error.

Please try this first:```
sudo apt-get install linux-headers-generic 
sudo apt-get install bcmwl-kernel-source
sudo modprobe wl
```Please capture and report any errors.

I will be out for an hour or so and will try to check in later.

---

### Post by Buruk on 2012-12-13
Here's the output. I'm guessing the stuff that was ran has to be deleted and then installed again to get the errors. I'll wait further instruction.

paula@paula-Inspiron-1545 ~ $ sudo apt-get install linux-headers-generic[sudo] password for paula: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
paula@paula-Inspiron-1545 ~ $ sudo apt-get install bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
bcmwl-kernel-source is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
paula@paula-Inspiron-1545 ~ $ sudo modprobe wl
paula@paula-Inspiron-1545 ~ $

---

### Post by chili555 on 2012-12-13
Now your wireless should be working! How about:```
rfkill list all
iwconfig
sudo iwlist eth1 scan
```

---

### Post by Buruk on 2012-12-14
This is interesting.

paula@paula-Inspiron-1545 ~ $ rfkill list all
0: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
paula@paula-Inspiron-1545 ~ $ iwconfig
eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

lo        no wireless extensions.

paula@paula-Inspiron-1545 ~ $ sudo iwlist eth1 scan
[sudo] password for paula: 
eth1      Failed to read scan data : Invalid argument

paula@paula-Inspiron-1545 ~ $

---

### Post by Buruk on 2012-12-14
I just found out I need to press that little button with the tower image, now it isn't hard blocked.
Upon re-doing your instructions (after pressing the key) I got this.

```
paula@paula-Inspiron-1545 ~ $ rfkill list all
0: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
paula@paula-Inspiron-1545 ~ $ iwconfig
eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

lo        no wireless extensions.

paula@paula-Inspiron-1545 ~ $ sudo iwlist eth1 scan
[sudo] password for paula: 
eth1      Scan completed :
          Cell 01 - Address: E0:91:F5:BB:52:01
                    ESSID:"epperson"
                    Mode:Managed
                    Frequency=2.422 GHz (Channel 3)
                    Quality:5/5  Signal level:-28 dBm  Noise level:-92 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD7A0050F204104A0001101044000102103B0001031047001000000000000010000000E091F5BB5201102100044E54475210230009776E72323030307633102400016E104200046E6F6E651054000800060050F204000110110016574E5232303030763328576972656C65737320415029100800020086103C000103
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 02 - Address: 84:1B:5E:71:9E:A8
                    ESSID:"NETGEAR55"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:1/5  Signal level:-86 dBm  Noise level:-92 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD7A0050F204104A0001101044000102103B0001031047001000000000000010000000841B5E719EA8102100044E54475210230009776E72323030307633102400016E104200046E6F6E651054000800060050F204000110110016574E5232303030763328576972656C65737320415029100800020086103C000103
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 03 - Address: A0:21:B7:B9:DE:E3
                    ESSID:"Edmister"
                    Mode:Managed
                    Frequency=2.432 GHz (Channel 5)
                    Quality:1/5  Signal level:-83 dBm  Noise level:-92 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD7F0050F204104A0001101044000102103B0001031047001000000000000010000000A021B7B9DEE3102100044E54475210230009776E72323030307633102400016E104200046E6F6E651054000800060050F20400011011001B574E5232303030763328576972656C6573732041502D322E344729100800020086103C000103
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 04 - Address: 00:07:7D:14:E7:90
                    ESSID:"ciscosb - house"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:1/5  Signal level:-83 dBm  Noise level:-92 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 12 Mb/s
                              24 Mb/s; 48 Mb/s
          Cell 05 - Address: 98:FC:11:4C:FA:CE
                    ESSID:"CleverDog"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:1/5  Signal level:-86 dBm  Noise level:-92 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD810050F204104A00011010440001021041000100103B0001031047001058C50787EBA995D182D4DD88850618F21021000C4C696E6B73797320496E632E1023000D4C696E6B7379732045323030301024000776312E302E30311042000234321054000800060050F20400011011000D4C696E6B737973204532303030100800020084
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 06 - Address: 98:FC:11:4C:FA:CF
                    ESSID:"CleverDog-guest"
                    Mode:Managed
                    Frequency=2.462 GHz (Channel 11)
                    Quality:1/5  Signal level:-89 dBm  Noise level:-92 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s

paula@paula-Inspiron-1545 ~ $
```

---

### Post by chili555 on 2012-12-14
> paula@paula-Inspiron-1545 ~ $ sudo iwlist eth1 scan
[sudo] password for paula: 
eth1      Scan completed :
          Cell 01 - Address: E0:91:F5:BB:52:01
                    ESSID:"epperson"
                    Mode:Managed
                    Frequency=2.422 GHz (Channel 3)
                    Quality:5/5  Signal level:-28 dBm  Noise level:-92 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
<snip>Excellent. Now can you click the Network Manager icon, see your network and connect?

---

### Post by Buruk on 2012-12-14
It just started working now. For a while no networks were detected.

I guess the problem is solved unless there's something else I should do.

Thank you for your help. You have ended the 4 day long reign of terror this problem has created.

---

### Post by chili555 on 2012-12-14
The only things left to do are to use thread tools at the top to mark Solved and have fun!> You have ended the 4 day long reign of terror this problem has created.We aim to do just that.

---

