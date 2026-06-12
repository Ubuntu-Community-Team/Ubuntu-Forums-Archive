---
title: "Gap around maximized terminal window?"
date: 2011-04-15
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by r-senior on 2011-04-15
I'm not sure where to report this, so looking for a pattern as to where it does and does not happen.

When I switched to the Nouveau drivers on my desktop, there was an update to Terminal around the same time that brought in styled tabs and scrollbar. Since then I find that maximizing the terminal window leaves a gap of about 5-10px around the body of the window, most noticeable between the top of tabs and the global menu.

On my laptop, also running Unity works OK. The difference being the graphics card and drivers. So I suspect Nouveau.

Can anyone confirm similar problems, maybe establish a pattern and I'll file a bug?

---

### Post by rbrick49 on 2011-04-15
yes the first screen shot is your unity apps bar on the left the second screen shot is with your apps bar hidden and the space on the right hand side is a scroll bar keep playing with it you will get the hang of it

---

### Post by rbrick49 on 2011-04-15
heres a screenshot of mine now this is on a hp 23 inch widescreen if you click in left top corner your aps bar will appear or hide good luck

---

### Post by ricsi-pontaz on 2011-04-15
For me it is okay (gts250, nvidia blob):

---

### Post by r-senior on 2011-04-15
> **rbrick49 said:**
> ... the space on the right hand side is a scroll bar keep playing with it you will get the hang of it
Thank you. Yes, I will keep working at the scroll-bar until I become more proficient. ;)

It's the gaping hole between the top of the tabs and the global menu that I believe is a display bug. Anybody tried it with the Nouveau driver?

---

### Post by tormod on 2011-04-15
Just tested this on a Quadra NVS 160M card, in a live session after installing libgl1-mesa-dri-experimental from universe. There was no gap nor white borders, everything looks fine.

But I get these X/compiz freezes that I have seen on ati and seen reported on intel as well...

---

### Post by mc4man on 2011-04-15
Your second screen looks a bit different than expected with a close button on the right - did you customize a theme?
(noticed earlier that the white border can appear with some theme edits

---

### Post by r-senior on 2011-04-15
No theme customization, just standard Ambiance (with Faenza icons but I get the same without). The 'X' is the "Close Tab" button on the right side of a tab (File -> Open Tab), and the gap is between the top of the tab and the global menu.

I think I may have cropped those screenshots a little too much. ;)

The gap is really a gap - transparent. It's only white on my screenshots because there's another window maximized behind it.

---

### Post by r-senior on 2011-04-16
Ended up doing:

```

$ unity --reset

```

This solved it but I don't know which setting was the culprit. Probably messed something up when I was playing around with a white window problem.

---

