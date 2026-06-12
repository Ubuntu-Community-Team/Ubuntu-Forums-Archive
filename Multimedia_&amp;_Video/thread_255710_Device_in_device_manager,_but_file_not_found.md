---
title: "Device in device manager, but file not found"
date: 2006-09-11
forum: Multimedia &amp; Video
---

### Post by dcroxton on 2006-09-11
I have a Hauppauge WinTV-PVR-250 installed.  I have had it working, including with MythTV, in the past, but I haven't used it in a while (since Breezy, anyway).  Now I have the strange problem that it shows up in my device manager, but I can't seem to use it because I'm getting a "file not found" error for /dev/video0.  It doesn't work for a simple "cat /dev/video0 > test.mpeg", nor can MythTV use it.  I know this is the device file I used before.

So am I using the wrong file, or has something become configured wrong, or what?  I can't tell from the device manager whether /dev/video0 means anything, because the path is in the form /sys/devices/ and some pci address.

I'd be glad to post any other information, such as the output of dmesg, if it would be useful.

Sincerely,
Derek

---

