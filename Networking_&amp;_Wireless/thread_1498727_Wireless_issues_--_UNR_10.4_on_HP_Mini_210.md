---
title: "Wireless issues -- UNR 10.4 on HP Mini 210"
date: 2010-06-01
forum: Networking &amp; Wireless
---

### Post by Karandr on 2010-06-01
Hi there,
just installed Ubuntu Netbook Remix on my new HP Mini 210 ([info]("http://www.shopping.hp.com/webapp/series/category/notebooks/mini210_series/3/computer_store")). Everything is working fine -- webcam, shortcut keys etc, but I'm having some difficulties connecting to our wireless network. When I click on the network panel item, there are no networks visible. Now, I also have Windows 7 Starter on the netbook (what I'm using right now) and that's able to connect to the network fine. Feel free to ask for any info you need.

Thanks in advance. :D

---

### Post by Karandr on 2010-06-01
I don't know what the rules are in this forum in regards to bumping, but I've fallen off the first few pages, so hopefully I'm safe.

---

### Post by pdc on 2010-06-02
I suspect you have a broadcom card in there 

type

> lspci  in a terminal: you find the terminal under System: accessories; terminal

look for broadcom

from this post

[http://ubuntuforums.org/showthread.php?t=1460797](http://ubuntuforums.org/showthread.php?t=1460797)

> Broadcom Corporation BCM4312 802.11b/g (rev 01)

looks like the 4312 broadcom

here is a guide to installing the sta driver this needs

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

if you can plug into an ethernet cable and do a wired download, that may be helpful;

carefully read the instructions a couple of times: 

let us know how it goes

---

