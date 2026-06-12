---
title: "Supported Ethernet Cards"
date: 2010-04-29
forum: Networking &amp; Wireless
---

### Post by Dorje871 on 2010-04-29
Hello all

I'm running Ubuntu 9.0.4 with an Intel PRO/100 VE Network Connection

I have been trying for a couple weeks now different techniques to get my wired ethernet connection working properly.  I have a seeming common issue with my e100 driver dropping connection and having hard time picking it back up sometimes.

I am GIVING UP.  I want to purchase a relatively inexpensive Ethernet card whose generic Linux driver actually operates it CORRECTLY, open up comp and put it in, and update to 9.10.

Can anyone point me to a list of Ethernet cards that are know to work flawlessly on Ubuntu, or at least tell me which card YOU are using that works perfect without having to write code, install wrapper programs, etc...?

Thank you

---

### Post by dandnsmith on 2010-04-29
I can't give a lot of help but -
1. I purchased a cheap ethernet card in November (I think from Amazon) which gave no trouble, but cannot find the details. Unfortunately it's no good giving you chipset, as they never get advertised that way.
2. most of these cards have one of the chipsets which will work (I've bought a few over the years, and only had a slight problem setting up one from about 1990).
3. I see your particular chipset has caused problems from several years back - so guess you got a bad buy there. Not a lot you can do it it's integrated into the motherboard.

---

### Post by Dorje871 on 2010-04-29
ah, so my Intel PRO/100 is integrated into my motherboard?  So that means that using this box, i am stuck with using this chipset?  there is no way to disable and add a card in a slot?

if not then its back to trying to get ndiswrapper to work.  btw, my issue with that is the last time that i tried to COMPLETELY remove the last ndiswrapper install, i also deleted the ndiswrapper.ko file from /lib/modules/2.6.28-18-generic/kernel/ubuntu/ndiswrapper and also the ndiswrapper.ko from /lib/modules/2.6.28-18-generic/misc and so now i don't know how to get those correct files back

---

### Post by SlugSlug on 2010-04-29
[http://www.ebuyer.com/product/25986](http://www.ebuyer.com/product/25986)

should work

---

### Post by dannyboy79 on 2010-04-29
u can have multiple ethernet cards in a box! i have 2 in a machine which shares its connection with an xbox. any card which uses the SIS module or the TULIP module in lucid lynx works just fine.

[http://hardware4linux.info/module/tulip/](http://hardware4linux.info/module/tulip/)

OR

you can check this page out. [http://www.linux.org/docs/ldp/howto/Ethernet-HOWTO-4.html](http://www.linux.org/docs/ldp/howto/Ethernet-HOWTO-4.html)

---

### Post by Dorje871 on 2010-04-29
ok, so theoretically, all i need to do is forget about the Intel chip, open up comp, put in that card you suggested (thank you by the way), plug the ethernet cable into that slot instead, turn on computer, and Ubuntu should see the new device, attach the right driver, and use that for eth0 automatically instead of the e100?  

or will it still wait for the Intel chip to be plugged in as it is already associated with eth0?

or will it create a new connection (such as eth1) and thus we can still ignore eth0?

thank you.  i'm just sick of messing around with all this and want a plug and play and keep ubuntu.  don't wanna go back to "evil empire"

---

### Post by dandnsmith on 2010-04-30
Sometimes you can disable the onboard one in the BIOS, but if you can't then select the new as the primary interface (shouldn't really give much hassle, but you may have to find a way to declare it), and disable the other. It would be easier if the onboard interface wasn't working at all.

---

### Post by Dorje871 on 2010-04-30
well, that D-Link card u linked was discontinued in the US 9 years ago.  should probably go with another, but ty.  anyone else know a good card for linux?

---

### Post by dandnsmith on 2010-05-02
If you don't want to buy-and-try, despite the cheapness, you could search for a couple, and then post to see if anyone has tried them.
That way someone might know the chipset involved and respond with a good/bad rating.

---

