---
title: "Mythbuntu &quot;media library&quot; live samba browsing"
date: 2008-12-03
forum: Multimedia Software
---

### Post by davidstoll on 2008-12-03
I setup the "Media Library" (in the main menu) to point to a folder with some samba shares.  However, it seems that I have to hit the "Video Manager" menu item (in the Utilities/Setup menu) and wait (what seems like) forever for it to re-scan the samba shares and re-build the database so the the new videos show up in the "Media Library".  Is there any way to just browse "live" from within myth to samba shares?  Preferably through the "Media Library".

Worse case scenario would be to run a cron job that would re-scan every so often.  This would be ok, but live browsing would be best.  If someone knows of the command line entry for a cron job, I would appreciate it.

Thanks

---

### Post by davidstoll on 2008-12-11
bump?

---

### Post by pbmissions on 2009-11-13
This is really great news. Thank you for sharing it with us!

---

### Post by SupraGuy on 2010-01-31
Looking for the same information. I have a bunch of SMB/CIFS shares on my network, some of which are not available full-time, but I want to be able to use media from any of them similar to what I can do with XBMC

---

### Post by sports.car.guy on 2010-01-31
MythTV is not designed to have part time shares. There is no need for it, and it is counter productive to the whole multimedia at your finger tips design structure. You make the shares mountable by Linux at boot and scan once. That is how it should be.

Unlike XBMC, MythTV relies on storing everything information wise in a DB from my understanding of the differences between the two. This allows for all the cool features like storage of metadata. Without the shares you have media on that you scanned you are now having it go wait where is this, and this, and this, to eventually error.

You need the shares to be mounted at boot and available. Or you will have to rescan everytime so that MythTV knows what is actually available.

---

