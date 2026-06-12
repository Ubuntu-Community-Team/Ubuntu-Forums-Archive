---
title: "Very low audio gain"
date: 2009-06-26
forum: Mythbuntu
---

### Post by GuiGuy on 2009-06-26
Hi,
Audio gain on my mythbuntu box has always been very low (~18months), but I've put up with it thinking things could only improve.

Howvever, since the recent updates that involved kernel 2.6.28-13, audio levels are now so low that the amplifier has to be cranked up to max to be able to hear anything at all. 

Relevant mixer gains and the gain in the frontend configuration are maxed as well.

I am at the point of switching distros (the problem doesn't exist in mythdora), but of course would try any reasonable suggestion first if anyone has one.

---

### Post by AKADAP on 2009-06-27
I don't know how to help you. On my system, mythTV is always 10 dB lower than anything else. I'd like to see a fix as well.

---

### Post by mathog on 2009-06-27
> **GuiGuy said:**
> Hi,
Audio gain on my mythbuntu box has always been very low (~18months)

Run whatever mixer applications you have and be sure all the output devices are all the way up and are not muted.

There is also an initial volume setting somewhere or other in mythtv or mythtv-setup, find it and make sure it isn't set to a low value.

That said, the sound output level from my mythtv box is much lower than from other devices (a DVD player and a VCR).  They all feed into one analog TV, and the sound level on the TV for Mythtv has to be around 38 to match the loudness of the other two at around 25.

---

### Post by GuiGuy on 2009-06-28
> **mathog said:**
> Run whatever mixer applications you have and be sure all the output devices are all the way up and are not muted.


As stated in th OP, that's done and confirmed. VLC and XINE produce reasonable sound levels.

> 
That said, the sound output level from my mythtv box is much lower than from other devices (a DVD player and a VCR).  They all feed into one analog TV, and the sound level on the TV for Mythtv has to be around 38 to match the loudness of the other two at around 25.
[/QUOTE]

In some ways that is correct. The issue might appear to be in MythTV's internal player.

However, a number of things have started to really annoy me with Ubuntu so I have replaced the mythbuntu box with mythdora. The gain is back up.

Cheers

---

