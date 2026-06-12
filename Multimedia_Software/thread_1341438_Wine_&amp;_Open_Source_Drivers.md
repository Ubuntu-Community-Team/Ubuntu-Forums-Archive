---
title: "Wine &amp; Open Source Drivers?"
date: 2009-11-29
forum: Multimedia Software
---

### Post by morefeo on 2009-11-29
Hi all!

I have enabled 3d acceleration on my jaunty jackalope, my video card is ati radeon saphire 9250 and i'm using the open source drivers (I can't use the propietary ones, they're obsoletes).

The problem is, wine seems to not use 3d acceleration, so my question is: it's a problem of wine, a problem of drivers (maybe they don't give the features wine needs?) or it's my problem and i need to configure something?

Does anyone has 3d acceleration under wine with this video card?

Thanks in advance.

---

### Post by Melcar on 2009-11-29
If you have 3D acceleration under your Linux desktop, you will also get 3D acceleration under WINE.  Keep in mind that WINE needs OpenGL2.x for a lot of the stuff it does and the open source drivers are only OpenGL1.5; this will cause some games to either not run at all or run very slowly.

---

### Post by morefeo on 2009-11-30
Thank you for the answer.

I've got compiz enabled (but some effects like water desktop doesn't work) and I've played a 3d game (linux native) without errors and very smooth at high res (1680x1050), but in wine, I can't play games (just 1 tested..) and applications have some draw errors when I choose the virtual desktop (if I move the windows, some "rectangles" dissappear).

So...is there a problem I can solve or...is it normal?

---

### Post by benmoran on 2009-11-30
You can try installing the DirectX 9 dlls (try the winetricks script). They're still a bit more compatible, and may fix your problems. If that doesn't do it, you just have to wait until the Free drivers hit OGL2.x. I'm waiting patiently myself. Radeon Xpress 1150 here :p

---

