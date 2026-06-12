---
title: "Network Unclaimed - Broadcom  BCM4312"
date: 2010-02-28
forum: Networking &amp; Wireless
---

### Post by raymonds0528 on 2010-02-28
Can someone please help me out.. I have an Aspire One AOD250-1151 netbook with Ubuntu 9.10 Karmic installed.  For some reason I am unable to get my wireless to work.  I have tried various things I have found on the forums and elsewhere and have gotten as far as seeing the below:

```
 
$sudo lshw -C network
  *-network UNCLAIMED
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:57100000-57103fff

```I can see the hardware listed when I enter lspci as: 
```
01:00.0 Network Controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
```

What has got me puzzled at this point is if I do ifconfig I see:
```

eth0      Link encap:Ethernet  HWaddr 00:26:22:51:4d:42  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:44026 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11619 errors:0 dropped:0 overruns:0 carrier:2
          collisions:0 txqueuelen:1000 
          RX bytes:27294076 (27.2 MB)  TX bytes:921500 (921.5 KB)
          Interrupt:29 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:568 (568.0 B)  TX bytes:568 (568.0 B)

```And if I do iwconfig I see:
```

lo        no wireless extensions.

eth0      no wireless extensions.

```Can someone please help me with getting my wireless adapter working?  I am desperate.

Thanks

---

### Post by Zero_Black on 2010-03-21
Hi I currently have a similar problem. I have the same wireless card in an HP550. I recently installed the linux-backports-modules-karmic in order to solve a different issue (didn't help) and at the time nothing seemed to change. A few days went by and my wireless carried on working. Then yesterday I restarted the laptop after some bugfix updates (first restart after installing the backports) and after the reboot, the wireless wouldn't work. I am able to use an ethernet cable to gain access to the network/internet etc. but no joy with the wireless.

I am running Kubuntu with Karmic and the linux version is 2.6.31-20-generic

output from lshw -C network:```

  *-network
       description: Ethernet interface
       product: 82562GT 10/100 Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:24:81:42:60:2d
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k2 duplex=full firmware=1.1-2 ip=192.168.0.102 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:28 memory:e4600000-e461ffff memory:e4620000-e4620fff ioport:4020(size=32)
  *-network UNCLAIMED
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:e4000000-e4003fff
```output from lspci | grep Network:
```
00:19.0 Ethernet controller: Intel Corporation 82562GT 10/100 Network Connection (rev 03)
10:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
```ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:24:81:42:60:2d
          inet addr:192.168.0.102  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::224:81ff:fe42:602d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:52064 errors:0 dropped:0 overruns:0 frame:0
          TX packets:30094 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:73553431 (73.5 MB)  TX bytes:2679024 (2.6 MB)
          Memory:e4600000-e4620000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:42 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2408 (2.4 KB)  TX bytes:2408 (2.4 KB)

```iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

```I don't have enough experience with linux to solve this on my own so any help would be greatly appreciated.

Thanks

---

### Post by bkratz on 2010-03-21
Here is a pretty good description of what should take care of your problems. Some of the commands probably won't be necessary ( assuming you didn't also try b43!) and will probably say something about module not found, but shouldn't be a problem. You really didn't want to include the backports-module unless you needed it for something else. Anyway, here it is

[http://ubuntuforums.org/showpost.php?p=8510764&postcount=12](http://ubuntuforums.org/showpost.php?p=8510764&postcount=12)

Also, if something else requires ssb, it should let you know.

---

### Post by Zero_Black on 2010-03-21
Thanks  for your reply, but unfortunately that didn't help... I have just found something else though, not sure if it is supposed to be the case but here's the contents of /etc/modprobe.d/blacklist-bcm43.conf:

```
# Warning: This file is autogenerated by bcmwl-kernel-source. All changes to this file will be lost.
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
```

I thought b43 and ssb were the wireless drivers being used or am I wrong?

---

### Post by bkratz on 2010-03-21
> **Zero_Black said:**
> Thanks  for your reply, but unfortunately that didn't help... I have just found something else though, not sure if it is supposed to be the case but here's the contents of /etc/modprobe.d/blacklist-bcm43.conf:

```
# Warning: This file is autogenerated by bcmwl-kernel-source. All changes to this file will be lost.
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
```

I thought b43 and ssb were the wireless drivers being used or am I wrong?

Generally the 4312 uses the STA driver. I have seen people use the b43, but seem to have a lot less success.

---

### Post by Zero_Black on 2010-04-02
Ok I managed to get my wireless working, turns out although I *thought* I'd removed the backports, they were in fact still present and removing them fixed my wireless issues. Thanks for the help bkratz :)

---

### Post by bkratz on 2010-04-02
> **Zero_Black said:**
> Ok I managed to get my wireless working, turns out although I *thought* I'd removed the backports, they were in fact still present and removing them fixed my wireless issues. Thanks for the help bkratz :)

Well congratulations! You did it, I did very little except point you in a direction.  Since there seems to be a lot of postings regarding this device recently, you might want to further explain what you did and mark the thread as solved in the above thread tools just in case it helps someone else.


Just noticed you weren't the OP so you can't mark it as solved! Sorry, but it would still help to say what you did.

---

