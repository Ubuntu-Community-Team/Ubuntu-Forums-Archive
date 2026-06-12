---
title: "SAFE GRAPHIC MODE : really quick question"
date: 2008-01-19
forum: Multimedia &amp; Video
---

### Post by VoXoM on 2008-01-19
How do I do to go in safe graphic mode? Isn't there a key you have to push like in windows (F8 or something similar??)

I tried to install a driver for my video card and the screen is all messed up, can't see a thing. Now, I am really a noob at linux but I had a couple VERY important files that I have to recover.

PLEASE, help.

---

### Post by Kralizec on 2008-01-19
Can you get to the login screen, or do graphics just not work completely now? Because the only safe graphical mode I know of in Ubuntu is 'Failsafe GNOME'; choose it from the Sessions menu at the login screen. If you can't get to that, you'll have to fix it from the terminal.
To get to the terminal, when booting and it says your Grub version, press escape and it will give you a menu of kernels to boot. Boot the safe version of your current kernel and it will boot into terminal. From there, though I can't help much. You might try reconfiguring your xserver:
```
dpkg-reconfigure xserver-xorg
``` and choosing a different video driver like that.

Good luck.

---

### Post by VoXoM on 2008-01-19
I managed (with the help of this community) to fix everything AND install a driver for my Radeon card in another thread.

I <3 this community

---

