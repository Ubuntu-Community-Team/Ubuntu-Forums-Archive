---
title: "DNS problem?"
date: 2006-07-14
forum: Networking &amp; Wireless
---

### Post by dakaling on 2006-07-14
Let me start off at saying that I'm a complete n00b to linux. That being said, I just installed Ubuntu 6.06 on my laptop and after a little tinkering I got my wireless card (Linksys WPC54GS) to work at home.

     I brought my laptop to work (a hotel) where we have wireless access, and suprise it didn't work. There is no encryption, its a completely open network. I was able to ping just fine, but when I would type an address into the browser nothing would work. After tinkering with it I found out I if I used a numerical adrress (ex. 64.233.179.99 for google) it would work. The windoze machine in the lobby is working fine though. 

     Anyone have any ideas as to what may be the problem?

---

### Post by Soarer on 2006-07-14
It certainly sounds like DNS.

If you go to System>Administration>Networking & select your interface, there is a DNS tab. You may need to enter in there the DNS server in use at your work.

I've noticed that Windows sometimes can extract this information in configurations that Ubuntu can't. They probably set up the DHCP server (which provides the DNS informtion) for Windows systems.

---

### Post by tturrisi on 2006-07-14
It is also possible that both lans use the same ssid, e.g. common ssid like "linksys" or "netgear".  If have linksys at home and linksys at work, then ubuntu will not realize they are 2 different wlans & try to use the dns servers from home at work.

---

