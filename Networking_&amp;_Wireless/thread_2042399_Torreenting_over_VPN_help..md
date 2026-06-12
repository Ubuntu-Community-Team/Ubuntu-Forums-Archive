---
title: "Torreenting over VPN help."
date: 2012-08-14
forum: Networking &amp; Wireless
---

### Post by JOBAfunky on 2012-08-14
My problem was that after updating in Distro 11 my ability to torrent through my VPN broke. Instead of trying to troubleshoot this I'd just like to start from scratch. 
     I'm updated to distro 12 now and would like advice on setting up a torrent client to run through a VPN. I am open to any client, I was using Transmission before, and I'm open to new VPN service providers(used VPNUK) My router is running Gargoyle but I'd consider dd-wrt or even factory firmware. My only requirements are that I am connectable, and that I can force all traffic through the vpn such that if my vpn goes down the system is off WAN.

***EDIT*** after the third time trying to talk with my vpn provider tech I found out that they had p2p traffic accidentally blocked. Customer support did so poorly handling this that I am dropping the service(VPNUK) so does anybody have any good Ubuntu/torrent friendly VPN Provider recommendations?

---

### Post by steviematt on 2012-08-19
There are a few specialist ones but rather than advertise I will point you to an article covering the subject: [http://torrentfreak.com/which-vpn-providers-really-take-anonymity-seriously-111007/](http://torrentfreak.com/which-vpn-providers-really-take-anonymity-seriously-111007/)

I use my VPN mainly for unblocking websites while working in China. However I do sometimes like to download things and avoid the sneaky throttling from my isp while back in the UK.

It's important to know that some VPN companies log all of your activity, so the above link seems to be a good guide separating the good guys from the bad guys... I mean you do want your Viirtual Private Network to be somewhat private afterall;)

If you want the VPN provider I use, just PM me. At first I had trouble setting the OpenVPN up through the OpenVPN package but they provided me with a shell script installer that installed their own client and it couldn't have been more straight forward. PPTP was a doddle to set up too.

---

### Post by Kirk Schnable on 2012-08-19
I have a VPN I use for personal use (not for torrenting) which I run on a dedicated server from OVH.  Their Kimsufi line of servers is very cost effective and provides tons of bandwidth.  [www.kimsufi.ie](www.kimsufi.ie)

I am not sure what their network management policies think about torrenting, though. 

Kirk

---

