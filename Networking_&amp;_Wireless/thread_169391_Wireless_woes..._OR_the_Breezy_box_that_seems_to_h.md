---
title: "Wireless woes... OR the Breezy box that seems to hate my router..."
date: 2006-05-02
forum: Networking &amp; Wireless
---

### Post by pyromidget on 2006-05-02
Hey all - first post here and it's of the beg-for-help variety...

Basic situation first:

[B]Broadband Internet
[INDENT]-> Wireless router[/INDENT]
[INDENT][INDENT]-> Various online Windows laptops.[/INDENT][/INDENT][/B]
And everything's all well and good.  Now introduce an Breezy box and it looks more like:

[B]Broadband Internet
[INDENT]-> Wireless router of DOOM!![/INDENT]
[INDENT][INDENT]-> Various online Windows laptops[/INDENT][/INDENT]
[INDENT][INDENT][INDENT]-> Total lack of Internet for Breezy box.[/INDENT][/INDENT][/INDENT][/B]

I have 4 different wireless cards that I've tried. One doesn't seem to be supported at all so I've discounted it, the other three show up in **ifconfig** and **iwconfig** fine, but no matter what settings I try they won't connect to the router... ](*,)

Interesting sidenote.  If I chuck a Breezy live CD into one of the laptops, then it can pick up and connect to the network fine using the same chipset thats in one of the cards I've been trying...

I'm fairly new to the whole Linux thing, but I've worked my way through all the troubleshooting guides with no joy.  You guys all seem to be pretty hot in the whole fixing-things department so any suggestions would be appreciated.  

I'm pretty sure you'll need more info than this, but I don't know what so if you need me to post any thing up just let me know and I'll get it.

Cheers.

---

### Post by brickhead20 on 2006-05-02
Hey, Im a newbie too, but I found the trick with mine lie in the WEP encryption. First turn it off (at the router too) and if that works then atleast you know you it might work with encryption. Randomly install wpasupplicant with

sudo apt-get install wpasuplicant


because I heard that helped. If you have a WEP key, set it with

sudo iwconfig wlan0 key PUT_YOUR_KEY_HERE

assuming wlan0 is the network. Maybe that will then work. To be honest, wireless support in Ubuntu is shockingly bad at the minute unless you have a Ralink chipset in your card or whatever. If that doesn't work: pray. Pray someone else will reply to this post with some useful information. Mines still so sektch,  I have to wait/beg/offer sacrifices before it connects.

Have fun now...

Rich, good luck

---

### Post by brickhead20 on 2006-05-02
Hey, Im a newbie too, but I found the trick with mine lie in the WEP encryption. First turn it off (at the router too) and if that works then atleast you know you it might work with encryption. Randomly install wpasupplicant with

sudo apt-get install wpasuplicant


because I heard that helped. If you have a WEP key, set it with

sudo iwconfig wlan0 key PUT_YOUR_KEY_HERE

assuming wlan0 is the network. Maybe that will then work. To be honest, wireless support in Ubuntu is shockingly bad at the minute unless you have a Ralink chipset in your card or whatever. If that doesn't work: pray. Pray someone else will reply to this post with some useful information. Mines still so sketch,  I have to wait/beg/offer sacrifices before it connects.

Have fun now...

Rich, good luck

---

