---
title: "Vsync in movies (Divx, Xvid, H264), and other questions.."
date: 2008-07-05
forum: Multimedia Software
---

### Post by Shadow_Fi on 2008-07-05
Im total noobie here, first time usin Linux, but im learning! Anyway, i have a maybe stupid questions, but...

1. how i get VSYNC working in movies? I have fast enough PC, GF8800GT with manually installed newest drivers, and its fully working. So is Vsync even possible in linux? :D

2. What player is most popular / best in ubuntu? 

3. Is there something like Ffdshow on linux? Like postprocessing, blur effects plugin? 

4. How i get internal ac3 track working with h264 video?

---

### Post by Shadow_Fi on 2008-07-06
No one can answer me? Too stupid questions? ;)

---

### Post by Prefix100 on 2008-07-06
1. Why do you want to enable vsnyc? it should be done easily enough via the nvidia controls, type ' sudo apt-get install nvidia-settings ' into a terminal, then when its installed type nvidia-settings.

2 and 3. VLC media player. [http://www.videolan.org/](http://www.videolan.org/)

---

### Post by shirilover on 2008-07-06
> **Shadow_Fi said:**
> Im total noobie here, first time usin Linux, but im learning! Anyway, i have a maybe stupid questions, but...

2. What player is most popular / best in ubuntu? 
I prefer an svn build of MPlayer.

3. Is there something like Ffdshow on linux? Like postprocessing, blur effects plugin? 
FFdshow is merely a win32 port of FFmpeg. Postprocessing and others can be configured in your media player.

4. How i get internal ac3 track working with h264 video?
Not sure I understand this. If you want to combine an H.264 video stream with an AC3 audio stream, I suggest muxing them in a matroska container. This can be done by installing mkvtoolnix and running mmg.

---

### Post by Shadow_Fi on 2009-02-21
Well, after long time, i didnt find any solution at all....

Funniest thing is, that, Im on laptop, installed linux, X3100 Intel accelerator.. AND SAME PROBLEM!

Ive tried, Ubuntu, Mandriva, Mint... Same same same... No vertical sync. 

This is making me crazy for real... 

Compiz works fine. Mplayer, VLC, both are having this issue.

BTW i have been succesful to make a screenshot! ;)

[http://img4.imageshack.us/img4/4581/nosync2.jpg](http://img4.imageshack.us/img4/4581/nosync2.jpg)

Any one have some idea?

IS VSYNC POSSIBLE in Linux?

---

### Post by DavidBeijer on 2009-02-21
The Vsync should be configurable in the nVidia configuration program. I also have had lots of tearing in videos, it finally got solved by switching off Compiz desktop effects (and using Metacity instead) and rendering to a gl surface. This setting should be settable in the mediaplayer of your choice.

---

### Post by Shadow_Fi on 2009-02-21
> **DavidBeijer said:**
> The Vsync should be configurable in the nVidia configuration program. I also have had lots of tearing in videos, it finally got solved by switching off Compiz desktop effects (and using Metacity instead) and rendering to a gl surface. This setting should be settable in the mediaplayer of your choice.

Nope, that didnt help.

---

### Post by Prometheus28 on 2009-03-03
vsync is not possible in ubuntu. 

[http://img7.imageshack.us/img7/2005/vsyncbrokenlatesti386.png](http://img7.imageshack.us/img7/2005/vsyncbrokenlatesti386.png)


To test for yourself:: move a dark window against a light background rapidly, at the same time attempt a screenshot.

Tearing is always occuring even with compiz off, but it is far less obvious. When you turn compiz on any existing tearing gets severly exaggerated. Tearing also occurs with the open source nv drivers. something must be done.

[http://img7.imageshack.us/img7/2005/vsyncbrokenlatesti386.png](http://img7.imageshack.us/img7/2005/vsyncbrokenlatesti386.png)


Freedesktop.org: the people who make xorg-server (which both kde and gnome use) don't even know what vsync is or why anyone wants it.

[http://www.freedesktop.org/wiki/FindPage?action=fullsearch&context=180&value=vsync&fullsearch=Text](http://www.freedesktop.org/wiki/FindPage?action=fullsearch&context=180&value=vsync&fullsearch=Text)

Your search query "vsync" didn't return any results. Please change some terms and refer to HelpOnSearching for more information.

---

