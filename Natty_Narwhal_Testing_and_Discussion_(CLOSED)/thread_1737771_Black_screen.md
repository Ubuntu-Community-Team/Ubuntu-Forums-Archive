---
title: "Black screen?"
date: 2011-04-23
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by kostageas on 2011-04-23
When I run ubuntu 11.04 from a usb (I tried both 32 and 64 bits) I get to the screen where I chose to try without changing my computer, and I get the splash screen, the login sound, and then nothing but a black screen with a mouse.  I can move the mouse around, but that's it.  Any suggestions?

---

### Post by ikt on 2011-04-23
> **kostageas said:**
> When I run ubuntu 11.04 from a usb (I tried both 32 and 64 bits) I get to the screen where I chose to try without changing my computer, and I get the splash screen, the login sound, and then nothing but a black screen with a mouse.  I can move the mouse around, but that's it.  Any suggestions?

After you select to boot off of the CD/USB:

when you see the big purple screen with the little keyboard + little man at the bottom hit Enter;

Choose language and leave the default Try as a live cd or whatever it says again;

Important: hit F6 and then Esc to see the boot line

file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --

move the cursor backwards and remove quiet splash;

Then hit enter, you should see lots of text and hopefully you can see some error messages on why your screen is blank.

---

