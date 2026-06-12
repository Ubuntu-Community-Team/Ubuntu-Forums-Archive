---
title: "BitTorrent Kills Networking"
date: 2009-11-23
forum: Networking &amp; Wireless
---

### Post by Mazinger-Z on 2009-11-23
Whenever I BitTorrent, no matter what client, it eventually does something that makes my network services on my Ubuntu box dead.  I have had this issue for a couple of revisions in Ubuntu, starting since Feisty.  This issue also persists no matter what client I am using (Transmission, TorrentFlux/BitTornado, Vuze, etc)...

I know my ISP is killing my outgoing connection's speed at some point, but that is not my specific problem. Eventually the networking becomes laggy, in that just doing basic ssh is slow as tar.  When I kick the networking services, everything picks up speed again, but all my networked drives and everything doing any network operations crashes and burns (torrent client will pick back up, but breaks on putting the files onto my file server).

I'm at a loss as to where to begin to diagnose this problem.  I have tried different clients, torrenting locally, etc... No amount of help there.  What could cause the networking stuff to lag and eventually die, while my other networked machines and outbound connection are fine.

---

### Post by doas777 on 2009-11-23
the problem is probably a glut of half formed connections that are not getting flushed quickly enough. do you use an IP filter list like IPlist or moblock? they could be the cause or the solution, depending.

first off, are you behind a router? are you sure that it is your box misbehaving and not the router? (eg, can you surf from another box, while your torrenting one is swamped?)

also are you throttling your upstream? if not, back it down to something like 20kB/s per 512kbps of upstream carrier. I have 768kbps upstream, so i throttle my torrent client to 30-35kB/s (b = bit. B = Byte).

also you mentioned your fileserver. are you downloading through your torrent host, and saving the data to a fileshare on the fly? if so you may have your network traffic for that one node tripping all over itself.

---

### Post by Mazinger-Z on 2009-11-23
> **doas777 said:**
> the problem is probably a glut of half formed connections that are not getting flushed quickly enough. do you use an IP filter list like IPlist or moblock? they could be the cause or the solution, depending.

first off, are you behind a router? are you sure that it is your box misbehaving and not the router? (eg, can you surf from another box, while your torrenting one is swamped?)

also are you throttling your upstream? if not, back it down to something like 20kB/s per 512kbps of upstream carrier. I have 768kbps upstream, so i throttle my torrent client to 30-35kB/s (b = bit. B = Byte).

also you mentioned your fileserver. are you downloading through your torrent host, and saving the data to a fileshare on the fly? if so you may have your network traffic for that one node tripping all over itself.

IIRC, I've had this issue when I've been saving items locally as well as remotely, in response to that last part.  I can reconfigure and give it another go tonight.

I can surf out when I'm torrenting, unless I'm getting throttled by Comcast.  When the Networking services lag out (the torrent box itself is not laggy, but anything dealing with the networking is) Comcast eventually de-throttles and I surf fine while the box is floundering.

I throttle 10 kB/s going up.

I do not use IPlist or moblock.

---

### Post by doas777 on 2009-11-23
hmmm. it may well all be your ISP. or you may be getting a syn flood ([http://en.wikipedia.org/wiki/SYN_flood](http://en.wikipedia.org/wiki/SYN_flood)) either maliciously or not. 
i would set up some form of blocklist, just to get the obvious spys and the bad data feeders. some clients will run a block list all by themselves (vuze for instance).

---

### Post by Mazinger-Z on 2009-11-23
I'd think my network was not so old as to be susceptible to SYN attacks.

I haven't had this issue on Windows, but I need my windows machine for gaming.

---

