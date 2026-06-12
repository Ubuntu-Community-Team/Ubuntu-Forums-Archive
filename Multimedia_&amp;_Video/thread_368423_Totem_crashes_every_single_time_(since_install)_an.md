---
title: "Totem crashes every single time (since install) and takes entire system"
date: 2007-02-23
forum: Multimedia &amp; Video
---

### Post by colinnwx on 2007-02-23
Hey everyone,
I'm a first time Ubuntu user (fresh off Windows) and installation was kind of a hairy process for me (story for another day). When I ran the live CD, I tried out the Totem movie player, and the entire screen hung with the cursor on the ticking clock immediately, shortly after which I was promptly booted to a black screen and nothing got me out except for the power button.
Of course, being fresh to Linux and hearing about it's famous stability this was kind of a rude shock for me but I went ahead and installed it anyway : )
Every time I've run Totem, the same thing has happened since then without fail.
I posted the original bug at Bug Launchpad where a gentleman called Sebastien was kind enough to help me out but we found that it wasn't a totem bug after examining my /var/log/syslog, /var/log/messages and /var/log/Xorg.0.log. The original thread is here:

[https://launchpad.net/ubuntu/+source/totem/+bug/81614](https://launchpad.net/ubuntu/+source/totem/+bug/81614)

I've decided to bring it to this forum to give it a little more attention.
FYI, i have a dual boot setup with XP and Ubuntu Edgy Eft, and a shared FAT32 hard drive partition where my video files are on. My graphics controller is an Intel Mobile 915 GM / GMS /910GML Express. Or that's what it says under Device Driver. Sorry for being clueless but i don't know how to check my video drivers.
I think that's most of the information I can provide right now. Please help me out! Not being able to watch videos is a pretty big hurdle!
Thanks in advance you guys.
Colin

---

### Post by louis_nichols on 2007-02-23
Hi colinnwx. Sorry to hear about your problem. Hope it won't get you down and leave a bitter taste about Linux. I know what I'll be proposing here is not an actual solution, but you might take it into consideration.

How about using a different media player? The great thing about Linux and open source in general is you have many choices. There are many other very good media players. vlc, mplayer, gxine are just a few. I especially recommend vlc, because it supports most formats and is in my opinion the simplest to use.

---

### Post by colinnwx on 2007-02-25
Hey all,
I followed Louis' advice and installed VLC media player and it loaded fine, but when I tried to open a movie, the sound loaded for about 1s followed by the VLC screen turning blue and then being booted out (once again) to a black screen with the ticking cursor.
Looks like it's a video card problem?
Not sure how to go along with this though. Any idea what steps I can take next to try n get it to work? Any other drivers i can load? Really not sure how to proceed from here.
Colin

---

### Post by elfgoh on 2007-08-08
Well i have met up with colinnwx and manage to pin point the problem. Seems that it is a problem with the xorg i810 driver. The problem has been resolved by using xorg vesa driver.

However, as vesa does not provide graphics acceleration, he has to switch back to metacity as window manager. So no more aiglx for him.

Any ideas if this bug can be resolved?

---

