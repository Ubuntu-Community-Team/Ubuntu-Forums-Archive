---
title: "Closing router ports"
date: 2011-09-23
forum: Networking &amp; Wireless
---

### Post by hyperAura on 2011-09-23
Hi, 

I have a THOMSON TG585 v7 router and I would like to know how to configure it, in order not to be able for anyone connected to the router to download torrents..
 
Thanks

---

### Post by sffvba[e0rt on 2011-09-23
*Thread moved to **Networking & Wireless**.*


404

---

### Post by CharlesA on 2011-09-23
I don't think those have a setting that can block torrents.

---

### Post by hyperAura on 2011-09-23
ok.. but is there any way do to this? maybe by installing a program on the machines that are accessing the network?

---

### Post by elliotbeken on 2011-09-23
its not easy to block bittorrent on the network as there are so many port that can and are used.

---

### Post by SparTacux on 2011-09-23
I've just read the spec on those modem/routers and it says it has a SPI Firewall included.

Some of these work from top to bottom - in that the top rule is executed first.

You could start by applying a 'bottom' level rule by blocking all outgoing connections on TCP and UDP ports ( 0-65535 ). Then open outgoing ports ( above the bottom level rule ) that you need such as NTP, DNS, POP, SMTP, HTTP, HTTPS , etc. This would block all outgoing traffic except what you allow out.  It's pretty restrictive but may be what you are looking for.

---

### Post by Dangertux on 2011-09-23
You should find the procedure for port forwarding and configuring the firewall in [this manual (PDF)]("http://www.google.com/url?sa=t&source=web&cd=1&ved=0CB0QFjAA&url=http%3A%2F%2Fwww.technicolorbroadbandpartner.com%2Fgetfile.php%3Fid%3D7099&rct=j&q=THOMSON%20TG585%20v7%20manual&ei=57t8TqHPB4aatwef7u1f&usg=AFQjCNGAmyw0UOCciGRezCfEcDhGW9kcVg&sig2=tSdrZiDlvdqhuqQp6Ljk8g&cad=rja")

Also, Stateful Packet Inspection just means that the firewall just makes sure incoming tcp packets conform to a proper 3 way handshake. The device could still only open ports based on UPnP (some really cheap ones do this)

---

### Post by hyperAura on 2011-09-24
thanks people.. i have added a new level of security of firewall on the router and now i am setting restrictions.. thanks again..

---

