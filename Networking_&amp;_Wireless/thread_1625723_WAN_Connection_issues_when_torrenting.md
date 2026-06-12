---
title: "WAN Connection issues when torrenting"
date: 2010-11-19
forum: Networking &amp; Wireless
---

### Post by InkyDinky on 2010-11-19
I have a box setup to do some torrent downloading. I've seen that box achieve over 1MB/s traffic. However, when torrenting at rates above 80-100kB/s my roommates Windows 7 box can't seem to connect to the 'net at all. Sometimes I also have problems with my Ubuntu 10.04 boxes with Firefox timing out. Also, smart net enabled devices such as the Tv and Bluray player that can do Pandora and Netflix can't connect under these traffic conditions.
I realize that the easiest solution is to just pause or BW limit the torrent. However, for some torrents, peak 'net usage time is the only time I connect to any peers.
However, my question is why can the network sustain the 1MB/s traffic yet not let multiple people surf the web?
Are the Tx packets not getting out?
Are the Rx packets not getting in (from the http requests)?
Is there a solution *besides* BW limits on the torrent.
Is there a router configuration that might alleviate or fix this problem? 
The service is Att Uverse with a 2Wire 3801HGV router.

Thanks in advance!

---

### Post by annoyingrob on 2010-11-19
Check your upload rate during those times where others can't connect. If you're saturating the upload, it can prevent other peoples requests from getting out.

---

### Post by InkyDinky on 2010-11-20
Is there a rule of thumb as to how fast an upload has to be to saturate the connection? I typically cap uploads at <100KB/s and that rate isn't often really needed.

---

### Post by annoyingrob on 2010-11-20
It all depends on your internet connection. For example, my cable connection is 8mbit down, and .75mbit up, which works out to about 1MB/sec download, and 90KB/sec upload. If I'm uploading 80+KB/sec, it doesn't matter what my download is at, it's going to cause problems for other users. If I use a torrent, I usually cap my upload around 50KB/sec to prevent problems with other users on my network.

---

