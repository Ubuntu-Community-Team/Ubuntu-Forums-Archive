---
title: "How Good is Wireless Support?"
date: 2005-12-10
forum: Networking &amp; Wireless
---

### Post by Orporg on 2005-12-10
I can't help but get the impression from reading this forum that the wireless support in Ubuntu/Linux is... not yet ready for prime time.  Is this basically correct or am I getting an incorrect vision of Ubuntu here?  I also ask because I'm hoping to borrow another wireless card to see if I can get it working but I'm not sure if there's much point.

---

### Post by Rinzwind on 2005-12-10
My wireless worked out of the box so I needed zero support on it.
What kind of support do you expect that specifically addresses wireless? Cuz it's just another piece of hardware and another way of setting up a network.On these forums people always help, even with wireless networks ;)

I'm happy cuz I have kwifimanager for my own connection (shows speed etc), wifiradar (to scan for wireless metworks).

---

### Post by matthew on 2005-12-10
[quote=Orporg]I can't help but get the impression from reading this forum that the wireless support in Ubuntu/Linux is... not yet ready for prime time. Is this basically correct or am I getting an incorrect vision of Ubuntu here? I also ask because I'm hoping to borrow another wireless card to see if I can get it working but I'm not sure if there's much point.[/quote]It really depends on the wireless card. Some manufacturers don't make drivers for Linux at all and at the same time won't even release the technical specifications for their hardware so that someone else can write the drivers. In those cases the wireless cards may not be able to be made to work. In some instances it is possible to use the Windows driver for the wireless card with a program called "ndiswrapper" and get the wireless card working. A quick forum search should help you with that.

There are some wireless cards that will work right out of the box with Linux. My Intel ipw2200 worked perfectly upon install. It took a little research on these forums to get WPA encryption working, but even that wasn't difficult.

Ultimately, this isn't just an Ubuntu thing, it's a Linux-wide issue. Until hardware manufacturers choose to make Linux drivers available for their products or at least release the specs necessary for someone else to write them it is best to do your research up front and find out if the hardware you are considering is already known to be compatible.

---

### Post by taurus on 2005-12-10
I have a Linksys WPC54G v2 (pcmcia) and it works just fine (on a HP laptop) with the driver that I downloaded from Linksys' site using ndiswrapper.

---

### Post by dubz on 2005-12-10
many wireless devices use the prism drivers. i was surprised when my senao usb wireless card worked semi-perfectly.....

---

### Post by az on 2005-12-10
Wireless is always a pain.  Even in Windows.  I have found wireless to be less wonky in linux, though - even with the chipsets that require you to use ndiswrapper. The catch is that you need to use the latest version of the windows driver (the one that comes with your device may be too old.  The ndiswrapper developers always have the latest versions to work with.)

But a surprising number of devices have out-of-the-box support.  You do not even need your driver disk or anything.

---

### Post by Orporg on 2005-12-10
I can't seem to get my wireless working and I think the people on the forums have given up on me (I can't blame them).  

I understand about the drivers issue.  It doesn't make that much sense to me though.  I would think the hardware manufacturers would be happy to have people write drivers for them, for free.  And if there is a driver that will simply increase their user base.  If you can get a cut of the Linux market, without having to pay programmers to write drivers for you, I would think it makes good businesse sense to release tech specs.

However.... I do think that not having easy wireless support is a fairly big blow to the OS.  I realize it's not the Linux developers fault and probably nothing can be done about it.  But it does seem like a rather large hole.

---

### Post by matthew on 2005-12-10
[quote=Orporg]I understand about the drivers issue. It doesn't make that much sense to me though. I would think the hardware manufacturers would be happy to have people write drivers for them, for free. And if there is a driver that will simply increase their user base. If you can get a cut of the Linux market, without having to pay programmers to write drivers for you, I would think it makes good businesse sense to release tech specs.[/quote]
I agree with you. I wish the hardware folks could realize that as well.
>  However.... I do think that not having easy wireless support is a fairly big blow to the OS. I realize it's not the Linux developers fault and probably nothing can be done about it. But it does seem like a rather large hole.Yeah. It's a known hole, though, and it is being worked on as quickly and in as much detail as is possible. I heard that the Broadcom chip drivers have been reverse engineered recently (not by Ubuntu, but by some Linux lovers) and that drivers for them are in the process.

Drop by drop the river overflows.
-Arabic proverb

---

### Post by Orporg on 2005-12-10
Are there other distros with better wireless support?  I want to use Linux and I want to use Ubuntu but I simply can't without wireless.

The worst part is that my D-link card is supposed to be supported out of the box, according to the wiki.

---

### Post by az on 2005-12-10
[QUOTE=Orporg]Are there other distros with better wireless support?  I want to use Linux and I want to use Ubuntu but I simply can't without wireless.[/QUOTE]

I do not think so.

[QUOTE=Orporg]

The worst part is that my D-link card is supposed to be supported out of the box, according to the wiki.[/QUOTE]

What kind of card?

---

