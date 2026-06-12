---
title: "Wireless working, but fails to connect to secure net [Intel PRO/11.04/Gateway CX2620]"
date: 2011-04-29
forum: Networking &amp; Wireless
---

### Post by Jioruji Derako on 2011-04-29
As the title suggests...

Just upgraded to Ubuntu 11.04 (from 10.10), and now suddenly the wireless networking is broken. Wired connection still works fine, and the wireless can still detect all the routers in the area, but attempting to connect to any of them - with the exception of one of the unsecured networks in the area - refuses to connect.
When attempting to connect to my own network, which is secured with a WEP-128bit passkey, the network manager displays the usual "connecting" animation, then eventually times out and asks for the passkey once again. I've double- and triple-checked the network passkey (which was working perfectly fine in 10.10, and even saved when upgrading to 11.04), and I'm positive it's correct, yet it still refuses to go through.

Given that it can in fact connect to the one unsecured network in the area, I'm inclined to believe either there's some error in the system that's screwing up the passkey, or something in my settings has been reset and broken (the working setup and network connection from 10.10 remained intact after the upgrade, so I'm thinking something new changed).

Info, before anyone has to ask:

Gateway CX2620 laptop
Ubuntu 11.04
2.6.38-8-generic i686
06:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
Module:
libipw
Used by:
ipw2200

ifconfig:
```
geo@Pandora:~$ ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:e0:b8:8a:4f:4a  
          inet addr:192.168.0.176  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:b8ff:fe8a:4f4a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:514318 errors:0 dropped:0 overruns:0 frame:0
          TX packets:261172 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:774034376 (774.0 MB)  TX bytes:19450999 (19.4 MB)
          Interrupt:16 

```network configuration:
```
  *-network
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 4
       bus info: pci@0000:06:04.0
       logical name: eth1
       version: 05
       serial: 00:16:6f:55:ec:b6
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=32 link=no maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:c8006000-c8006fff

```I've gone through a couple of reboots, and tried a few changes to the network connection's settings, but no luck so far. I can always re-install 10.10 if need be (I have my /home in a separate partition), but I'd much rather not have to go through with that, as I am enjoying the rest of 11.04 so far (although I do miss one or two other things).

I'd appreciate any help you fellas can provide. As I said, the wired connection works fine, but I have to steal the ethernet cable from my main desktop rig to do so, which is very much an issue (and removes my ability to share documents between the two computers through the local network).

::EDIT::
an addendum; I reset my router, but no changes. I did notice something while I was doing so, however; my router displays a connection activity log, and notes that - at some point recently - it did indeed assign an IP address to my laptop when it attempted to connect. I'm no expert, but that seems to tell me that the laptop is at least getting through to the router, even though it's not seeming to be able to complete the connection...

::EDIT2::
unknown what the issue was exactly, but changing the router's wireless passkey somehow did the trick. Nothing in Ubuntu's network settings changed at all, with the exception of the passkey, so no clue what fixed it. I was able to "break" it again by changing the passkey once again, after which it refused to work again until the security was switched from WEP over to WPA-personal. Apparently a repeatable error - it'll fail whenever the wireless is switched from WPA to WEP security - though I'm still not quite sure what the exact cause is (again, noting that it worked perfectly from Ubuntu 8.04 all the way up to 10.10).

---

