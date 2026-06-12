---
title: "sound keeps cutting out in videos"
date: 2008-11-17
forum: Multimedia Software
---

### Post by pickarooney on 2008-11-17
Since I upgraded my laptop to Intrepid and installed Gnome with the Mac4Lin theme, I've been having big problems with jerky video playback and sound cutting out every so often - I have to rewind a few seconds to get it to work again. I guess this is a side-effect of Compiz running on a 2GHz machine with 750MB RAM, but would like other opinions on it before I go and format and install xubuntu or similar. The problem happens in Xine and Totem, SMplayer stopped playing video files altogether about a day after I installed Intrepid/GNOME.

Has anyone a foolproof diagnostic to find out whether low resources are causing the issues and tips as to what processes, settings and services to cut out in order to improve performance?
I have KDE4 installed on the same machine (upgrade from Hardy with KDE3) but have never used it, although I imagine KDE is, if anything, more resource-hungry than GNOME?

---

### Post by psyke83 on 2008-11-17
> **pickarooney said:**
> Since I upgraded my laptop to Intrepid and installed Gnome with the Mac4Lin theme, I've been having big problems with jerky video playback and sound cutting out every so often - I have to rewind a few seconds to get it to work again. I guess this is a side-effect of Compiz running on a 2GHz machine with 750MB RAM, but would like other opinions on it before I go and format and install xubuntu or similar. The problem happens in Xine and Totem, SMplayer stopped playing video files altogether about a day after I installed Intrepid/GNOME.

Has anyone a foolproof diagnostic to find out whether low resources are causing the issues and tips as to what processes, settings and services to cut out in order to improve performance?
I have KDE4 installed on the same machine (upgrade from Hardy with KDE3) but have never used it, although I imagine KDE is, if anything, more resource-hungry than GNOME?

It's possible that PulseAudio's default buffering (or "fragment" settings) is causing this issue.

First, look at my [PulseAudio Fixes]("http://ubuntuforums.org/showthread.php?t=789578") guide, and find the question about stuttering in Appendix B.

Edit your /etc/pulse/daemon.conf file, and instead of changing the values for the fragment settings, comment those two lines (i.e. place a "#" at the beginning of the lines).

After logging out and back in, see if your problem still occurs.

---

### Post by pickarooney on 2008-11-18
Cheers psyke. I followed all that to the letter but it unfortunately didn't make a blind bit of difference. At least it's ruled out PA as a problem and it's most likely a reources issue then.

---

