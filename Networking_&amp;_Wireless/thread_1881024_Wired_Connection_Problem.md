---
title: "Wired Connection Problem"
date: 2011-11-14
forum: Networking &amp; Wireless
---

### Post by dparry711 on 2011-11-14
I am having a problem with a Wired internet connection. Since upgrading to 11.10 my internet is ridiculously slow, at times slowing down to less than 20kb/sec. This is a wired connection and when I connect another computer to it I do not have the same problem so I am pretty confident that it is the computer not the connection. At times the connection works fairly well, and then slows way down. For the most part though it is slow. It is connected though as I can ping or run the host command from the terminal. I am a newbie to this I searched the forums and found similar problems but none that seemed to fit mine (I tried a few of the solutions which didn't seem to work/apply). 

Here is the info I saw people asking for on the other forums.

```
lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:16.3 Serial controller: Intel Corporation 5 Series/3400 Series Chipset KT Controller (rev 06)
00:19.0 Ethernet controller: Intel Corporation 82578DM Gigabit Network Connection (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation 3400 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
01:00.0 VGA compatible controller: nVidia Corporation G92 [GeForce 9800 GT] (rev a2)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
```

```
sudo lshw -C network
[sudo] password for david: 
  *-network               
       description: Ethernet interface
       product: 82578DM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 06
       serial: 70:f3:95:00:64:3e
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.3.10-k2 duplex=full firmware=0.12-2 ip=192.168.1.138 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:41 memory:fb120000-fb13ffff memory:fb148000-fb148fff ioport:f040(size=32)

```

```
ifconfig
eth0      Link encap:Ethernet  HWaddr 70:f3:95:00:64:3e  
          inet addr:192.168.1.138  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::72f3:95ff:fe00:643e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:56295 errors:0 dropped:0 overruns:0 frame:0
          TX packets:49840 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:76688099 (76.6 MB)  TX bytes:4677875 (4.6 MB)
          Interrupt:20 Memory:fb120000-fb140000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:456 errors:0 dropped:0 overruns:0 frame:0
          TX packets:456 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:34952 (34.9 KB)  TX bytes:34952 (34.9 KB)
```

---

### Post by jonobr on 2011-11-14
Hey there

Thanks for posting the information below,

Could you also post /etc/resolv.conf

if you open two windows and in one put google.com and in the other 
put  [http://74.125.224.82](http://74.125.224.82)

execute them both at the same time,
do they look as if the take the same amount of time?

---

### Post by dparry711 on 2011-11-14
There is no resolve.conf in etc. there is a resolvconf which is a directory containing update-libc.d which contains a file avahi-daemon.

Do you mean open two internet tabs and access them both at the same time, or terminal window and ping them?

---

### Post by dparry711 on 2011-11-14
In an internet window both seem to take a long time, as in more than a minute.

---

