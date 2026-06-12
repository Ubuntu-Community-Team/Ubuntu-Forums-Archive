---
title: "Connected to internet but can't browse??!?"
date: 2010-10-14
forum: Networking &amp; Wireless
---

### Post by iainstott on 2010-10-14
Hi guys, I'm a newbie really with ubuntu and Linux in general. Have installed ubuntu a few times in the past but if I've had to get messy with the command line I bailed.
So given that I wanted to set up a home server/media center, I tried win server, but given research had told me that it is easier to accomplish all the features I wanted with Linux I decided the time had come to really see what I'd been missing out on.
So what I am looking to accomplish is a full lamp stack, xbmc, samba, mail server, VMWare server, rtorrent, ftp, an probably a few others I have forgot because I can't get to my check list right now.
Settled on ubuntu 10.10, had installed it a couple of times while it was still in beta, just to get a feel for it and get everything working so that when it was released i could do a fresh install knowing how to configure everything straight of the bat.
So on Sunday the time came.
Everything was going fine until last night, I was installing roundtable webmail and all I came to download something and FireFox can't display any web pages, postfix can't deliver mail. The server can ping local machines but not google.com or another internet site, I can ssh into it an get a remote desktop session via various methods, both either over the local network, or internet. The website is getting served both locally or internet. I just cant seem to make any outbound connections to the outside world.
Can anyone help please
Iain

---

### Post by Peter09 on 2010-10-14
Can you post the output of the terminal command
 
```
route
```
 
you are most probably not seeing the default gateway (which should be your router). Either that or not seeing the DNS server.

---

### Post by iainstott on 2010-10-14
Cheers for your reply, am not at my server right now and have closed the ports to remote onto it so won't e able to post results until I get home from work in a couple of hours.
Iain

---

### Post by iainstott on 2010-10-14
Have been able to do it via webmin via my phone 
[http://www.iaincstott.co.uk/route.txt](http://www.iaincstott.co.uk/route.txt)
If ya want it here's the output of ifconfig
[http://www.iaincstott.co.uk/ifconfig.txt](http://www.iaincstott.co.uk/ifconfig.txt)

---

### Post by vanyrow on 2010-10-14
yes i have the same problem and also the same **output **of the command "route" >>>>

---

### Post by mogaio on 2010-10-14
i also have the same problem since installing ubuntu 10.10 i tried the "route" command and got the same output also .......

---

### Post by Peter09 on 2010-10-14
So this looks like a dns issue. Your router should be giving you the name of a domain name server, however that does not appear to be the case.
 
Try rightclicking on the network icon and selecting the edit mode, then select the network to edit. From memory I think you should be able to enter the ip address of a dns server. Intitially try your router. While you are there disable the IPV6 protocol as some routers get confused by it.

---

### Post by iainstott on 2010-10-14
Ok got it sorted now, think it maybe a "cowboy" job but ill let you decide.

I edited /etc/networking/interfaces, and changed it from a static ip address to DHCP and it worked.

I say this may be a cowboy job because, since i have been trying to setup my server i have always set the ip through the 'interfaces' file and it has always worked. It just seemed to stop working when i installed roundcube, and i thought it a bit strange that that installation could cause this.

Thank you for your help.
Hope this thread helps the two others experiencing the same issues as me.

Iain

---

### Post by Peter09 on 2010-10-14
DHCP is the best way of configuring your machine - it lets your router sort out the allocation of IP addresses. Even if you wish for a static IP the best way is to instruct your router to allocate this against a machine.

---

