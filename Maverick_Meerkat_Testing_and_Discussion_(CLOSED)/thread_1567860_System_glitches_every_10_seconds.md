---
title: "System glitches every 10 seconds"
date: 2010-09-04
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by teachop on 2010-09-04
Test-running the beta on a new Dell E6510 with i7 and nvidia.  The user interface has a pause every 10 seconds for a split second, which causes mouse movement, typing characters, scrolling etc to all stop.  The blips are enough to be pretty annoying.

The Dell laptop doesn't do this with 10.04.  The beta installed on my older Sony doesn't do this.

It is clearly visible in the System Monitor Resources tab, where a blip takes place on one thread every 10 seconds on the graph while the rest are mostly idle.  Most blip to 40%, sometimes it goes to 100%.  Nothing corresponding is visible in the Processes tab - must be too quick for the refresh there.

I tried turning off everything I could in Startup Applications.  Any other ideas on how to narrow this down?

---

### Post by ranch hand on 2010-09-04
Try opening the terminal, maximize it, and run;
```

top

```
this is pretty much the same as "processes" but much more real time.

---

### Post by teachop on 2010-09-04
Using top provided for the identification, thank you.  It is called "kslowd001".  I found a bug report based on that, 595764, that seems to indicate it is fixed in 2.6.35-7 but I have -19 in the beta, so I don't think it is!

---

### Post by ranch hand on 2010-09-04
Did you add a comment to the bug?  Or maybe file a new one mentioning the old bug?  Not sure how you should handle this exactly but you need to report it one way or another.

---

### Post by teachop on 2010-09-04
Yes I did add a comment.  I don't know since the status is "Fixed" if it will raise any flags, not aware how that works in the bug system.  Knowing the name now, google shows a number of similar discussions in various other web-places.  They all look kinda stale by a month though, so that concerns me...

---

### Post by ktp on 2010-09-04
> **teachop said:**
> Yes I did add a comment.  I don't know since the status is "Fixed" if it will raise any flags, not aware how that works in the bug system.  Knowing the name now, google shows a number of similar discussions in various other web-places.  They all look kinda stale by a month though, so that concerns me...

I would write up a new one and reference the old one in the new one.

---

### Post by ranch hand on 2010-09-04
See there, some folks know how to deal with this.

---

### Post by teachop on 2010-09-04
This is new bug 630299 now.  Thanks.

---

### Post by teachop on 2010-09-11
This seems to be the same issue being worked on:

[https://bugs.freedesktop.org/show_bug.cgi?id=29536](https://bugs.freedesktop.org/show_bug.cgi?id=29536)

---

### Post by teachop on 2010-09-12
This is only happening when I use the nouveau driver, if I switch to the proprietary NVIDIA, it goes away (and there are much worse problems instead but that is another story).  Is anyone else experiencing this 10 second hicup in the mouse/ui with the nouveau driver in use?

---

