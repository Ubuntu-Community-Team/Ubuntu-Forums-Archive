---
title: "Plugged in network cable *BOOM*, what happened?"
date: 2013-02-09
forum: Networking &amp; Wireless
---

### Post by OrangeVixen on 2013-02-09
I'm not that all experienced with network/hardware and thankfully this happened to a Windows computer.

I plugged a 10Mbit cable from a switch to a Windows computer that needed to use the net, as soon as I plugged it in, there was a spark, and a *BOOM* not a loud boom but like a boom/pop kind of sound.

The computer was off and unplugged, I think I plugged in the network cable first, was I not suppose to do that?

Anyways, the motherboard was fried and I had to replace it, now its working again and I was wondering what is the correct way to plug in a network cable? or did something else happen to cause all this?

---

### Post by tgalati4 on 2013-02-09
Newer routers have Power-over-Ethernet (PoE) and they send 5 or 12VDC down the pairs.  Newer network cards have isolators so that the DC voltage is blocked and the AC network signals pass through.  I'm guessing that the old 10BaseT card was not isolated (because is was before PoE was even thought of) and zap goes the motherboard.  Most routers with PoE can be turned off on a port-by-port basis, but you need to log into the router to do this.

Of course, it could be something else.

---

### Post by OrangeVixen on 2013-02-11
Ah I see, that is probably what happened.

It was a switch actually, not a router, and it does have power, though it's plugged into A/C.

The motherboard had a built in ethernet card and it was made in 2006.

The switch is a 1GB, sorry about the confusion, it was made this year, so maybe that was the cause.

---

### Post by tgalati4 on 2013-02-11
2006 is relatively new, and the ethernet port should be isolated, but if there was a bad or shorted cable, or a bad crimp, that could blow something.  Realize that all computers made in 2004 to 2006 are suspect to bad capacitors and bad soldering.

---

### Post by OrangeVixen on 2013-02-12
Maybe it was because it was not grounded? The computer was not plugged in (PSU-wise) and the ethernet card was plugged in first.

It's in LA and you are there too, you know how dry and staticy it is lately here.

---

### Post by tgalati4 on 2013-02-12
Static electricity would cause a slight shock, but if you heard something pop, that would require some current.  Was the machine plugged in, then unplugged recently?  The capacitors would hold on to current for a while.  Does that switch port still work with other machines?

---

### Post by OrangeVixen on 2013-02-13
> **tgalati4 said:**
> Static electricity would cause a slight shock, but if you heard something pop, that would require some current.  Was the machine plugged in, then unplugged recently?  The capacitors would hold on to current for a while.  Does that switch port still work with other machines?

The computer was moved from one room to another, it was plugged in, so yes it probably did have some current in the Motherboard's capacitors.

The switch is still working, the router is a Linux box and most of the computers connected to it are iMacs.

---

