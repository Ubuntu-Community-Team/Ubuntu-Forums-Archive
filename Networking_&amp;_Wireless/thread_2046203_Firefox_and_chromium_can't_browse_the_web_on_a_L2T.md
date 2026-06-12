---
title: "Firefox and chromium can't browse the web on a L2TP vpn connection"
date: 2012-08-22
forum: Networking &amp; Wireless
---

### Post by piquezino on 2012-08-22
Hello everybody !

I'm registered to this forum for explain my problem with the L2TP protocol.

I use Ubuntu 11.10 and I have Internet by a WiFi Hotspot. But a lot of  ports are blocked. (FTP, SIP and other...). Therefore, I need to bypass  the firewall of the hotspot. I'm suscribed to hidemynet, and I started  to configure the VPN. 
I downloaded [l2tp-ipsec-vpn]("https://launchpad.net/l2tp-ipsec-vpn/")  available on launchpad (I need this software for establish the  L2TP/IPSec VPN connection). I entered the connect informations of the  ISP, it's good, i'm connected ! 
I ping google.com (Today, 50% of the  pings are lost), I have a access to Skype and apt. but when I launch  Firefox, the status of the connection is "Waiting for google.com", such  as geektionnerd.net, siteduzero.com execpt perdu.com and monip.org . 

How is this done ?

Thanks for your help and your replies.

Cordially,
[RIGHT]Alexandre
[/RIGHT]

---

### Post by piquezino on 2012-08-23
Up :)

---

### Post by piquezino on 2012-08-23
I solved the problem. It's due to the MTU. I configure it with Ifconfig. But I use my Linux desktop as router. Therefore, I must set the MTU on the Windows machines behind my router. it work very fine !

---

