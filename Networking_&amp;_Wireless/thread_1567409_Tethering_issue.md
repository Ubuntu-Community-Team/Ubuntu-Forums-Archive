---
title: "Tethering issue"
date: 2010-09-03
forum: Networking &amp; Wireless
---

### Post by wigglez85 on 2010-09-03
Hi,

I've tethered my Droid to my ubuntu netbook using azilink.

I don't understand this, but when I have it up and running it connects ok, but doesn't let me access the internet... unless I already have a connection with my wireless

I confirmed this with speedtest.net

just wireless i get about 11mbps, when connected to wireless and tethered i get 2mbps, but why does it only work when i'm connected?

---

### Post by wigglez85 on 2010-09-04
I figured out what was wrong.  For anyone else who needs to know, you need to add

--set-security 2

to the openvpn command.

now if i can just get it to recognize as an internet connection on the comp...  then i can get empathy to work.

Edit:  Whoops, its --script-security 2

---

