---
title: "Slow internet in 8.10"
date: 2009-02-20
forum: Networking &amp; Wireless
---

### Post by madbam on 2009-02-20
After upgrading to 8.10 I have problems with the speed of my internet connection. My flatmate cannot surf when I use communication-intensive applications, as torrent or downloads files. In my syslog I get a lot of messages like these:
> sky2 eth1: rx length error: status 0x45a0100 length 598
(Do anyone knows what this means?)

My network card is BCM4311 and I have tried to remove, change and reinstall the drivers for that, but it does not help. I do not think that that is my problem.

I have also removed ipv6, but that did not help either.

sudo lshw -C network gives:
>   *-network               
       description: Ethernet interface
       product: 88E8071 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 15
       serial: 00:16:d3:ef:f8:5a
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.22 duplex=full firmware=N/A ip=192.168.0.150 latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: eth0
       serial: 00:1d:d9:2c:71:dc
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=172.31.240.63 multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 12:9d:84:34:aa:7a
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion


My /etc/network/interfaces just contained 
> auto lo
iface lo inet loopback
but I have changed that into:
> auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto lo
iface lo inet loopback

But that did not help.
Any suggestions?

---

### Post by konqueror7 on 2009-02-20
have you disabled ipv6? because when i first installed 8.10, my internet was also somewhat slow...

oh, btw, welcome to the forums! :)

---

### Post by madbam on 2009-02-20
Yes, I have disabled ipv6, but it didn't make things any faster.

And thanks for your welcoming me! :)

Btw - many seems to have similar problems but only regarding wireless, and they are often help by using an earlier kernel. I have tried that - but still the same (I'm using 2.6.27-12 now)

---

### Post by superprash2003 on 2009-02-20
post output of ifconfig from the terminal.. is it browsing speed?? if so try changing DNS servers to opendns - 208.67.222.222 and 208.67.220.220

For reference : [http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://www.prash-babu.com/2008/04/how-to-configure-dns-servers-in-linux.html)

---

### Post by madbam on 2009-02-20
I notice the problem most when downloading torrent-files, but then surfing also gets extremely slow (or is impossible). The result from ifconfig is: 

> ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:d9:2c:71:dc  
          inet addr:192.168.1.200  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:795 errors:0 dropped:0 overruns:0 frame:0
          TX packets:920 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:145694 (145.6 KB)  TX bytes:99253 (99.2 KB)

eth1      Link encap:Ethernet  HWaddr 00:16:d3:ef:f8:5a  
          inet addr:192.168.0.135  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:576  Metric:1
          RX packets:2015548 errors:0 dropped:644 overruns:0 frame:644
          TX packets:1259954 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:225515183 (225.5 MB)  TX bytes:1674541217 (1.6 GB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:130 errors:0 dropped:0 overruns:0 frame:0
          TX packets:130 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9824 (9.8 KB)  TX bytes:9824 (9.8 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1D-D9-2C-71-DC-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


---

### Post by mpsii on 2009-02-20
Based upon your current output, I see that you have ip addresses for both your wired and wireless connection. Why is that? If you have wireless, why is your ethernet connection even plugged in?

I have noticed on my notebook that I can surf the web just fine with both my wired and wireless connections running. But, performance is better all around if I just pick one and disable the other.

---

### Post by madbam on 2009-02-20
I don't know why I have both wired and wireless, I think that is something NetworkManager have done for me. But unfortunately I do not get any more speed if I try them "xor". But thanks for the suggestions, got any more ideas?

---

### Post by Sillywombat on 2009-02-20
I had the same problem.
Never fixed it, actually, changed back to 8.04.

However, this isnt so much as a fix, but have you tried tweeking firefox?
[http://www.freerepublic.com/focus/f-news/1299854/posts]("http://www.freerepublic.com/focus/f-news/1299854/posts")

---

### Post by madbam on 2009-02-20
> **Sillywombat said:**
> I had the same problem.
Never fixed it, actually, changed back to 8.04.


Well, I am considering going back to 8.04, but I do not know of an easy way to dp that and I am not sure that it will solve my problems. But if it worked for you, then there is a small chance that it will work for me as well... ;)

---

### Post by superprash2003 on 2009-02-21
your mtu values for eth1 is 576 which is low,, try changing it [http://www.prash-babu.com/2008/06/how-to-change-mtu-values-in-linux.html](http://www.prash-babu.com/2008/06/how-to-change-mtu-values-in-linux.html)

---

### Post by madbam on 2009-02-21
Thanks, I have no idea what that does or how it can help me, but since I'm pretty desperate I try it. But first some sleep, I hope to come back with some good news tomorrow!

---

### Post by gardenhose on 2009-02-21
Hi all,
I have the same problem. I tried some tricks in other forums, like disabling ipv6 and modifying /etc/sysctl.conf files but no luck.
Can someone please help me?
I am getting around 1000 kb/s on ubuntu while more than 2000 kb/s on my windows xp wireless laptop.

Obviously there is something wrong. Please help!!

---

### Post by KevNice on 2009-02-22
I am having similar problems.. here is my ifconfig:

```
 ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1c:23:ad:95:e1  
          inet addr:219.70.22.120  Bcast:219.70.22.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:576  Metric:1
          RX packets:3999 errors:31 dropped:0 overruns:0 frame:31
          TX packets:3550 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1755011 (1.7 MB)  TX bytes:413646 (413.6 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:152 errors:0 dropped:0 overruns:0 frame:0
          TX packets:152 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12080 (12.0 KB)  TX bytes:12080 (12.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1b:77:e0:0d:1e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-1B-77-E0-0D-1E-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```

---

### Post by superprash2003 on 2009-02-22
your eth0 too has MTU 576 , this is pretty low , i guess its a big in intrepid.. try changing MTU values, look at my previous post..

---

### Post by madbam on 2009-02-22
Hey, Prash, you really are super. Something I have done recently helped, it could have been changing the mtu or else it was that I disabled the propriety drivers. Any way, thanks man!

---

### Post by regiert on 2009-02-23
I had been wrestling with this for a few weeks.  Access to my gmail account and the Seattle server on Speakeasy.net were very slow.  I disabled Ipv6 and it didn't help.  Then I changed my MTU to 1500 (which is the default in 8.04) and things are back to normal.  It may be a combination of the ipv6 and the MTU, or just the MTU.  Thanks, Prash.

---

### Post by superprash2003 on 2009-02-25
it looks like a bug.. as most intrepid users have 576 as MTU value which is way too low!!

---

