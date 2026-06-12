---
title: "Ubuntu Server Wireless Setup - WPA2 Personal - Airport Extream"
date: 2013-03-13
forum: Networking &amp; Wireless
---

### Post by tgrux on 2013-03-13
**Scenario:**
I am trying to setup a wireless connection on Ubuntu Server 12.10. I rebuilt a Dell Dimension E521 desktop and I'm using it as a test server in my house.  The problem is I don't have a hardwire connection where the server is setup, so I need wireless. Trying to connect to Apple Airport Extreme which is secured using WPA2 Personal.  

[B]Specs:
[/B]Dell Dimension Desktop - 64bit
Ubuntu Server 12.10 - fresh install
lsusb = ID 0b05:17ab ASUSTek Computer... USB-N13 802.11n Network
Wifi Connection: Apple Airport Extreem - WPA2 Personal encryption


**What I Tried:**
[LIST]
[*]I briefly installed Ubuntu Desktop 12.10 and wireless worked right out of the box.  I didn't have to install any drivers or anything, just entered my WPA2 password.  So I assume it should be pretty easy for the server edition.
[*]When running iwconfig on Ubuntu Server, the card is recognized as a wireless card.  It just seems like the system doesn't want to use it.
[*]I have been all over the forum looking at posts and trying suggestions, but nothing has worked.
[/LIST]

If anyone has any suggestions, I re-installed the OS so I'm starting fresh and open to ideas.

---

### Post by tgrux on 2013-03-14
A few updates on my progress.  The issue seems to be with simply finding network.  When I run "iwlist wlan0 scanning" I get back "no scan results".

---

### Post by chili555 on 2013-03-14
The usual method in a server is to complete the details in /etc/network/interfaces something like this:```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static  [COLOR="#FF0000"]<---you did want to be able to find it, ftp, ssh, etc., correct?[/COLOR]
address 192.168.1.101  [COLOR="#FF0000"]<---an address outside the DHCP range in the router[/COLOR]
netmask 255.255.255.0
gateway 192.168.1.1
wpa-ssid <your_network>
wpa-psk <your key>
dns-nameservers 192.168.1.1 8.8.8.8
```Then restart the interface:```
sudo ifdown wlan0 && sudo ifup wlan0
```Did it get the x.101 address?```
ifconfig
```Can you reach the world?```
ping -c3 www.google.com
```Of course, your details will be different. 

Post back if it doesn't go perfectly.

---

### Post by chili555 on 2013-03-14
> **tgrux said:**
> A few updates on my progress.  The issue seems to be with simply finding network.  When I run "iwlist wlan0 scanning" I get back "no scan results".Please let us see:```
iwconfig
dmesg | grep wlan
```Is the result the same with: ```
**sudo** iwlist wlan0 scan
```

---

### Post by tgrux on 2013-03-14
Yes, the iwlist wlan0 scan was the same result.  

I ended up re-installing the Ubuntu Desktop version since it was working with no issues.  I really wanted a "pure" server but I don't think servers were meant to run with a wifi connection...In other words I think it might have been more work then it was worth.

Anyway, sorry for the questions and then jumping ship on the issue.  Hopefully someone else can benefit from your good advise.

---

### Post by chili555 on 2013-03-14
> I don't think servers were meant to run with a wifi connection.No more or less so than any other interface. There is nothing inherent in servers that's unfriendly to wireless. Whether it is worth the time and effort is, of course, entirely up to you.

I would have been very happy to troubleshoot and I'm quite confident we'd have been successful.

---

### Post by Dougy00 on 2013-04-05
> **chili555 said:**
> No more or less so than any other interface. There is nothing inherent in servers that's unfriendly to wireless. Whether it is worth the time and effort is, of course, entirely up to you.

I would have been very happy to troubleshoot and I'm quite confident we'd have been successful.

I config the wlan0 and now I got the ip but I can't ping Google. I running on a clean install of ubuntu server 12.10.

```
wlan0     Link encap:Ethernet  HWaddr f0:7b:cb:29:ca:9e
          inet addr:192.168.1.24  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::f27b:cbff:fe29:ca9e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1512 errors:0 dropped:291 overruns:0 frame:0
          TX packets:192 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:230429 (230.4 KB)  TX bytes:29498 (29.4 KB)

server@server:~$ ping -c3 www.google.com
ping: unknown host www.google.com


```

Ping to router
```

PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_req=1 ttl=64 time=1.38 ms
64 bytes from 192.168.1.1: icmp_req=2 ttl=64 time=2.57 ms
64 bytes from 192.168.1.1: icmp_req=3 ttl=64 time=5.50 ms
64 bytes from 192.168.1.1: icmp_req=4 ttl=64 time=0.952 ms
64 bytes from 192.168.1.1: icmp_req=5 ttl=64 time=0.905 ms
64 bytes from 192.168.1.1: icmp_req=6 ttl=64 time=0.973 ms
64 bytes from 192.168.1.1: icmp_req=7 ttl=64 time=0.946 ms
64 bytes from 192.168.1.1: icmp_req=8 ttl=64 time=0.952 ms
64 bytes from 192.168.1.1: icmp_req=9 ttl=64 time=3.01 ms
64 bytes from 192.168.1.1: icmp_req=10 ttl=64 time=0.961 ms

--- 192.168.1.1 ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 9003ms
rtt min/avg/max/mdev = 0.905/1.817/5.507/1.426 ms

```

---

### Post by chili555 on 2013-04-05
> **Dougy00 said:**
> I config the wlan0 and now I got the ip but I can't ping Google. I running on a clean install of ubuntu server 12.10.

If you can get to the router, but not the world at large, that suggests a problem with DNS nameservers. May we please see:```
cat /etc/network/interfaces
```Please obscure your wireless key; something like 'wpa-psk xxyyzz' will be fine.

---

### Post by Dougy00 on 2013-04-06
> **chili555 said:**
> If you can get to the router, but not the world at large, that suggests a problem with DNS nameservers. May we please see:```
cat /etc/network/interfaces
```Please obscure your wireless key; something like 'wpa-psk xxyyzz' will be fine.

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
address 192.168.1.24
netmask 255.255.255.0
gateway 192.168.1.1
wpa-ssid YYYYYYYYY
wpa-psk XXXXXXXXX
dnsnameservers 192.168.1.1 8.8.8.8

```

Edit: Find the error I forgat the "-" in dns-nameservers. Thanks for all the help.

---

### Post by chili555 on 2013-04-06
> dnsnameservers 192.168.1.1 8.8.8.8Ah, ha! There is an error here and, unfortunately, the system has no 'I know what you really meant' function. Please amend your file so the line reads:```
dns[COLOR="#FF0000"]**-**[/COLOR]nameservers 192.168.1.1 8.8.8.8
```Proofread carefully and save. Then restart the interface:```
sudo ifdown wlan0 && sudo ifup wlan0
```Confirm you are all set:```
ping -c3 www.google.com
```

---

### Post by Dougy00 on 2013-04-06
> **chili555 said:**
> Ah, ha! There is an error here and, unfortunately, the system has no 'I know what you really meant' function. Please amend your file so the line reads:```
dns[COLOR=#FF0000]**-**[/COLOR]nameservers 192.168.1.1 8.8.8.8
```Proofread carefully and save. Then restart the interface:```
sudo ifdown wlan0 && sudo ifup wlan0
```Confirm you are all set:```
ping -c3 www.google.com
```

I works now. Thanks for the help!

---

