---
title: "Problem with using Freecom DVB-T USB with Hauppauge Nova-T PCI"
date: 2007-09-03
forum: Multimedia &amp; Video
---

### Post by oscarsfriend on 2007-09-03
Hi,

I've been successfully using a Freecom DVB-T USB tuner for some weeks now, and today I added a Hauppauge Nova-T PCI card as a second tuner.  Separately both tuners work fine, however, if I try to have the two tuners connected at once my Freecom tuner shows up twice as /dev/dvb/adapter1/ and /dev/dvb/adapter2/, and MythBackend activates the tuner on start up (yellow light on USB stick turns green).  Anyone have any ideas what's going on here, and how I fix it?

---

### Post by wieman01 on 2007-09-03
Wow, 2 adapters? Why is that? :-) No solution that I am aware of.

---

### Post by oscarsfriend on 2007-09-03
Not sure what happened, but I seem to have sorted it now.  I powered off and removed the PCI card then powered on again.  Again, my Freecom tuner showed up as two devices, however it appeared to work fine.  I powered down and inserted the PCI card again, then rebooted.  My computer is now showing two (instead of three) dvb cards, and the Freecom card is not being activated by MythBackend for no reason.

---

### Post by oscarsfriend on 2007-09-03
I spoke too soon.  The Freecom tuner is still being activated whenever MythBacend starts (it never did when I used it by itself).  It seems the tuner activating happens when I configure MythBackend to use the same source for the two tuners.  Again, anyone know what's going on?

---

### Post by oscarsfriend on 2007-09-03
Looks like I sorted it now.  I had to set an option for the card from MythSetup to only open the card on demand. :oops:

---

### Post by wieman01 on 2007-09-03
> **oscarsfriend said:**
> Looks like I sorted it now.  I had to set an option for the card from MythSetup to only open the card on demand. :oops:
Sure? ;-)

---

### Post by oscarsfriend on 2007-09-03
I shall find out in about three minutes when it starts (fingers crossed) recording two things at once.

EDIT: It worked.

---

