---
title: "ufw in ubuntu 10.04 is not opening ports"
date: 2011-07-29
forum: Networking &amp; Wireless
---

### Post by jamiebux on 2011-07-29
Hello, 

I'm using Ubuntu 10.04 x64 server as a router for our small office network. We are using ufw was the firewall was able to get IP forwarding working just fine. However, we are unable to open ports. We are trying to up port 1723 for our VPN tunnel, but it just won't open. 

root@brainbox:~# ufw status verbose 
Status: active
Logging: on (low)
Default: allow (incoming), allow (outgoing)
New profiles: skip

To                         Action      From
--                         ------      ----
1723                       ALLOW IN    Anywhere
22/tcp                     ALLOW IN    192.168.1.0/24

 
Also, when we set the ufw default incoming port to deny, we are unable to ssh, even with that port open as well. We would like to have the incoming port set to deny and open the ports we need since this is the most secure thing for our server. 

This seems pretty basic and simple. But its just not working for us. I have a good amount of linux experience and provide you any info you need. We really need to get this working and I'm looking into trying the latest version of Ubuntu Server(11.04) to see if this issue still exist. Any help is much appreciated and needed. 

Thanks alot!!

---

### Post by iponeverything on 2011-07-30
Opening the ports is not going to do it. Your internal addresses are RFC 1918. You need to setup port forwarding for ports in question.

---

### Post by jamiebux on 2011-08-01
Thats very interesting. We currently have some ports forwarded right now. So pretty much, just forwarding the ports to the IP should it. I would think that having the ports open should be able to get us to the world. But I will give this a shot and keep you posted. Thanks for the idea. '

Cheers,

---

### Post by jamiebux on 2011-08-01
This is still causing me some headaches. Port forward for our outside network is working. But even without the firewall, something else seems to be going on. I'm currently looking into this to find some solution, but the weird question right now, port forwarding works on the outside, but ports aren't open on the inside??

---

