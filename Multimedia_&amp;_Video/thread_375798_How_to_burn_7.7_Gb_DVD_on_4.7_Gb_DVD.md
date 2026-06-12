---
title: "How to burn 7.7 Gb DVD on 4.7 Gb DVD????"
date: 2007-03-04
forum: Multimedia &amp; Video
---

### Post by puneit on 2007-03-04
I have few video DVDs which I would like to copy to a normal DVD. The source DVDs are of 7.7 GB each and I have blank DVDs of 4.7 GB. How can  do this? I have tried using DVD rip or acid rip, but I can't really figure out how to accomplish the desired task.
Any pointers would be appreciated.

---

### Post by gosh on 2007-03-04
did you try k9copy?
it's in the repo's

---

### Post by puneit on 2007-03-05
Hi.... K9 doesn't seem to do the job for me.. 
 The source DVD is 7.7 GB and K9 compresses it to 5.7 - 6 GB. Tried twice... 
I have checked the settings.. Even though DVD size under configuration of K9 is mentioned as 4400 MB, it made the iso file for 5.7 GB. When I reduced it to 3400 MB the iso file size increased to 6 GB.
Is there a way to get the contents fit on a 4.7 GB DVD
I don't mind dividing the contents on 2 DVDs of 4.7 GB each, but then the DVDs should run on a DVD player. Thats my only concern.
Thanks for your reply

---

### Post by dannyboy79 on 2007-03-05
what about dvd shrink (works great in windows)?? here's a link, [http://www.ubuntuforums.org/showthread.php?t=366739](http://www.ubuntuforums.org/showthread.php?t=366739), I found it by using the search feature in this forum.

---

### Post by mverrilli on 2007-03-05
If you are lucky, and don't care about the additional DVD content (behind the scenes, outtakes, etc), you could extract just the movie VOB and leave out all the extra content.  It might be small enough to fit on a single-layer DVD.  

Otherwise, you'll need to cut down some video quality, or split the video and put them on two single-layered DVDs.  Or buy a dual-layer burner, although the media is still kind of expensive last I looked.

---

### Post by eclectica on 2007-10-19
Try using dvd95 in the Ubuntu package.

---

### Post by phidia on 2007-10-25
> **eclectica said:**
> Try using dvd95 in the Ubuntu package.

Thanks for that tip dvd95 does appear to convert however it just produces a 135MG WS_iso withoutt any clues what to do with that?
I am going to look at the dvd95 home page to see if there are any docs there.

Actually trying to use dvd95 to evaluate the disc dvd95 crashes. The terminal output is:

> Floating point exception (core dumped)

---

### Post by Malik on 2007-10-25
.iso is an image
you burn it into the dvd and it creates the dvd

---

### Post by dannyboy79 on 2007-10-26
in feisty fawn, you can simply right click on the iso and chose, write to disk and it'll know that it needs to write the iso image contents to the disc, not just burn that iso file onto the disc. Pretty sweet!

---

