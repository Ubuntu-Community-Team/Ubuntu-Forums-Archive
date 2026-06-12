---
title: "Server Conection problem"
date: 2010-04-05
forum: Networking &amp; Wireless
---

### Post by vipswiss on 2010-04-05
I am having a problem with unbuntu 9.10 I am new to Linux and can't figure out the problem. Everything seems to be installed and I can connect via ssh but after 10-15 minuts connection to the box dies I am running a static IP on eth0 what might be the problem ?

---

### Post by Iowan on 2010-04-05
I've seen a couple of similar threads - not necessarily SSH. 
[http://ubuntuforums.org/showthread.php?p=9077063#post9077063]("http://ubuntuforums.org/showthread.php?p=9077063#post9077063")
[http://ubuntuforums.org/showthread.php?t=1397722]("http://ubuntuforums.org/showthread.php?t=1397722")

---

### Post by vipswiss on 2010-04-06
When i boot up with keyboard and monitor everything seems to be working fine but when I remove monitor and keyboard and boot up then 5 min later the connection is dead how can I fix this

---

### Post by vipswiss on 2010-04-06
The problem only persist when remove monitor and keybord and reboot. If I boot up with keyboard and monitor log in to account and then remove them everything seems to work any suggestions please help .

---

### Post by Iowan on 2010-04-06
Kinda looks like a bug, since the symptoms have shown up in a couple of threads. I'll search [https://bugs.launchpad.net/]("https://bugs.launchpad.net/") to see if anything similar has been reported. (or you could - and/or submit one yourself)

Not identical, but [this]("https://bugs.launchpad.net/ubuntu/+source/sshfs-fuse/+bug/554749") bug involves SSH and headless server.

---

