---
title: "network comes and goes -- but problem is with my computer, not my ISP!"
date: 2011-03-09
forum: Networking &amp; Wireless
---

### Post by skief on 2011-03-09
I have two laptops on my desk: one running Jaunty Jackalope, the other running Lucid Lynx. I have one Ethernet cable running straight to the wall. When I plug in Jackalope, I get a connection. When I plug in Lynx, I *sometimes* get a connection, sometimes not. Meanwhile I change no settings.

Behavior on Lynx is very strange. My ISP provides IP addresses of the form 69.90.X.X. Recently however, through DHCP I sometimes wind up with an address of the form 192.168.0.X, suggesting I were on a LAN, which, as far as I know, I am not.

Here is a sample:
```

$ sudo ifup eth2
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth2/00:0b:97:dc:59:2e
Sending on   LPF/eth2/00:0b:97:dc:59:2e
Sending on   Socket/fallback
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 7
DHCPOFFER of 69.90.53.177 from 69.90.52.1
DHCPREQUEST of 69.90.53.177 on eth2 to 255.255.255.255 port 67
DHCPNAK from 192.168.0.1
DHCPDISCOVER on eth2 to 255.255.255.255 port 67 interval 5
DHCPOFFER of 192.168.0.191 from 192.168.0.1
DHCPREQUEST of 192.168.0.191 on eth2 to 255.255.255.255 port 67
DHCPNAK from 69.90.52.1
DHCPACK of 192.168.0.191 from 192.168.0.1
bound to 192.168.0.191 -- renewal in 4097 seconds.
 * Stopping the Firestarter firewall...
   ...done.
 * Starting the Firestarter firewall...
   ...fail!
run-parts: /etc/network/if-up.d/50firestarter exited with return code 2
ssh stop/waiting
ssh start/running, process 6732

```

Sure enough, I've got the address 192.168.0.191:
```

$ ifconfig
eth2      Link encap:Ethernet  HWaddr 00:0b:97:dc:59:2e  
          inet addr:192.168.0.191  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20b:97ff:fedc:592e/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:902738 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2228 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:76115742 (76.1 MB)  TX bytes:190957 (190.9 KB)
          Interrupt:19 Base address:0x2000 

```
and no connection:
```

$ ping google.com
ping: unknown host google.com

```

Today, on the other hand, I started up Lynx, and got a nice connection with an address starting with 69.90.

**But this is not even the whole problem!** Sometimes I get an address starting with 69.90 and *still* cannot open any web pages, ping anything, ssh anything, etc. etc. Nothing works.

It seems to be completely random.

I have changed no settings.

The only thing I can think of that has changed is that I have installed updates from Update Manager once or twice since this problem began. Still, why should that result in this kind of random, hit-or-miss behavior?

Here is my /etc/network/interfaces file:
```

$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth1
iface eth1 inet dhcp
wpa-ssid ########
wpa-psk ########

auto ath0

auto wlan0

auto eth2
iface eth2 inet dhcp

```

Can anyone figure this out? Thank you for any ideas!

---

### Post by doas777 on 2011-03-09
well all else aside, cablemodems don't like to have their cabling changed without a reboot, so if you are changing the host connected to the cable modem directly, then you will likely have to reboot the CM every time. 

I'd get a switch if not a router.

---

### Post by skief on 2011-03-17
I had been considering getting a switch, and, on your advice, went ahead with it. That was nearly a week ago, and so far the problems have been eliminated. Looks like a solution. Thanks for the advice!

---

