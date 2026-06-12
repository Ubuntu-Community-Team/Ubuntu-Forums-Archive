---
title: "Managing home network from outside"
date: 2009-04-11
forum: Networking &amp; Wireless
---

### Post by waspbr on 2009-04-11
Hello everywone, like most people I have a small wired/wireless network at home. This network is supported bt a D-Link 524 wireless router. I know that I have an IP address that comes from my ISP and other addresses from inside the network 192.168.0.* for each machine. I normally manage the computers inside the network with ssh, like ssh 192.168.0.* to access the machine's shell.

Long story short I wanted to know if anyonw knew how I could do that from outside my home network.

thanks in advance

---

### Post by totalnub on 2009-04-11
Yes, this is very possible and i do it on a regular basis.

What you need do decide is, what are you looking to do (ssh, webserver, etc.) and what computer is it on?

This means that you can setup port forwarding (the actual setup varies between router/modem manufactures) so that any requests for port 22 to your external IP get forwarded to your internal machine running ssh.

You will want to check if you have 2 dhcp servers on your network, one from the modem and one from the wireless/wired router. You can do this by going to the routers configuration page and looking for external or WAN IP and seeing if it is either 10.*.*.*, 192.168.*.* or 172.16.0.0 &#8211; 172.31.255.255. If it is any of these IPs, you will want to go into your modem's configuration and turn off DHCP

i.e. your IP = 192.168.0.7 router internal ip = 192.168.0.1, router WAN IP = 10.0.0.2, modem internal IP = 10.0.0.1, modem external ip = your actual ip [www.whatismyipaddress.com](www.whatismyipaddress.com).

I don't have alot of time to help, as i am busy for the day, but try looking at port forwarding tutorials and you should be golden. Also, look into a dynamic dns to make remembering your actual IP easy.

GL

p.s. having ssh access to a machine outside your network helps alot when testing.

---

