---
title: "Internet very slow after I connect to a windows VPN server"
date: 2008-12-14
forum: Networking &amp; Wireless
---

### Post by cmsimike on 2008-12-14
Hello All,

I've set up a VPN connection to connect to a Windows VPN host as described here [http://www.cmsimike.com/blog/2008/11/16/connect-to-a-windows-vpn-pptp-from-ubuntu-810-intrepid-ibex/](http://www.cmsimike.com/blog/2008/11/16/connect-to-a-windows-vpn-pptp-from-ubuntu-810-intrepid-ibex/) (hehe self promotion, but it is exactly how I set it up). As usual, once the VPN was connected, I would not be able to access the internet at all from my computer. Using this link [http://ubuntuforums.org/showthread.php?t=934946](http://ubuntuforums.org/showthread.php?t=934946), I was able to finally keep the internet working on my computer while connected to a VPN, however when the vpn is connected, my internet becomes VERY slow. Not slow as in huge pings times or anything, but, for instance, time between each ping response is longer. 

here is a tracepath to [www.google.com](www.google.com) with no vpn connection:

```
mike@computer:~$ tracepath www.google.com
 1:  computer.lan (192.168.0.100)                             0.151ms pmtu 1500
 1:  router.lan (192.168.0.1)                              1.169ms 
 1:  router.lan (192.168.0.1)                              1.230ms 
 2:  IP.pacbell.net (x.x.x.x)                              36.368ms 
 3:  dist3-vlan50.irvnca.sbcglobal.net (67.114.50.1)       36.449ms 
 4:  bb1-g2-0.irvnca.sbcglobal.net (151.164.41.221)        36.210ms 
 5:  ex2-p8-0.eqlaca.sbcglobal.net (151.164.41.33)         38.701ms asymm  7 
 6:  no reply
 7:  no reply
 8:  no reply
 9:  no reply
10:  no reply
11:  no reply

```

Here is the ping to google.com
```

ping 74.125.19.104
PING 74.125.19.104 (74.125.19.104) 56(84) bytes of data.
64 bytes from 74.125.19.104: icmp_seq=1 ttl=242 time=21.5 ms
64 bytes from 74.125.19.104: icmp_seq=2 ttl=241 time=23.6 ms
64 bytes from 74.125.19.104: icmp_seq=3 ttl=241 time=23.3 ms
64 bytes from 74.125.19.104: icmp_seq=4 ttl=242 time=23.9 ms
^C
--- 74.125.19.104 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3011ms
rtt min/avg/max/mdev = 21.519/23.116/23.947/0.948 ms

```

Here are the same things with the VPN active.
```

mike@computer:~$ tracepath www.google.com
 1:  computer.lan (192.168.0.100)                             0.164ms pmtu 1500
 1:  router.lan (192.168.0.1)                              1.157ms 
 1:  router.lan (192.168.0.1)                              1.076ms 
 2:  IP.pacbell.net (x.x.x.x)                              41.692ms 
 3:  dist3-vlan50.irvnca.sbcglobal.net (67.114.50.1)       42.416ms 
 4:  bb1-g2-0.irvnca.sbcglobal.net (151.164.41.221)        36.885ms 
 5:  ex2-p8-0.eqlaca.sbcglobal.net (151.164.41.33)         38.668ms asymm  7 
 6:  no reply
 7:  no reply
 8:  no reply
 9:  no reply
10:  no reply
11:  no reply
12:  no reply


```

```

mike@computer:~$ ping www.google.com
PING www.l.google.com (74.125.19.104) 56(84) bytes of data.
64 bytes from cf-in-f104.google.com (74.125.19.104): icmp_seq=1 ttl=241 time=21.7 ms
64 bytes from cf-in-f104.google.com (74.125.19.104): icmp_seq=2 ttl=242 time=24.1 ms

```
For this ping, I stopped it after 2 because it was just taking too long to respond, but you wouldn't be able to tell that just looking at the ping time. 

What am I doing wrong here?

---

### Post by cmsimike on 2008-12-14
I should also note that VPN speed does not seem to be effected at all. This was tested using ping to a computer on the VPN. The response times were quick.

---

