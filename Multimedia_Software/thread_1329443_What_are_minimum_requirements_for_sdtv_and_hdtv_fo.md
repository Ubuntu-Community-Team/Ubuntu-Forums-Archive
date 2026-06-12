---
title: "What are minimum requirements for sdtv and hdtv for a video card?"
date: 2009-11-17
forum: Multimedia Software
---

### Post by mulluysavage on 2009-11-17
I'm trying to build a mythtv box from as close to trash as possible. I would like to use a processor that can't handle video and use a video card that can - so what are the specs needed for standard definition and HD to be able to display video out to s-video? I'm playing with a WYSE 9450XE winterm with one pci slot.

---

### Post by ozzman2 on 2009-11-17
I would love to know the answer to this too.  (anybody???)

From what I've read so far, the Nvidia cards work better with Ubuntu than ATI cards.  I'd like to build an HTPC (that handles HD video).  I'm not so concerned about the cost as I am with keeping the heat and noise down.  Don't need the latest and greatest card for gaming, just want it to handle High Def video.

Is there such a thing as a video card *and* _open source driver_ that will handle HD in Ubuntu?  If not, does anybody have any recommendations on a video card "just good enough" for HD content?

Thanks


:popcorn:

---

### Post by beerse on 2009-11-20
> **mulluysavage said:**
> I'm trying to build a mythtv box from as close to trash as possible. I would like to use a processor that can't handle video and use a video card that can - so what are the specs needed for standard definition and HD to be able to display video out to s-video? I'm playing with a WYSE 9450XE winterm with one pci slot.

As far as I know those wyse winterm stuf, that is not even a decent pc in its time. You want to use it for mythtv? Mythtv can be seen in the next parts:
- a back-end that act as receiver, recorder, transformer and storage. I donnot think your wyse machine can handle that.
- a front-end, that acts as the monitor/controller, the one connected to the display. This wyse might be able to do this. See if you can hook a dvd to it and get that playing. If it can play the dvd, then you should be able to use it as front-end.

If you can get the wyse boot from cdrom (or usb) get hold of a mythbuntu image and boot from that to see if it is of any use.

---

### Post by xzero1 on 2009-11-20
You will want hardware video acceleration built into the motherboard for lowest heat generation. I have used a motherboard with an onboard ati 3300IGP and had no problems playing any HD video I could throw at it. Now, this was with the fglrx driver and there were various tweaks in xorg that had to be done.

At this time, Nvidia might be a better bet but Ati might get there faster for an open source driver. As I understand it there is already some video acceleration in the radeon drivers but it is in their future plans.

BTW, you can't play HD video via s-video unless it is downconverted to 480.

See post #23 in this thread:
[http://ubuntuforums.org/showthread.php?p=8347605#post8347605](http://ubuntuforums.org/showthread.php?p=8347605#post8347605)

Current open source radeon driver status:
[http://xorg.freedesktop.org/wiki/RadeonFeature](http://xorg.freedesktop.org/wiki/RadeonFeature)

---

### Post by mulluysavage on 2009-11-22
Okay, let's look at it this way:

I want to use a cpu that probably can't handle video. If I was going to have my video card handle the video would this mean hardware acceleration? What are the featres of the card that I need to look for to handle video without help from the cpu? memory? clock speed? other specifications?

---

### Post by xzero1 on 2009-11-22
Unlesss the card has specific hardware for HD video you will not be able to play HD content this without a powerful cpu.

---

