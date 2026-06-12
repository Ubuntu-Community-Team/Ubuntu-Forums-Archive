---
title: "Menu size Mythmusic"
date: 2010-01-07
forum: Mythbuntu
---

### Post by DwalerXIII on 2010-01-07
I have a strange little problem. I'm running a fully working Mythbuntu-box.
But the menu (m-button)in Mythmusic became so small (text and window) I can't read it anymore. This was not the case in the beginning. 
How can I get it back to normal?
All other menus are fully readeble.

---

### Post by DwalerXIII on 2010-01-10
Plaese help! Does anyone know this problem?
All menu's are normal exept for the music. When I press the m-button looking at the playlist I get a very small menu. Everyting is in there but the frame and the font is so small I can't read it.

---

### Post by DwalerXIII on 2010-01-13
When the screenresolution is lowered too 800 x 600 the menu is clearly readeble. The full resolution of my TV is 1300 x 768. In this resolution the menu's in mythmusic are too small to read. I tried with different themes but with the same result.
All other menu's have normal size in all screenresolutions.

Has anyone seen this problem before?

---

### Post by gwagchunks on 2010-01-13
Not sure... have you checked setup/setup/appearance then next a few times and see what size you have for the fonts. Mine are set to:

small = 12
Medium = 16
large = 25

---

### Post by DwalerXIII on 2010-01-15
I have the same font size in appearance setup as yours.
The problem only appears in mythmusic. 
As the appearance setup is a general setting is would be strange that this was the problem.

Does someone know if a config file extists where the resolution can be set?

---

### Post by whittylp on 2010-02-04
Yup I have the same problem, only my TV is running at 640x480 so no chance of reducing the resolution to improve things :-(

As far as google can tell - no-one else seems to be affected.

---

### Post by whittylp on 2010-02-04
Spoke too soon - the problem is recorded back as far as 2005 - It seems that some of the mythtv code is written to expect 96x96 (or 100x100) and thus font-scaling is based on this assumption.  Forcing X to treat your display as 96x96 DPI rather than asking for it or deriving it makes the fonts render nicely.

As recorded back in '05, with X config suggestions that might be out of date.
  [http://www.outflux.net/blog/archives/2005/10/16/mythtv-dpi/](http://www.outflux.net/blog/archives/2005/10/16/mythtv-dpi/)

See this wiki page for other ways to set your DPI setting.
  [http://wiki.archlinux.org/index.php/Xorg#Display_size_and_DPI](http://wiki.archlinux.org/index.php/Xorg#Display_size_and_DPI)

At least it worked for me :D

---

