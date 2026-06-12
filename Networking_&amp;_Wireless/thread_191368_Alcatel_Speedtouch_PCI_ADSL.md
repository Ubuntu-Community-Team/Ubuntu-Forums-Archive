---
title: "Alcatel Speedtouch PCI ADSL"
date: 2006-06-07
forum: Networking &amp; Wireless
---

### Post by woot on 2006-06-07
Hey, I have some older pc at home which is on 24/7 and currently running win2k, im planning to switch it to ubuntu. Im kinda researching how I'll have to configure ubuntu for it. 

So to be concrete:
this is how the hardware part looks like, its a pci alcatel speedtouch modem, it has one entry for a normal telephoneplug. 

[IMG]http://selfcare.belgacom.net/static/pc/support/solution/adsl/drivers/driverpage/alcatel_spdtch_pc-modif.gif[/IMG]

Ive found quit some howto's for usb adsl speedtouch modems but i guess this is not the same at all.

but this seems promising:
[https://wiki.ubuntu.com/ADSLPPPoE](https://wiki.ubuntu.com/ADSLPPPoE)

allthough: A DSL modem to which you connect using an Ethernet network card

in my case the modem and ethernet card are 2 in 1 right? im just wondering wheter ill have to download additionaal packages (drivers) and ifso which so i can download em in advance...

does anyone has a setup like this?

---

### Post by woot on 2006-06-08
*kick* and update:


it seems that the way to do this in the past was
(very brief)

install pppd (which is now already in dapper)
install roaring penguin PPP ([http://www.roaringpenguin.com/penguin/open_source_rp-pppoe.php](http://www.roaringpenguin.com/penguin/open_source_rp-pppoe.php) and compile)

and
insmod -f itex1483-2.4.8.o vpi=8 vci=35 framing=1

the last step is the problem :S the itex1483 module seems to have been developped till kernel 2.4.* but after that no support is given out anymore i think

As im on 1.6.*...I have a problem...

Anyone else who has a working PCI adsl ethernet card? (kindof an internal modem) , plz speak up!

---

### Post by GoBieN on 2006-06-08
Hmm, i'm afraid i've never seen any drivers for the Speedtouch PCI home. I know the card though, a friend of mine had the same card from the early ADSL period in belgium with Belgacom. I wish you the best of luck.

I'm currently wrestling with a Speedtouch USB (the green jellyfish one :D ), i've done it before, but now things seem to go wrong :o

---

### Post by woot on 2006-06-09
hehe jip, the modem is also from the early belgian adsl time :D Its been working for a while now so i dont know why i should buy a new one..but it has to work! Oh well i figured out: or the itex module i want/need is backwards compatible or i have to use a 2.4.* kernel.

---

### Post by woot on 2006-06-09
well as there isnt much to find on this topic, for anyone else looking:


[http://jp.dhs.org/~itex/2.6/](http://jp.dhs.org/~itex/2.6/)

that is the hacked itex module for a 2.6 kernel, somehow i stumbled upon it...wooohoo!!

i have yet to try it out myself though

---

### Post by david2tm on 2007-04-29
mm...

I'm a complete n00bie with Linux
so, some, step by step how-to-do-it will help me
I've installed ubuntu
I've this very modem

And I've no Internet connection in ubuntu, so I can't even start learning using ubuntu.

---

