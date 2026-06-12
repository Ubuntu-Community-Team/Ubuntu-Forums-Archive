---
title: "VLC not allowing laptop to sleep"
date: 2009-03-12
forum: Multimedia Software
---

### Post by Vitamin_A on 2009-03-12
Hello all.

I have just tried to put my laptop to sleep, but, as soon as I try to, I get a notification bubble emanating from the battery icon saying:
**Request to suspend**
**vlc** has stopped the suspend from taking place: **Playing some media.**.

The main problem here, is that I didn't run vlc since I turned on my computer, and, I was able to put it to sleep numerous times in between start-up and now.  Additionally, vlc is not in the processes list of my system monitor.

How do I solve this problem?
Thanks.

---

### Post by sunset_studies on 2009-03-14
hi, I've had this problem too except I've always been running vlc some time between boot and the problem appearing. Every time I've checked and there's definitely been no instance of vlc running though, so I think there's a vlc bug that needs fixing here.

Anyway, my solution which applies regardless of the app preventing the suspend:

open a terminal and enter

killall gnome-power-manager
gnome-power-manager

then you should be able to suspend again.

---

