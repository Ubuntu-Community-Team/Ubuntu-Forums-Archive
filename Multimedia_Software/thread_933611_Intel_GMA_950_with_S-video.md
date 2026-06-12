---
title: "Intel GMA 950 with S-video"
date: 2008-09-29
forum: Multimedia Software
---

### Post by C.S.Cameron on 2008-09-29
I'm thinking of building a mini ITX system using the Intel D945GCLF2 motherboard with dual-core Atom and S-video.
I understand there are issues with S-video and Intel graphics.
Has anyone managed to get S-video working with Intel GMA 950.

---

### Post by kappe on 2008-10-07
i have buy this MB one week ago, instal ubuntu 8.04 but i don't know how to configure the s-video output, anyone can help me?

---

### Post by viperet on 2008-11-26
I have this MB too, with Ubuntu 8.10 S-Video our is working at least partialy - image on TV is in black and white

---

### Post by jdusablon on 2008-12-07
I also am having issues with this. I got TV-out working with colour, but desktop size is too big for screen size. Resolution and other monitor/video functions are acting weird.

---

### Post by glurgle on 2008-12-10
Hey would anybody who has gotten it working at all mind posting how they did it? I have the same board and I am stuck at xrandr refusing to believe my TV is connected. (xubuntu 8.10)

---

### Post by jdusablon on 2008-12-11
I reduced my resolution to 800x600, which forced 60Hz vertical refresh. This allowed me to use the desktop, but as soon as xorg needs to do overlay or switch into another mode, the screen starts rolling. Apparently, the hardware is OK, because windows can handle it. It's an xorg problem.

I'm hoping someone will correct this soon, because I like this Atom mobo.

---

### Post by glurgle on 2008-12-11
could you do me a favour and post the output of "sudo xrandr --verbose"? I can't get mine to see that the TV is connected, so it won't let me enable the display.

Or if you had to make a custom xorg.conf that would be useful as well

---

### Post by Lure on 2008-12-14
On mine, it detects the TV properly, but the display is only on half the TV screen (squeezed) and rolling (up-down). :-(

I have attached my xrandr output.

---

### Post by Lure on 2008-12-21
This seems to be upstream issue with some possibility to get fixed for Jaunty.

See:
[https://launchpad.net/bugs/298422](https://launchpad.net/bugs/298422)
[https://bugs.freedesktop.org/show_bug.cgi?id=17776](https://bugs.freedesktop.org/show_bug.cgi?id=17776)

---

### Post by Wolframator on 2009-02-03
Are there some news/updates/... ?

---

### Post by fjmv on 2009-06-09
> **Lure said:**
> On mine, it detects the TV properly, but the display is only on half the TV screen (squeezed) and rolling (up-down). :-(

I have attached my xrandr output.

Hi, I have exactly the same problem. I have just bought a mini-itx based on Intel D945GCLF2, with s-video output, but I am unable to watch it on my tv properly. The xrandr --verbose and xrandr show the same information as in your case.

Any new information?

---

