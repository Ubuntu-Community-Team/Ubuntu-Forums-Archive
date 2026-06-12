---
title: "firefox doesnt load some web pages"
date: 2009-01-25
forum: Multimedia Software
---

### Post by basilwatson on 2009-01-25
Hi there , As per , Firefox  doesn't load some web pages, The laptop DOES no problem there, but the desktop DOESN'T.  The only difference I can see is ADOBE flash 10 ( or one of the new restricted media )  and Firefox version , Desktop three , laptop fire-fox 2 

The I have tried to open the eweb pages using Opera , sea-monkey and knoquoror and the page  will not load ...

anyone???????? I am sort off lost with ideas now , below is the output of my ifconf 


Stephen




auto lo
iface lo inet loopback

This is the output from my network file my ifconf is as follows
eth0 Link encap:Ethernet HWaddr 00:10:dc:cd:c7:89
inet addr:192.168.0.3 Bcast:192.168.0.255 Mask:255.255.255.0
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:1752 errors:0 dropped:0 overruns:0 frame:0
TX packets:1929 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:1448248 (1.4 MB) TX bytes:391799 (391.7 KB)

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:130 errors:0 dropped:0 overruns:0 frame:0
TX packets:130 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:10404 (10.4 KB) TX bytes:10404 (10.4 KB)


I added mtu 1492 in the network file but it didnt make a difference


also changed it to 1454 no joy ...

those pages just wont open

---

### Post by Sam Lars on 2009-01-25
So you're saying that Firefox 2 works, but Firefox 3 and the others do not?
What pages are you trying to load?

---

### Post by basilwatson on 2009-01-25
> **Sam Lars said:**
> So you're saying that Firefox 2 works, but Firefox 3 and the others do not?
What pages are you trying to load?

[www.stuff.co.nz](www.stuff.co.nz)
hotmail
letsjapan 

[http://torrent.eval.hu/](http://torrent.eval.hu/) ( this will open until the vital point in which it times out like the rest ) 

and one or 2 others 

the hot-mail is important as its the wife's email...( yes i know but I live with a Luddite ) ... 


you probably will find your browser will open these pages , others have said they do , ( my laptop does using Gos,) 

but it just times out on the desktop 

can leave the page going all night and it wouldnt connect or say timed out ,

Stephen

---

