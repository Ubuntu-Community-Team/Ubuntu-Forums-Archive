---
title: "2 Ubuntu-only PCs - cable modem"
date: 2006-01-08
forum: Networking &amp; Wireless
---

### Post by DirkP on 2006-01-08
Can I hook up 2 Ubuntu-only PCs (5.04 & 5.10) to a cable modem, that has only one ethernet port? 

I would like to share the modem/internet connection, being able to use both PCs at the same time. I'm not sure how the internal IPs and/or MACs would work - likely a critical point (charter.com - they don't support linux), and I'm assuming DHCP.  I do not necessarily need to share files or printers between the PCs.

I have 3 different brand ethernet cards (all Ubuntu HCL)

Can I use a hub or switch, with firestarter as the GUI front-end to the IPtables? A USB bridge?

Or put 2 NICs in one PC - cable from the modem into one NIC - cable from 2d NIC (1st PC) to 3rd NIC in 2d PC?

Better way to get a router? 

I downloaded the instruction guide for the linksys WRT54GL - it seems to be based on non-L models, as it refs a windows wizard setup

I also have 2 D-Link wireless cards (not sure how the new place/physical barriers will work out wrt). 

In the past, I've been the lone Linux machine LANed into a pre-existing Windows network primary via a router - everything just worked.

Thanks for your help,
Dirk

---

### Post by kairu0 on 2006-01-08
You have two options:

1. You buy an Internet Sharing router. You plug it into the DSL modem and plug your PCs into it. With the exception of opening network ports for p2p, online gaming, etc. you are good to go.

2. You put 2 NICs in one machine and have this machine share the Internet to your other computer. You use IPchains to do this.

[http://www.ubuntuforums.org/showthread.php?t=91370](http://www.ubuntuforums.org/showthread.php?t=91370)

This page will tell you how. The drawback is that the sharing computer must obviously be running for the other to access the Internet.

---

### Post by matthew on 2006-01-08
kairu0 is right. I just wanted to add that I have done both and buying an inexpensive router is likely to be the easier method, but configuring a PC with two nics really isn't too difficult and you might have some fun. If you check the sales you could find one for $30 US. If you want to spend a little bit more, I have the wrt54G (older, similar to the L model) and it has been excellent.

---

### Post by kairu0 on 2006-01-08
[QUOTE=matthew]two nics really isn't too difficult and you might have some fun.[/QUOTE]

...and it's good experience. You might find it more rewarding in the long run.

On the other hand, configuring ports to forward with ipchains is not as fun or user-friendly as doing it on a cheap router.

---

### Post by LightShear on 2006-01-08
Random question. Would the 2-NIC method be slower for the second (or both) computer(s), rather than if both were connected to a router individually?

---

### Post by matthew on 2006-01-08
[quote=LightShear]Random question. Would the 2-NIC method be slower for the second (or both) computer(s), rather than if both were connected to a router individually?[/quote]Only if both computers are doing bandwidth-intensive tasks at the same time and if the router would allow a greater amount to flow through it from individual connections. That sounds weird...let me try to illustrate using totally arbitrary numbers

Option A - router has 1000 Mb/s bandwidth total from a cable modem to the router, connect 2 computers to it whose nics max out at 100 Mb/s...each can download at full bandwidth

Option B - router is limited to 100 Mb/s total by the DSL modem it is attached to, the two computers connected to is are each capable of 100 Mb/s connections, but are limited by the capability of the router to a total of 100 Mb/s distributed between them as needed...often each will reach it's full potential, but there may be occasional bottlenecks if both are trying to download large files at the same time

Option C - one computer connects to another each using 100 Mb/s nics. The second computer connects to the internet with a second 100 Mb/s nic and this connection is shared with the first computer. Again the total throughput wll be limited to 100 Mb/s and there could be occasional bottlenecks.

In practice, for the home user any of these will be just fine and you aren't likely to notice any real slowdowns. I say it's a wash and you can do as you like.

I personally have a computer attached directly to my Linksys wrt54g by a cable, and another by wireless. The laptop that connects via wireless also has a desktop occasionally attached to it at the other end of the house via a crossover cable and shares the wireless connection. I've never had a problem sharing the connection. You may notice a time difference if both computers are downloading 300 Mb files at the same time, but for email, web browsing, and general stuff there's no big performance hit.

Hope that helps! Have fun. :)

---

### Post by LightShear on 2006-01-08
I figured there wouldn't be a noticible decrease. Thanks for the totally arbitrary illustration. :)

---

### Post by DirkP on 2006-01-09
Thanks for all the responses. Just had a +12hr power outage where I live.

I will go the router, um, route. 

Perhaps I should repost under a new sub:

If i get a WRT54GL, or pre-rev5 WRT54G (am also looking at a DL DI-624), do I just manually configure the connection (using info from the cable ISP, after following the sequential physical hook-up procedures)?

How do I get to the router's prompts/fields for user name, pw, adjust user and security settings, etc?

Open a web browser and type in 192.168.1.1 (or is it 192.168.0.1?)?

Rgds,
DirkP

---

### Post by DirkP on 2006-01-10
I found this

[http://www.linux.org/docs/ldp/howto/Linksys-Blue-Box-Router-HOWTO/index.html](http://www.linux.org/docs/ldp/howto/Linksys-Blue-Box-Router-HOWTO/index.html)

Rgds,
DirkP

---

### Post by heftigrat on 2006-01-10
[QUOTE=matthew]Option A - router has 1000 Mb/s bandwidth total from a cable modem to the router, connect 2 computers to it whose nics max out at 100 Mb/s...each can download at full bandwidth

Option B - router is limited to 100 Mb/s total by the DSL modem it is attached to, the two computers connected to is are each capable of 100 Mb/s connections, but are limited by the capability of the router to a total of 100 Mb/s distributed between them as needed...often each will reach it's full potential, but there may be occasional bottlenecks if both are trying to download large files at the same time

Option C - one computer connects to another each using 100 Mb/s nics. The second computer connects to the internet with a second 100 Mb/s nic and this connection is shared with the first computer. Again the total throughput wll be limited to 100 Mb/s and there could be occasional bottlenecks.[/QUOTE]

In both options A and B the PC's would each be limited to their individual 100Mbps connections with the built in switch on the router.  The bandwidth limitations _should_ be the same in both cases, correct?

In option C if the PC with 2 nic's is, say for instance, downloading many 30M p0rn files all at once ;)  and using nearly 100% of the bandwith of that connection, the second PC would get crawling Internet speeds no matter what its usage is over the connection to the PC in the middle.
-----
EDIT:  And the reverse situation, if the PC w/1 NIC were attempting to utilize the full 100M connection to the PC w/2 NIC's, would the middle PC prioritize the packet scheduling so the PC w/1NIC's total bandwidth would be ~50M?  I could be completely wrong in my assertion if that's not the case.

But yes, you are definitely correct in saying that if neither of the PC's is really doing any heavy dl-ing, it shouldn't be an issue.

---

### Post by mips on 2006-01-10
Once you buy a router the manual should give you the routers preconfigured IP address and on some routers it is even printed on the bottom of the device. Same goes for username and password.

Access is via web browser.

I would not worry to much about that site as they basically go to extremes. The manual that comes with the device is usually good enough and then there is always the web...

---

