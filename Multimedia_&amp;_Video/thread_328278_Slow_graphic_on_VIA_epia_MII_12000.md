---
title: "Slow graphic on VIA epia MII 12000"
date: 2006-12-30
forum: Multimedia &amp; Video
---

### Post by Staach on 2006-12-30
I´m having a problem with very slow graphics on my VIA EPIA MII 12000. I have looked around but am not sure if this is covered else where. 
My problem is this: it seems the pc´s screen update is very slow. When I move a window around on the screen it doesn't "remove" the "old" windows untill I stop dragging the window around. However when I play a movie with Totem (tried .avi) it "only" uses 60% or less of the cpu.
Can any one help me with an advice?:confused:

---

### Post by crispy_420 on 2006-12-30
video driver issue?

what desktop/specs do you have?

if low try xfce as your desktop.

just my 2 cents...

---

### Post by Staach on 2006-12-31
While this might help, I cannot believe a 1,2GhZ, 512Mb Ram pc cannot run gnome!!! Any one else who might have an idea? I know a lot have problems getting dri up and running but it seems that mine is running..](*,)

---

### Post by Staach on 2007-01-03
Please..can no one help me on this???:(

---

### Post by hackeron on 2007-05-19
There is a slight improvement if you edit /etc/X11/xorg.conf and change VESA to VIA -- but there's a huge improvement if you follow the instructions here:

[https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)

The instructions aren't very trivial and keeping things up to date with ubuntu is a pain in the *** as an apt-get dist-upgrade can break everything, but the improvement is fantastic.

---

