---
title: "Broadcom 4401 Ethernet: No &quot;Wired Connections&quot; showing up in Network Manager"
date: 2011-04-10
forum: Networking &amp; Wireless
---

### Post by whitesilence on 2011-04-10
Hey everyone,

I've been struggling with this a bit now, and I'm not sure what the problem is.

I have a laptop with a BCM4401 Ethernet card as well as a BCM4311 Wireless card. The wireless card works great out of the box, I'm able to connect with it perfectly. The problem is the ethernet card. Here is the situation:

[LIST]
[*]The NetworkManager menu doesn't list "Wired Networks" at all (ie. it doesn't say "not managed", it just only lists Wireless networks)
[*]Going into Network Connections, there is an "Auto eth0" entry
[*]ifconfig shows eth0 (which I assume means NetworkManager isn't managing eth0)
[*]I have edited /etc/NetworkManager/nm-system-settings.conf to say managed=true
[*]I have edited /etc/network/interfaces to remove any mention of eth0 (all that's left is the "lo" lines)
[/LIST]

So I'm not sure why eth0 is still showing up when I run ifconfig, and why Network Manager is not managing it. Any ideas?

**Edit:** Not sure what I did but now ifconfig spits out this:

```
eth0      Link encap:Ethernet  HWaddr 00:1c:26:2c:60:75  
          inet addr:10.0.1.12  Bcast:10.0.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:26ff:fe2c:6075/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17614 errors:0 dropped:0 overruns:0 frame:266046
          TX packets:13068 errors:16 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:19574095 (19.5 MB)  TX bytes:1867945 (1.8 MB)
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr 00:1c:23:8f:d4:39  
          inet6 addr: fe80::21c:23ff:fe8f:d439/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:110 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:27606 (27.6 KB)  TX bytes:9323 (9.3 KB)
          Interrupt:21 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:74 errors:0 dropped:0 overruns:0 frame:0
          TX packets:74 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5388 (5.3 KB)  TX bytes:5388 (5.3 KB)

```

eth0 shows up in the NetworkManager menu now, but after trying to connect to "Auto eth0" for about 30 seconds I get a message saying it's disconnected.

The MAC address of the "Auto eth0" entry is 00:1C:23:8F:D4:39, the same as the eth1 entry that ifconfig spits out.

Very confused now.

---

### Post by bkratz on 2011-04-10
> **whitesilence said:**
> Hey everyone,

I've been struggling with this a bit now, and I'm not sure what the problem is.

I have a laptop with a BCM4401 Ethernet card as well as a BCM4311 Wireless card. The wireless card works great out of the box, I'm able to connect with it perfectly. The problem is the ethernet card. Here is the situation:

[LIST]
[*]The NetworkManager menu doesn't list "Wired Networks" at all (ie. it doesn't say "not managed", it just only lists Wireless networks)
[*]Going into Network Connections, there is an "Auto eth0" entry
[*]ifconfig shows eth0 (which I assume means NetworkManager isn't managing eth0)
[*]I have edited /etc/NetworkManager/nm-system-settings.conf to say managed=true
[*]I have edited /etc/network/interfaces to remove any mention of eth0 (all that's left is the "lo" lines)
[/LIST]

So I'm not sure why eth0 is still showing up when I run ifconfig, and why Network Manager is not managing it. Any ideas?



If you are using the STA driver for your wireless card one of the things it does is blacklist ssb and b43. Unfortunately, the 4401 ethernet connection requires the b44 driver and ssb. You might want to look at 

lsmod

and see if those are listed (post them back using copy/paste and the code tags or #) since this may be a bit long.
By the way that was LSMOD in lowercase.

---

### Post by whitesilence on 2011-04-10
> **bkratz said:**
> If you are using the STA driver for your wireless card one of the things it does is blacklist ssb and b43. Unfortunately, the 4401 ethernet connection requires the b44 driver and ssb. You might want to look at 

lsmod

and see if those are listed (post them back using copy/paste and the code tags or #) since this may be a bit long.
By the way that was LSMOD in lowercase.

Just ran lsmod, they are listed like so:

```
Module                  Size  Used by
b44                    26253  0 
ssb                    39320  1 b44

```

along with a bunch of other entries.

**Edit:** I looked in Synaptic Package Manager, I have bcmwl-kernel-source installed as well as firmware-b43-installer and b43-fwcutter. Should I have them all installed?

---

### Post by bkratz on 2011-04-10
Well that wasn't it! Will look some more.

---

### Post by whitesilence on 2011-04-10
By the way here are the contents of my /etc/NetworkManager/nm-system-settings.conf:

```
[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=true

```

and /etc/network/interfaces:

```
auto lo
iface lo inet loopback
```

---

### Post by whitesilence on 2011-04-10
Alright here's what daemon.log shows when I try to connect to eth0 up until it disconnects:

```
Apr 10 17:02:48 Jordan NetworkManager[920]: <info> Activation (eth1) starting connection 'Auto eth0' 
Apr 10 17:02:48 Jordan NetworkManager[920]: <info> (eth1): device state change: 3 -> 4 (reason 0) 
Apr 10 17:02:48 Jordan NetworkManager[920]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled... 
Apr 10 17:02:48 Jordan NetworkManager[920]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) started... 
Apr 10 17:02:48 Jordan NetworkManager[920]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) scheduled... 
Apr 10 17:02:48 Jordan NetworkManager[920]: <info> Activation (eth1) Stage 1 of 5 (Device Prepare) complete. 
Apr 10 17:02:48 Jordan NetworkManager[920]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) starting... 
Apr 10 17:02:48 Jordan NetworkManager[920]: <info> (eth1): device state change: 4 -> 5 (reason 0) 
Apr 10 17:02:48 Jordan NetworkManager[920]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) successful. 
Apr 10 17:02:48 Jordan NetworkManager[920]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled. 
Apr 10 17:02:48 Jordan NetworkManager[920]: <info> Activation (eth1) Stage 2 of 5 (Device Configure) complete. 
Apr 10 17:02:48 Jordan NetworkManager[920]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) started... 
Apr 10 17:02:48 Jordan NetworkManager[920]: <info> (eth1): device state change: 5 -> 7 (reason 0) 
Apr 10 17:02:48 Jordan NetworkManager[920]: <info> Activation (eth1) Beginning DHCPv4 transaction (timeout in 45 seconds) 
Apr 10 17:02:48 Jordan NetworkManager[920]: <info> dhclient started with pid 5400 
Apr 10 17:02:48 Jordan NetworkManager[920]: <info> Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Apr 10 17:02:48 Jordan dhclient: Internet Systems Consortium DHCP Client V3.1.3
Apr 10 17:02:48 Jordan dhclient: Copyright 2004-2009 Internet Systems Consortium.
Apr 10 17:02:48 Jordan dhclient: All rights reserved.
Apr 10 17:02:48 Jordan dhclient: For info, please visit https://www.isc.org/software/dhcp/
Apr 10 17:02:48 Jordan dhclient: 
Apr 10 17:02:48 Jordan dhclient: /var/run/nm-dhclient-eth1.conf line 25: no option named rfc3442-classless-static-routes in space dhcp
Apr 10 17:02:48 Jordan dhclient: rfc3442-classless-static-routes,
Apr 10 17:02:48 Jordan dhclient: ^
Apr 10 17:02:48 Jordan dhclient: /var/run/nm-dhclient-eth1.conf line 25: ntp-servers: expected option name.
Apr 10 17:02:48 Jordan dhclient: rfc3442-classless-static-routes, ntp-servers;
Apr 10 17:02:48 Jordan dhclient:                                              ^
Apr 10 17:02:48 Jordan NetworkManager[920]: <info> (eth1): DHCPv4 state changed nbi -> preinit 
Apr 10 17:02:48 Jordan dhclient: Listening on LPF/eth1/00:1c:23:8f:d4:39
Apr 10 17:02:48 Jordan dhclient: Sending on   LPF/eth1/00:1c:23:8f:d4:39
Apr 10 17:02:48 Jordan dhclient: Sending on   Socket/fallback
Apr 10 17:02:48 Jordan dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
Apr 10 17:02:51 Jordan dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 5
Apr 10 17:02:56 Jordan dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
Apr 10 17:03:09 Jordan dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 13
Apr 10 17:03:22 Jordan dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
Apr 10 17:03:34 Jordan NetworkManager[920]: <warn> (eth1): DHCPv4 request timed out. 
Apr 10 17:03:34 Jordan NetworkManager[920]: <info> (eth1): canceled DHCP transaction, DHCP client pid 5400 
Apr 10 17:03:34 Jordan NetworkManager[920]: <info> Activation (eth1) Stage 4 of 5 (IP4 Configure Timeout) scheduled... 
Apr 10 17:03:34 Jordan NetworkManager[920]: <info> Activation (eth1) Stage 4 of 5 (IP4 Configure Timeout) started... 
Apr 10 17:03:34 Jordan NetworkManager[920]: <info> (eth1): device state change: 7 -> 9 (reason 5) 
Apr 10 17:03:34 Jordan NetworkManager[920]: <info> Marking connection 'Auto eth0' invalid. 
Apr 10 17:03:34 Jordan NetworkManager[920]: <warn> Activation (eth1) failed. 
Apr 10 17:03:34 Jordan NetworkManager[920]: <info> Activation (eth1) Stage 4 of 5 (IP4 Configure Timeout) complete. 
Apr 10 17:03:34 Jordan NetworkManager[920]: <info> (eth1): device state change: 9 -> 3 (reason 0) 
Apr 10 17:03:34 Jordan NetworkManager[920]: <info> (eth1): deactivating device (reason: 0). 
```

Some sort of DHCP issue?

It seems eth0 refers to the wireless card while eth1 is being used for the ethernet card. ifconfig is showing both eth0 and eth1 entries (as well as lo).

**Edit:** Well I couldn't fix the DHCP issue but my main goal was to get Internet Connection Sharing to work (to use my laptop's wifi connection on my desktop) which did manage to work after I had to install dnsmasq-base (which wasn't installed for some reason).

Still thank you for the help bkratz!

---

