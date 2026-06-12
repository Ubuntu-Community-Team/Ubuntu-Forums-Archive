---
title: "Wireless Internet not working....?"
date: 2010-02-14
forum: Networking &amp; Wireless
---

### Post by Nihilius on 2010-02-14
I recently installed Ubuntu.
 
 
I just installed ndiswrapper so I could install my wireless PCI [URL="http://www.linuxforums.org/forum/#"][COLOR=blue][COLOR=blue ! important][FONT=Verdana][COLOR=blue ! important][FONT=Verdana]card [/FONT][/COLOR][COLOR=blue ! important][FONT=Verdana]drivers[/FONT][/COLOR][/FONT][/COLOR][/COLOR][IMG]http://kona.kontera.com/javascript/lib/imgs/grey_loader.gif[/IMG]
[/URL].
 
 
I did that and it is recognized and so is the network I want to connect to.
 
 
But for some reason, it just wont connect. It will spend a long time trying to connect, but then just says "disconnected".
 
 
What could be the problem? It's not like I have a bad connection or anything. My internet on Windows is fast.
 
 
Thanks!

---

### Post by northd_tech on 2010-02-14
Can you post the results when you run the following commands from a terminal in Ubuntu?

```
lspci

lsusb

lsmod

uname -a

sudo lshw -C network 

ifconfig

iwconfig
```

---

### Post by Nihilius on 2010-02-15
lspci-00:00.0 Host bridge: Intel Corporation 82925X/XE Memory Controller Hub (rev 04)

00:01.0 PCI bridge: Intel Corporation 82925X/XE PCI Express Root Port (rev 04)

00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)

00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)

00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)

00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)

00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)

00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)

00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)

00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)

00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)

00:1f.2 IDE interface: Intel Corporation 82801FR/FRW (ICH6R/ICH6RW) SATA Controller (rev 03)

00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)

01:00.0 VGA compatible controller: nVidia Corporation G80 [GeForce 8800 GTS] (rev a2)

02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)

04:02.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)


lsusb-Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 001 Device 002: ID 058f:6331 Alcor Micro Corp. 

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 003 Device 002: ID 045e:0083 Microsoft Corp. Basic Optical Mouse

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


lsmod-Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 001 Device 002: ID 058f:6331 Alcor Micro Corp. 

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 003 Device 002: ID 045e:0083 Microsoft Corp. Basic Optical Mouse

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

cowslayer@ubuntu:~$ lsmod

Module                  Size  Used by

nls_iso8859_1           3740  1 

nls_cp437               5372  1 

vfat                   10716  1 

fat                    51452  1 vfat

binfmt_misc             8356  1 

snd_intel8x0           30168  2 

snd_ac97_codec        101216  1 snd_intel8x0

ac97_bus                1532  1 snd_ac97_codec

snd_pcm_oss            37920  0 

snd_mixer_oss          16028  1 snd_pcm_oss

snd_pcm                75296  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss

snd_seq_dummy           2656  0 

snd_seq_oss            28576  0 

snd_seq_midi            6432  0 

snd_rawmidi            22208  1 snd_seq_midi

snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi

snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event

snd_timer              22276  2 snd_pcm,snd_seq

snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq

iptable_filter          3100  0 

ip_tables              11692  1 iptable_filter

snd                    59204  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device

soundcore               7264  1 snd

snd_page_alloc          9156  2 snd_intel8x0,snd_pcm

dell_wmi                2564  0 

ppdev                   6688  0 

lp                      8964  0 

x_tables               16544  1 ip_tables

parport_pc             31940  1 

dcdbas                  7292  0 

parport                35340  3 ppdev,lp,parport_pc

usbhid                 38208  0 

usb_storage            52544  1 

tg3                   109600  0 

uname -a - Linux ubuntu 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux


