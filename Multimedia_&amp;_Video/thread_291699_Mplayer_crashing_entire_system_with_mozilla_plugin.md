---
title: "Mplayer crashing entire system with mozilla plugin"
date: 2006-11-02
forum: Multimedia &amp; Video
---

### Post by Grog140 on 2006-11-02
Alright here is the routine;

Lately I have been having some major problems with the mplayer plugin. Yesterday and today I will have it crash my entire system if I try playing two movies at once in different tabs. It won't lock the mouse but nothing on the screen can be clicked and the curser will not change if I hover over things.

Then today recently I will be watching a live stream of a video and firefox will crash. When I restart firefox and watch it again it will crash my system like the previous crash.

Any assistance available?

---

### Post by Steve H on 2007-02-10
I had a similar problem where the mplayer plug-in would crash out my X-desktop. I read one of the forum entries that suggested having a look in /usr/lib/firefox/plugins and delete the following links to the totem player (which is installed by default in Ubuntu)

libtotem-basic-plugin.so
libtotem-basic-plugin.xpt
libtotem-complex-plugin.so
libtotem-complex-plugin.xpt
libtotem-gmp-plugin.so
libtotem-gmp-plugin.xpt
libtotem-mully-plugin.so
libtotem-mully-plugin.xpt
libtotem-narrowspace-plugin.so
libtotem-narrowspace-plugin.xpt

It worked for me, it might work for you. If not try looking at which video driver you are using in the preferences of Mplayer, that also caused issues for me at first. I ended up using gl2 instead of the defaulted xmga one which was being used and also caused crashes for me.

GOOD LUCK

---

### Post by Steve H on 2007-02-10
Further to my last reply, i have noticed that X11 codec also works with Mplayer, maybe try using that instead. It also is the necessary codec for online videos, such as BBC.

---

