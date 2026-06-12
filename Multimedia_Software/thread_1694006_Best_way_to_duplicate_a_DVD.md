---
title: "Best way to duplicate a DVD?"
date: 2011-02-23
forum: Multimedia Software
---

### Post by The Cog on 2011-02-23
I finally got round to transcribing our wedding video from VCR to DVD. Now I would like to duplicate that video a few times and pass copies round the family, more to preserve it than to bore the relatives.

I dragged the DVD icon from the desktop to a thunar (file manager) window and it created a folder containing this lot:
> WeddingVideo/
WeddingVideo/VIDEO_RM
WeddingVideo/VIDEO_RM/VIDEO_RM.BUP
WeddingVideo/VIDEO_RM/VIDEO_RM.DAT
WeddingVideo/VIDEO_RM/VIDEO_RM.IFO
WeddingVideo/VIDEO_TS
WeddingVideo/VIDEO_TS/VIDEO_TS.BUP
WeddingVideo/VIDEO_TS/VIDEO_TS.IFO
WeddingVideo/VIDEO_TS/VIDEO_TS.VOB
WeddingVideo/VIDEO_TS/VTS_01_0.BUP
WeddingVideo/VIDEO_TS/VTS_01_0.IFO
WeddingVideo/VIDEO_TS/VTS_01_1.VOB
WeddingVideo/VIDEO_TS/VTS_01_2.VOB Total size 1.3 GB.
But I have no idea what to do with these files.

I tried this command:
> sudo dd if=/dev/dvd of=weddingvideo.isoand ended up with a 4.4 GB file, which Archive Manager says contains the above folders, and presumably also contains an image of 3.1 GB of formatted but unused disk.

What's the best thing to do here? The ISO file will presumably burn a good DVD copy but it's a waste of disk space to keep it, (I'd like to keep a copy on hard disk too) and I guess will also take needlessly long to burn. 

Can I create a smaller ISO from the file folders? If so, is there an app to edit the titles before I do so? The recorder put a second title "Empty Title" on the title page which I'd like to get rid of. I discovered by accident that the VOB files play in parole media player - one is the title screen, and the other two contain about half the video each. So I don't know what all the other files are about.

---

### Post by The Cog on 2011-02-25
Bump...

---

### Post by howefield on 2011-02-25
I use the Brasero Disc copy function, which has never let me down. Not sure if you have that on your system. Thunar.. is that the Xfce file manager ?

I've played with K9copy also, a KDE application, but seems to work well enough.

---

### Post by The Cog on 2011-02-25
Aha! Brasero does the trick, thank you.

Yes, I'm using XFCE. I might try KDE again at the next release, but last time I tried it, too many things just didn't work. Something about Gnome irritates me a little, though I can't put my finger on what. Xfce seems like a good choice at the moment, not because I'm short on hardware but it seems a good mix of enough features but not too many. It doesn't install CD/DVD ripping and creation tools by default though, and I don't do it often enough to remember which does what.

---

### Post by SouthJersey on 2011-09-18
I copied a dvd from my TV, then i put it in my computer, I ran Windows Movie Maker and it ask for the file Video_RM.BUP plugin, where can I get a copy of this prgm.?

---

### Post by VanillaMozilla on 2011-09-19
We can't/won't give you Windows help, but you can usually just copy any file from within a DVD, using Linux.  Windows usually doesn't show you these files, but to Linux a DVD is just another disk.

---

