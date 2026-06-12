---
title: "Traffic Shaping + torrent + web navigation + ps3"
date: 2009-06-09
forum: Networking &amp; Wireless
---

### Post by Pinteiro on 2009-06-09
Hi,

I've assembled a spare computer as a router for my home lan, it's conected to the internet via a 1mpbs up/ 300 kbps down adsl link (ppp0) and it's conected to the lan via a ethernet card (eth2).

I've got NAT, dhcp and upnp working just fine. 

The router box also has torrentflux instaled. Problem is that when the torrent are running full speed (in my conection, at about 100kBps download) It's daunting to surf on the net or play on-line (obviouly, as the conection is in full use by the torrent).

I've tried wondeshaper and it got slightly better (now remote ssh is usable), but it concentrates too much in the egress queue (the upload) and almost doesn't touch the download queue.

What I really want is to have the torrent running at full speed and, when there are connections made for web surfing or ps3 gaming to, have the torrent automatically slowed to a fraction of the total bandwidth. Is it possible?

---

### Post by puppywhacker on 2009-06-09
the reason traffic shaping is focusing on the egress is because you control that part, you can not control the incoming side. The download speed for web surfing is affected since the queue size towards you will increase and on the uplink your ack's aren't sent back quickly enough. I'm using the latest transmissionbt which can ratelimit the incoming and the outgoing connections. So you can request less download from the peers making your internet connection fully usable.

---

### Post by Pinteiro on 2009-06-09
I know I can't control what people are sending me, but, because of the way tcp/ip works, ifI stard droping packets the senders will slow down transmission. So the idea is: if there is a conection at port 80 or one from the ps3 console, stard dropping packets coming for the torrent automatically, so the senders start sending them slower, increasing the download bandwidth avaiable for web surfing and the ps3.

The rest of the time (ie, when there is no conections to port 80 or conections from the ps3) I want the torrent to use all the avaiable bandwidth (automatically).

Is that possible?

---

### Post by mr.propre on 2009-06-09
Using iptables you can configure QOS, but it's not easy and there is a limited documentation.

After googlen for QOS + ubuntu, i foudn this thread:
[http://ubuntuforums.org/showthread.php?t=927705](http://ubuntuforums.org/showthread.php?t=927705)

With a link to mastershaper:
[http://www.mastershaper.org/index.php/Main_Page](http://www.mastershaper.org/index.php/Main_Page)

EDIT: with QOS you can give some ip, programs or protocols an higher priority. So in your Case you PS3 needs an higher priority then your torrent client.

---

### Post by Pinteiro on 2009-06-09
Answering to my own question. There´s no way to do what I want (shaping inbound traffic, that is) with the stock kernel, as the ingress qdisc just supports trafic limits but no classication.

To do that one needs to patch the kernel with the imq patch.

---

