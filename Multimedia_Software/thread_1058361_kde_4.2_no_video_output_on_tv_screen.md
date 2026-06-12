---
title: "kde 4.2 no video output on tv screen"
date: 2009-02-02
forum: Multimedia Software
---

### Post by sniffy96 on 2009-02-02
Hi:

I'm running kubuntu 8.10 with the kde 4.2 packages on an old laptop with a tv out card. When I hook the laptop up to a tv, I get a second display but any video programs (eg. dragon player, mplayer) display a black window on the tv and no video (the video does play correctly on the laptop screen). If I change the video output in mplayer to -vo gl the video does display on the tv, but I get maybe 3 frames/sec (so still unplayable). 

specs:
kubuntu 8.10 (with kde 4.2 from kubuntu packages) 
dell inspiron 4100
ati radeon mobility 
tv out using s-video cable

I've seen some postings on the web, but they seem to be out of date (eg. older than 2005). 

I get output to the tv by opening a console and running:
xrandr --addmode s-video 800x600
xrandr --output s-video --set tv_standard ntsc
xrandr --output s-video --mode 800x600

Once I do that, I get a my desktop on the tv

thanks

---

### Post by du@dde on 2009-02-17
Have you tried to set the Xv overlay to appear on the TV with the following command?
xvattr -a XV_CRTC -v 1
A 0 instead of the 1 and you will be back where you started.

GL

---

