---
title: "Brasero loads plug-ins then exits - never shows gui"
date: 2012-04-10
forum: Multimedia Software
---

### Post by EarlsFurniture on 2012-04-10
I have tried repeatedly, either using the menu under Applications -> Sound & Video, or via command line, and the results are the same:  nothing. No GUI ever shows up.

If I issue ```
brasero -g
``` I get a long listing of what looks like brasero loading plug-ins and checking to see what the hardware can handle, then it just stops.

No errors.  Nothing.  It just exits.

I've tried ```
sudo apt-get remove brasero --purge && sudo apt-get install brasero
``` to no avail.

Note, if I insert a blank disc I do get a pop-up asking me what I want to do (burn a disc, etc.) but that only allows me to drag and drop files in nautilus and make data DVD's or CD's.  I can't get the gui which allows me to create projects, specifically video DVD's that will play on a DVD player. (I have dvdauthor and ubuntu-restricted-extras installed)

```
brasero --video
``` does nothing.

```
brasero --empty
``` does nothing.

Any ideas?


Update - 5/16/2012

It seems a reboot did the trick.  I'm not sure why it wasn't working before.  In fact, it NEVER worked in over 2 years, even after the initial fresh install.  I just got around to looking for a solution.  But lo and behold, a reboot after a kernel update fixed it!

---

