---
title: "Why is Ubuntu offline (except torrents) while Windows is online?"
date: 2012-06-28
forum: Networking &amp; Wireless
---

### Post by fahimdhk on 2012-06-28
I am using a static wired connection. Everything was perfect.
  But suddenly from few hours back I can't access any website. Dropbox, Ubuntu One also can't connect.
  Ping request is also unsuccessful, **but I can download through torrent**.
  One important point is that this connection works perfectly on Windows on this same PC (My PC is dual-boot).
  I can't understand what's happening. Please anyone help me. 

I have tried with DNS 8.8.8.8, it works fine for few hours, but again I'm facing the same problem. Please help.


Thanks.

---

### Post by wirelessmonkey on 2012-06-28
If your torrents are utilizing your max bandwidth, it can cause other services like Web, UbuntuOne, DropBox, etc... to disconnect due to timeout. If you disable your torrent client, can you reconnect?

---

### Post by fahimdhk on 2012-06-28
Thanks for your reply. But I'm not trying torrent and other services like, Dropbox, Ubuntu One at a time. So, even when my full bandwidth is available I can't connect to cloud storage and also any website.

---

### Post by fahimdhk on 2012-06-29
From yesterday I'm facing this problem. Suddenly, Ubuntu gone offline, while windows is working perfectly. **I  have tried sudo sh -c 'echo nameserver 8.8.8.8 > /etc/resolv.conf',  and also changed the DNS server address to 8.8.8.8 at network manager,  but unfortunately it works only for few hours.** After that I am facing same problem again. **Important point is that previously ping 8.8.8.8 was responding, but it is not responding now.** Please help anyone so that I can solve this problem ASAP.

---

