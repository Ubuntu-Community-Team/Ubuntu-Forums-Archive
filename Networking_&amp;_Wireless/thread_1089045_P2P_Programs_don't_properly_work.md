---
title: "P2P Programs don't properly work"
date: 2009-03-06
forum: Networking &amp; Wireless
---

### Post by Kalma on 2009-03-06
I use Ubuntu 8.10 with GNOME. I have installed an USB WiFi adapter using ndiswrapper. The connection works fine when surfing the web and downloading files. Nevertheless, when trying to use a P2P program I find some problems:

- amule program simply disappears after a couple of hours without leaving any error message (checked with dmesg)
- mldonkey (with mldonkey-gui and also the web interface on port :4080) is able to stay a little bit more, even getting a very good download rate (around 200 Kb/s in total) but finally it slows down and loses all connections. I have reduced the max_opened_connections to 200, and the max_indirect_connections to 150, but I had the same result.

The only way to solve it is to reset the WiFi connection and the mldonkey server. I believe (I'm not sure) it may be a Network problem. Any suggestion? Is there any way to check and configure the Network parameters of a driver installed with ndiswrapper? Anybody had the same problem?

---

