---
title: "No Xvid/Dvix in gstreamer"
date: 2009-11-14
forum: Multimedia Software
---

### Post by jlimon on 2009-11-14
It seems that no matter how many codecs and repos I add to my system I cannot play xvid or dvix files..

Every time I try to play one the codec finder tells me there's no packages which support my files.

The traditional "solution" is to get someone to use VLC (I've resorted to this lately) but now I need to EDIT some files and all the mainstream GNOME video editors use gstreamer.

I've installed and reinstalled every known gstreamed codec package in the repos and I'm ready to throw my computer out the window..

Any ideas?

---

### Post by jlimon on 2009-11-14
I just want to add that the goal of this thread is to get xvid/divx working in gstreamer. I know VLC will play them fine but that is not the goal.

---

### Post by jlimon on 2009-11-15
Output from command line.

deadpool [ /media/Deathstar/Movies ] : totem Van\ Wilder.avi 
** Message: Missing plugin: gstreamer|0.10|totem|XVID MPEG-4 decoder|decoder-video/x-xvid (XVID MPEG-4 decoder)
/usr/lib/python2.6/dist-packages/GnomeCodecInstall/MainWindow.py:300: DeprecationWarning: Accessed deprecated property Package.candidateRecord, please see the Version class for alternatives.
  record = pkg.candidateRecord
/usr/lib/python2.6/dist-packages/GnomeCodecInstall/MainWindow.py:305: DeprecationWarning: Accessed deprecated property Package.candidateRecord, please see the Version class for alternatives.
  major, minor = pkg.candidateRecord["Gstreamer-Version"].split(".")
** Message: No installation candidate for missing plugins found.

---

### Post by jlimon on 2009-11-15
For some weird reason removing all gstreamer directories from my $HOME seems to have fixed everything.. odd.

---

### Post by telorn on 2009-11-22
Same for me, after deleting .gstreamer... folder in $HOME directory everything works fine

---

### Post by Chozabu on 2010-12-01
Yep! deleting .gstreamer* worked for me too :) loads of other threads had some rather extreme solutions - I suspect they just ended up purging this dir... I should have backed it up to see what the problem was...

---

### Post by cotcot on 2011-04-15
Confirm. Works after deleting .gstreamer.

---

