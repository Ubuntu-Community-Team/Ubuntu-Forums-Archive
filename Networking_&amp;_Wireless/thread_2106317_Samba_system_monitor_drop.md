---
title: "Samba system monitor drop"
date: 2013-01-18
forum: Networking &amp; Wireless
---

### Post by swordsusa on 2013-01-18
hello, I've recently set up a file sharing PC with a mini-atx board that has an atom 2550 CPU. I know there are some problems with the graphics driver on this chip but I don't need the graphics power so it shouldn't be a problem. This is the link to the cpu/mobo combo I'm using. [http://www.newegg.com/Product/Product.aspx?Item=N82E16813135334](http://www.newegg.com/Product/Product.aspx?Item=N82E16813135334) I have several drives shared with samba full read/write access and I can see these drives on windows computers and copy to them although the speed is a bit disappointing, 300mbit/s on gigabit network. In my initial efforts to troubleshoot this I open the system monitor on my ubuntu machine, when I do so the copy stops....I have network monitors on my windows machine as well that confirm that when I open the network monitor the copy does indeed stop entirely and I am unable to access any of the networked drives until i restart the networking services in Ubuntu. I have a raid card installed but it does not seem to matter whether I am copying to the drives on the raid card or the drives on the on board sata ports. 
anyone have an idea as to what's going on?
I should mention that even though newegg has that as a 10/100 port it is gigabit. shows as gigabit in os, in manual, and on manufacturer's site.

[]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813135334")

---

### Post by dpurgert on 2013-01-18
300mbit/sec raw xfer speeds over a gigabit network isn't that bad. You've got to allow for the network overhead, drive read/write speeds, amount of ram on the source/destination machines, etc.

---

### Post by swordsusa on 2013-01-18
using the same hardware with windows sharing the drives, I can get 6-800mbit/s transfer speeds.

---

