---
title: "Amarok - probably a little bug"
date: 2008-07-15
forum: Multimedia Software
---

### Post by houbysoft.xf.cz on 2008-07-15
Hi all, I think that I have found a little bug in Amarok. You know the blue "popup" or how to call it that is showed when a song ends for providing you with the name, album, album art, etc.? It has a little transparency, and so you see what's under it, but if you move the window that is under it, the popup still shows the same thing, it doesn't notice the move of the window.

I know this almost hasn't got any importance, but it sure would be another step to perfection if someone would fix it :)

---

### Post by Shunsuke_01 on 2008-07-15
I notice the same thing too. Sadly, I can't do anything about it. I hope someone else can follow it up though. :)

---

### Post by gnuvistawouldbecool on 2008-07-15
I would say that it isn't so much a bug, as an unexpected occurrence.  

See, the program will be written such that the transparency will be worked out by Amarok, and will display that so that it looks nice and transparent.  After that though, considering that it's only there for a few seconds, the transparency will be the same as at the start, since there is no real need to change the appearance.  

As a moving window 'under' the OSD changes position, to implement what you want, would have to return an interrupt to Amarok, telling it that the window transparency will need changing and to do that.  Which then uses processor power each pixel moved, for something that isn't really needed, and also what if the OSD isn't there?  Then it doesn't need to check if it's moved, but it needs to know whether the OSD is there or not.

A different method would be simpler, as only Amarok would need to do much, by Amarok checking every 1/50 seconds if anything moved underneath it, and if it has to update the transparency, but that's a lot of processor time used to do that.

Remember, a jpg image might be small, only 1 MB for a 5 megapixel image, but the graphics card will extend that to say 15 or maybe 20 MB for actual display.  the OSD won't be that big, but it would take a fair bit of resources to change itself every 1/50 of a second or so to ensure it appears truly transparent.  On a high end comp that could be good, but otherwise it would really be overkill.



PS, I think that's how it could/would work.:P

---

