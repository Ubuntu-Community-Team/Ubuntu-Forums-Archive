---
title: "WIRED networking disconnects"
date: 2010-08-13
forum: Networking &amp; Wireless
---

### Post by CMDRSweeper on 2010-08-13
I have seen a lot of strange things, but never that a WIRED network loses connection.
Basically after a certain period after boot it will disconnect and I have to yank the plug and reseat it to make it work again.
For a server, needless to say this is indeed very bad as my only means of controlling it is via TightVNC.

So the question is, how do I fix and get rid of this behaviour?

---

### Post by varunendra on 2010-08-13
Try some/all of these first:

[LIST=1]
[*]Clean ethernet sockets on both sides (on the router's end, better swap it with another one)
[*]Replace the cable with a fresh one
[*]If ethernet is a PCI card (not onboard), pull it out > clean the contacts > replace.
[/LIST]
Yes, I know these are silly things to do, but sometimes the basics are overlooked. (Like today I spent 2+ hrs on troubleshooting sound problem while it was simply the 'Wrong pin in wrong Jack' !! ;))

Then, please post the outputs of:
```
ifconfig -a
```
```
cat /etc/network/interfaces
```
```
cat /etc/NetworkManager/nm-system-settings.conf
```

---

### Post by CMDRSweeper on 2010-08-13
Well I already tried the different cables, as for the networking controller it is PCI connected but onboard.
ABIT decided to use a free PCI rather than a PCI-E when building this motherboard for their ethernet.

Anyways, the output from ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:50:8d:b7:10:fd  
          inet addr:192.168.2.55  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::250:8dff:feb7:10fd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:847 errors:0 dropped:0 overruns:0 frame:0
          TX packets:848 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:835595 (835.5 KB)  TX bytes:147170 (147.1 KB)
          Interrupt:23 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1200 (1.2 KB)  TX bytes:1200 (1.2 KB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:172.16.0.1  Bcast:172.16.0.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:65 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:172.16.155.1  Bcast:172.16.155.255  Mask:255.255.255.0
          inet6 addr: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:66 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:08:a1:79:72:f2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

And the second output from the Network interfaces:

```
auto lo
iface lo inet loopback

```

And the final output you requested:

```
# This file is installed into /etc/NetworkManager, and is loaded by 
# NetworkManager by default.  To override, specify: '--config file' 
# during NM startup.  This can be done by appending to DAEMON_OPTS in 
# the file:
#
# /etc/default/NetworkManager
#

[main]
plugins=ifupdown,keyfile

no-auto-default=00:50:8d:b7:10:fd,

[ifupdown]
managed=false

```

The first problem I noticed was that it tended to actually just refuse to get an IP from the DHCP server, so I set it manually to one and it worked up until this started bugging me.

---

### Post by varunendra on 2010-08-14
Apparently, everything seems normal except the "no-auto-default=....." line in the nm-system-settings.conf file. It is not there by default but I don't think this may be the cause for your problem. However, it maybe the reason why your card's not getting address from dhcp. You may try:
```
sudo gedit /etc/NetworkManager/nm-system-settings.conf
```to add # before that line to comment it out, and then
```
sudo dhclient
```to see if it can get an address from dhcp.

Anyways, back to your **Original** **problem**. I've seen a couple of threads in the past with similar problems like "dead-slow" browsing or "slow-motion disconnection". Solution was to set MTU to a lower value (1400, or sometimes an even lower value; you may need to do some exercise to find an optimal value).

On the NetworkManager applet, **right-click>edit connections>select eth0 (under 'Wired' tab)>edit**. Then, under 'Wired' tab, **set the value of MTU to 1400**. Close the dialogues, right-click again on the nm applet>clear the tick on 'Enable Networking' to disable it, wait 10-20 sec. then re-enable clicking on it again.

Now run ifconfig again to verify if the MTU has changed.

Other than this, I am clueless!

---

### Post by CMDRSweeper on 2010-08-14
I might be on to something here, as it may be the router software.
It seems the DLink hardware is quite faulty and has some incompatabillity with Broadcom chipsets that is used elsewhere in the network, and as a result it doesn't function properly.

So I will take down the network and restructure it in a bit and it should improve I hope, I will get back to you if it doesn't.

---

### Post by varunendra on 2010-08-14
> **CMDRSweeper said:**
> I will get back to you if it doesn't.

Oh.... please tell us whatever result you get.

And yes, I've also heard a few bad things about D-Link's firmware compatibility (with linux). It's strange for me though, 'cause it is considered to be a high-quality brand!

---

### Post by CMDRSweeper on 2010-08-14
Well I took the network down and redid the configuration of the routers, making sure that the WLAN bridge was done by two routers that both were operating Broadcom and the problem seems to have disappeared.
I will monitor the situation for a bit and report back.

Update: It seems like the culprit was the router, or rather the DLink router with DD-WRT on an Atheros chipset not being compatible with the Broadcom router equipped Linksys router it was communicating with.
So I basically redid the network by setting the bridge between the two Broadcoms back to the Linksys I had so it was 2 routers of the same type communicating with each other and the crappy Dlink into forwarding mode, or switch mode so the network is still fairly clean to do NAT on.

---

