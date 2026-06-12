---
title: "[SOLVED] Good cheap PCI card for twin 1440x900 LCDs ?"
date: 2007-06-27
forum: Multimedia &amp; Video
---

### Post by neilb on 2007-06-27
Hi

I'm trying to use a 1440x900 LCD monitor with my Dell Dimension 3100 (Ubuntu 7.04 with KDE).

The motherboard has a built in Intel Graphics Accelerator 900 which doesn't seem to do 1440x900, so I'm considering filling one of the spare PCI slots with a graphics card (not AGP or PCI-Express).

Can anyone recommend a cheap PCI card which will support twin 1440x900 monitors ?

Thanks

---

### Post by reclusivemonkey on 2007-06-27
What's your budget?

What country are you buying in?

I'd certainly recommend getting a Nvidia card.

---

### Post by neilb on 2007-06-27
> **reclusivemonkey said:**
> What's your budget?

cheap-ish :) i'd rather get it from a scrapped machine but there are none to hand at the moment.  i certainly don't need cutting edge.

> **reclusivemonkey said:**
> What country are you buying in?

uk

thanks

---

### Post by reclusivemonkey on 2007-06-27
> **neilb said:**
> cheap-ish :) i'd rather get it from a scrapped machine but there are none to hand at the moment.  i certainly don't need cutting edge.

uk

thanks

I had a quick look on Google products; it seems all the nvidia pci cards are pci express. I would say your best best it eBay (new cards are £20, so don't pay a lot). Alternatively, if there are any computer recycling centres around your area you could try there.

---

### Post by bigken on 2007-06-27
why don t you look at ebay its full of old pci graphic cards I would imagine it would only cost you about £20 but doubt it would support duel monitors

oops too slow lol

---

### Post by bigken on 2007-06-27
just had a quick browse on ebay matrox pci cards average about £15 with duel monitor support ;)

---

### Post by neilb on 2007-06-27
ok thanks

looks like i have a bit of digging to do if this machine's going to get two monitors running

---

### Post by neilb on 2007-07-11
i found an ATI Radeon PCI card for £16 which fits perfectly and found out why a back up of xorg.conf is a wise thing - after fitting the card and rebooting the machine, x vanished :(

lspci showed that the graphics controller defined in xorg.conf had shifted to a different bus address, so i restarted in safe mode and ran

$ sudo apt-get install xorg-driver-fglrx
$ sudo dpkg -reconfigure xserver-xorg
$ lspci

and noted the pci bus address of the card and checked that the correct driver and PCI address were listed in /etc/X11/xorg.conf.  they weren't, so i changed them and x came back

(there is a bit of difference in how PCI bus addresses are listed in different files - lspci reports 0000:00:02.0; xorg.conf expects PCI:0:2:0, so 0000:03:01.0 would become PCI:3:1:0)

---

