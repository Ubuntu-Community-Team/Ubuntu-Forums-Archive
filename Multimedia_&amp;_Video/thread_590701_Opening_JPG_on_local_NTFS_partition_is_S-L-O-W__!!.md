---
title: "Opening JPG on local NTFS partition is S-L-O-W  !!!"
date: 2007-10-25
forum: Multimedia &amp; Video
---

### Post by sohosources on 2007-10-25
Hi, gang:

I just installed 7.10 on a fast dual-core machine, and I'm now trying to make it work like a normal PC.

Installed codecs, etc, with automatix2, and I'm impressed so far...but a few things are still quite confusing...

I have an NTFS partition on a second hard drive in the same PC. I can mount it from 7.10's "Places" menu and read and write files...but...

If I open the drive and double-click on a jpg file, for example, GNOME won't open it!  HUH?

If I right-click on the jpg and click on open with file viewer, it takes ABOUT 10 SECONDS to open and display the file...  HUH?

Similarly, I can't get VLC, my preferred MM player, to play a video hosted on a nearby XP box, even though I can read and write files to that share through the "Network" portion of 7.10's "Places" menu.

What am I missing?  And should Ubuntu be this balky?

Thanks in advance!

--KK in MN

---

### Post by sohosources on 2007-10-28
Hi Gang:

The solution was to tell GNOME to use the gThumb image viewer as default instead of the normal viewer.

gThumb opens the file in 1/3 of a second versus 13 to 15 seconds with whatever GNOME normally uses.

Don't ask me why!

--KK in MN

---

