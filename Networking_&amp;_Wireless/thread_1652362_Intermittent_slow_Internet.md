---
title: "Intermittent slow Internet"
date: 2010-12-24
forum: Networking &amp; Wireless
---

### Post by red91sit on 2010-12-24
I have recently replaced a hard drive on a Toshiba Satellite L35, I installed ubuntu 10.10.  The one problem I have is only certain sites work.  Google works everytime, but only about half the links from google work.  The other half will either partially load, or not load at all and just sit at "waiting for www.sitename.com...", I can watch the network monitor, and as soon as this happens it drops down to zero.  If I go to a working site, it pops right back into working.  

I've tried disabling ipv6 both in firefox, and on the whole computer.  I've tried chromium, and chrome, with the same results.  I even went as far as installing mint on the same computer, but it has the exact same problem.  It downloads updates no problem, and youtube can stream certain videos.  I am typing this from my netbook connected to the same network.  I'm using XP right now, but when I boot into Ubuntu 10.10 on this computer, it works absolutely fine.  

Also, yahoo seems to be worst site (and my primary email adress). On my own very basic website, all the pages are built off the same basic template, the only differences are the text and pictures.  Even here though, only about half the pages will load.  

Thanks for any help!

red91sit

:EDIT: I should probably mention the reason for the hard drive replacement... Late one evening, my computer decided to partake in the festivities and drank about half of an adult beverage.  I soaked it in rubbing alcohol (worked on my last computer and smartphone) but this time the hard drive went poop.  I replaced it with a used one (full of stuff written in German).  I tried to also put XP on this drive, but it wouldn't go, Linux didn't go on easy either... it took about 10 tries for each one to load completely.

It doesn't seem like a wireless card issue (since it's more site specific) but I figured that I would mention this minor detail.

---

### Post by red91sit on 2010-12-25
Update, I did several ping tests, and It would go through if it was under 1448, so I set my MTU to 1440, but after a restart, it was acting just like it did before?  With MTU set to Auto or 1500, I get this when I ping things

```
ping www.cisco.com -c 1 -s 1450 -M do
PING origin-www.cisco.com (72.163.4.161) 1450(1478) bytes of data.
From George (192.168.1.104) icmp_seq=1 Frag needed and DF set (mtu = 1440)

--- origin-www.cisco.com ping statistics ---
0 packets transmitted, 0 received, +1 errors
```It seems to be fine with a lower count, as shown here

```
ping www.cisco.com -c 1 -s 1400 -M do
PING origin-www.cisco.com (72.163.4.161) 1400(1428) bytes of data.
1408 bytes from www1.cisco.com (72.163.4.161): icmp_req=1 ttl=106 time=152 ms

--- origin-www.cisco.com ping statistics ---
1 packets transmitted, 1 received, 0% packet loss, time 0ms
rtt min/avg/max/mdev = 152.830/152.830/152.830/0.000 ms

```

I changed it because it was acting very similar to this thread [http://ubuntuforums.org/showthread.php?t=1376506](http://ubuntuforums.org/showthread.php?t=1376506)
unforunatly, this doens't seem to fix my problem :-(

Also, it works fine when plugged into the router through a wired connection, so I can do that, I'd just really prefer to get my wifi working.

Thanks!

---

