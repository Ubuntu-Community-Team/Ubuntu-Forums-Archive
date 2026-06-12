---
title: "More ATI woes - X 200G integrated AMD64."
date: 2006-06-06
forum: Multimedia &amp; Video
---

### Post by Frank-Hamersley on 2006-06-06
Have been trawling the forums but have not found an exact instance that matches my situation...I have installed Dapper 64 bit to a HP dx5150 AMD system which has the ATI X200G mobo chipset for graphics.  I have an LG 32LX2D HDTV connected usingDVI-D to HDMI.  There is a DVico DVB-T Dual installed but not yet functional (I'm guessing that it is PCI device 3:10:0).

Every time I try to switch to the fglrx driver (distro supplied) my system locks up (caps lock unresponsive) and I have to boot in maint mode to switch back to the ati driver.  Symptoms are ... all looks good until X is loaded, at which point the screen goes blank (monitor then reports no signal).  The system still produces the audio (drum roll) as if it has presented the login prompt but crashes shortly after that.

There is not much nasty stuff written into the attached logs although I did notice the following that seemed a bit unusual ...

(--) PCI:*(1:5:0) ATI Technologies Inc RS480 [Radeon Xpress 200G Series] rev 0, Mem @ 0xd0000000/27, 0xfdbf0000/16, I/O @ 0xcc00/8
(--) PCI: (1:5:1) ATI Technologies Inc unknown chipset (0x5854) rev 0, Mem @ 0xc8000000/27, 0xfdbe0000/16
(--) PCI: (3:10:0) unknown vendor (0x14f1) unknown chipset (0x8800) rev 5, Mem @ 0xfc000000/24
[snip]
(II) Primary Device is: PCI 01:05:0
(II) ATI Proprietary Linux Driver Version Identifier:8.25.18
(II) ATI Proprietary Linux Driver Release Identifier: LGDr8.25g1                           
(II) ATI Proprietary Linux Driver Build Date: May 18 2006 09:58:41
(II) ATI Proprietary Linux Driver Build Information: autobuild-rel-r6-8.25.1-driver-lnx-x86_64-268237
(WW) fglrx: No matching Device section for instance (BusID PCI:1:5:1) found
(--) Chipset RADEON XPRESS 200 (RS480 5954) found

So what is PCI:1:5:1? Is it bogus? Is it the other mobo VGA connector?  

Should I think about pulling the DVico?  BTW I will try using the VESA driver before doing that.

Any other suggestions?

Cheers Frank.

---

### Post by bjtuna on 2006-06-07
Another thread on this topic already exists, but no solution yet. I'm starting to think we need to wait for the new ATI drivers. 

[http://ubuntuforums.org/showthread.php?t=187074](http://ubuntuforums.org/showthread.php?t=187074)

---

### Post by Frank-Hamersley on 2006-06-07
OK - switching to the vesa driver stops the total system lockups - but X itself is unreliable - crashes as soon as I log in.

No log messages from what I can find.  Is there a debug switch to get more info as it crashes?

Cheers, Frank.

---

### Post by redhed on 2006-09-27
> **Frank-Hamersley said:**
> Should I think about pulling the DVico?  BTW I will try using the VESA driver before doing that.


I had the same problem, so I pulled my DVICO card. Has anyone found a workaround to use the DVICO and ATI cards together? For me vesa and ati drivers also do not work. I don't get the hard lockup that I get with fglrx, but basically I get a completely garbled display.

I have tried Edgy, Dapper and Breezy all with the same outcome.

Dan

---

### Post by Frank-Hamersley on 2006-10-02
I have been diverted to other activities so haven't devoted any time to this for a bit - hopefully I will get a chance this week!

Cheers, Frank.

---

### Post by Ragnarol on 2006-10-03
The blank screen problem is fixed usually disabling dri in your xorg.conf or changing the card setup in the bios to use both UMA and Sideport memory, maximum external memory.

good luck!

Anyway, DRI does not work on HP notebooks (almost all of them) unless you use driver 8.24

---

