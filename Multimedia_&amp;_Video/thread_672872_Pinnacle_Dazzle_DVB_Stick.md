---
title: "Pinnacle Dazzle DVB Stick"
date: 2008-01-20
forum: Multimedia &amp; Video
---

### Post by spegru on 2008-01-20
Hello I just bought one of these USB Digital TV tuners (pretty cheap as £25 , and I previously had good results with Freecom and Hauppauge devices, so worth a risk)

I did a trawl of the posts here and got linked to this:
[http://linuxtv.org/wiki/index.php/DVB-T_USB_Devices](http://linuxtv.org/wiki/index.php/DVB-T_USB_Devices)

However I am reluctant to try the em2880 driver because installing it is much more complex than the Freecom & Hauppauge devices I got working before (just add firmware to  /lib/firmware  and away you go) - and it doesnt even mention my device - 


Things I tried so far

**lsusb** 
2304:022b Pinnacle Systems, Inc. [hex]
(Googling for that didnt find anything - maybe its new)

**dmesg | grep dvb** 
nothing at all.

Why is it that other DVB sticks are understood by dmesg, even when the correct firmware is not present (at least you get sensible error messages) whereas this one does nothing?

Did anyone else try this device and get it working?

spegru

---

### Post by nosami on 2008-01-21
I'm in the same boat. See here [http://www.linuxtv.org/wiki/index.php/AF9015](http://www.linuxtv.org/wiki/index.php/AF9015)

---

### Post by spegru on 2008-01-21
the link was empty.......

PC world currently has piles of these sticks at arounf £25. Must be loads of people with it ......

---

### Post by spegru on 2008-02-02
Gave up on this and swapped it for a Hauppauge one for £29 - which works fine.

---

### Post by unlotto on 2008-06-14
There's a development driver in the works at [http://linuxtv.org/hg/~anttip/af9015/](http://linuxtv.org/hg/~anttip/af9015/)

I can't get it to tune, but I did succeed in compiling the driver, and getting all the necessary /dev/dvb stuff. 

I posted some info about it here [http://linuxtv.org/wiki/index.php/DVB-T_USB_Devices#Currently_Unsupported_DVB-T_USB_Devices](http://linuxtv.org/wiki/index.php/DVB-T_USB_Devices#Currently_Unsupported_DVB-T_USB_Devices)

Support must be just around the corner.

---

