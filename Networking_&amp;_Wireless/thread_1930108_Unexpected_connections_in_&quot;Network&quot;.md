---
title: "Unexpected connections in &quot;Network&quot;"
date: 2012-02-23
forum: Networking &amp; Wireless
---

### Post by 7cardcha on 2012-02-23
Ok recently I opened up the "Network" folder and saw a BUNCH of computers with peoples names i've never heard of. (Here is a screenshot [http://i.imgur.com/pzuNd.png](http://i.imgur.com/pzuNd.png)) I checked my router. No strange connections. Anybody know what this is?(BTW I am pretty competent. I program in C++ and do OpenGL so I doubt it's a l33t hack3r messing with me.)

---

### Post by Grenage on 2012-02-23
Is this a laptop, do you regularly connect to other access points?  I'm merely wondering if details have been cached.

---

### Post by raja.genupula on 2012-02-23
> **7cardcha said:**
> Ok recently I opened up the "Network" folder and saw a BUNCH of computers with peoples names i've never heard of. (Here is a screenshot [http://i.imgur.com/pzuNd.png](http://i.imgur.com/pzuNd.png)) I checked my router. No strange connections. Anybody know WTF this is?(BTW I am pretty competent. I program in C++ and do OpenGL so I doubt it's a l33t hack3r messing with me.)

* I too have seen things like that , but i am using internet from a local service provider, there i am seeing the systems which are using the interet in windows and connected to a public network .  . may be those also connected to a public network .

the above case is work for a comman internet service provider (in my case)

* stalk the IP's connected to your PC . is there any IP which looks fishy . 
[http://superuser.com/questions/261818/how-can-i-list-all-ips-in-the-connected-network-through-terminal-preferably](http://superuser.com/questions/261818/how-can-i-list-all-ips-in-the-connected-network-through-terminal-preferably)

---

### Post by 7cardcha on 2012-02-23
It's not public internet. Here is some IP's

Address                  HWtype  HWaddress           Flags Mask            Iface
Office.local             ether   7a:79:05:44:ca:3f   C                     ham0
5.84.1.123               ether   7a:79:05:54:01:7b   C                     ham0
Bisho-Darras-MacBook-Pr  ether   7a:79:05:c3:1c:a2   C                     ham0
5.192.190.116            ether   7a:79:05:c0:be:74   C                     ham0
JolliffeFamily.local     ether   7a:79:05:91:fb:5b   C                     ham0
Rickys-MacBook-Air.loca  ether   7a:79:05:8c:cc:a5   C                     ham0
192.168.1.134            ether   00:18:c0:56:38:1e   C                     eth0
192.168.1.123            ether   00:26:22:58:3f:58   C                     eth0
5.36.4.146               ether   7a:79:05:24:04:92   C                     ham0

I edited out the IP's of my computers. BTW what is ham0? Thanks for helping me out.

---

### Post by greenpeace on 2012-02-23
Could ham0 be a hamachi interface for use with [Hamachi]("https://secure.logmein.com/products/hamachi/") VPN clients?

[http://ubuntuforums.org/showthread.php?t=135036](http://ubuntuforums.org/showthread.php?t=135036)

Does that sound familiar to you?

---

### Post by Grenage on 2012-02-23
[http://en.wikipedia.org/wiki/Hamachi_%28software%29](http://en.wikipedia.org/wiki/Hamachi_%28software%29)

Per chance, a cause?

---

### Post by 7cardcha on 2012-02-23
Well that would be the problem. Thanks. Joined some minecraft server's that used hamachi. Thanks.

---

### Post by raja.genupula on 2012-02-23
Cool now,  please mark the thread as solved from thread tools . 
Thank you .

---

