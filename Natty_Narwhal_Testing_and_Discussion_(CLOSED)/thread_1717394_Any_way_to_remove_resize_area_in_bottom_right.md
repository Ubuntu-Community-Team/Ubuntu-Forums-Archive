---
title: "Any way to remove resize area in bottom right?"
date: 2011-03-29
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by anders_c_ on 2011-03-29
Is there any way to remove that resize thing in the bottom right, I think it looks hideous with some applications and i never use it.

---

### Post by papibe on 2011-03-29
Could you post a pic?
Regards.

---

### Post by mc4man on 2011-03-29
I believe that may be done in gtk (resize_grip), though not 100%. If so it would be a bit of work to remove from the source and have a workable install
(In gtk+3, patched into gtk+2
The only time I even notice here is using a terminal without scrollbar, - stays a solid white rather than blend in
(using ambiance borderless

---

### Post by mc4man on 2011-03-30
While with the light thems the grip area is generally hard to see, did notice a few things.
Obviously a transparent terminal with no or moved to left side scroll bar looks weird. (screen 1

Also it tends to cover the bottom of a scroll bar when there is no bottom 'border' area like you can have in firefox, actually makes using the bottom arrow not easy (screen 2

So with a minor edit to the gtk source, (not a source one would want to mess with too much), made the grip area 'go away', not particularly as something I'd do in a real install, but more as to how I'd like it to look in these situations
(though in the light themes there is no need for this grip area anyway.

Will edit in same screens from other install where I made the change

Somewhat feels like a bug - covering part of scroll bar and the terminal deal, though have no inclination to pursue

---

### Post by anders_c_ on 2011-03-30
Thanks! I was hoping it was just a setting somewhere, don't think I will edit the source.
And I agree that it looks buggy when there's no bottom bar.

---

### Post by mc4man on 2011-03-30
> **anders_c_ said:**
> Thanks! I was hoping it was just a setting somewhere, don't think I will edit the source.
And I agree that it looks buggy when there's no bottom bar.

At this point probably best to leave alone - though I've gotten to like not seeing that triangle in firefox and certainly in terminal.

Will kept around here for the moment and may  revisit around release - other than that the build takes some time and a fair amount of build-deps (200+MB), quite easy.
Out of 3 ways i saw to do went with making no changes at all except to the size of the grip. So it's still being drawn, atm it's only 1x1.

---

