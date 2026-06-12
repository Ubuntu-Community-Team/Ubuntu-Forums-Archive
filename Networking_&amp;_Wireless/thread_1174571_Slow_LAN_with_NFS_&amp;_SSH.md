---
title: "Slow LAN with NFS &amp; SSH"
date: 2009-05-31
forum: Networking &amp; Wireless
---

### Post by detroit/zero on 2009-05-31
I have a small LAN consisting of two wireless laptops behind a Linksys WRT54GL router, connected to the internets via high-speed cable connection.

My speeds to/from the internet are "as advertised", and sometimes even better. My local speeds are what's giving me problems.

My two laptops are a Toshiba Satellite a135 and an Acer Travelmate 2480. The Toshiba is running an up-to-date Hardy Heron, the Acer is running Jaunty. The router is a WRT54GL using Tomato v1.24

I have ssh access to both computers, and regularly use SSH & SCP to move files between the two. I also have NFS enabled on both machines withs several folders being exported from each system. Of course, using Firestarter, I've opened all the relevant ports on each machine for connections from the other host.

My NFS transfer speeds are beyond horrible, when they work at all. For small files - for example, using open office to edit a file placed into one of the shared folders - it seems OK and no performance issues are evident. But for copying & pasting large files (i.e., 700MB .avi) from a local folder into one of the shares, speeds max out at around 150K/s, and transfer usually freezes around 18 or 20MB. Sometimes, it will begin again with the same slow speeds, but freeze after a period of time. Rinse, repeat.

SSH/SCP speeds seem slow to me, but in Googling around, seem about average for most people. I realize there's some encryption overhead with SSH & SCP, and that makes it a slower choice for file transfers, but what makes me wonder is that some people report speeds of 10 and 12Mb/s, while I'm averaging a consistent 1.3 or 1.4 Mb/s. I would expect speeds like that over the internet, but for two computers behind the same router on the same subnet, with no other traffic in or out of either computer? 

For NFS, I followed [these]("http://ubuntuforums.org/showthread.php?t=249889") [how]("http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html")-[tos]("http://nfs.sourceforge.net/nfs-howto/") and referred to various online sources. A typical entry in /etc/exports looks like:
```
/FILE/TO/SHARE/HOST-A    HOST-B(rw,async)
```
And a typical entry in fstab looks like:
```
HOST-B:/FOLDER/BEING/SHARED /LOCAL/MOUNTPOINT/ON/HOST-A nfs rw,rsize=32768,wsize=32768,hard,intr,nfsvers=3,tcp,noatime,nodev,async,lock
```
The entries are the same in the other computer, only with the hostnames reversed.

For SSH, I followed the instructions [here]("http://principialabs.com/beginning-ssh-on-ubuntu/"), as well as the referred-to articles for setting up rsa & dsa keys ([1]("http://www.ibm.com/developerworks/library/l-keyc.html"), [2]("http://www.ibm.com/developerworks/library/l-keyc2/"), [3]("http://www.ibm.com/developerworks/library/l-keyc3/")).

Can anyone give me any pointers on how to improve the transfer speeds between these two laptops?

---

### Post by detroit/zero on 2009-06-02
2 day bump

If I need to provide more info just say so. I'll be happy to post anything up...

---

### Post by detroit/zero on 2009-06-17
Two week+two day bump?

---

