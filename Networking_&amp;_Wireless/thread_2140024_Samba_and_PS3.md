---
title: "Samba and PS3?"
date: 2013-04-28
forum: Networking &amp; Wireless
---

### Post by kr651129 on 2013-04-28
Im looking for a solution to allow me to share media from my Ubuntu server to my PS3.  I've come accross other howto's but none of them have worked for me so far.  I'm running Ubuntu 12.10 x64.  Has anyone come accross a good solution for this?

---

### Post by SeijiSensei on 2013-04-28
PS3's use something called "DLNA" as their native streaming protocol.  There's a highly-regarded program called [ps3mediaserver]("http://www.ps3mediaserver.org/") that runs on a server and converts video files on-the-fly then sends them to the PS3 with DLNA.  There's a document on using this program on Ubuntu [here](https://help.ubuntu.com/community/Ps3MediaServer).

I'm running 13.04 and just downloaded ps3mediaserver and its associated dependencies from its PPA repository using these commands:
```
sudo add-apt-repository ppa:happy-neko/ps3mediaserver
sudo apt-get update
sudo apt-get install ps3mediaserver
```

---

### Post by kr651129 on 2013-04-28
Thanks for the info!  I installed it and everything seems to be running fine on the machine but PS3 isn't seeing any media servers.  Any thoughts on what might be going on?

---

