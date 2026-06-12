---
title: "[SOLVED] *.wav files do not play in some players"
date: 2008-11-17
forum: Multimedia Software
---

### Post by jenkinbr on 2008-11-17
EDIT:
I came to a solution, which can be viewed in this thread: [http://ubuntuforums.org/showthread.php?t=987654](http://ubuntuforums.org/showthread.php?t=987654)
/EDIT
___________________________
After upgrading to ubuntu 8.10, I have begun to notice that some players (like totem) and some CD burners (Brasero) no longer play .wav audio or burn it to an audio CD.  This is rather annoying, as I use .wav files frequently due to the high sound quality they hold.  Even .wav files created by dragging from an audio CD do not play.

There is nothing wrong with the files - Amarok, alsaplayer, +others play the files just fine, and I can open them in Audacity without issue.

I'm guessing that this may be an issue with gstreamer (btw, I installed gstreamer*, thereby giving me all the plugins), but I am not sure.  Any ideas?

---

### Post by jenkinbr on 2008-11-17
???

---

### Post by SuperSonic4 on 2008-11-17
Have you tried wavpack or something?

---

### Post by jenkinbr on 2008-11-17
No.  Never heard of it, but am downloading now...

---

### Post by jenkinbr on 2008-11-18
> **SuperSonic4 said:**
> Have you tried wavpack or something?

> **jenkinbr said:**
> No.  Never heard of it, but am downloading now...

Already had them installed (wavpack and libwavpack).  Still no wav playback or burning.  I've set alsaplayer as the default program for wav files, but I still need to be able to burn them, preferrably using serpentine or brasero.

---

### Post by jenkinbr on 2008-11-18
???

---

### Post by CraigPaleo on 2008-11-18
I've been having the same problem. Mplayer now sees my wav files as streaming - if that has anything to do with it. 



__________________
[Raw Paleolithic Diet]("http://www.rawpaleodiet.com")

---

### Post by jenkinbr on 2008-11-19
That's my exact problem within MPlayer, gMplayer, totem, + a couple others.  I cannot burn audio disks from wav files in brasero or serpentine (both throw errors stating that the track(s) are shorter than 6 seconds and will be padded.

Glad someone can comfirm this.  Hewever, nobody seems to visit this section of the forum, so I am considering bringing this up elsewhere as well

---

### Post by CraigPaleo on 2008-11-19
Great! I'll look for the new thread.


__________________
[Raw Paleo Diet Group]("http://health.groups.yahoo.com/group/rawpaleodiet/")

---

### Post by jenkinbr on 2008-11-24
I have come to a solution here: [http://ubuntuforums.org/showthread.php?t=987654](http://ubuntuforums.org/showthread.php?t=987654)

---

