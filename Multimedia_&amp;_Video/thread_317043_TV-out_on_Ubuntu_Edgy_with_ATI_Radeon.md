---
title: "TV-out on Ubuntu Edgy with ATI Radeon"
date: 2006-12-11
forum: Multimedia &amp; Video
---

### Post by josef_renklint on 2006-12-11
Hi! 

I've just migrated from Windows XP and I'm very pleased with my experience so far. The one thing I can't seem to be able to get going is watching movies on my TV using the tv-out on my graphics card. 

Getting my screen on the TV worked right after installation, but whenever I started playing a movie, the window where there were the movie was supposed to be always went black. After some dabbling with the settings and MPlayer I actually got an image in that window, but the problem is I can't get it centered on my TV. It's always off-set a little bit to the left and top, respectively. I'm using fglrx for graphics driver.

Any ideas, or anyone who has had the same problem but has gotten it to work, please reply here or e-mail me directly. 

kind regards, josef

---

### Post by fabbaz on 2006-12-27
i have the exact same problem.
i tried to mess around with the "multimedia" video settings, but that didn't do anything.
the testcolor video viewed there is visible on both screen and tv correctly, but any video, no matter what codec used, is only visible on my screen, on the tv there is only a black placeholder where the overlay is supposed to be.

---

### Post by Mateo on 2006-12-27
Similar problems here.

You can get the video to show up if you go into /etc/X11/xorg.conf and set overlay to off.

But my screen is still not perfectly centered.  Not sure how to fix it.  Just as a tip, using the terminal program "aticonfig" you can make adjustments.  i tried some but never saw in differences.  getting any help on the subject is difficult as well.  i'll reply here if I figure anything out.

---

