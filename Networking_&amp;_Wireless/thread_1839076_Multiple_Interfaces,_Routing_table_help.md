---
title: "Multiple Interfaces, Routing table help"
date: 2011-09-04
forum: Networking &amp; Wireless
---

### Post by HuckBerry on 2011-09-04
I have an Ubuntu Server 10.04 LTS install on a desktop. I recently installed two more nic's into it. Currently I have the following configuration:

eth0 - dhcp - global - 68.232.xxx.xxx
eth1 - dhcp (static lease) - local - 10.0.0.2
eth2 - dhcp (static lease) - local - 172.16.0.1 (unused)

I want this server to have two purposes. 
1) On the public interface, as a torrent box
2) On the private interface, as a media streaming server.

Here's my problem: When eth0 is the only thing plugged in everything works great. Torrents work, I can ssh in via 68.232.xxx.xxx. awesome. The routing table looks like this:

```
me@Beta:~$ ip route
68.232.xxy.xxx/20 dev eth0  proto kernel  scope link  src 68.232.xxx.xxx
default via 68.232.xxy.xxx dev eth0  metric 100

```

But when I plug the eth1 port in, suddenly all my torrents stop. I can't ping the outside world at all, but I can ssh in at either address. The routing tables look like  this:

```
me@Beta:~$ ip route
10.0.0.0/24 dev eth1  proto kernel  scope link  src 10.0.0.2
68.232.xxy.xxx/20 dev eth0  proto kernel  scope link  src 68.232.xxx.xxx
default via 10.0.0.1 dev eth1
default via 68.232.xxy.xxx dev eth0  metric 100

```

So my question is what process controls the automagic creation of these tables, what commands can I use to control them, and (in general) how does linux manage multiple ports and what aids in it's decisions of how to route things.

---

### Post by Antoniya001 on 2011-09-24
I'm having a similar question, did you solve it ? 
 
My thread : [http://ubuntuforums.org/showthread.php?t=1849241](http://ubuntuforums.org/showthread.php?t=1849241)
 
Ar

---

### Post by terminus1 on 2011-09-29
I found this link to be helpful: [Configuring Multiple Default Routes in Linux]("http://kindlund.wordpress.com/2007/11/19/configuring-multiple-default-routes-in-linux/").

---

### Post by collisionystm on 2011-09-29
I had a similar problem. Look at the last post on this thread.

[http://ubuntuforums.org/showthread.php?t=1766575](http://ubuntuforums.org/showthread.php?t=1766575)

---

### Post by HuckBerry on 2011-10-03
I had seen the kindlund link (bookmarked it in fact) however I find that the easiest solution for my situation is to 

```
sudo ip route del default via 10.0.0.1
```

which simply removes eth1 as a default gateway. It doesn't make traffic leave the port it entered, but it does make all traffic originating at the client to leave via eth0, which was my short term goal.

---

