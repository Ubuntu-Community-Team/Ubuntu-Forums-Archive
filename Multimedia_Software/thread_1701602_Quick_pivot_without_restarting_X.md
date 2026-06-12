---
title: "Quick pivot without restarting X"
date: 2011-03-06
forum: Multimedia Software
---

### Post by amazing mustard on 2011-03-06
Hello,

I just bought two big 23" screens, set up in a standing/vertical position. This way I can load most webpages in a single screen without any scrolling. Life is good :)

Anyway, I don't game, but occasionally I want to preview/watch a movie on my computer screen, and the vertical position is undesirable for this. So, I use the pivot function of the screen(s).

Currently, for rotating I added the follinging line to my /etc/X11/xorg.conf in the Device section:

    Option     "Rotate" "CCW"

I works perfectly. The only problem is SWITCHING between the widescreen/landscape setup and vertical setup. I wrote a little script to comment out a certain section of my xorg.conf with sed and then restarting X. This is NOT ideal. I'd like to rotate my screen instantly, without restarting X. In Microsoft Windows, this can be done w/ CTRL+ALT+arrowkey, depending on your drivers.

Could anyone help me out?

OS: Ubuntu v10.10
GPU: NVIDIA GeForce 7025 / nForce 630a 
Screens: 2x Dell U2311H 23" (1080x1920 each)

Thanks in advance

---

