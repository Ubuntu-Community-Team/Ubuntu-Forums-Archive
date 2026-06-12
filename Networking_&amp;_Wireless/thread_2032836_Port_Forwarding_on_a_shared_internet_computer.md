---
title: "Port Forwarding on a shared internet computer"
date: 2012-07-24
forum: Networking &amp; Wireless
---

### Post by laserman on 2012-07-24
My satellite internet failed so I took a box with Ubuntu 10.04 and connected my USB Broadband card, accessed connections and shared ETH0 where I had a router connected. In order to recognize the broadband stick every time the computer was booted, I had to add usb-modeswitch which corrected the issue. Accessing the internet from this box or any wireless device connecting to the router has never been an issue. 

I have a program that I utilize with amateur radio that requires port forwarding inbound/outbound UDP 5198 and 5199 but have not been successful since switching over to my "alternative" internet connection. The box sharing the internet on eth0 has a gateway ip of 10.42.43.1

I'm pretty sure this can happen, just not sure of what needs to transpire to make it happen. I look forward to any comments.

laserman

:confused:

---

### Post by Kirk Schnable on 2012-07-29
A lot of cellular networks don't give you a public IP, they use a private IP and do some NAT on their end.  I've noticed AT&T doing this with my iPad connection.

If this is the case (which your 10.x.x.x IP sugests, as that's a private IP range) you probably can't do it.

Kirk

---

### Post by laserman on 2012-07-29
> **Kirk Schnable said:**
> 

If this is the case (which your 10.x.x.x IP sugests, as that's a private IP range) you probably can't do it.

Kirk

The 10.x.x.x IP is actually issued by Ubuntu through the shared port (eth0) that the broadband card is connected to. 

I have a "public IP" address that is issued by the broadband card (66.87.0.x) and that changes every time the card accesses the internet. I'm just not sure how to make that part an "invisible" through put, so to speak. Probably not the correct terminology but I don't want the shared port to be a hindered in port forwarding.

---

### Post by Kirk Schnable on 2012-07-30
> **laserman said:**
> The 10.x.x.x IP is actually issued by Ubuntu through the shared port (eth0) that the broadband card is connected to. 

I have a "public IP" address that is issued by the broadband card (66.87.0.x) and that changes every time the card accesses the internet. I'm just not sure how to make that part an "invisible" through put, so to speak. Probably not the correct terminology but I don't want the shared port to be a hindered in port forwarding.

Ah, I see. My iPad has an internal IP on AT&T's network, so I know some carriers do it that way. 

If you run a server application on the Ubuntu machine hosting the cellular card, is it open to the Internet? If so, I can definitely help you forward the port onward. Should be a simple iptables rule. 

Kirk

---

### Post by laserman on 2012-08-01
> **Kirk Schnable said:**
> Ah, I see. My iPad has an internal IP on AT&T's network, so I know some carriers do it that way. 

If you run a server application on the Ubuntu machine hosting the cellular card, is it open to the Internet? If so, I can definitely help you forward the port onward. Should be a simple iptables rule. 

Kirk

My apologies for the delay, been a busy couple of days at work, regrouping after a lightning strike.

The machine with the aircard does have access to the internet but not sure on the "server" portion. Is that a separate installation from a standard install? Definitely willing to give it a shot and as I was previously thinking, an iptables rule adjustment but I am not that versed with that but willing to learn. 

laserman

---

### Post by Kirk Schnable on 2012-12-04
I just mean try installing a server application... web server, ftp server, ssh server, etc, and see if they are accessible to the outside world on your public IP address from another computer.

A few package ideas...
apache2 (web server)
vsftpd (ftp server)
openssh-server (ssh server)

---

