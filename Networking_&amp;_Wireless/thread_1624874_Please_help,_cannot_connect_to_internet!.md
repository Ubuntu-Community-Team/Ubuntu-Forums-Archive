---
title: "Please help, cannot connect to internet!"
date: 2010-11-18
forum: Networking &amp; Wireless
---

### Post by germanix on 2010-11-18
Hi all, I have received an mail in my Forum inbox from someone unknown to me but requesting help. I myself have no idea what his/her problem is but would like, with your help, to help this user. here is a copy of the letter I received:

I'm new to linux environment....... I have a dsl broadband connection which requires user-name and password to connect. I usually connect to internet using SUDO PON DSL-PROVIDER and disconnect using SUDO POFF. But now i cant access internet now........ some of my observations are....


hari@hari-desktop ~ $ sudo pon dsl-provider
Plugin rp-pppoe.so loaded.
RP-PPPoE plugin version 3.8p compiled against pppd 2.4.5


hari@hari-desktop ~ $ ifconfig
>
eth0 Link encap:Ethernet HWaddr 00:1a:92:0c:c9:18
inet addr:192.168.1.2 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::21a:92ff:fe0c:c918/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:50 errors:0 dropped:0 overruns:0 frame:0
TX packets:39 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:100
RX bytes:3694 (3.6 KB) TX bytes:1858 (1.8 KB)
Memory:fdfc0000-fdfe0000

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:52 errors:0 dropped:0 overruns:0 frame:0
TX packets:52 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:2584 (2.5 KB) TX bytes:2584 (2.5 KB)

ppp0 Link encap:Point-to-Point Protocol
inet addr:117.204.119.188 P-t-P:117.204.112.1 Mask:255.255.255.255
UP POINTOPOINT RUNNING NOARP MULTICAST MTU:1460 Metric:1
RX packets:21 errors:0 dropped:0 overruns:0 frame:0
TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:3
RX bytes:986 (986.0 B) TX bytes:54 (54.0 B)

hari@hari-desktop ~ $ plog
hari@hari-desktop ~ $ dpkg -s pppoeconf
Package: pppoeconf
Status: install ok installed
Priority: optional
Section: net
Installed-Size: 340
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: all
Version: 1.19ubuntu1
Depends: whiptail-provider | whiptail, ppp (>= 2.4.2+20040428-2) | pppoe (>= 3.0), ppp (>= 2.4.1.uus2-4), gettext-base (>= 0.13), sed (>= 3.95)
Recommends: locales
Suggests: xdialog
Description: configures PPPoE/ADSL connections
User-friendly tool for initial configuration of a DSL (PPPoE) connection.
Original-Maintainer: Gregory Colpart <reg@debian.org>
hari@hari-desktop ~ $ ping [http://www.google.com](http://www.google.com)
ping: unknown host [http://www.google.com](http://www.google.com)
 
Any idea what this all means and how I can help this user?
thanks

---

### Post by pricetech on 2010-11-18
I'd suggest that the user post to this, or some other, forum himself / herself.

If they can send you an email, they can post.

Certainly not criticizing you for trying to help someone out, but whenever you add a "middleman" to the conversation, something gets lost, if nothing but time.

We can help much better if they post directly.

---

### Post by germanix on 2010-11-18
I agree fully. For that reason I mailed the user a link to this post and asked him/her to watch this post himself and to follow the instructions posted here. I am no longer the middle man.

---

### Post by pricetech on 2010-11-18
Good answer.

---

### Post by dineshs on 2010-11-19
> ppp0 Link encapoint-to-Point Protocol
inet addr:117.204.119.188 P-t-P:117.204.112.1 Mask:255.255.255.255
UP POINTOPOINT RUNNING NOARP MULTICAST MTU:1460 Metric:1
RX packets:21 errors:0 dropped:0 overruns:0 frame:0
TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:3
RX bytes:986 (986.0 B) TX bytes:54 (54.0 B)
Means connected.If pages are not loading try a different DNS
Run this in a terminal```
sudo gedit /etc/resolv.conf
```
Backup the contents of the file first .then let it contain only```
nameserver 4.2.2.1
```save and close.Try if pages are loading
Note :Any text editor can be used instead of [COLOR="Blue"]gedit[/COLOR]
Any working DNS can be used instead of [COLOR="Blue"]4.2.2.1[/COLOR]

---

