---
title: "Find ip remotely"
date: 2011-10-20
forum: Networking &amp; Wireless
---

### Post by alejandro.mc on 2011-10-20
Hey sorry to disturb.. I finally figured how to start and control remotely my computer.. but I have a problem. My ip provided by my ISP Fibertel in Argentina is dynamic, changes every now and then.. So if a leave home for a couple of days I can't start my computer remotely because I don't know my new ip..

How could I fin out my new assigned.. I talked to my ISP support here but they can't help me..

I don't think there is a solution for this but if anyone can help me..

Thanks in advance..

Cheers,

Alejandro
Buenos Aires
Argentina

---

### Post by spiky001 on 2011-10-20
You need to use 1 of these [http://www.no-ip.com/services/managed_dns/free_dynamic_dns.html](http://www.no-ip.com/services/managed_dns/free_dynamic_dns.html)
or
[http://dyn.com/dns/dyndns-free/](http://dyn.com/dns/dyndns-free/)

---

### Post by oldfred on 2011-10-20
Someone just posted this:

 [http://ubuntuforums.org/showthread.php?t=1863666](http://ubuntuforums.org/showthread.php?t=1863666)
older
 [http://ubuntuforums.org/archive/index.php/t-526176.html](http://ubuntuforums.org/archive/index.php/t-526176.html)

---

### Post by alejandro.mc on 2011-10-27
Hi, thanks a lot for replying.

I have read everything and set up an account and host.

The question that I still have is, if I need software installed in my computer to recognize the ip address that changed dynamically, I supposse the computer has to remain TURNED ON for this methods to work? Because what I'm trying to do is to turn on the computer remotely..

Thanks again in advance for future replies!



Alejandro
Buenos Aires
Argentina

---

### Post by haqking on 2011-10-27
> **alejandro.mc said:**
> Hi, thanks a lot for replying.

I have read everything and set up an account and host.

The question that I still have is, if I need software installed in my computer to recognize the ip address that changed dynamically, I supposse the computer has to remain TURNED ON for this methods to work? Because what I'm trying to do is to turn on the computer remotely..

Thanks again in advance for future replies!



Alejandro
Buenos Aires
Argentina

How are you proposing to turn on a powered off computer remotely ?

I presume WOL is enabled on the machine in question ?

---

### Post by alejandro.mc on 2011-10-27
Yes it is. I've done it already. Actually I do it everyday. The problem I have is I won't be here, so I won't know the IP address once it changed..so I'll have no address where to send the magic packet.. cause I'll not know my own ip address..

Thanks in advance!

Alejandro
Buenos Aires
Argentina

---

### Post by haqking on 2011-10-27
> **alejandro.mc said:**
> Yes it is. I've done it already. Actually I do it everyday. The problem I have is I won't be here, so I won't know the IP address once it changed..so I'll have no address where to send the magic packet.. cause I'll not know my own ip address..

Thanks in advance!

Alejandro
Buenos Aires
Argentina

ok so as mentioned above you can use a dyndns service.  Is the machine behind a router i take it ? and the router WAN IP changes via ISP, so either purchase a static or use a dynamic tracking service, then that packet has to be forwarded to the LAN machine

---

### Post by alejandro.mc on 2011-10-27
Thank you very much! It appears to be working flawlessly, before changing status to solved or sth else.. I'd like to check the turning on from other location. Once I do I'll edit the post!

Thanks you very much!!

Cheers!!

Alejandro
Buenos Aires
Argentina

---

