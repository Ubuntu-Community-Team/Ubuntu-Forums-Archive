---
title: "intel 945 video tearing - give up or not?"
date: 2009-02-07
forum: Multimedia Software
---

### Post by stando007 on 2009-02-07
Hi,
I have spent a looooooot ooooooof time searching internet for finding solution, but without success. When I am playing video (mplayer, totae, vlc) on fullscreen video on some scenes tears. It is not so much, but is annoying quite nice. When I compare to windows, the video in windows is silky smooth. I tried deactivating compiz, setting sync to vblank on/off in compiz, different drivers in mplayer... Nothing helps. It looks the image is being torn abit even when moving windows (but this would not be so much important for me).

My machine is Dell Optiplex gx620 P4-3GHz, 2.5GB DDR2 RAM, i945 vga, lcd 1680x1050.

The question now is if is reasonable to continue searching for some solving or not? Do not people who are developing ubuntu and linux stuff know about such problems? It would be enough to say "Unfortunately this has no solving, the video performance could not be better" and I will stop trying... Or to say "Install this, and configure this and it will be fine"

So what people? Should I believe linux is only for servers and low video performance desktop apps and Windows is also for multimedia entertainment? :confused:

---

### Post by stando007 on 2009-02-12
Just for info I have found the workaround:

"You have to tell xine to use xv_preferred_method=overlay (instead of textured)."

[http://forums.opensuse.org/applications/multimedia/404432-kaffeine-xine-vsync-problem-videos.html](http://forums.opensuse.org/applications/multimedia/404432-kaffeine-xine-vsync-problem-videos.html)

But I still have the question why does not it work wothout this?

---

### Post by densou on 2009-02-14
I had followed the *Multimedia Guide for Hardy* or similar (don't remember the correct thread title, it should be sticky) and Gecko works amazing. (I prefer it over mplayer/vlc/totem)

you can upgrade 2d drivers here:
[https://launchpad.net/~intel-gfx-testing/+archive/ppa](https://launchpad.net/~intel-gfx-testing/+archive/ppa)




From a 945 user. :P

---

