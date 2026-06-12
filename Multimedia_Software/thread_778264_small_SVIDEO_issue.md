---
title: "small SVIDEO issue"
date: 2008-05-01
forum: Multimedia Software
---

### Post by jimoz on 2008-05-01
Hi all

Ive been using my laptop to play movies via the tvout/svideo plug, on an nvidia geforce go 7300. Currently using 8.04. Only issue I have is that you have to either disable the primary (laptop) display or at least reset the resolution to match the tv (and then vice versa when finished). What I would like is to be able to use the tv-out option in totem, so that i dont have to mess around with the nvidia settings each time - just let it pipe the movie to tv direct. At the moment, the option is disabled (ive tried nvtv, and messing with nvidia settings). I dont have to use totem if another player will accomplish this.

BTW, what would be really nice would be something like a compiz backend that could pipe a selected window straight to tvout, whether it be movie/image/etc. 

Any ideas?

---

### Post by CarpKing on 2008-05-02
I don't use nVidia, but for ATI I installed gxvattr, which lets me set which screen to display the Xv overlay on.  MPlayer then fullscreens to the size of whichever screen that is (using clone mode in XRandR).  This program says it's for Radeon, but you should look through whatever settings program you have for an option related to "video overlay" or something.  It might by pretty cryptic; gxvattr calls it "Xv_DEVICE_ID."

---

