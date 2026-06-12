---
title: "WEP problem - Wirless almost working!!"
date: 2006-03-01
forum: Networking &amp; Wireless
---

### Post by Brendtos on 2006-03-01
Hi,

I've read through all the forums and have at least got to the stage when my two systems are able to ping each other but now I'm getting

Rx invalid crypt:409

Which I believe means that there is an encryption problem. So I then typed

sudo iwconfig eth0 key off

and turned WEP off in my windows machine but the problem is still there!!

Also when I ping my windows machine I can see the packets as received but they do not show on the my laptop (linux) ping reads

4packets transmitted, 0 received, 100% packet loss, time 3000ms

What is wrong can someone please help me!!

Thanks
Brendt

---

### Post by Lambert on 2006-03-02
[QUOTE=Brendtos]Hi,



and turned WEP off in my windows machine but the problem is still there!!


Thanks
Brendt[/QUOTE]

Give a little more about your set up? The above statment gives impression you're connected via adhoc and not a router/access point? 

How are you assigning an ip? DHCP or static.

Anything else about your network might help.

---

