---
title: "Adding second HDD"
date: 2008-01-28
forum: Mythbuntu
---

### Post by voctikal on 2008-01-28
Currently have a 320 gig HDD that is almost full.  If I add in another HDD  will it be auto-detected.  

Also will I need to the change the file paths for my video files or can I just add an additional file path in the mythtv setup?

Just to mention I am wanting to have video on both drives.

---

### Post by stdPikachu on 2008-01-29
It'll be *detected* but the machine won't format it automatically, you'll need to tell it to do so. I usually do this sort of stuff on the command line because I find it easier and quicker, but if you fire up an app like GParted it should be able to partition and format the drive for you. IIRC there should be an app labelled "disk manager" in applications somewhere.

As to storing stuff on both drives at once - this is where it gets a bit complicated. Myth doesn't currently support having two different places to record TV to (that's coming in the next release) so for two hard drives you have the following options:
Keep your current hard drive as the system drive, copy the TV data onto the new (larger?) drive and use that as a dedicated recording device. You might want to use the newly available space on your original drive for MythVideo or similar
"Glue" the drives together (so they look like one big drive) using LVM, although this can be complicated and I wouldn't recommend it if you're a n00b :)

---

### Post by newlinux on 2008-01-29
> **voctikal said:**
> Currently have a 320 gig HDD that is almost full.  If I add in another HDD  will it be auto-detected.  

Also will I need to the change the file paths for my video files or can I just add an additional file path in the mythtv setup?

Just to mention I am wanting to have video on both drives.

Just in case...
If you are speaking of your Mythvideo files and not myth recordings you can have two different directories for your video files by separating them by a colon in the Mythvideo setup menu in mythfrontend. If you are talking about myth recordings your question has already been answered :)

---

### Post by larsolav on 2008-01-29
> **stdPikachu said:**
> It'll be *detected* 
"Glue" the drives together (so they look like one big drive) using LVM, although this can be complicated and I wouldn't recommend it if you're a n00b :)

I still consider myself a n00b, but two weeks ago I followed the LVM directions in the sticky ( [http://ubuntuforums.org/showthread.php?t=584473](http://ubuntuforums.org/showthread.php?t=584473) ) and the directions were easy to follow, and I learned a thing or two while doing it. It just took a long time to copy all the data (a couple of hours or so to copy about 250 GB of recordings...).

Good luck

---

### Post by voctikal on 2008-01-29
Thanks for the replies.


I dont have cable or satellite so it would only be myth video.

---

### Post by ubnewbie2 on 2008-01-29
> **voctikal said:**
> Thanks for the replies.


I dont have cable or satellite so it would only be myth video.

What about free to air TV recordings?

---

### Post by voctikal on 2008-02-02
dont use a tuner card either   :)

---

