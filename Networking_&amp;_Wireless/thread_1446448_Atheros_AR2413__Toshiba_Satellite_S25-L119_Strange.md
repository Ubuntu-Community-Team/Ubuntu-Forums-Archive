---
title: "Atheros AR2413 / Toshiba Satellite S25-L119: Strange wireless issues on certain APs"
date: 2010-04-04
forum: Networking &amp; Wireless
---

### Post by dewiniaid on 2010-04-04
So I'm having the strangest problem with my wireless connection (Atheros 2413 chipset) -- it hardly seems like the sort of problem that would be at the wireless level but I'm stumped for all other causes.

The problem as described here affects me on one specific access point on kernel 2.6.31 (both on Karmic and Lucid) and on both access points I have access to on kernel 2.6.32 (tested on Lucid only).  It only happens under Ubuntu -- Windows XP seems to be unaffected.

Over the wireless connection, select websites fail to load.  It's consistent as to which websites they are, but there seems to be no rhyme or reason in determining whether a given website will be affected.  The list of affected websites is the same across both access points:

[http://www.google.com/](http://www.google.com/) loads instantly.
[http://google.com/](http://google.com/) times out
[https://anything.anywhere/](https://anything.anywhere/) times out
Package updates from aptitude may or may not work (using [http://archive.canonical.com](http://archive.canonical.com))

The selectiveness of the issues almost makes it feel as if some sort of proxy or firewall is causing issues, but there are no significant firewall rules on either routers and no proxying involved.

I can ssh into my work server and use links/elinks and access all of the affected sites just fine.  Plugging into the AP with an ethernet cord also solves the problem.

AP#1 (where connectivity is always sporadic) is a Linksys WRT54G v6, using the latest stock firmware.
AP#2 (only sporadic on 2.6.32) is a Linksys WRT54G v1.1, using DD-WRT firmware.

System: Toshiba Satellite L25-S119 (laptop)
lspci reports
> 09:04.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)ifconfig reports:
> 
wlan0     Link encap:Ethernet  HWaddr 00:11:f5:a6:81:2d  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:f5ff:fea6:812d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:42 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1634 (1.6 KB)  TX bytes:10431 (10.4 KB)
iwconfig reports:
> 
wlan0     IEEE 802.11bg  ESSID:"linksys"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:18:F8:58:50:8E   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=64/70  Signal level=-46 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
Using ath5k kernel module

lshw -c Network reports:
> 
  *-network:1
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 4
       bus info: pci@0000:09:04.0
       logical name: wlan0
       version: 01
       serial: 00:11:f5:a6:81:2d
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=2.6.32-19-generic firmware=N/A ip=192.168.1.100 latency=168 link=yes maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
       resources: irq:22 memory:c0200000-c020ffff


---

### Post by EarlsFurniture on 2011-04-21
Did you ever solve the problem?  I have very similar issues here with the same model laptop running either Xubuntu 11.04b2 or Mint XFCE.  It connects so far to any wifi open or WEP2 except a Belkin54g which demonstrates the same odd issues you described.  It isn't the Belkin as far as I can determine, because two Macs connect to it just fine, and a wired eth0 has no problems on the same laptop.  It's clearly something with the wifi card in the Toshiba, but only when connected to this specific router.

---

### Post by paul_ik on 2011-05-11
Have very similar problem.
Using same chipset Atheros AR2413 with ath5k driver.
The problem is that some random resources don't load. I use "resources" to say that sometimes the page itself doesn't load, sometimes some picture or javascript or css in the page doesn't load.

So I used wireshark to see what is going on. And the thing I saw was VERY strange. For http requests of those un-fetchable resources the underlying tcp packets were not receiving corresponding ACKs. The strange thing was that the subsequent tcp retransmissions were not successful also! It was like series of tcp retransmissions of the same packet over and over again taking page load forever.

But if I stop page load this and then try to reaload page after some time then those un-fetchable resources have pretty good chances to load.

Anybody, any ideas?

---

### Post by paul_ik on 2011-06-27
Finally managed to solve the problem. Tested it for some time and can confirm the solution works for me.
The solution is in this tracker issue:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/568090](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/568090)

The thing which did everything for me was loading ath5k driver with nohwcrypt option:
```
sudo modprobe ath5k nohwcrypt
```

Hope this helps other users of ath5k, and they can enjoy ubuntu with wifi working properly! :popcorn:

---

