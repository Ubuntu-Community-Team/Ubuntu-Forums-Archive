---
title: "Samba (file sharing to Windows computers) and transfer speed"
date: 2009-11-05
forum: Networking &amp; Wireless
---

### Post by altonbr on 2009-11-05
I have a local network using a wired/802.11g router with my Ubuntu desktop setup to share files via Samba with other computers (Windows XP and Vista laptops) connecting to it via a mapped network drive (e.g. \\computer\folder).

I have many movies I've ripped in there and want to share them on my network but the users are complaining the transfer speeds are slow (to where the movies are slightly choppy). I counted one laptop out because it was simply too old to handle the transfer speeds, nor did it have a powerful enough video card.

The others have 802.11n wireless cards, so they're fairly new and up-to-date laptops. Assuming the network is running at full speed and is not bogged down, is there any reason why the transfer speeds would be so slow? Does samba have a lot of overhead? Is there any optimizing I can do?

Secondly (but less importantly), can I see what files are being accessed (how often or had the most data transferred) to see which are the most popular?

Thank you

---

### Post by altonbr on 2009-11-05
I found a tip telling me to add this to my /etc/samba/smb.conf file, but even after restarting the samba daemon, the transfers are still too slow to stream a movie.

```
socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
```Is it because the router is 802.11g? I mean, my computer has a 100Mbps wired-interface, so the only thing I can think of is that the wireless speeds are too slow, or it's Samba struggling to talk to Windows. I assume the prior at the moment.

Some starting documentation: [http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/speed.html](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/speed.html)

---

