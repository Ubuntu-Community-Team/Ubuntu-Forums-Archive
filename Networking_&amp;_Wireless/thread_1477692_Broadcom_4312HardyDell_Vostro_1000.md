---
title: "Broadcom 4312/Hardy/Dell Vostro 1000"
date: 2010-05-09
forum: Networking &amp; Wireless
---

### Post by Nuu on 2010-05-09
I've already got the b43-fwcutter package and a driver called 'b43' appears in System > Administration > Hardware Drivers but it does not seem to enable. Another, Broadcom STA wireless driver, does enable, but I'm not picking up the wireless signal.

```
 $lspci 05:00.0 Network controller: Broadcom Corporation BCM4312 802.11a/b/g (rev 01)
08:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)

```

```
$ sudo lshw -C network
SCSI                      
  *-network        
       description: Wireless interface
       product: BCM4312 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth1
       version: 01
       serial: 00:1f:e2:80:c6:9f
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 latency=0 module=wl multicast=yes wireless=IEEE 802.11a
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:1d:09:db:19:21
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=10.1.1.4 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s

```

```
$ uname -mr
2.6.24-27-generic i686

```

```
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:09:db:19:21  
          inet addr:10.1.1.4  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::21d:9ff:fedb:1921/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12144 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10481 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11660719 (11.1 MB)  TX bytes:1584671 (1.5 MB)
          Interrupt:21 

eth1      Link encap:Ethernet  HWaddr 00:1f:e2:80:c6:9f  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:338 errors:0 dropped:0 overruns:0 frame:0
          TX packets:338 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:20814 (20.3 KB)  TX bytes:20814 (20.3 KB)
```

```
$ iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

eth0      no wireless extensions.
```

I don't really want to upgrade to lucid as I don't want any more problems at the moment and apparently my AMD fglrx graphics driver is not compatible.

Can anyone help please?

---

### Post by bkratz on 2010-05-09
Could you also unplug the ethernet cable and post the outputs of 

sudo iwlist scan

and 

rfkill list

---

### Post by Nuu on 2010-05-10
sudo iwlist scan:

```
 lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.
```

And apparently rfkill is not a command.

---

### Post by pdc on 2010-05-10
did you type

> rfkill list

as I think that is what bkratz wanted

see here

[http://manpages.ubuntu.com/manpages/lucid/man1/rfkill.1.html](http://manpages.ubuntu.com/manpages/lucid/man1/rfkill.1.html)

have you seen this guide to broadcom devices?

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

you might like to have a read at it before bkratz guides you further and helps you

---

### Post by Nuu on 2010-05-11
[https://launchpad.net/ubuntu/lucid/+package/rfkill](https://launchpad.net/ubuntu/lucid/+package/rfkill)

It says that rfkill is included in Linux 2.6.31. As I am running Hardy I've got 2.6.24.

---

### Post by bkratz on 2010-05-11
> **Nuu said:**
> [https://launchpad.net/ubuntu/lucid/+package/rfkill](https://launchpad.net/ubuntu/lucid/+package/rfkill)

It says that rfkill is included in Linux 2.6.31. As I am running Hardy I've got 2.6.24.



Don't know much about Hardy, except a lot of people seemed to be having problems with the rev. 2 of your card! (did a lot of google-ing). Did find this thread where everyone seemed to end up getting the rev 1 to work in various ways.

[http://ubuntuforums.org/showthread.php?t=1056446](http://ubuntuforums.org/showthread.php?t=1056446)

Hope it helps.

---

