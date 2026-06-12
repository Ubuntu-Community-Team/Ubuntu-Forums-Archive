---
title: "Another wireless connection problem..."
date: 2009-04-09
forum: Networking &amp; Wireless
---

### Post by spongebodge on 2009-04-09
I'm pretty new to Ubuntu (just installed it a couple days ago) and I haven't been able to get my wireless to work. I have a feeling Ubuntu isn't recognizing my router and/or the driver's not installed properly or something?? I've got a 2wire 2701HG-G router and I'm using a Dell Inspiron 6400 with Windows XP Home Edition. 

If you need any more info just tell me what commands I should enter and I'll post back with the results.

Any help will be greatly appreciated. Thanks in advance!

---

### Post by t0mppa on 2009-04-09
It's a weenie bit hard to figure out what's the problem with the limited info provided, so here's a few commands to help clear things up.The basic info needed is

[LIST=1]
[*]your Wireless chip type, which you can find with:```
lspci | grep Ethernet
```
[*]Wireless network configuration, which will be revealed by: ```
iwconfig
```
[*]Wireless networks available. Mainly 2 things of interest here: Can you see any networks (if there are networks other than yours present of course)? Can you see your routers network? To find out, run: ```
sudo iwlist scan
```
[/LIST]

---

