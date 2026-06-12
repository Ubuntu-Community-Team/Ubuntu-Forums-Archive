---
title: "Questions/Help on identifying Hauppauge tuner card"
date: 2008-10-23
forum: Mythbuntu
---

### Post by CGW on 2008-10-23
I've both searched this board and Googled for this info...but so far no luck.  What I have found has been contradictory.  So hopefully someone here will be able to answer these questions.

First off, I purchased this card used from a guy I know.  

[IMG]http://www.shspvr.com/pvr_model/haup_freestyle_rev2.jpg[/IMG]

He claimed this was a PVR-250.

My questions are:  Is it really?  And if it is, does *this* version support hardware encoding under Mythbuntu?

Thanks in advance.

---

### Post by ian dobson on 2008-10-23
Hi,

Came across this

> There use to be lots of the 250's and 350's on eBay.
Not anymore. (gratefully I bought 3 of the "48432" versions for my Myth box.)

The 48432 is an OEM version that was bundled with HP boxes, if memory serves me.
This was causing some confusion for buyers, but was a great way to pickup a 250 for half the cost.

and [http://www.shspvr.com/smf/index.php?topic=8847.0](http://www.shspvr.com/smf/index.php?topic=8847.0)

So it looks as if it's an OEM version of the PVR-250 with a hardware MPEG encoder onboard.

Regards
Ian Dobson

---

### Post by CGW on 2008-10-23
Thanks for the help!

It's JUST a encoder and not a decoder...right?

How much does software decoding task a system?

---

### Post by anonymousdog on 2008-10-23
Even fairly low powered systems will smoothly decode SD recordings, especially if they have nVidia graphics that can do XvMC.  It's usually a good idea to experiment with different playback profiles and deinterlacing methods to get the best results on low-power machines.  I have a P3 866 box with 512MB SDRAM that performs beautifully as a diskless frontend using the CPU-- playback profile and XvMC.

---

### Post by CGW on 2008-10-23
The box I'm building is a P4/3GHz/1GB RAM.  The only thing I wasn't sure about was the tuner card.  I ended up with this one after being mislead.  The seller told me this was both a encoder and decoder card.  Which is why I was asking.

Thanks again

---

### Post by newlinux on 2008-10-23
I don't think the PVR-250 have any decoding, but with a 3GHz P4 you don't need it. My P4 3Ghz decodes HD just fine without XvMC. This card just does analog SD signals.

---

### Post by CGW on 2008-10-23
Awesome...thanks for the help.
:guitar:

---

