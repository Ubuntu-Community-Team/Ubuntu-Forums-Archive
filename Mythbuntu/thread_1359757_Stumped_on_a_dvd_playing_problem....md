---
title: "Stumped on a dvd playing problem..."
date: 2009-12-20
forum: Mythbuntu
---

### Post by mdifabio on 2009-12-20
Hello,

I was hoping some kind soul out there could give me some help.  There seem to be posts about DVD problems, but I think mine is a little different.

I did a fresh install of 9.10 on two different frontends that had been working well with 8.10.  Also upgraded my backend.  I have managed to stumble through getting everything to work again as it was before, except for "Play DVD" from the "Optical Disks" menu on the two frontends.  They worked fine in 8.10, but now when I go to select "Play DVD" nothing happens, not even a flinch.  I think the disks are mounting all right.  And if I go to the desktop and start VLC, I can play the DVD fine that way.

Will somebody please help me troubleshoot this?  Caution, I am pretty raw at this so I may need the full step by step instructions, if you ask me to do something too tricky.  

There is probably some other moron like me out there that this may help too.  Thanks in advance for the help.

---

### Post by mdifabio on 2009-12-20
...and yes, I have installed libdvdcss2.

---

### Post by mdifabio on 2009-12-20
Solved:

Ok, boy do I feel stoopid.

Here was my solution.  After looking for days for something more complicated, I realized that 9.10 had selected xine for the default dvd player.  But during the installation process, xine was never installed.  And even though the "alternate player" button (with "internal" as a alternate) was selected, it did not kick in when xine failed to play the dvd.

Anyway, once I installed xine it worked.

Hope this helps somebody.

Jeez!

---

