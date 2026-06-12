---
title: "VPN All Traffic"
date: 2009-06-15
forum: Networking &amp; Wireless
---

### Post by LinuxLars on 2009-06-15
Using Ubuntu 9.04.

How do I restrict the VPN? I do not want all traffic routed through the VPN.

---

### Post by gombadi on 2009-06-15
> 
How do I restrict the VPN? I do not want all traffic routed through the VPN. 


A lot more information would be useful :-)

What type of VPN is it?

Can you tell us a bit about your network setup - local networks, remote networks via the VPN, remote networks via the Internet. What are you using for a default gateway?

The more information you can give us the better the answer we can provide.

BTW - It all depends on the kernel routing table as to which packets get sent to which interface.

---

### Post by MaindotC on 2009-06-16
Also be sure to tell us if you are dual booting and if you've downloaded and installed all of the latest updates.

---

### Post by superprash2003 on 2009-06-16
take a look at this as well [http://www.cyberciti.biz/faq/linux-setup-default-gateway-with-route-command/](http://www.cyberciti.biz/faq/linux-setup-default-gateway-with-route-command/)

---

### Post by LinuxLars on 2009-06-18
Lordy - this should be a quick answer...

Everything is current.
Booting only into Ubuntu 9.04.
I'm VPN-ing into a Microsoft PPTP network. 
The VPN connection works fine.

Except that ALL traffic is routed through the VPN. So I can't browse, get email, etc. 

I was able to restrict it in a previous version of Ubuntu, but I don't seem to be able to figure it out in 9.04. 

Easily done on my Mac (note to developers - on the Mac, the checkbox option, defaulted off, is:
 [ ] Send all traffic over VPN connection
Sweet.).

What should I be looking at?

---

### Post by MaindotC on 2009-06-20
I'm going to guess that the route command can help you.

---

### Post by LinuxLars on 2009-06-22
You would think, but so far nothing has worked.

---

### Post by LinuxLars on 2009-06-25
I obtained the information requested in the Route dialog from the VPN admin. We've tried several combinations, and still have not been able to achieve a routed connection. 

I have attached a screen print of the Routes dialog, along with the syslog and messages log.

We have to find a way to make this easier if Ubuntu is going to be accepted mainstream. I've spent hours on this, as has the VPN admin. With my Mac, it just worked first time without hassle. And that should be the goal IMHO.

Has anyone been able to get a routed connection to work on 9.04?

---

