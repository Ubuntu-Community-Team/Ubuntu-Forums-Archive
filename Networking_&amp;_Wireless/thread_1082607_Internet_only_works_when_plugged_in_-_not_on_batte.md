---
title: "Internet only works when plugged in - not on battery"
date: 2009-02-28
forum: Networking &amp; Wireless
---

### Post by Maheriano on 2009-02-28
I put together a Dell D600 for my brother with 32 bit 8.1 on it and it worked perfect for me. I'm positive I had it running on my wireless network on the battery power when it was here. Now he's got it in his possession 5000 kilometres away on his own network and it'll only connect to the network when plugged in.

He'll be running on battery power and he'll see the network and connect to it. It says he's connected but when he opens Firefox it won't display any pages. He has to plug the computer into the wall, reboot and then it'll work no problem. He tried it multiple times and I find it very bizarre. I know this laptop has a Fcn button for turning the wireless on/off but it's not like he keeps turning it off every time for no reason. Where do I even begin with this?

---

### Post by Iowan on 2009-02-28
Check "power savings" options (BIOS, maybe?).

FYI, [here]("http://ubuntuforums.org/showthread.php?t=1082853") is a thread about a laptop that won't even boot on battery.

---

### Post by Maheriano on 2009-03-16
So here's the pinging from the Terminal and as you can see, it just stops reaching the server. This happens with webpages or anything. For some reason it'll connect and then about 20 seconds later it's not connected anymore. The wireless signal says it's connected, the router is about 8 feet from me and all the settings are correct. I'm broadcasting b and g and this computer is b only. It's weird. I got nothing else on the wireless on this router, just a desktop and a server wired into it.

> travis@travis-laptop:~$ ping [www.yahoo.ca](www.yahoo.ca)
PING frontpage.ca.fy10.b.yahoo.com (206.190.34.135) 56(84) bytes of data.
64 bytes from w1.fp.ca.vip.re2.yahoo.com (206.190.34.135): icmp_seq=1 ttl=54 time=68.7 ms
64 bytes from w1.fp.ca.vip.re2.yahoo.com (206.190.34.135): icmp_seq=2 ttl=54 time=69.4 ms
64 bytes from w1.fp.ca.vip.re2.yahoo.com (206.190.34.135): icmp_seq=3 ttl=54 time=64.8 ms
64 bytes from w1.fp.ca.vip.re2.yahoo.com (206.190.34.135): icmp_seq=4 ttl=54 time=65.0 ms
64 bytes from w1.fp.ca.vip.re2.yahoo.com (206.190.34.135): icmp_seq=5 ttl=54 time=64.8 ms
64 bytes from w1.fp.ca.vip.re2.yahoo.com (206.190.34.135): icmp_seq=6 ttl=54 time=421 ms
64 bytes from w1.fp.ca.vip.re2.yahoo.com (206.190.34.135): icmp_seq=7 ttl=54 time=66.0 ms
64 bytes from w1.fp.ca.vip.re2.yahoo.com (206.190.34.135): icmp_seq=8 ttl=54 time=64.7 ms
64 bytes from w1.fp.ca.vip.re2.yahoo.com (206.190.34.135): icmp_seq=9 ttl=54 time=65.4 ms
64 bytes from w1.fp.ca.vip.re2.yahoo.com (206.190.34.135): icmp_seq=10 ttl=54 time=70.2 ms
64 bytes from w1.fp.ca.vip.re2.yahoo.com (206.190.34.135): icmp_seq=11 ttl=54 time=69.7 ms
64 bytes from w1.fp.ca.vip.re2.yahoo.com (206.190.34.135): icmp_seq=12 ttl=54 time=73.6 ms
64 bytes from w1.fp.ca.vip.re2.yahoo.com (206.190.34.135): icmp_seq=13 ttl=54 time=76.9 ms
64 bytes from w1.fp.ca.vip.re2.yahoo.com (206.190.34.135): icmp_seq=14 ttl=54 time=71.9 ms
64 bytes from w1.fp.ca.vip.re2.yahoo.com (206.190.34.135): icmp_seq=15 ttl=54 time=70.3 ms
64 bytes from w1.fp.ca.vip.re2.yahoo.com (206.190.34.135): icmp_seq=16 ttl=54 time=65.5 ms
64 bytes from w1.fp.ca.vip.re2.yahoo.com (206.190.34.135): icmp_seq=17 ttl=54 time=70.3 ms
64 bytes from w1.fp.ca.vip.re2.yahoo.com (206.190.34.135): icmp_seq=18 ttl=54 time=70.2 ms
64 bytes from w1.fp.ca.vip.re2.yahoo.com (206.190.34.135): icmp_seq=19 ttl=54 time=66.3 ms
64 bytes from w1.fp.ca.vip.re2.yahoo.com (206.190.34.135): icmp_seq=20 ttl=54 time=64.7 ms
64 bytes from w1.fp.ca.vip.re2.yahoo.com (206.190.34.135): icmp_seq=21 ttl=54 time=63.7 ms
64 bytes from w1.fp.ca.vip.re2.yahoo.com (206.190.34.135): icmp_seq=22 ttl=54 time=83.7 ms
64 bytes from w1.fp.ca.vip.re2.yahoo.com (206.190.34.135): icmp_seq=23 ttl=54 time=68.6 ms
64 bytes from w1.fp.ca.vip.re2.yahoo.com (206.190.34.135): icmp_seq=24 ttl=54 time=64.7 ms
64 bytes from w1.fp.ca.vip.re2.yahoo.com (206.190.34.135): icmp_seq=25 ttl=54 time=70.1 ms
64 bytes from w1.fp.ca.vip.re2.yahoo.com (206.190.34.135): icmp_seq=26 ttl=54 time=67.9 ms
64 bytes from w1.fp.ca.vip.re2.yahoo.com (206.190.34.135): icmp_seq=27 ttl=54 time=64.8 ms
64 bytes from w1.fp.ca.vip.re2.yahoo.com (206.190.34.135): icmp_seq=28 ttl=54 time=91.1 ms
64 bytes from w1.fp.ca.vip.re2.yahoo.com (206.190.34.135): icmp_seq=29 ttl=54 time=79.5 ms
64 bytes from w1.fp.ca.vip.re2.yahoo.com (206.190.34.135): icmp_seq=30 ttl=54 time=67.3 ms
64 bytes from w1.fp.ca.vip.re2.yahoo.com (206.190.34.135): icmp_seq=31 ttl=54 time=75.1 ms
64 bytes from w1.fp.ca.vip.re2.yahoo.com (206.190.34.135): icmp_seq=32 ttl=54 time=68.9 ms
64 bytes from 206.190.34.135: icmp_seq=33 ttl=54 time=65.7 ms
From travis-laptop.local (10.0.0.3) icmp_seq=65 Destination Host Unreachable
From travis-laptop.local (10.0.0.3) icmp_seq=66 Destination Host Unreachable
From travis-laptop.local (10.0.0.3) icmp_seq=67 Destination Host Unreachable
^Z
[2]+  Stopped                 ping [www.yahoo.ca](www.yahoo.ca)
travis@travis-laptop:~$ 


---

