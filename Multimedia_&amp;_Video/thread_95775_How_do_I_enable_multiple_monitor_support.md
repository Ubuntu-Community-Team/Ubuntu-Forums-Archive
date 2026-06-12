---
title: "How do I enable multiple monitor support"
date: 2005-11-27
forum: Multimedia &amp; Video
---

### Post by CarnMeynen on 2005-11-27
Hi Folks

How do I enable multiple monitor support in Ubuntu? I have a desktop machine with 3 monitors plugged into 3 ATI graphics cards, but only the primary monitor is used by Ubuntu.

TIA

---

### Post by autocrosser on 2005-11-27
If you take a look at some of my older posts--I discuss various Xorg Configurations---You will need to modify your xorg.conf (located in /etc/X11/xorg.conf) to reflect your installed cards & monitors.

First know exactly your card types & monitor specs--If you search back thru the forums you will find a wealth of information on the subject:smile:

---

### Post by CarnMeynen on 2005-11-30
Well, all three monitors and graphics cards are identical so I suppose it is straight forward.

---

### Post by autocrosser on 2005-11-30
So you will need to know the PCI slot addresses for the cards--I'd use the Xorg.conf you have as a starting point--add the other card addresses & rename the cards like ati1-ati2-etc--then attach a monitor to each card--include the spec for the monitors (refresh-etc) & the last part would to enable Xinerama (right of-left of). You will find one of my posts involving dual cards & dual monitors--just expand on that:smile:

---

