---
title: "Telstra elite/ultimate USB modem"
date: 2011-08-12
forum: Networking &amp; Wireless
---

### Post by Jagoly on 2011-08-12
Ok, so I am buying my uncle a new netbook/notebook. He has never used a computer before, so he isn't very tech savvy. He needs 3G modem as he'll be taking it around with him. So, what I'm asking is will a telstrq bigpond elite USB modem work with ubuntu? I can set up it up first off, but after that, it needs to work without problems. Unfortunately optus and other carriers aren't an option, because up in the northern territory (or down for most of the world) only telstra has a reliable signal.

Thanks for any insight.

---

### Post by pdc on 2011-08-13
by trying this 

[http://lmgtfy.com/?q=linux+Telstra+elite%2Fultimate+USB+modem](http://lmgtfy.com/?q=linux+Telstra+elite%2Fultimate+USB+modem)

you get some replies

[http://forums.whirlpool.net.au/archive/1560593](http://forums.whirlpool.net.au/archive/1560593)

Terry reckons it works well

> User #313381   606 posts
terryjay
Whirlpool Enthusiast
	

Mine works "out of the box" in Ubuntu (desktop) and Linux Mint 9 (laptop) speed is amazing for such a compact device especially on the desktop with a roof mounted yagi.

Terry
	
anchor: whrl.pl/RcDeCh
posted 2011-Jan-31, 4pm AEST

if you go into a friendly Telstra NT shop; ask to plug the modem into a linux laptop

capture

> lsusb

and if you have

> dmesg | grep tty

also ready to go in a terminal, and you get 

> ttyUSB0  back, that says it is seen as good to go:

but Terry reckons it is already good to go?

and this user (same thread as above) says

> User #253042   41 posts
Just_A_Number Forum Regular
	
I have a Telstra Elite Mobile Pre-Paid Broadband ZTE-668 package. Works well with Sakis3G.
	
anchor: whrl.pl/RcDhep
posted **2011-Feb-1, 9a**m AEST

sakis 3g is an excellent dialler for linux

[http://lmgtfy.com/?q=sakis+3g](http://lmgtfy.com/?q=sakis+3g)

---

### Post by Jagoly on 2011-08-13
I have done a bit of googling, but I what I found was a heap of mixed results. Some people say it works, some say it doesn't. And  alot of them were from a few years ago, so I didn't know if they still applied.

Also I can't really take it in to test it, Telstra is the only option. I will try to do that, though. It needs to work. I'll give it a go, anyway. If it doesn't work, I'll take it back and get a gateway instead.

---

### Post by pdc on 2011-08-13
I would believe the more recent ones; (that say it works fine);

the ZTE modems have a generic ID when plugged in

> 192d:2000

that is their virtual CD-ROM ID; 

linux has a simple

> eject /dev/sr0  command built-in now

that "flips" the ID and the modem ID is revealed; eg I have the MF636 and it flips from 19d2:2000 to 19d2:0031 

if it works on Sakis 3g that is another good pointer;

---

### Post by Jagoly on 2011-08-13
Thank you for help, but I've decided to get a wifi hotspot insted. that's easier because we decided on a plan instead of prepaid.

Marked as solved :KS

---

