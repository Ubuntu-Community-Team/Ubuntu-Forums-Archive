---
title: "How can I watch videos from other sources (Mythbuntu)"
date: 2010-12-02
forum: Mythbuntu
---

### Post by Epiphyte on 2010-12-02
I've got my Mythbuntu V10.04 system up and running to watch & record TV.

I want to view videos from other sources (not ripped from DVDs); namely movie cameras etc. or stuff supplied by friends. The output from them seems to be in mpg, AVI or XVid formats.

How do I get these onto my Myth box so that the system "sees" it and will play it?

---

### Post by thatguruguy on 2010-12-02
MythVideo.

Set up your storage groups, put your videos in the storage group for videos, and watch them with MythVideo.

---

### Post by Epiphyte on 2010-12-04
I've set up my Groups and Storage Directories in /var/lib/mythtv; with videos being /var/lib/mythtv/videos.

I copied a small (50MB) .avi file to that directory.

However, Myth does seem to recognise it when I use the frontend menu system - it just says "No files found" when I try to "Watch Videos".

What do I need to do to have this recognised?

---

### Post by Meph1st0 on 2010-12-04
In mythvideo press M to open the menu and select "scan for changes".

---

### Post by GnomicGhost on 2010-12-13
Thank you so much for this!!
I have also been putting files everywhere, making and deleting new directories etc

Is there a page somewhere with common keyboard shortcuts at all?
Volume, skip forward/backward etc?

Again, ty for replying to this :)

---

### Post by MonsterMaxx on 2010-12-13
> **GnomicGhost said:**
> 
Is there a page somewhere with common keyboard shortcuts at all?
Volume, skip forward/backward etc?


[http://www.keyxl.com/aaa3626/343/MythTV-keyboard-shortcuts.htm](http://www.keyxl.com/aaa3626/343/MythTV-keyboard-shortcuts.htm)

---

### Post by Epiphyte on 2011-01-04
> **Meph1st0 said:**
> In mythvideo press M to open the menu and select "scan for changes".
Thanks Meph1st0

That worked for me.

Regards

---

### Post by newlinux on 2011-01-04
> **GnomicGhost said:**
> Thank you so much for this!!
I have also been putting files everywhere, making and deleting new directories etc

Is there a page somewhere with common keyboard shortcuts at all?
Volume, skip forward/backward etc?

Again, ty for replying to this :)

> **MonsterMaxx said:**
> [http://www.keyxl.com/aaa3626/343/MythTV-keyboard-shortcuts.htm](http://www.keyxl.com/aaa3626/343/MythTV-keyboard-shortcuts.htm)

These are also configurable via mythfrontend and mythweb, if you want to change them.

---

