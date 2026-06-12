---
title: "wireless DOA after 8.10 &quot;upgrade&quot;"
date: 2008-12-23
forum: Networking &amp; Wireless
---

### Post by digitalramble on 2008-12-23
OK.  Guys, I've been using Ubuntu for two plus years on this same computer.  I have NEVER had trouble with the wireless card in here, EVER.  So I upgrade to 8.10 and suddenly it's acting like wireless just doesn't exist.  From perusing the forum, it's clear that Ubuntu ****** <i>something</i> up although perhaps in a kernel update immediately after 8.10 itself.  

However every time I attempt to find a way to resolve this crap, I run into instructions on how to install ndiswrapper.  This, to me, is a step backwards.  A huge step backwards.  I would be far more understanding of this if I had new hardware or something, but this simply isn't the case.  Something that worked as far back as Warty Warthog is now belly up.  Excuse me?

IS there a way for me to fix this without ndiswrapper?  I've been looking/waiting for a kernel or other update but no joy so far.  

Here's the outline of what I've got, in case anyone has suggestions for solutions not involving ndiswrapper.  If I go to Systems->Administration->Hardware Drivers, it comes up empty handed of *any* drivers of any kind.  Lovely (that probably explains why graphics, while functional, is slowed down as well).  Thanks for any help...



<code>
dr@nemesis $ ifconfig -a
eth1      Link encap:Ethernet  HWaddr 00:00:00:60:be:54  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::200:ff:fe60:be54/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2037486 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1990054 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1555367660 (1.5 GB)  TX bytes:674157215 (674.1 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:151 errors:0 dropped:0 overruns:0 frame:0
          TX packets:151 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13284 (13.2 KB)  TX bytes:13284 (13.2 KB)

pan0      Link encap:Ethernet  HWaddr f2:80:94:f9:87:3f  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)



dr@nemesis $ sudo lshw -C Network
  *-network:0 UNCLAIMED   
       description: Network controller
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 7
       bus info: pci@0000:02:07.0
       version: 05
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=64 maxlatency=24 mingnt=3
  *-network:1
       description: Ethernet interface
       product: 82801DB PRO/100 VE (MOB) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth1
       version: 81
       serial: 00:00:00:60:be:54
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=full firmware=N/A ip=192.168.1.103 latency=66 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: f2:80:94:f9:87:3f
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
dr@nemesis $ sudo lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub



dr@nemesis $ sudo lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3580] (rev 02)
00:00.1 System peripheral [0880]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3584] (rev 02)
00:00.3 System peripheral [0880]: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller [8086:3585] (rev 02)
00:02.0 VGA compatible controller [0300]: Intel Corporation 82852/855GM Integrated Graphics Device [8086:3582] (rev 02)
00:02.1 Display controller [0380]: Intel Corporation 82852/855GM Integrated Graphics Device [8086:3582] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [8086:24c4] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 [8086:24c7] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 81)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge [8086:24cc] (rev 01)
00:1f.1 IDE interface [0101]: Intel Corporation 82801DBM (ICH4-M) IDE Controller [8086:24ca] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller [8086:24c3] (rev 01)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 01)
00:1f.6 Modem [0703]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller [8086:24c6] (rev 01)
02:03.0 CardBus bridge [0607]: Ricoh Co Ltd RL5c476 II [1180:0476] (rev ac)
02:03.1 CardBus bridge [0607]: Ricoh Co Ltd RL5c476 II [1180:0476] (rev ac)
02:03.2 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C552 IEEE 1394 Controller [1180:0552] (rev 04)
02:07.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection [8086:4220] (rev 05)
02:08.0 Ethernet controller [0200]: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller [8086:103d] (rev 81)


dr@nemesis $ sudo uname -m
i686
</code>

Again, thanks for any help...

---

### Post by jsacks on 2009-02-11
I am having the same problem
I get:

jared@dell-desktop:~$ sudo ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device
jared@dell-desktop:~$ 

and

jared@dell-desktop:~$ sudo iwlist wlan0 scanning
wlan0     Interface doesn't support scanning.

and then for this command i get:

this is what i got after running the command:
jared@dell-desktop:~$ lsmod | grep iwl
iwl3945                96920  0
rfkill                 17176  2 iwl3945
lbm_cw_mac80211       215856  1 iwl3945
lib80211               15236  1 iwl3945
lbm_cw_cfg80211        46744  2 iwl3945,lbm_cw_mac80211
led_class              12164  1 iwl3945

I've also tried installing: linux-backports-modules-intrepid
but that doesnt do anything...

Any ideas???????????

---

### Post by digitalramble on 2009-02-12
I did solve this issue, but I had to use the "nuclear option"...that is to say I saved off all my data, reformatted the disk and installed ubuntu clean.

I've been told that the upgrades can sometimes kind of muck things up in a way that a clean complete install won't.  Um, "muck" being the super duper technical term here...

:twisted:

---

### Post by doccpu on 2009-06-13
i have been trying to get a usable linux box for years. Either it wont do as the help files say, cant find software that will run , and now i load 8.10 from scratch and it wont see any wifi at all. No wonder linux hasnt ousted microsoft  yet. It simply doesnt run.
I use samba for a windows file server and it goes monthes with out a problem ( after days getting it to kindah work using hopeless help files. they dont tell you how to set up users that the system doesnt see. and local access to files is different and conflicts with network access to files. ) i have run web servers for over a year  with only 2 reboots to physically move the machine. But i have yet to be able to use linux for even an hour without unusability problems cropping up. No codecs, not see cd, no wifi, no fixes for no wifi. This is getting really frustrating.
what is a version of ubuntu that you can actually use on an acer one?

---

