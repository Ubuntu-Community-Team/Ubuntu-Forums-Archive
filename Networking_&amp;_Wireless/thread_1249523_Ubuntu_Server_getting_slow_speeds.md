---
title: "Ubuntu Server getting slow speeds"
date: 2009-08-25
forum: Networking &amp; Wireless
---

### Post by m0ngr31 on 2009-08-25
For some reason I am getting really slow speeds from my Apache web server running on Ubuntu Server 9.04.
 
It is connected to the network through a Netgear WG602 Access Point converted into a bridge via DD-WRT. It recieves wireless from my Linksys WRT54gs router, also running DD-WRT. It is getting good signal strength (about 75%), and niether side has reported any signal or packet loss.
 
But when I try to upload something to my samba share on the server, my max speed is about 64k and my FTP transfer speed is even worse.
 
When you try to pull up one of my hosted sites it is extremely slow too. (Probably caused by my ISP's slow uplink speed though)
 
I can't figure out what the problem might be. I don't have iptables or anything else setup yet, so no firewall issues.
 
Could it be a problem with IPv6? For some reason it looks like they compiled it into the kernel this build and it can't be turned off through the blasklist file anymore. Other than that, I'm not sure what the problem could be.
 
Any guesses?
 
**ps: before I stuck the AP there to be a bridge, I was using a USB wireless card and it seemed to work ok. There wasn't any speed issues if I remember correctly. It would drop the connection alot though because I think my old server didn't like usb that much.

---

### Post by m0ngr31 on 2009-08-25
As a side note, I have my xbox plugged into a netgear ap (same model) that has the exact same configuration as the one plugged into my server. And I am able to play on live, stream videos over the network and have not had any problems with that at all.

Thanks

---

