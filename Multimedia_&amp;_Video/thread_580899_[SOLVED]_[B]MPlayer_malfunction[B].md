---
title: "[SOLVED] [B]MPlayer malfunction[/B]"
date: 2007-10-19
forum: Multimedia &amp; Video
---

### Post by Marinodimare on 2007-10-19
Hi,

Ever since I upgraded to 7.04 some months ago, I have trouble with my MPlayer setup. The thing is, it won't play DVDs, and it won't go to full screen mode. That is, when I turn on full screen, the video is displayed in it's original size, surrounded by a full screen black background. I hoped the upgrade to 7.10 would solve the problem, but alass... Any ideas?

M.

---

### Post by andreeh on 2007-10-19
No idea why it won't play your DVD's, but for the fullscreen issue, try adding -zoom to your command line.

---

### Post by Marinodimare on 2007-10-21
Good idea, it seems to work. I'd like to add the -zoom option as an alias, so that it will be activated when I use the graphical interface, and choose full screen mode. Could you tell me how to do that?

M.

---

### Post by Marinodimare on 2007-10-21
hi,

I edited the /etc/mplayer/input.conf file to include 

zoom=yes

and the problem was solved. Still, there is another question. I'd like MPlayer to go in and out of fullscreen mode when I double-click the video window. However,. I didn't find any examples in named file how to ocnfigure mouse behaviour. Does anyone have any idea?

M.

---

### Post by Nameless_one on 2007-10-22
By the way, I had the same problem, and this is no solution whatsoever. The zoom option is software-based, which means that watching something in fullscreen mode uses a lot of CPU, and in my case there were short pauses every now and then during playback. Mplayer was reporting that there was no XVideo support for my card and so it was using the x11 output driver as a fallback option. 

Searching high and low, I found that certain old versions of the fglrx driver for ATI cards (and incidently the one that is in the Edgy repositories), have trouble with Xv, if I remember correctly. The problem was solved after a clean Gutsy install, with a much later fglrx version. You'd be surprised at how far back Edgy is in fglrx. 

If mplayer whines about xv, this is probably what's wrong. If you are having trouble with this, PM me and I will at least point out the things I found back when I did too. That is if Gutsy doesn't solve the problem for you. ;)

---

### Post by Marinodimare on 2007-10-23
Thanks for the reply! Fortunately, my machine is fast enough to handle the software-based zoom function, I don't notice anything out of the ordinary. Unfortunately, I have an ATI x1600 card, so, hardware zooming is out. I'll wait for the new ATI driver to come out, if all goes well version 8.42 sould solve quite a few problems.

---

