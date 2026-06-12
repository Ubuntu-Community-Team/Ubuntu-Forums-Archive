---
title: "Intel 4965 AGN DHCP timeout on open access point"
date: 2009-09-10
forum: Networking &amp; Wireless
---

### Post by modafokaxx on 2009-09-10
Hello boys and girls, I'm kinda stumped by this one so if you have an idea, I'm all ears! :KS

I am trying to connect to an open wi-fi network, unsuccessfully. No encryption, plain open acces point advertising itself as "linksys".

It has worked a few times but it has stopped working the past few days and, strangely, has never worked on my girlfriend's computer, even though it has the same chip (Intel 4965 agn) and the same up to date version of Ubuntu (9.04).
I'm (we are) using NetworkManager v 0.7.0.1000

I've pretty much tracked it down to being a DHCP issue. Ie: network manager calls dhclient which in turns sends DHCPREQUESTs on the broadcast address, never gets a reply in time, and gives up.
When it has worked, the dhclient does it's work fine and the DHCPREQUESTs are met with a DHCPOFFER.
What I can't exlpain anyway is way it has worked many times for me, only failing now and then, and consistently failed for on my girlfriend's laptop.

I have reasons to believe that the DHCP server on the other side (to which I do not have access) is not entirely usual. It serves an Australian "Big Pond" connection and when connected, gives an address that is an external IP address that appears to be given out directly by the ISP.
The subnet mask for instance is unusual, though consistent with large subnets: 255.255.248.0

Is it possible the router is not to blame and the ISP's DHCP server may not be doing its thing right?

I have tried many things: disabling draft N network compatibility with modprobe, connecting to the AP manually with sudo iwconfig wlan0 essid="linksys" and then running dhclient manually does not work any better. I've also tried editing /etc/dhclient3/dhclient.conf to minimize the stuff requested by dhclient, but that doesn's help either.
On my own computer I've also tried installing linux-backports-modules-jaunty and linux-backports-modules-jaunty-generic, but didn't change anything.
I have not tried changing dhcp client, how would I go about that, would NetworkManager automatically adjust?

Anyway, any ideas are most welcome!

Thanks everyone :)

4965 agn Intel Wireless chip

lspci -v | less
```
06:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedro
n] Network Connection (rev 61)
        Subsystem: Intel Corporation Device 1101
        Flags: bus master, fast devsel, latency 0, IRQ 2296
        Memory at fa000000 (64-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>
        Kernel driver in use: iwlagn
        Kernel modules: iwlagn
```


Relevant part of daemon.log
```
21:52:18  NetworkManager: <info>  Activation (wlan0) starting connection 'Auto linksys' 
21:52:18  NetworkManager: <info>  (wlan0): device state change: 3 -> 4 
21:52:18  NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
21:52:18  NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
21:52:18  NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
21:52:18  NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
21:52:18  NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
21:52:18  NetworkManager: <info>  (wlan0): device state change: 4 -> 5 
21:52:18  NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto linksys' requires no security.  No secrets needed. 
21:52:18  NetworkManager: <info>  Config: added 'ssid' value 'linksys' 
21:52:18  NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
21:52:18  NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE' 
21:52:18  NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
21:52:18  NetworkManager: <info>  Config: set interface ap_scan to 1 
21:52:18  NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning 
21:52:20  NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating 
21:52:20  NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated 
21:52:20  NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> completed 
21:52:20  NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'linksys'. 
21:52:20  NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled. 
21:52:20  NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started... 
21:52:20  NetworkManager: <info>  (wlan0): device state change: 5 -> 7 
21:52:20  NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction. 
21:52:20  NetworkManager: <info>  dhclient started with pid 6181 
21:52:20  NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete. 
21:52:20  dhclient: Internet Systems Consortium DHCP Client V3.1.1
21:52:20  dhclient: Copyright 2004-2008 Internet Systems Consortium.
21:52:20  dhclient: All rights reserved.
21:52:20  dhclient: For info, please visit http://www.isc.org/sw/dhcp/
21:52:20  dhclient: 
21:52:20  NetworkManager: <info>  DHCP: device wlan0 state changed normal exit -> preinit 
21:52:20  dhclient: Listening on LPF/wlan0/00:1d:e0:xx:xx:xx
21:52:20  dhclient: Sending on   LPF/wlan0/00:1d:e0:xx:xx:xx
21:52:20  dhclient: Sending on   Socket/fallback
21:52:23  dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
21:52:28  dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
21:52:34  dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
21:52:47  dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
21:52:59  dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
21:53:06  NetworkManager: <info>  Device 'wlan0' DHCP transaction took too long (>45s), stopping it. 
21:53:06  NetworkManager: <info>  wlan0: canceled DHCP transaction, dhcp client pid 6181 
21:53:06  NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Timeout) scheduled... 
21:53:06  NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Timeout) started... 
21:53:06  NetworkManager: <info>  (wlan0): device state change: 7 -> 9 
21:53:06  NetworkManager: <info>  Activation (wlan0) failed for access point (linksys) 
21:53:06  NetworkManager: <info>  Marking connection 'Auto linksys' invalid. 
21:53:06  NetworkManager: <info>  Activation (wlan0) failed. 
21:53:06  NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Timeout) complete. 
21:53:06  NetworkManager: <info>  (wlan0): device state change: 9 -> 3 
21:53:06  NetworkManager: <info>  (wlan0): deactivating device (reason: 0). 
```


