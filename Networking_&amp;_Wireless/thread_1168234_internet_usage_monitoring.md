---
title: "internet usage monitoring"
date: 2009-05-23
forum: Networking &amp; Wireless
---

### Post by vpnm_87 on 2009-05-23
my ISP allows me to use upload/download of 1.5GB totally per month...
is there any software for Ubuntu 8.10 to keep track of amount of bytes i download from internet...

To put it simple when i open ubuntuforums.org i should be able to know how much bytes i downloaded from internet to view the website..any software or browser plugins for that in ubuntu 8.10?

---

### Post by ad_267 on 2009-05-23
I don't think there's anything available that will tell you how much you've downloaded to view a single web page, but vnstat is good for monitoring your total usage over a time period.

To install:
sudo apt-get install vnstat
sudo vnstat -u -i eth0

You might have to replace "eth0" with the correct interface.

vnstat is a command line program. Run "man vnstat" in a terminal to see how to run it. If you use conky you can pipe the output from vnstat to conky.

---

### Post by vpnm_87 on 2009-05-23
I tried conky but i guess i dont see any bytes downloaded from Internet in that window...ll try vnstat as u said

the reason why i asked for bytes downloaded specifically is my ISP has one link that clearly shows startin and ending browsin time with exact amount of bytes used...

the prob is their site is always overloaded and it takes 20 min to load..
after tryin for 4 days today only i saw that page..

---

### Post by vpnm_87 on 2009-05-24
vnstat did the job:D
thanks dude:D

---

