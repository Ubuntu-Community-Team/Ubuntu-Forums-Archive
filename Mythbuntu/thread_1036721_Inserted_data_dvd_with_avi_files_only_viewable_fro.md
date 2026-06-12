---
title: "Inserted data dvd with avi files only viewable from mythgallery"
date: 2009-01-11
forum: Mythbuntu
---

### Post by Caysho on 2009-01-11
I have mythbuntu set to monitor the CD/DVD drive and for it to hand control to the appropriate plugin.
The disk is mounting on the desktop and can be viewed normally from there (eg VLC).

When in mythtv:
If I insert a data dvd, mythbuntu will sometimes present me with mythgallery with the contents of the disk, but this does not always happen.  Each avi file plays ok when selected.

I would prefer the disk contents made available when viewing Media Library > Video.  I don't know why mythgallery is being selected when there are no pictures on the disk.

---

### Post by uMuppet on 2009-01-12
> **Caysho said:**
> 

I would prefer the disk contents made available when viewing Media Library > Video.  

I don't think you can do this, unless you add a link to your cd drive in the MythVideo folder.  That might work, but then I guess you would have to do a scan in the video manager before you could browse it.

If you add avi to the filetypes in Mythgallery setup it will automatically try and play them when it detects them in the drive

---

### Post by Caysho on 2009-01-12
I've fixed this.

Utilities/Setup > Setup > Media Settings > Videos Settings > General Settings:
Default view: Listings
Show Unknown File Types = Ticked
Video Browser browses files = Ticked
Video List browses files = Ticked

I left the other settings alone.
When the disk is inserted, I go to Media Library > Watch Videos and get the contents of the disk.

---

