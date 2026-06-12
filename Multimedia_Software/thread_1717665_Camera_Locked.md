---
title: "Camera Locked"
date: 2011-03-30
forum: Multimedia Software
---

### Post by andrewpb on 2011-03-30
Howdy,

I just switched over to Ubuntu 10.10 and I just transferred all my photo's into Shotwell.  Now I'm attempting to upload some photo's from my Nikon D3100 and Shotwell is claiming that the camera is locked by another application.  However the only other application open is the music player, and I doubt it's that.  I attempted to download the Camera application through the software manager, but it won't even open.

Any thoughts?

Thanks

---

### Post by RyanGT on 2011-04-08
I have the exact same issue, also with a Nikon DSLR (D60).

---

### Post by RyanGT on 2011-04-08
I took the SD card out and put it in a card reader.  This worked fine, but when I open Nautilus it suggests using the gThumb import tool.  I have used (and liked) gThumb's importer in the past.  I wonder if somehow gThumb and Shotwell are fighting over ownership of the importing responsibilities.  However, I did not have gThumb open when I first plugged in the camera.  I also was not allowed to import using gThumb when I plugged the camera in directly.

---

### Post by RyanGT on 2011-04-08
Rebooting seems to have solved my problem.  One potential explanation for my case is that it seems like the gThumb import tool no longer automatically ejects the media after import.  So, I think I unplugged the camera without unmounting it previously.

---

### Post by RyanGT on 2011-04-10
Sorry to continue high-jacking this thread, but things seem to work fine for me immediately after a fresh reboot.  After my wife and I each log in and log out to our different accounts a couple of times, things stop working.  It seems like the mounting of removable media with multiple users logged in had been buggy for a while.

---

