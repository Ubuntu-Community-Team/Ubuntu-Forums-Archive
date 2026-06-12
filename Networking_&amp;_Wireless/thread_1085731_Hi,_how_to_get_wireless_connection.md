---
title: "Hi, how to get wireless connection?"
date: 2009-03-03
forum: Networking &amp; Wireless
---

### Post by Jurgisk on 2009-03-03
Hello, i'm very new to ubuntu. Friend just gave cd to me, and i installed it. :) :)
When i installed ubuntu, there was black screen and error showed:  that something wrong with wireless, [http://linuxwireless.org/en/users/drivers/b43](http://linuxwireless.org/en/users/drivers/b43) - that i need download.. 

Okay, so i don't have any internet connection on laptop, i don't have chance to get CABLE, only wireless..
I read *Comprehensive ndiswrapper troubleshooting guide*, used search for while, but don't get any sense of it..

i tried to use this command on terminal
**ndiswrapper -l**
but it says, that i don't have any ndiswrapper installed :/ 

Ah, i don't know what i really need to know..

I have Amilo A1645 laptop

used **lshw -c network** command..
it shows
```
network:0
..
.  
network:1
description: Network Controller
product: BCM4318 [airforce one 54g] 802.11g wireless lan controller
vendor: Broadcom corporation
...
..
.
```
so i think it recognizes laptop wireles.. i made wireless connection too, and tried connect to it, but nothing happens when i press connect button, dialog just dissapers, no error messages, no alerts.. :(


what i need to get wireless connection?
thanks! ;)

---

### Post by N04h on 2009-03-04
I believe this may use the same chip as the dell 1501.  Any solutions for that should work for you, however, can you plug it into an ethernet port somewhere and run the update?  If you can do this it should work right out of the box.

---

