---
title: "enable ports 80 and 443"
date: 2013-05-09
forum: Networking &amp; Wireless
---

### Post by Pedroski55 on 2013-05-09
Hi,
I am trying to use my laptop as a server, just for the sake of learning how to do this. I have apache2 running, and on my computer I can call my home-made web page in Firefox. 

I am having trouble enabling port-forwarding in my router, but that is another problem, I will have to call the technician from China Telecom. However, assume I have port forwarding working. I read apache2 needs ports 80 and 443 enabled.

Question: would they be enabled by default in Ubuntu 12.04 on my laptop, or do I have to tell the Firewall to open them?? 

In Fedora, I can open the Firewall settings, and just tell it to enable port 80, it is that simple. However, in Ubuntu it seems a lot more complicated. I am not very worried about security at the moment, as I don't have a fixed ip, I am just trying things out.

I have installed Firewall Builder 5.0.0.3568 which I got from Ubuntu software centre. But I have not created any Firewall or compiled or installed any firewall, because I need to read a lot more about how to do that. It seem very complicated.

---

### Post by steeldriver on 2013-05-09
Ports don't really need to be 'enabled' as far as I know - as soon as you start a service that listens on a particular port that port is 'open' until you put a firewall in place to close it. If you are behind a NAT router which is only forwarding particular ports then that *is* a firewall in the sense that everything else is open from within your LAN but closed to everyone outside of it.

I'm not familiar with Firewall Builder but in general I'm leery of 3rd party firewall add-ons - you can use UFW/GUFW (very easy). You can look at things like fail2ban to prevent bruteforcing on open ports. Or someone here (not me! haha) should be able to help you set up iptables directly.

---

### Post by Pedroski55 on 2013-05-09
Thanks for that. After reading a bit and watching the videos of Firewall builder, I learnt how to set http and https, so I told it to compile and install. Seems to me, FB tried to upload to the router. But the router wasn't having any of it. I got a big 'failure'. Hardly surprising if it tries to alter settings in the router without the admin user name and password! It's hard enough when you have them, router all in Chinese and all!

I'll have to ask  the technician! What is GUFW?? Where can it be had??

---

### Post by steeldriver on 2013-05-09
GUFW is a GUI front end for UFW (the default Uncomplicated Firewall)

[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)

---

### Post by Pedroski55 on 2013-05-09
Thanks again. That looks more like something I can handle!

One more question: What is a port actually, physically??

---

