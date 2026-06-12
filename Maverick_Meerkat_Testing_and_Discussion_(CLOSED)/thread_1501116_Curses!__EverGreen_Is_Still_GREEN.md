---
title: "Curses!  EverGreen Is Still *GREEN*"
date: 2010-06-03
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by PGHammer on 2010-06-03
As expected, even with the latest in kernels (I'm actually running 2.6.35-rc1 from Lucid mainline, compiled just yesterday), AMD HD5xxx gets no respect from Maverick (as-shipped X is stable-but-slow, and there is no acceleration to be had any sort of way, because Catalysta Penguinista is still problematical with 2.6.34 or newer).  Amusingly, dropping back to HD3450 (with half the RAM) results in a performance increase.

Just goes to show; live on the Penguin Edge, expect to get ice sliced.

---

### Post by screaminj3sus on 2010-06-03
The open source drivers are still implementing important base features on cards older than evergreen, you shouldn't expect them to work that great with a 5xxx card right now even with maverick.

And you know ati's track record with supporting new kernels/xorg in their proprietary driver, they are always slow and it is to be expected. fglrx usually never works until well near the end of testing where we get a pre-release driver if we are lucky.

---

### Post by Seren on 2010-06-04
From the infamous Phoronix site:

[http://www.phoronix.com/scan.php?page=news_item&px=ODMwNg](http://www.phoronix.com/scan.php?page=news_item&px=ODMwNg)

Evergreen *basic* FLOSS support should not land in kernel before 2.6.36, so Ubuntu 11.04 at the earliest.

---

### Post by xeizo on 2010-06-04
I gave up well before Karmic, now it's Nvidia all the way on my Linux-boxes. It's a relief, even the latest GTX470 works flawlessly with the Nvidia proprietary driver  :)

Needless to say I wish ATI finds a better way of keeping their driver up to date, it would be nice to actually have a choice.

---

### Post by PGHammer on 2010-06-04
> **xeizo said:**
> I gave up well before Karmic, now it's Nvidia all the way on my Linux-boxes. It's a relief, even the latest GTX470 works flawlessly with the Nvidia proprietary driver  :)

Needless to say I wish ATI finds a better way of keeping their driver up to date, it would be nice to actually have a choice.

For Linux-only boxen, you may well have a point.

For too many of us, Linux-only is not possible (budget reasons), and Windows has a place (in some cases, place of primacy) on our hardware.  nVidia has too many issues on *Windows* for me to trust them there with latest-and-greatest (that is besides their hardware being pricier than equivalent AMD GPU hardware), and if you are willing to pay a premium for hardware due to their *Linux* support, then it kinda throws out the entire point of the Linux/FOSS argument.

This PC is multi-boot (Windows 7 and Kubuntu, both x64), but Windows has place of primacy (too much I *still* can't properly do on Linux).

Further, I did state that the state of Evergreen support was *expected*.

Unlike some, I don't expect to get away without cuts living on the bleeding edge; anyone that does is fooling themselves.  (And that includes those in politics.)

---

### Post by xir_ on 2010-06-05
evergreen support is still coming.

But your fall back card is now getting quite well supported.

Eventually ati will totally switch to gallium 3d for all their drivers and we will see a much simplified driver set with much faster development time.


Id suggest the catalyst driver for now on ati as it will keep you going. There just isn't really an alternative right now.

---

