---
title: "Properly set up internal VPN ports"
date: 2010-02-08
forum: Networking &amp; Wireless
---

### Post by wesg on 2010-02-08
My Ubuntu server is running VPN software and I can connect to it properly, but right now it isn't very useful. I can connect with SSH using my local IP, but that's about it. 

Are there any settings that would open ports so my setup is more useable? I'd love to be able to browse the internet using my home IP and connect to my server with AFP.

---

### Post by DGortze380 on 2010-02-08
> **wesg said:**
> My Ubuntu server is running VPN software and I can connect to it properly, but right now it isn't very useful. I can connect with SSH using my local IP, but that's about it. 

Are there any settings that would open ports so my setup is more useable? I'd love to be able to browse the internet using my home IP and connect to my server with AFP.

I think you're a little confused.

What exactly are you trying to do?

You say you're running a VPN Server and can connect, but then you say you can only SSH to the box. Those are two different things.

This isn't a matter of 'opening ports'. You need services listening on those ports.

For internet over a VPN, configure your VPN to use the redirect-gateway directive and if you're using a firewall add appropriate routes.

AFP: [http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/](http://www.kremalicious.com/2008/06/ubuntu-as-mac-file-server-and-time-machine-volume/)

---

### Post by wesg on 2010-02-08
Thanks for the message. What I meant was that I want to be able to use services on my home network from outside, and right now I don't think VPN packets are being redirected to the services I'm requesting. I made the change to ip_forward, I think, but still as soon as I connect to the VPN, there are no services available. I don't think I have a firewall running right now, but I'll check.

---

### Post by DGortze380 on 2010-02-08
> **wesg said:**
> Thanks for the message. What I meant was that I want to be able to use services on my home network from outside, and right now I don't think VPN packets are being redirected to the services I'm requesting. I made the change to ip_forward, I think, but still as soon as I connect to the VPN, there are no services available. I don't think I have a firewall running right now, but I'll check.

What VPN Server are you using?

---

### Post by wesg on 2010-02-09
> What VPN Server are you using?

PPTPd, with Webmin.

---

