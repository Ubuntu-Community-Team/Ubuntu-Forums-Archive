---
title: "Moved hard drive, can't see cursor..."
date: 2007-07-10
forum: Multimedia &amp; Video
---

### Post by elmerfud on 2007-07-10
My laptop failed.  I pulled the hard drive from it and I am attempting to run it on a desktop machine.  The hard drive is loaded with feisty.

The computer boots the hard drive.  I can get to a text console, but the characters are really big and the command line doesn't display on the screen.  Obviously the video card in the desktop machine is different from the one in the laptop. 

The video card in the laptop was an nvidia product and I had the nvidia custom driver loaded.

How do I force Linux to resense the video card in the desktop machine ?

Thanks

---

### Post by elmerfud on 2007-07-10
Anyone ?

---

### Post by elmerfud on 2007-07-10
I solved this. 

First I ran the Ubuntu recovery image by selecting it in the boot screen.  That got me a command line that worked.

Then I went to /etc/X11 and renamed by old xorg.conf file so that there was no xorg.conf  file. 

Then I ran xinit.

That got me a working X session, although I still have a couple display issues to resolve.

---

