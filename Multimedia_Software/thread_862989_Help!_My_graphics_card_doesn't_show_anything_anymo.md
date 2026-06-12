---
title: "Help! My graphics card doesn't show anything anymore"
date: 2008-07-18
forum: Multimedia Software
---

### Post by Josephp22 on 2008-07-18
So.. I tried to install my Nvidia graphic card's driver and I did it with this tutorial: [http://ubuntuforums.org/showthread.php?t=797270]("http://ubuntuforums.org/showthread.php?t=797270")

Now, when I start up, I can see the loading icon, but once it gets past that, the screen becomes black with multicolored lines on the screen. Is there any way for me to start up ubuntu without using the dedicated card, and use the integrated one instead?

And then, is there a way for me to uninstall the drivers and then go back to my dedicated card? 

=x please help

---

### Post by xc3RnbFO8P on 2008-07-18
Try first:
> Reboot your PC and when you see the "GRUB menu loading" prompt, hit ESC.
(if you don't dual boot)

Then boot into "Recovery" mode.

Once at the root prompt, enter:
dpkg-reconfigure xerver-xorg -phigh <ENTER>

And then:
reboot<ENTER>

That should try to create a new graphic configuration file using auto detection.

---

### Post by Josephp22 on 2008-07-18
I figured it out, I just booted into recovery mode, and then fixed the X server.

Now, I need help installing the driver =/ I tried EnvyNG and the same problem happens.. what do I do?

---

### Post by xc3RnbFO8P on 2008-07-18
What is your graphic card?
Did you enable the restricted drivers?

---

