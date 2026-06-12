---
title: "Two ethernet cards"
date: 2009-01-22
forum: Networking &amp; Wireless
---

### Post by _pekka_ on 2009-01-22
Hi
I have an integrated network card and a USB to ethernet device on my laptop.
(integrated is eth0 and USB is eth1)
I want to connect to the internet by using eth0 and to a (private)LAN using eth1.
There is a router in the LAN but it is not allowed to use is for the internet connection. Both nets use DHCP.
What should I do? Edit /etc/network/interfaces ???
USB device is A-link NA1GU. Manufacturer says that it will work with Linux but I don't know how. Should I install some driver?

---

### Post by _pekka_ on 2009-01-22
ifconfig -a shows
eth0      Link encap:Ethernet  HWaddr 00:03:0d:21:d6:77  
          inet addr:ax.xx.15.129  Bcast:ax.xx.15.255  Mask:255.255.255.128
          inet6 addr: 2001:708:30:10b0:203:dff:fe21:d677/64 Scope:Global
          inet6 addr: fe80::203:dff:fe21:d677/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3375 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1301 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1263724 (1.2 MB)  TX bytes:198056 (193.4 KB)
          Interrupt:18 Base address:0xd800 

eth1      Link encap:Ethernet  HWaddr 00:1a:9f:0b:00:60  
          inet6 addr: fe80::21a:9fff:fe0b:60/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:55 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:12369 (12.0 KB)

eth1:avahi Link encap:Ethernet  HWaddr 00:1a:9f:0b:00:60  
          inet addr:169.254.3.90  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3852 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3852 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:192600 (188.0 KB)  TX bytes:192600 (188.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:0c:76:ff:ec:7f  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr 00-0C-76-FF-EC-7F-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by superprash2003 on 2009-01-22
presuming you want to share internet connection.. follow this [http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)

---

### Post by _pekka_ on 2009-01-22
No. I don't want share connection. I will use this LAN mainly for printing.

---

### Post by Iowan on 2009-01-22
In the older version I use (7.10), editing the information into /etc/network/interfaces was the only way to activate two interfaces at the same time.  I don't know if [this]("http://ubuntuforums.org/showthread.php?t=974382") workaround for static IP address could be adjusted to get both your cards activated.

[Another]("http://ubuntuforums.org/showthread.php?t=1022569") thread about activating two interfaces.

---

### Post by _pekka_ on 2009-01-24
Still not working :cry:

At first the promlem was that my laptop tried to access the internet by using the LAN. Then I tried
route add -net 192.168.0.1/24 netmask 255.255.255.128 dev eth1
or something like that. I also tried static settings for LAN. Then everyting started to work :o

I updated my computer and restart it. (Maybe few times)

Then I suddenly noticed that network isn't working any more.

I started the computer network cable unplugged. Internet (and eth0) started to work with command sudo /etc/init.d/networking restart

Everything is working with Windows XP HOME.

Router (in the Lan) can see A-link (and its mac-address).
Router has reserved ip for A-link so you could think that Lan is static.

Do you how to check whether A-link is working properly?

Is it possible to restore defaults? (for network or for A-link)

---

### Post by _pekka_ on 2009-01-25
anyone :?:

---

### Post by Iowan on 2009-01-25
I'm not familiar with A-links, but I thought you should probably see [this]("http://ubuntuforums.org/showpost.php?p=6571057&postcount=6") post.

---

### Post by _pekka_ on 2009-01-26
Thanks.
Unfortunately package gnome-network-admin is only for Intrepid but I am using 8.04 Hardy :(

Is it still possible to install it for Hardy? How?

---

### Post by Dareajoe on 2009-01-26
I need drivers to link my two gigabit ethernet cards to double my bandwith?I have an integrated ethernet card and a pci ethernet card that I need to link them togather to lower my latency for online games please help I have an xps 720 computer from dell.

---

### Post by Iowan on 2009-01-26
_pekka_
On Hardy (8.04), you should indeed be able to edit /etc/network/interfaces file to enable both cards.

Dareajoe
See [this]("http://ubuntuforums.org/showthread.php?t=1037422") thread - maybe your connection is different...

---

### Post by adoniasv on 2011-10-22
Try this

[http://kindlund.wordpress.com/2007/11/19/configuring-multiple-default-routes-in-linux/](http://kindlund.wordpress.com/2007/11/19/configuring-multiple-default-routes-in-linux/)

or

[http://www.linuxhorizon.ro/iproute2.html](http://www.linuxhorizon.ro/iproute2.html)

Wks 4 me!

@adoniasv

---

