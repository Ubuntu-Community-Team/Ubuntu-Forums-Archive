---
title: "Screen resolution"
date: 2007-04-14
forum: Multimedia &amp; Video
---

### Post by ELMIT on 2007-04-14
I had to install the system of my laptop (Toshiiba Portege 3440CT) on another notebook and swapped the hard disk.
The file /etc/X11/xorg.conf   did not fit, I could not start graphic at all. I renamed it and restarted, and get now a screen of 800x600 max. Worse it has a 1" black frame around!

I can remember on another Linux system was a program sax (?) what allowed you to create a new xorg.conf. What can Ubuntu offer to set-up the screen resolution. The previous windows system could handle much higher resolutions, so the screen can handle it.

bye

Ronald

---

### Post by RaZer0r on 2007-04-14
you might want to try and install 915resolution package, it's in the source list, just run
sudo apt-get 915resolution, it modifies your screen res, and some more stuff to enhance grapics enabled controllers...

---

### Post by ELMIT on 2007-04-14
I found how to set-up at:

[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

Thanks!

bye

Ronald

---

