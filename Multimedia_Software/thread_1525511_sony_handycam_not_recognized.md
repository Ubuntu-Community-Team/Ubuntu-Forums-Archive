---
title: "sony handycam not recognized"
date: 2010-07-06
forum: Multimedia Software
---

### Post by Duckslammer on 2010-07-06
I am running xubuntu 10.04 under wubi.  I have a Sony Handycam 700x Digital8.  It is plugged into the USB port and not recognized.  Nothing shows for it with lsusb.

How do I get the files off it?  And once I get them, how do I edit?

(this was sooo wasy with windoze... ;))

---

### Post by Duckslammer on 2010-07-06
The fix: use kino with firewire (ieee 1394 cable - apt-get install kino)

If kino gripes about a missing raw1394 kernel module, chmod 777 /dev/raw1394 - you won't even have to reload kino.

If kino complains about not detecting a camera, trying continuing anyway - you might find it really is working.

---

