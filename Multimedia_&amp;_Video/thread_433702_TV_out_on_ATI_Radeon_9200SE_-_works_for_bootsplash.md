---
title: "TV out on ATI Radeon 9200SE - works for bootsplash but not X"
date: 2007-05-05
forum: Multimedia &amp; Video
---

### Post by nlogax on 2007-05-05
Hi all,
does anyone know how to get X.org to play nicely with the Radeon 9200SE's S-Video output plugged into a TV?  It displays text mode stuff and bootsplash (framebuffer) graphics perfectly...  it's only when X starts that the TV starts to go nuts.

We're using the open source 'radeon' driver, as there is no fglrx version for X.org 7.2 which supports this model of Radeon.  It doesn't seem as if we have a lot of options here.

Our xorg.conf is pretty vanilla, although we've dropped the resolution to 800x600 and 16 bit colour depth and set refresh:

    Option "HorizSync" 30.00 - 50.00
    Option "VertRefresh" 60

I've also attempted to get X.org working using the framebuffer, but in Feisty the framebuffer device file /dev/fb0 has disappeared!

Any help would be appreciated.

Thanks, Nlogax

---

### Post by glenndavy on 2007-05-20
bump!

---

### Post by gleesond on 2007-08-12
so I'm having the same problem, did you ever figure out how to get this to work?

---

### Post by nlogax on 2007-09-16
No, my brother has decided to stick with Windows for his media centre PC for the time being.

However, the recent ATI/AMD promise to provide full specifications and open source drivers for ATI hardware could make be what we have been waiting for.

---

