---
title: "Video cards for cable DVR functionality"
date: 2011-02-02
forum: Mythbuntu
---

### Post by SpartanB312 on 2011-02-02
Hi all- I'm new to Mythbuntu, though I've been using Ubuntu for several years now and love it. One of my personal projects for this year is to build a home theatre PC and run an open-source system on it, thereby getting rid of expensive (and annoying and unreliable and ad-filled) proprietary cable-company DVR solutions and eliminating the need for an Xbox LIVE Gold subscription. I suspect that part or all of the questions I'm about to ask have been answered before, so I apologise in advance if this is merely repeating old questions.
 
My questions concern the kind of video card required for an HTPC setup to record, transcode, and play programs recorded from cable or satellite set-top boxes. Currently my home DVR (for which I'm paying way more than I'd like) allows me to record two programs simultaneously, and I can record a show on one channel while watching a show on another channel. From my limited understanding of PVR cards, this requires multiple PVR cards and not all PVR cards will offer the ability to record one show while watching another.
 
Therefore: what PVR cards can be recommended in order to create an HTPC that essentially functions like a TiVO box? What kind of motherboard/processor/specs would be required to support these cards? Finally, and most importantly, can Mythbuntu support these cards?
 
Again, my apologies if this has been asked before; thanks for your patience and suggestions.

---

### Post by nickrout on 2011-02-02
If the STB's are Hi Def then your only option is the HD-PVR.

If they are Std Def, then any linux compatible analogue card should be fine.

---

### Post by SpartanB312 on 2011-02-04
Hi nickrout- the set-top box is indeed an HD box. This would mean that the only PVR cards that I can buy would be the Hauppauge HD card and other similar cards, correct? Does the Mythbuntu kernel handle the Hauppauge PCI cards, such as the WinTV-HVR-1250?

---

### Post by nickrout on 2011-02-04
If you want to capture from an STB in HD your ONLY choice is the HD-PVR, which is a USB device. [http://www.mythtv.org/wiki/Hauppauge_HD-PVR](http://www.mythtv.org/wiki/Hauppauge_HD-PVR)

Hauppauge have also recently released an internal HDPVR. It does not presently work in mythtv.

[http://www.gossamer-threads.com/lists/mythtv/users/470753](http://www.gossamer-threads.com/lists/mythtv/users/470753)

---

### Post by LowSky on 2011-02-04
hdpvr is the only way to go if you want hd cable box recordings.

if yuo really only watch and record the local channels like nbc, cbs, abc, and fox, then you can get an internal card and do QAM recordings.

you can also do sd quality recording using hte cable box's coax but its not worth the trouble.

---

