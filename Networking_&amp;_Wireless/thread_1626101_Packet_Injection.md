---
title: "Packet Injection?"
date: 2010-11-19
forum: Networking &amp; Wireless
---

### Post by crossing.bridges on 2010-11-19
For some reason while testing the security of my friend's wifi network I can't seem to establish a wpa 4 way handshake. Could this be a packet injection problem? The wireless card I'm using is a: 
[B][SIZE=1]Alfa AWUS036H 1000mW 1W 802.11b/g USB Wireless WiFi network Adapter with 5dBi Antenna 
[/SIZE][/B]

and I believe my card uses a rtl8187 chipset. I successfully installed the drivers for it on Ubuntu 10.04 and the card seems to work well so far, but for some reason cannot establish a wpa 4 way handshake. I've tried to do the same with various networks in our building to no avail either. Any help is greatly appreciated. Thanks in advance for any help. :D

---

### Post by eatberrys on 2010-11-19
Im assuming you can auth with other networks, wep or unprotected?

If you think it is a packet level issue, I would open wireshark or TCPdump on your wlan interface, filter for the APs IP. Then check if the correct packets are being sent.

Wiki has a good description of the four way handshake.
[http://en.wikipedia.org/wiki/IEEE_802.11i-2004](http://en.wikipedia.org/wiki/IEEE_802.11i-2004)

Hope this helps!

---

### Post by spiky001 on 2010-11-20
Hi if the card dose work for injection If you have some 1 connect to the other machine it will speed up get the arps also it can take a long time to get a handshake did you use aireplay to try speed it up have a look [here]("http://www.aircrack-ng.org/doku.php?id=cracking_wpa")

---

### Post by crossing.bridges on 2010-11-28
Hey all, sorry for the long delay in response. I've been away. To answer your question eatberrys as far as the handshake goes I receive ACKS back so the authentication process moves along as it should, but the handshake never actually takes place? I've tried to make multiple attempts (enough not to slow down his network, but enough that a handshake should have taken place) I've reviewed you're wiki doc also spikey and so far none of the techniques have worked for me? I'll try wireshark and see what's the deal. Possibly something I've overlooked. Again, thank you for all the help you guys, and anymore feedback would is definitely appreciated! Take care out there!

---