sudo lshw -C network -network               

       description: Ethernet interface

       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express

       vendor: Broadcom Corporation

       physical id: 0

       bus info: pci@0000:02:00.0

       logical name: eth0

       version: 01

       serial: 00:11:11:a1:55:f0

       capacity: 1GB/s

       width: 64 bits

       clock: 33MHz

       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation

       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.99 firmware=5751-v3.23a latency=0 link=no multicast=yes port=twisted pair

       resources: irq:16 memory:dbff0000-dbffffff

  *-network UNCLAIMED

       description: Ethernet controller

       product: 88w8335 [Libertas] 802.11b/g Wireless

       vendor: Marvell Technology Group Ltd.

       physical id: 2

       bus info: pci@0000:04:02.0

       version: 03

       width: 32 bits

       clock: 66MHz

       capabilities: pm bus_master cap_list

       configuration: latency=64

       resources: memory:dbde0000-dbdeffff memory:dbdf0000-dbdfffff


ifconfig-eth0      Link encap:Ethernet  HWaddr 00:11:11:a1:55:f0  

          UP BROADCAST MULTICAST  MTU:1500  Metric:1

          RX packets:0 errors:0 dropped:0 overruns:0 frame:0

          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

          Interrupt:16 



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:4 errors:0 dropped:0 overruns:0 frame:0

          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

iwconfig-lo        no wireless extensions.



eth0      no wireless extensions.



















That's all of it.

---

### Post by northd_tech on 2010-02-15
> **Nihilius said:**
> lspci
02:00.0 Ethernet controller: **Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)**
04:02.0 Ethernet controller: [COLOR=Blue]**Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)**[/COLOR]

lsmod
Module                  Size  Used by
nls_iso8859_1           3740  1 
nls_cp437               5372  1 
binfmt_misc             8356  1 
tg3                   109600  0 

uname -a 
 Linux ubuntu 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux

sudo lshw -C network -network               
description: Ethernet interface
product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:02:00.0
logical name: eth0
version: 01
serial: 00:11:11:a1:55:f0
capacity: 1GB/s
width: 64 bits
clock: 33MHz
capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.99 firmware=5751-v3.23a latency=0 link=no multicast=yes port=twisted pair
resources: irq:16 memory:dbff0000-dbffffff

*-network UNCLAIMED
description: Ethernet controller
product: 88w8335 [Libertas] 802.11b/g Wireless
vendor: Marvell Technology Group Ltd.
physical id: 2
bus info: pci@0000:04:02.0
version: 03
width: 32 bits
clock: 66MHz
capabilities: pm bus_master cap_list
configuration: latency=64
resources: memory:dbde0000-dbdeffff memory:dbdf0000-dbdfffff

ifconfig-
eth0      Link encap:Ethernet  HWaddr 00:11:11:a1:55:f0  
UP BROADCAST MULTICAST  MTU:1500  Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
Interrupt:16 

lo        Link encap:Local Loopback  
inet addr:127.0.0.1  Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING  MTU:16436  Metric:1
RX packets:4 errors:0 dropped:0 overruns:0 frame:0
TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

iwconfig-
lo        no wireless extensions.
eth0      no wireless extensions.

Well, your wireless card is a [COLOR=Blue]**Marvell Technology Group Ltd. 88w8335 [Libertas]  802.11b/g Wireless (rev 03)**[COLOR=Black], and the other bolded part is your ethernet (cable) internet connection.

Unfortunately, I've never even heard of that WiFi interface- I'm thinking it must be pretty new.
[/COLOR][/COLOR] 
A quick search here found these 2 threads, each of which appears to have a fix:

[http://ubuntuforums.org/showthread.php?t=1370309&highlight=Marvell+88w8335](http://ubuntuforums.org/showthread.php?t=1370309&highlight=Marvell+88w8335)

[http://ubuntuforums.org/showthread.php?t=976928&highlight=Marvell+88w8335](http://ubuntuforums.org/showthread.php?t=976928&highlight=Marvell+88w8335)

I'd give those threads a read and see if any of that helps.

edit:  Also- you're running this 32-bit kernel: 2.6.31-14-generic

---

