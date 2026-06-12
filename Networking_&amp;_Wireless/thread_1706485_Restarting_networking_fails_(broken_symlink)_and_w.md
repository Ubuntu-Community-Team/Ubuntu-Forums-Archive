---
title: "Restarting networking fails (broken symlink) and wireless adapter unclaimed"
date: 2011-03-13
forum: Networking &amp; Wireless
---

### Post by kwah90 on 2011-03-13
For a while I've had issues using my built-in wireless network adapter (unsure of the cause) but I have a USB wifi adapter so have been able to just use this. 

A couple of months ago  I attempted to fix the issue and had gotten it to work again (IIRC something to with the drivers but I don't recall tbh..) but then it stopped working again.

I had been using wifi connections before this for a long time without issue but for the last 5 months or so I've been (mostly) connected via a wired network so haven't been keeping much of an eye on the status of my wireless connectivity.


Anyhow, recently I've noticed that restarting networking fails as follows:

```
$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                          
ifdown: failed to open statefile /etc/network/run/ifstate: No such file or directory
ifup: failed to open statefile /etc/network/run/ifstate: No such file or directory
                                                                                         [fail]

```After navigating to /etc/network/ I noticed that /etc/network/run/ is actually a broken inode/symlink with a "Link target:" to /dev/shm/network. The last modified date of this file is 2009 so I expect that the issue is that /dev/shm/network doesn't exist rather than any change to the link.


Long story short I'm not sure about how to get over these problems - guidance would be greatly appreciated.





Here's some outputs (with the usb wifi adapter unplugged) - just shout if I missed anything or more info is needed for diagnosis.

```
~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.2 LTS"

```Snippet from sudo lspci
```
06:01.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
06:02.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
```/etc/network/interface is an empty file.

```
~$ sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:06:01.0
       logical name: eth0
       version: 02
       serial: xx:xx:xx:xx:xx:xx
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=xxx.xxx.xxx.xxx latency=64 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:21 memory:d0010000-d0011fff
  *-network:1 UNCLAIMED
       description: Ethernet controller
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 2
       bus info: pci@0000:06:02.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=0 maxlatency=28 mingnt=10
       resources: memory:d0000000-d000ffff
~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr xx:xx:xx:xx:xx:xx
          inet addr:xxx.xxx.xxx.xxx  Bcast:xxx.xxx.xxx.xxx  Mask:255.255.255.0
          inet6 addr: xxxx:xxxx:xxxx:xxxx:xxxx/xx Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:994144 errors:0 dropped:0 overruns:0 frame:0
          TX packets:158916 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:376865275 (376.8 MB)  TX bytes:19434948 (19.4 MB)
          Interrupt:21 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:257540 errors:0 dropped:0 overruns:0 frame:0
          TX packets:257540 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:29060491 (29.0 MB)  TX bytes:29060491 (29.0 MB)

~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


```(nb, some parts have been intentionally replaced with xx-s).

---

