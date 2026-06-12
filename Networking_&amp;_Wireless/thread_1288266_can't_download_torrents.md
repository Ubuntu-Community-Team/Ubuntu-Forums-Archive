---
title: "can't download torrents"
date: 2009-10-11
forum: Networking &amp; Wireless
---

### Post by joudax on 2009-10-11
Hi
 
I've tried utorrent(wine), transmission , KTorrent ... but nothing seems to work , did a little googling and forwarded some ports but nothing changed, i have no problem downloading in windows so it's not ISP related , what do i do ?

---

### Post by lian1238 on 2009-10-11
Install a firewall (to open some ports), like firestarter.

Then configure your router, torrent client, and firewall accordingly with the same port ranges.

You've already forwarded the ports, so you need to configure your torrent client to use those ports, and open those ports in your firewall.

---

### Post by joudax on 2009-10-11
Thanx Lian

I did all that and double checked to make sure that ports i'm using r open and they are, but still nothing ' I'm out of ideas and tired of searching for now though i was hoping to break my last link to windows,anyway if anyone can help me with this i would really appreciate it else i'll post here if i found the solution

---

### Post by tuxxy on 2009-10-11
Are we talking about slow speeds or do they not even start to download? you could try deluge and also it shouldn't be necessary to configure your iptables to use torrents

```
sudo apt-get install deluge
```

---

### Post by brookie on 2009-10-11
Kudos for Deluge. 

Install it from synapitc, and even add a repo from their site to your sw sources to get the latest version. 

[http://dev.deluge-torrent.org/wiki/Faq#DoesDelugehaveitsownrepository](http://dev.deluge-torrent.org/wiki/Faq#DoesDelugehaveitsownrepository)

Also, this thread will walk you through almost any setting. 

[http://ubuntuforums.org/showthread.php?t=1259923](http://ubuntuforums.org/showthread.php?t=1259923) 

Cheers,
Brook

---