when working, here is the relevant part of daemon.log:
```
15:47:59 dhclient: Listening on LPF/wlan0/00:1d:e0:xx:xx:xx
15:47:59 dhclient: Sending on   LPF/wlan0/00:1d:e0:xx:xx:xx
15:47:59 dhclient: Sending on   Socket/fallback
15:47:59 dhclient: DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
15:47:59 dhclient: DHCPOFFER of 58.160.113.xxx from 10.228.48.1
15:47:59 dhclient: DHCPREQUEST of 58.160.113.xxx on wlan0 to 255.255.255.255 port 67
15:47:59 dhclient: DHCPACK of 58.160.113.xxx from 10.228.48.1
15:47:59 dhclient: bound to 58.160.113.xxx -- renewal in 18686 seconds.
15:47:59 NetworkManager: <info>  DHCP: device wlan0 state changed preinit -> bound 
15:47:59 NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) scheduled... 
15:47:59 NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) started... 
15:47:59 NetworkManager: <info>    address 58.160.113.xxx 
15:47:59 NetworkManager: <info>    prefix 21 (255.255.248.0) 
15:47:59 NetworkManager: <info>    gateway 58.160.112.1 
15:47:59 NetworkManager: <info>    hostname 'xxxxxxxxxxx' 
15:47:59 NetworkManager: <info>    nameserver '61.9.133.193' 
15:47:59 NetworkManager: <info>    nameserver '61.9.134.49' 
15:47:59 NetworkManager: <info>    domain name 'vic.bigpond.net.au' 
```

cat /etc/nework/interfaces
```
auto lo
iface lo inet loopback

```

Any other info needed I will happily provide. :popcorn:

Also, I tried searching the forums/bugtracker/mailing lists but to no avail. The closest interesting thing I found on my last search frenzy was [this](http://www.google.com/url?sa=t&source=web&ct=res&cd=2&url=http%3A%2F%2Fwww.nabble.com%2FConnecting-to-hotel-wireless-networks-td17405318.html&ei=t_2oSsqvLIKSsgPT49yYBQ&rct=j&q=NetworkManager%3A+%3Cinfo%3E++Device+%27wlan0%27+DHCP+transaction+took+too+long+(%3E45s)%2C+stopping+it.&usg=AFQjCNGmsX2NqJsPqFQBa2Z4-0jeI1MSng), but I can't get it to work, even though I can see how that info could help (I don't know what static route I'd need to set up, even though I can see where to do it in NetworkManager).

---

### Post by modafokaxx on 2009-09-12
Hmm, my problem doesn't seem to be sexy enough, no one interested? :D

Anyway, I've found a workaround.

By setting an IP address manually, I was able to connect to the AP, even though nothing else works. From there, I pinged broadcast to see if anything would answer
```
ping 255.255.255.255 -b
```
used nmap to see if any of the addresses answering could be a router/residential gateway:
```
nmap -a 192.168.x.x
``` told me the host was answering on port 80 so I then pointed Firefox to the address, and rebooted the router from there.

DHCP now works again.

So I would tend to believe that the router is an Old Piece of Crap&#8482; (Motorola SurfBoard 5100).

However, had the router been locked, without physical access to it I couldn't have solved this problem.
On the other hand, this isn't really Ubuntu or Linux problem. Hell, I tried to boot into Windows XP to see if there was any difference, I would eventually get an IP address, but connectivity remained useless.

So there, worked around, but not solved. And still no answer as to why it works on my computer but not on my girlfriend's.

EDIT: It now also works on my girlfriend's computer, my sanity is restored. Also, this cable modem is clearly crap.

---

