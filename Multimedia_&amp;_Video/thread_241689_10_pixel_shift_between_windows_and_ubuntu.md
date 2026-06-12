---
title: "10 pixel shift between windows and ubuntu"
date: 2006-08-22
forum: Multimedia &amp; Video
---

### Post by Falcon X on 2006-08-22
I'm new to Ubuntu, and I have a dual boot setup going.  I'm quite happy right now except for an odd difference between the two operating systems.  When I boot into Ubuntu (after using windows), the screen is displayed about 10 pixels too far to the right.  I have to manually change this via the monitor horizontal shift.  When I go back to windows, I have to undo this.

Is this a common problem?  How should I resolve this?

---

### Post by kalikiana on 2006-08-22
I encountered this problem, too, when I had freshley installed XUbuntu.
To fix this you need to install the ATI graphics driver properly. If you think it should be working but screen is still off, possibly you should look through the manuals on the forums and try again. Still what the original problem was is beyond my understanding, though.

---

### Post by codejunkie on 2006-08-22
installing the correct driver for your video card, use the nvidia-glx driver if you have an nvidia card, or the ati driver if you have an ati card etc, also have a look at the link below it will describe how to fix it without installing any video card drivers this might come in handy, if you have an integrated graphics card, i've seen some of them even if you install the correct drivers have the offset and you'll need to follow the guide and get the mode line to add to your /etc/X11/xorg.conf file to fix it.
[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

---

