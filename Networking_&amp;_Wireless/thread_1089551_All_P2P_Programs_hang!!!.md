---
title: "All P2P Programs hang!!!"
date: 2009-03-07
forum: Networking &amp; Wireless
---

### Post by Kalma on 2009-03-07
I do really need help on this or I will have to go back to Windows :-(

I use Ubuntu 8.10 with GNOME. I have installed an USB WiFi adapter using ndiswrapper. The connection works fine when surfing the web and downloading files. Nevertheless, when trying to use a P2P program I find some problems:

- amule program simply disappears after a couple of hours without leaving any error message (checked with dmesg)
- mldonkey (with mldonkey-gui and also the web interface on port :4080) is able to stay a little bit more, even getting a very good download rate (around 200 Kb/s in total) but finally it slows down and loses all connections. I have reduced the max_opened_connections to 200, and the max_indirect_connections to 30%, but I had the same result.

The only way to solve it is to reset the WiFi connection and the mldonkey server. I believe (I'm not sure) it may be a Network Management. Any suggestion? Is there any way to check and configure the Network parameters of a driver installed with ndiswrapper? Anybody had the same problem?

---

### Post by ugm6hr on 2009-03-07
I have never heard of those apps.

Transmission is very stable - how does that behave?

---

### Post by Kalma on 2009-03-07
The connection seems not to have any problem, After some hours, it seems something happens to the connections, though the wifi icon is present at the top right and the pop-up says "connected. Nevertheless, mldonkey is not able to connect to any server nor download or upload anything. Once this point is reached, navigation is also impossible.

---

### Post by ugm6hr on 2009-03-07
Is it the p2p app that fails, or is it the network connection (for all apps inc Firefox)?  Can you still ping the router at that stage?

Does the same happen if you leave the computer connected without p2p?

---

### Post by Kalma on 2009-03-07
It also happens to Firefox. Sorry, I didn't try to ping the router... I will next time. Anyway, this is something which only happens when a P2P is running. It seems to me like a sort of saturation, it is as if the Network couldn't properly manage the volume of data or connections needed for P2P... Though this is just a feeling. Once it is hung, can I diagnose it using any tool or similar so I can give you more information?

---

### Post by Kalma on 2009-03-07
One more clue: the router and the Internet connection are right when the connection of this PC is hung. I can access the Internet from other PCs I have at home (including a Mini-Dell with Ubuntu). So, the problem is restrained to this PC exclusively (and maybe because of the P2P programs, because it is the only one having those).

---

### Post by Kalma on 2009-03-16
Though my thread didn't seem to be very popular, I will leave here what I found in case somebody else suffers the same problem...

After lots of tests, lots of searches on the web and lots of apps installed, I have found out that the problem was the Adapter driver  (Window$ driver thru ndiswrapper) of the Thomson WLG-1500A USB WiFi Adapter. I have bought a new USB adapter and it's working fine.

---

