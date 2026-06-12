---
title: "bittorrent get past firewall"
date: 2012-08-25
forum: Networking &amp; Wireless
---

### Post by gameguy on 2012-08-25
When I try to bittorrent things at my house, it does not work. Our modem's firewall blocks the default bittorrent port, and my parents do not want me playing around with their modem. We are using a billion bipac 7404VNOX ([http://au.billion.com/product/voip/bipac7404vnox.php](http://au.billion.com/product/voip/bipac7404vnox.php)). I would, however, assume that all billion modems have the same firewall settings by default. The firewall is set to "medium security level". Does anyone know how to get bittorrent to work on a port like port 8080, 80, 23, 1863, etc, which isn't blocked by the firewall?

---

### Post by Cheesehead on 2012-08-25
Most torrent clients have a settings window or tab to change the tracker and swarm port numbers to something that is not blocked.

---

### Post by gameguy on 2012-08-25
I tried setting it to port 80. This didn't work, however. Could it have anything to do with the fact that when I go to [here]("https://www.grc.com") then click services, shields up, it detects all my ports as stealth?

---

### Post by Laiquendi on 2012-08-25
You may have your firewall blocking bittorrent, check this. What do you mean by &quot;do not work&quot;? You do not have the green icon (or whatever) or it's completely off-line?

---

### Post by gameguy on 2012-08-25
I don't know what you mean by the green icon, but it can't download the metadata for a torrent.

---

### Post by hawkmage on 2012-08-25
I do not let torent ports in through my firewall but I have no issues using a torent client.  So I have a feeling that the firewall you are behind is identifying torent traffic and disallowing it.  

A quick look at the manual for your firewall shows an option to block Torrents so it is likely that it is reconising the torent protocol so just changing the port will probally not get arround the firewall.

---

### Post by gameguy on 2012-08-26
That sounds about right. Thanks, but as you said, sounds like I'm not getting through.

---

### Post by beboylips on 2012-08-26
Force encryption or use a VPN.

---

### Post by gameguy on 2012-08-26
Forcing encryption doesn't appear to work, but thanks anyway.

---

