---
title: "Ubuntu hates my Graphics Card..."
date: 2007-11-22
forum: Multimedia &amp; Video
---

### Post by The Wise Monkey on 2007-11-22
It seems as if I am destined never to use Linux...

First of all, I had openSUSE installed and working fine, but for some reason it decided to stop picking up a network connection, so I decided to uninstall it. That, and the Yast thing was annoying me.

So I decided to install Ubuntu, as it seems to be one of the better distributions available. I downloaded the amd64 iso, burnt it to a CD, and tried to load into the Live CD - no dice. It booted from the CD, then when I selected the first option to install Ubuntu from the loader screen (the one with CD check and memtest etc) it said "Kernel Loaded" in the bottom corner, and then nothing. Completely blank screen, no flashing cursors, nothing. Same with Safe Graphics Mode.

So I thought it was a problem with the CD, so I re-downloaded the iso and try again - I encountered a distinct lack of dice. So I tried the alternate CD, which allowed me to install (finally!). However, when I decided to boot into my newly installed OS, I was met with the blank screen again.

I think it must be my GFX card, but openSUSE had no trouble with it, and XP certainly doesn't.

My system:
e6750@3.2
2GB RAM
1x WD Raptor 74GB drive, split in two for XP and Linux installation
1x WD 250GB SATA drive for storage
eVGA 8800GTS KO ACS3 edition 320MB - brand new :(


Any ideas would be greatly appreciated - I am really keen to get Ubuntu up and running. :)

---

### Post by scrooge_74 on 2007-11-22
if it boots, then go to a console (CTRL+ALt+F2) and log in, probably the video driver is not working correctly.  You need to look around for your specific card and check wich driver you have to use.

You can in the mean time try changing the driver to VESA to get a GUI working

sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by IanW on 2007-11-22
Try what I suggested in [this]("http://ubuntuforums.org/showpost.php?p=3800846&postcount=3") other thread.

---

### Post by The Wise Monkey on 2007-11-22
Thanks guys - I'll give these a try and get back to you. :)

---

### Post by The Wise Monkey on 2007-11-22
Success!

I tried what you said Ian, and it worked perfectly - thank you very much! :D

---

