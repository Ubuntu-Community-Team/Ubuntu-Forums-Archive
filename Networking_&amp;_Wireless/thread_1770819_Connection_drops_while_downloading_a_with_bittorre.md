---
title: "Connection drops while downloading a with bittorrent client"
date: 2011-05-29
forum: Networking &amp; Wireless
---

### Post by dusdus on 2011-05-29
I tried Ubuntu, Kubuntu and now Xubuntu, all 11.04. I've also tried Deluge, Transmission and Ktorrent.
With 10.10 everything worked fine (all variants). Also, in Windows 7 it's working fine.

But now it drives me crazy.
As soon as I start a torrent, the download starts but after 30 seconds or so the download drops to a zero. Also, I'm not able to browse anymore. The networkmanager tells me I still have a connection.

Some say it has something to do with the number of peers the client connects to, or it's my router. 
My router isn't the problem, as it's working fine with 10.10 and windows.
So maybe it's the number of peers right?

Question. Why can I connect with over 200 peers at the same time while I'm using 10.10 or windows, but can't do it with 11.04?

Better put, what should I do to get this working fine again? Going back to 10.10?

---

### Post by Giggity on 2011-08-01
I can verify the same problem, exclusive to 11.04.  I'll go check launchpad for a report.  *Aside: Wow, I've been using Ubuntu for 5 years as of today!

---

### Post by Giggity on 2011-08-08
I found a workaround that fixed the problem on my end.

It seems that something is wrong with the network-manager package, as this happens only when using that to manage my wifi connection.  Installing the WICD network manager fixed the problem:

```
sudo apt-get install wicd
sudo apt-get remove network-manager
```I set up my connection using this utility and now it runs screaming fast without a problem.

I'll search launchpad for a report regarding this, and if I can't find one I'll post one.

---

### Post by hike on 2011-08-21
got it solved with wicd

---