### Post by MaindotC on 2009-06-17
Prash my have some answers for you because [he did his own speed test](http://www.prash-babu.com/2009/05/nfs-vs-samba-vs-ssh-data-transfer-speed.html) to see that NFS was the fastest.  I'm not sure what's causing the crash for large files :(

---

### Post by detroit/zero on 2009-06-17
Thanks, but Prash doesn't have any answers for me. All Prash knows hot to do is copy & paste articles from everyone else and post them up so he has a blog to spam forums with.

Even the "article" you linked me to is a re-post of *someone else's* speed test, with no information and just a few re-linked screencaps.

Can anyone who is not a professional blogger tell me why all my NFS, FTP, and SSH LAN transfer speeds cap out around the same 1.3 or 1.4Mb/s?

---

### Post by MaindotC on 2009-06-17
LoL epic pwnage :p

---

### Post by detroit/zero on 2009-06-18
As a side note, I found out last night that samba transfers to the same computer cap out at like 300k/s.

---

### Post by MaindotC on 2009-06-20
Link, documentation, or word of mouth?

---

### Post by munzli on 2009-09-02
could be a cable problem but you need to provide more info...

have you tried a traceroute and checked the times? maybe you'll notice package loss while pinging? use ethtool or something to check and see with what speed your network is running... etc.

---

### Post by detroit/zero on 2009-09-02
I have good signal strength and ping times hold anywhere between 1 and 30ms, probably depending on what time of day it is and how many other networks are active on our channel, who is in what apartment using a microwave oven, etc..

Right now, it's running quite good. The signal is strong, there's low interference, and ping times are short as can be with no packet loss:```
zero@zero-laptop:~$ ping -c 5 192.168.1.100
PING 192.168.1.100 (192.168.1.100) 56(84) bytes of data.
64 bytes from 192.168.1.100: icmp_seq=1 ttl=64 time=7.57 ms
64 bytes from 192.168.1.100: icmp_seq=2 ttl=64 time=1.21 ms
64 bytes from 192.168.1.100: icmp_seq=3 ttl=64 time=1.25 ms
64 bytes from 192.168.1.100: icmp_seq=4 ttl=64 time=1.23 ms
64 bytes from 192.168.1.100: icmp_seq=5 ttl=64 time=1.74 ms

--- 192.168.1.100 ping statistics ---
[COLOR=Blue]5 packets transmitted, 5 received, 0% packet loss, time 4005ms
rtt min/avg/max/mdev = 1.212/2.601/7.570/2.492 ms[/COLOR]
zero@zero-laptop:~$ ping -c 5 192.168.1.100
PING 192.168.1.100 (192.168.1.100) 56(84) bytes of data.
64 bytes from 192.168.1.100: icmp_seq=1 ttl=64 time=1.25 ms
64 bytes from 192.168.1.100: icmp_seq=2 ttl=64 time=4.74 ms
64 bytes from 192.168.1.100: icmp_seq=3 ttl=64 time=1.45 ms
64 bytes from 192.168.1.100: icmp_seq=4 ttl=64 time=1.67 ms
64 bytes from 192.168.1.100: icmp_seq=5 ttl=64 time=1.20 ms

--- 192.168.1.100 ping statistics ---
[COLOR=Blue]5 packets transmitted, 5 received, 0% packet loss, time 4006ms
rtt min/avg/max/mdev = 1.207/2.066/4.747/1.351 ms[/COLOR]
zero@zero-laptop:~$ ping -c 5 192.168.1.100
PING 192.168.1.100 (192.168.1.100) 56(84) bytes of data.
64 bytes from 192.168.1.100: icmp_seq=1 ttl=64 time=2.01 ms
64 bytes from 192.168.1.100: icmp_seq=2 ttl=64 time=1.22 ms
64 bytes from 192.168.1.100: icmp_seq=3 ttl=64 time=1.25 ms
64 bytes from 192.168.1.100: icmp_seq=4 ttl=64 time=3.99 ms
64 bytes from 192.168.1.100: icmp_seq=5 ttl=64 time=1.32 ms

--- 192.168.1.100 ping statistics ---
[COLOR=Blue]5 packets transmitted, 5 received, 0% packet loss, time 4005ms
rtt min/avg/max/mdev = 1.220/1.961/3.998/1.059 ms[/COLOR]
```

---

### Post by detroit/zero on 2009-10-09
I'm going to bump my OP here. It's been a few months and no amount of tinkering with anything will change these speeds.

1.2Mb/s for a cap on wireless LAN transfer is ridiculous.

---

### Post by Jive Turkey on 2010-04-15
7 month bump I'm having a similar problem.

---

### Post by detroit/zero on 2010-04-15
> **Jive Turkey said:**
> 7 month bump I'm having a similar problem.
Yeah, you're not going to find help.

That's because about 1.3M/s is the speed limit on a secured WPA wifi connection, because of the encryption overhead.

If you go with unsecured WEP, you'll probably hit 2M/s or so, but those are the limitations of current wireless technology. At home, use a wired connection and you'll go as fast as your router (or probably ISP) will support.

Them's the breaks.

---

### Post by MaindotC on 2010-04-17
Or 802.11n!

---

