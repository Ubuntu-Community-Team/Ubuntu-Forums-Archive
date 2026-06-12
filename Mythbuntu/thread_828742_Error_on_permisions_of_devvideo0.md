---
title: "Error on permisions of /dev/video0"
date: 2008-06-14
forum: Mythbuntu
---

### Post by ppeetteerr on 2008-06-14
I reformated the hardrive of a system that was running mythtv and installed mythbuntu on it.  For the life of me I dont seem to be able to get it to work.  I can't get mythtv to recognize my video card.  I can use it fine in tvtime and I had used it before with mythtv but when I click on watch TV I get 

```

2008-06-14 00:33:42.185 Channel(/dev/video0)::Open(): Can't open video device, error "Permission denied"
ERROR: no valid capture cards are defined in the database.
Perhaps you should read the installation instructions?
2008-06-14 00:33:42.292 MediaServer:: Loopback address specified - 127.0.0.1. Disabling UPnP
2008-06-14 00:33:42.293 Main::Registering HttpStatus Extension

```

Any sugestions?

---

### Post by ian dobson on 2008-06-14
Hi,

What permissions does /dev/video0 have?

You know that Mythtvbackend runs as user MythTV.

Regards
Ian Dobson

---

