---
title: "wireless ad-hoc. HOW?"
date: 2010-08-05
forum: Networking &amp; Wireless
---

### Post by vangop on 2010-08-05
hi!
I just removed ubuntu-desktop in favor of kubuntu-desktop.
Now I can't create an ad-hoc wifi connection however hard I tried from network-manager.  It simply is not visible to other PCs. And when some connection is created on another ubuntu PC, I can't connect to it..

I switched NM off and tried the CLI [way]("https://help.ubuntu.com/community/WifiDocs/Adhoc").

```
sudo iwconfig eth0 mode ad-hoc
```
```
sudo iwconfig eth0 essid mysid
```
```
sudo iwconfig eth0 key s:abcde
```
+ setup the ip/mask.
ok, I got connected to the net this way, i can ping the other PC, but that PC can't ping me.
```
$ sudo tcpdump -i eth1 -vn
17:34:32.930093 ARP, Ethernet (len 6), IPv4 (len 4), Request who-has 169.254.111.1 tell 169.254.111.5, length 28
17:34:37.992986 ARP, Ethernet (len 6), IPv4 (len 4), Request who-has 169.254.111.1 tell 169.254.111.5, length 28
17:34:43.493074 ARP, Ethernet (len 6), IPv4 (len 4), Request who-has 169.254.111.1 tell 169.254.111.5, length 28
17:34:48.993146 ARP, Ethernet (len 6), IPv4 (len 4), Request who-has 169.254.111.1 tell 169.254.111.5, length 28
...

```

looks like my pc is not responding to arp-who so that PC can't connect to me :(

Can anybody help me with this mess? (any hint on how to setup wifi adhoc)

---

### Post by vangop on 2010-08-06
Ok, just for the record. The search revealed that one can't setup an ad-hoc wifi on kubuntu. The interface has 'create new network' but when you click it the window just hides and nothing happens. This bug has been here for years, so just remove NM and install wicd or use CLI to manage wifi.

---

