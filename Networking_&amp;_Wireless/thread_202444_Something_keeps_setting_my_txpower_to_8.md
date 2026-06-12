---
title: "Something keeps setting my txpower to 8"
date: 2006-06-23
forum: Networking &amp; Wireless
---

### Post by supermihi on 2006-06-23
Hi,

I still have massive problems with the wireless connection on my machine. I am using (self-compiled) madwifi-ng drivers, which usually work fine. But for some reason the connection drops after a few minutes and doesn't come back.
I now found that everytime I noticed that the connection was down and I ran iwconfig to see what's happening, the txpower was set to 8. If I then manually set it to something higher (e.g. 15), it starts working again. However, a few minutes later it's 8 again and the connection is down.
This is really annoying and I didn't find out which script or program does this yet. It can't be the ifupdown service, since it also happens if I ifdown the interface and then manually set the iwconfig parameters.

---

### Post by supermihi on 2006-06-25
*bump* what could this be???

---

