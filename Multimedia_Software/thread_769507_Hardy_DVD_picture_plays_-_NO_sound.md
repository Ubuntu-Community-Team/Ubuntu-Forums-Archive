---
title: "Hardy DVD picture plays - NO sound"
date: 2008-04-26
forum: Multimedia Software
---

### Post by pofigster on 2008-04-26
So, I've been following all the guides I can find on getting DVDs to play.  Using VLC I can see the picture, move around in the movie, etc...

However, I cannot hear anything.  Sound works on my system just fine.  I'm rocking out to Guns 'n Roses on Pandora right now.  I've stopped Pandora (and closed the tab) to make sure it's not a conflict with the sound card drivers.

Any ideas on why I don't get any sound?

---

### Post by pofigster on 2008-04-27
I used > export DVDCSS_METHOD=title && totem dvd://
and suddenly sound works!  Still, VLC and gxine refuse to cooperate and play sound.  I tried > export DVDCSS_METHOD=title && vlc dvd:// but all that did was create a bad key in the ~/.dvdcss folder which I deleted.  Still no sound.  I even did > echo "export DVDCSS_METHOD=title" >> ~/.bashrcexport to save the key grabbing method that worked.  Anywho - I'm out of ideas, I've looked everywhere for a solution to this, everything that's worked for other people doesn't work for me.

Any help at all would be appreciated.

---

### Post by pofigster on 2008-04-27
I installed > vlc-plugin-esd && mozilla-plugin-vlc restarted and it all worked.  Not just in VLC but in MPlayer, too.

Really weird, not sure why.  Not complaining though - it works!

---

