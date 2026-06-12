---
title: "Very very slow internet connection"
date: 2010-05-04
forum: Networking &amp; Wireless
---

### Post by rupsie on 2010-05-04
Hi, guys. I've been experiencing problems with my internet connection since I installed Ubuntu 10.04 beta on my laptop. It's painfully slow. I'm a newbie and I have no idea what to do. I read other topics on the same subject and what I did was iwconfig rate 54M (I really don't know what it does) and disabling ipv6 in firefox. Unfortunately these doesn't work for me. I have a Windows 7 machine and have no problems with it, the internet speed is as expected. Please help me, I like Ubuntu and don't want to change back to Windows just because of the internet but right now simple things like downloading a file or streaming video is a nightmare.

P.S. I forgot to say that the problem concerns the wireless connection, I've never tried plugging a cable in my laptop.

---

### Post by Iowan on 2010-05-04
[Here]("https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4") is a help page - much of which you may have already tried...

---

### Post by rupsie on 2010-05-05
Well, it's an article about disabling ipv6 but in my case lsmod doesn't show that ipv6 is active. So, this doesn't help... :( If I installed an older version of Ubuntu would the internet be ok? I've read in the forums that only people with 10.04 have this kind of problem. Is that so?

---

### Post by Iowan on 2010-05-05
Slow internet connection is not unique to 10.04...
[Here]("http://ubuntuforums.org/showthread.php?t=1468494") is another thread to check.

---

### Post by com.cr33p on 2010-05-06
I have the same problem!
I also disabled IPV6 in Firefox and systemwide, but that didn't help.

Until now I found no solution for this, can anyone help?

---

### Post by PeterG&gt; on 2010-05-06
You say you tried **iwconfig rate 54M** and it did not work...


the correct command should be:

**sudo iwconfig wlan0 rate 54M**


to figure out what it does type

*man iwconfig*

---

### Post by rupsie on 2010-05-08
Well, I did iwconfig wlan0 rate 54M and I think the internet is a bit faster now but definitely slower than Windows.. Torrent downloading is also extremely slow, I download a certain torrent in Windows with 2.5MB/s in Windows and 50KB/s in Ubuntu... :(

---

### Post by rupsie on 2010-05-15
I just wanted to say 10x to everyone for your help but what really fixed my problem was the last update of Ubuntu so now everything is working fine.

---

### Post by JohnDoe365 on 2010-05-19
The forum is full of complaints about WiFi speed, and it's not hardware related, at least not to a single chipset. As it seems to me it is a WiFi subsystem or even kernel regression.

Try the following:

When speed is slow: disable WiFi
re-enable WiFi and wait for re-association with AP. Is speed back to normal?

Also see [http://ubuntuforums.org/showthread.php?t=1473022&page=3](http://ubuntuforums.org/showthread.php?t=1473022&page=3) and [http://ubuntuforums.org/showthread.php?t=1487039](http://ubuntuforums.org/showthread.php?t=1487039)

If it has helped, it won't last for long, speed drops back to painful slow after some time.
Consider assigning yourself to
[https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/581936](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/581936) 
to raise awareness.

---

### Post by JohnDoe365 on 2010-05-19
The forum is full of complaints about WiFi speed, and it's not hardware  related, at least not to a single chipset. As it seems to me it is a  WiFi subsystem or even kernel regression.

Try the following:

When speed is slow: disable WiFi
re-enable WiFi and wait for re-association with AP. Is speed back to  normal?

Also see [http://ubuntuforums.org/showthread.php?t=1473022&page=3](http://ubuntuforums.org/showthread.php?t=1473022&page=3) and  [http://ubuntuforums.org/showthread.php?t=1487039](http://ubuntuforums.org/showthread.php?t=1487039)

If it has helped, it won't last for long, speed drops back to painful  slow after some time.
Consider assigning yourself to
[https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/581936](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/581936) 
to raise awareness.

---

### Post by JohnDoe365 on 2010-05-19
The forum is full of complaints about WiFi speed, and it's not hardware  related, at least not to a single chipset. As it seems to me it is a  WiFi subsystem or even kernel regression.

Try the following:

When speed is slow: disable WiFi
re-enable WiFi and wait for re-association with AP. Is speed back to  normal?

Also see [http://ubuntuforums.org/showthread.php?t=1473022&page=3](http://ubuntuforums.org/showthread.php?t=1473022&page=3) and  [http://ubuntuforums.org/showthread.php?t=1487039](http://ubuntuforums.org/showthread.php?t=1487039)

If it has helped, it won't last for long, speed drops back to painful  slow after some time.
Consider assigning yourself to
[https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/581936](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/581936) 
to raise awareness.

---

