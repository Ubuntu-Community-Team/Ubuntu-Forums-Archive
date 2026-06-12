---
title: "[SOLVED] How to play dvd file on hard drive"
date: 2007-11-13
forum: Multimedia &amp; Video
---

### Post by tmryan on 2007-11-13
I have ripped a dvd on to my hard drive, but can't figure out how to play it from there. I've tried Totem, MPlayer, and Gxine but all these players want to play a DVD from the DVD drive (it wants to look for a disk). Choosing File/Open from these players and then picking a .vob file will only play that one file. Can someone tell me how to play these files with full menu selection / scene selection etc. features? Thanks.

---

### Post by bingoUV on 2007-11-13
> **tmryan said:**
> I have ripped a dvd on to my hard drive, but can't figure out how to play it from there. I've tried Totem, MPlayer, and Gxine but all these players want to play a DVD from the DVD drive (it wants to look for a disk). Choosing File/Open from these players and then picking a .vob file will only play that one file. Can someone tell me how to play these files with full menu selection / scene selection etc. features? Thanks.

What method did you use to rip your DVDs? I am afraid you might have removed the information (menu / scene) that is needed to play the files like a DVD. Now they may just be plain simple video clips, which can be watched. You can create a playlist out of them , and play them one by one.

---

### Post by tmryan on 2007-11-13
> **bingoUV said:**
> What method did you use to rip your DVDs? I am afraid you might have removed the information (menu / scene) that is needed to play the files like a DVD. Now they may just be plain simple video clips, which can be watched. You can create a playlist out of them , and play them one by one.

No, I'm positive that's not the case. I used Dvdshrink (Windows) for ripping. All the dvd files are in a video_ts directory containing a bunch of .vob .ifo .bup files. I could play it fine in Windows. I think it's a case of me not knowing how to play them in the above mentioned softwares.

---

### Post by The Cokeaholics on 2007-11-13
This is how I play DVD from harddrive (VIDEO_TS):
```
sudo apt-get install kaffeine
```
From within kaffeine: open directory (containing folder VIDEO_TS). Kaffeine is a KDE applic but runs fine on Gnome.

Robert

---

### Post by tmryan on 2007-11-20
After much searching, I ended up installing Ogle. It lets you select a VIDEO_TS directory on the hard drive and plays it from there.  It has DVD menu support, access to scene selections, subtitles, chapters, etc...

The interface is a bit rough around the edges, but it works!

---

### Post by zorkerz on 2007-11-30
Im not a big fan of having to install so many media players. I would like to do the same thing with either totem-xine or vlc. Does anyone know if this is possible?

---

### Post by zorkerz on 2007-11-30
oops never mind it worked this time. You have to open directory in vlc. I don't think totem-xine can do this. I have heard xine can. Prolly totem-gstreamer (default in ubuntu) will not either.
cheers

---

### Post by treris on 2007-12-07
actually, if you add the Video_ts directory to the playlist of totem(-xine) it will play the files nicely in a row, just as it would if you were playing the dvd. Only thing that doesn't seem to work is using the menu on the dvd, you'll have to use the forward buttons in totem.

---

