---
title: "Superb bit torrent client"
date: 2009-01-26
forum: Multimedia Software
---

### Post by cannon_dt on 2009-01-26
Hi all,
Heres me just sharing a wonderful experience

I was a user of Bit Tornado while I was in windows. So I hunted these forums and got it running. However, some of the torrent sits that I use have the regular ratio restrictions. What this means is that we would have to seed the torrents once we fully get them down. Now BitTornado on an average uses at least 3-4 % of processor times. Now if I seed 10 torrents and leech another 5, my processor is totally being burnt. Now my machine configuration is inferior - intel M processor with 512 MB RAM only. And that is when I stumbled upon an extremely low-processor-intensive torrent client - rTorrent. 

This runs via comand line but believe me it is a breeze to operate. At this moment I am seeding 20 torrents and downloading five and this is what I get when I grep rTorrent with top
	PID   PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND 
	21458 20  0 59452  49m 6532  S 0.3  10.5   2:39.74 rtorrent 

If you see it is just taking .3%, now thats awesome. So all you folks who are torrent users and are in need of a great client, look no further.

A beautiful guide for setting this up (which is a breeze in itself) is at
[http://polishlinux.org/apps/p2p/rtorrent-console-p2p/](http://polishlinux.org/apps/p2p/rtorrent-console-p2p/)

And the official guides/wiki etc is at [http://libtorrent.rakshasa.no](http://libtorrent.rakshasa.no)

Have fun and hope some one finds this useful

---

