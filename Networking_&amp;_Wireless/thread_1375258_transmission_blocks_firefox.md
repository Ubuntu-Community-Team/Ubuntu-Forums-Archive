---
title: "transmission blocks firefox"
date: 2010-01-07
forum: Networking &amp; Wireless
---

### Post by hhall on 2010-01-07
Everytime I use Transmission for torrent download, even if I only have a single torrent, my firefox is unable to access the internet. I assume this cannot be a bandwidth problem, so what is it. Does anyone have any idea?

---

### Post by Dysport on 2010-01-07
Do other internet applications still work? (Skype, IM …)
Bittorrent creates a heap of connections, too much some modems or routers so they freeze. Are other computers on your network also unable to connect while you use Transmission?

---

### Post by hhall on 2010-01-08
Other programs tend to work, skype only intermittently, however. There are no other computers on the network. I also don't download lots of streams, in fact hardly ever more than 2 or 3.

---

### Post by Dysport on 2010-01-09
Even if you download only one torrent, transmission opens a lot of connections to all the peers you are seeding to or leeching from. From your description I would say that the problem isn't Ubuntu but more probably your modem and/or router which struggles with that many connections. 
Sometimes turning off the firewall or any other services that track or save each connection can help, plus I highly recommend to forward the port you set in transmission to your machine.
If nothing helps you may consider buying a new modem/router or use transmission only by night or while you're away.

---

### Post by hhall on 2010-01-09
That would make sense, I gather. How do I find out the port?

---

### Post by Dysport on 2010-01-09
You can set any port number you want in the transmission settings, I would recommend setting a high port (between 40000 and 60000) though.

The NAT port forwarding procedure differs from vendor to vendor, on [this page]("http://www.portforward.com/") you can find instructions for virtually any router on the market.

---

