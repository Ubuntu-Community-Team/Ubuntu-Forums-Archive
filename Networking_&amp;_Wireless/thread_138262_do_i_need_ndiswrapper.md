---
title: "do i need ndiswrapper?"
date: 2006-03-01
forum: Networking &amp; Wireless
---

### Post by veighjay on 2006-03-01
hi

being new to this, i am slightly confused about ndiswrapper... do i need it? i have an intel pro/wireless 2200bg.

the following are some command line results....

```
sudo lshw -C network
    *-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@02:02.0
       logical name: eth1
       version: 05
       serial: 00:0e:35:dd:13:34
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.0.6 firmware=ABG:9.0.1.5 (Oct 15 2004) link=no multicast=yes wireless=unassociated
       resources: iomemory:d0200000-d0200fff irq:10
```

```
lspci
.
.
.
0000:02:02.0 Network controller: Intel Corp. PRO/Wireless 2200BG (rev 05)
.
.
```

```
sudo cardctl ident
Socket 0:
  no product info available
```

```
sudo ifconfig
eth1      Link encap:Ethernet  HWaddr 00:0E:35:DD:13:34
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:35ff:fedd:1334/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2740 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2122 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2073723 (1.9 MiB)  TX bytes:376729 (367.8 KiB)
          Interrupt:10 Base address:0x4000 Memory:d0200000-d0200fff
```

my impression is that the card and driver are working... is that right?

thanks in advance...

---

### Post by sublime on 2006-03-01
when you plug the card into the computer is it automatically detected?  if it is, then no you dont, if it isn't then yes you do need it.

---

### Post by veighjay on 2006-03-01
[QUOTE=sublime]when you plug the card into the computer is it automatically detected?  if it is, then no you dont, if it isn't then yes you do need it.[/QUOTE]

well, its a laptop with wireless built in... and it comes up on all those config lists... so i guess i don't need it... in that case, how do i go about setting up wpa encryption, as opposed to wep?

and also (excuse all the questions), does it matter if the host name in windows and ubuntu are different? ipconfig /all in windows says my hostname is okid, whereas in ubuntu, system>admin>networking says host name is ubuntu.... i am troubleshooting atm coz internet is not working.... (if u really want, u can see my v long post re this matter here.... 
[http://ubuntuforums.org/showthread.php?t=137798](http://ubuntuforums.org/showthread.php?t=137798)     )

thanks!

---

