---
title: "Jaunty fails to network &quot;multitask&quot;"
date: 2009-05-13
forum: Networking &amp; Wireless
---

### Post by tionfyre on 2009-05-13
Sorry if this issue's already been answered, there was too much saturation in searching "jaunty, ubuntu, network, internet, issues, etc."

I'm running a clean install on a DELL E1505/6400 with the intel centrino duo/intel wireless card and I access my internet via wireless.

Everythings running relatively well except I can't browse the web whenever I use Azureus/deluge/transmission. Firefox simply hangs (not crash) when it tries to load a site before citing an inability to connect.

The problem seems to be the same when I do file transfers in pidgin.

I've tried both xubuntu and ubuntu clean installs and the problem was prevelant throughout.

Has anyone else had this problem and more importantly, has anyone found a solution to it?

Thanks for reading :-)

---

### Post by Peter09 on 2009-05-13
Can you post the output of

```
route
```

---

### Post by tionfyre on 2009-05-13
Here it is:

> Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     2      0        0 wlan0
link-local      *               255.255.0.0     U     1000   0        0 wlan0
default         192.168.1.1     0.0.0.0         UG    0      0        0 wlan0


---

### Post by Peter09 on 2009-05-13
Just read your initial post again - realize that you mean that downloading a torrent overwhelms your network.

Can you not rate limit the download in the application, see if that works.

Note that some ISP actually limit your bandwidth when you download a torrent.

---

### Post by tionfyre on 2009-05-13
Things are working. Throttled download and peers.

I'm at an absolute loss, I've never had to do that with any previous releases. And it was downloading at 9x slower speeds before modification of downloads&peers. What the...

Now to check pidgin.

... that works too.

WHAT IN THE WORLD?!?!

Anyways, thanks so much Peter09 :) 

Cheers

---

