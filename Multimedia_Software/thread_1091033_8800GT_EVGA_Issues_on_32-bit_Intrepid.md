---
title: "8800GT EVGA Issues on 32-bit Intrepid"
date: 2009-03-08
forum: Multimedia Software
---

### Post by De-Apex'd 7 on 2009-03-08
I recently updowngraded from 64-bit Hardy 8.04 to 32-bit Intrepid 8.10.  I did this because I was having a bunch of issue getting flash to work on Firefox.

Anyway, I had the graphics acceleration stuff working perfectly on 64-bit, I had desktop effects enabled and everything.

Now, on 32-bit I can't get the graphics acceleration to work at all.  Whenever I try to install the nvidia drivers I get this message (after going through the rest of the installation in Ctrl+Alt+F2 mode):

"Unable to open '/usr/lib/nvidia/libglx.so.xerver-xorg-core' for reading (no such file or directory)"

Also, this message pops up whenever I try to open the X control:

[IMG]http://i15.photobucket.com/albums/a378/rexpelagi/Computer%20Stuff/XServerFail.jpg[/IMG]

^I've down what it says, but it doesn't change a thing.

From searching around I've tried some things from the following links:

[http://www.ubuntugeek.com/how-to-fix-nvidia-acceleration-in-feisty-nvidia-8800-and-legacy-users.html](http://www.ubuntugeek.com/how-to-fix-nvidia-acceleration-in-feisty-nvidia-8800-and-legacy-users.html)

[http://ubuntuforums.org/showthread.php?t=656868&highlight=xserver-xorg-core](http://ubuntuforums.org/showthread.php?t=656868&highlight=xserver-xorg-core)

Nothing is working for me.

It is probably just user error, any clue what I'm doing wrong?

---

### Post by De-Apex'd 7 on 2009-03-09
Bump, any ideas?

---

### Post by cariboo on 2009-03-09
I would suggest removing all mention of nvidia using Synaptic, then start in recovery mode and selecting xfix at the menu, then select resume, to get back to your default desktop. Now open Synaptic and search for nvidia-glx-180 and mark it for installation, this should also mark all the dependencies needed to successfully install the nvidia driver. You may have to go to System-->Administration-->Hardware Drivers to enable the driver.

Jim

---

