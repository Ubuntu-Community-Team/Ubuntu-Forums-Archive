---
title: "Video Help!"
date: 2008-02-19
forum: Multimedia &amp; Video
---

### Post by hasek522 on 2008-02-19
So i am trying to run ubuntu on my 
p4 2.66 ghz
512 mb ram
x1600 ati card
with a flat screen monitor

after installing ubuntu i was prompted to install a proprietary driver for ATI so i did so.

Now every time i boot to ubuntu i get a completely black screen and my monitor gives me a warning saying it cannot display the current video.  
I am completely new to linux and command line so please bare with me and try to be as specific as possible.  Any help would be greatly appreciated.

---

### Post by magicfab on 2008-02-19
Reboot your PC and when you see the "GRUB menu loading" prompt, hit ESC.

Then boot into "Recovery" mode.

Once at the root prompt, enter:
dpkg-reconfigure xerver-xorg -phigh <ENTER>

And then:
reboot<ENTER>

That should try to create a new graphic configuration file using autodetection.

---

