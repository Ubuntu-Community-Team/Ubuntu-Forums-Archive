---
title: "Ubuntu 9.10 SIS 191 Force Gbit to 100 mbit"
date: 2009-10-31
forum: Networking &amp; Wireless
---

### Post by hoos on 2009-10-31
Hi All,

I just entered this forum, so if I ask any dumb questions.. please forgive me. ,)

As wel all know the sis191 driver in ubuntu is quite buggy.. there has been a lot of problems with it in my past experience.
Anyhow.. 

I just installed 9.10 and my internal laptop network card is recognised and I CAN surf the net on a wired interface. (when I set the MTU to 1250 or so)

only problem is that I have an instable connections (my guess is due collisions.)
My router is a Gbit router.. so I have a gbit connection to my DIR 655.. 
When I use my laptop directly to my WAN.. (which is 100 mbit) I have no collisions and the connection is perfect..
When my router comes in between.. the system recognises the gbit connection and then I have collisions. :(
My guess is that the sis191 driver doesnt handle gbit connections that well.

I tried forcing ubuntu to work on 100 mbit instead of the gbit.. 
but if I force ubuntu to use 100 mbit (in ethtool it state it uses 100 mbit.. but in dmesg is says 1000 mbit.)

hoos@Asus:/etc/init.d$ sudo mii-tool -F 100baseTx-FD
hoos@Asus:/etc/init.d$ sudo mii-tool 
eth0: negotiated 1000baseT-FD flow-control, link ok

hoos@Asus:/etc/wicd$ sudo /usr/sbin/ethtool -s eth0 speed 100 duplex full
hoos@Asus:/etc/wicd$ 
[27620.040522] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[27630.148037] eth0: mii ext = 0000.
[27630.172035] eth0: mii lpa=cde1 adv=01e1 exp=000d.
[27630.188030] eth0: link on 1000 Mbps Full Duplex mode.
[27630.284030] eth0: mii ext = 0000.
[27630.308030] eth0: mii lpa=cde1 adv=01e1 exp=000d.
[27630.324034] eth0: link on 1000 Mbps Full Duplex mode.
hoos@Asus:/etc$ 
hoos@Asus:/etc$ uname -a
Linux Asus 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux
hoos@Asus:/etc$ 
[sudo] password for hoos: 
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 03)
00:06.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:07.0 PCI bridge: Silicon Integrated Systems [SiS] PCI-to-PCI bridge
00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3400 Series
02:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
hoos@Asus:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:24:8c:1e:b6:08  
          inet addr:192.168.0.195  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1250  Metric:1
          RX packets:176981 errors:0 dropped:0 overruns:0 frame:0
          TX packets:90251 errors:0 dropped:0 overruns:0 carrier:0
          collisions:1203 txqueuelen:1000 
          RX bytes:222996008 (222.9 MB)  TX bytes:6143432 (6.1 MB)
          Interrupt:19 Base address:0xdead 

Update: I tried a new CAT6 cable to rule out any cable issues, unf. no effect. 


any ideas ?

Thanks in advance for any comments!

Hoos

---

### Post by hoos on 2009-11-01
*bump*

---

### Post by bs.jaze on 2009-11-04
hi hoos,
i;m a complete linux noob, and have the same sis191.  when i have connection problems it works to set MTU down, as u did, but then back to auto again.
hope it helps.

---

### Post by hoos on 2009-11-05
Thanks for your response..
Are you using a gbit connection to your router as well ?

if so,
If you key in : ifconfig eth0
do you see collisions in your network connection ?

---

### Post by bs.jaze on 2009-11-05
nope, a sweex, terrible peace of equip..
just after i  replied here got problems again and after fidling around got perfect intenet back with MTU to 1496, saw somewher on the bug platform that that is the max the driver with this card can have. but actually have not really a clue what it is.
sorry i cant help u ,
good luck

---

