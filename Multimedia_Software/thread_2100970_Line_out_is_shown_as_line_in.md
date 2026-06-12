---
title: "Line out is shown as line in"
date: 2013-01-03
forum: Multimedia Software
---

### Post by Panterogas on 2013-01-03
I use a MEDION AKOYA Laptop. With Ubuntu 12.10 and my Soundcard is ALC663        My problem is following:  If I plug my earphones in the front pannel (3.5 mm clinch) they are shown as Line In and I do not get any sound out of them.   So my ubuntu thinks that my earphones are a microphone. The mean thing is, when I plug my microphone in it is also shown as Line In and it works well.       at /usr/share/doc/alsa-base/driver/HD-Audio-Models.txt.gz  the part for ALC663 is only asus-mode1 to asus-mode8 all of them do not work,   when I change it at   sudo nano /etc/modprobe.d/alsa-base.conf      I have no idea how to make my Line Out a Line Out again.  If you have any idea how you could help me you will help me alot. Btw. I am Austrian, this is why my english is not the best but hopefully it will be good enough, that you will get my problem.  Fred

---

### Post by Panterogas on 2013-01-10
bump

---

### Post by tgalati4 on 2013-01-10
Line-Out will not provide enough power to drive headphones.  You need speaker or headphone out.  Many sound chips allow for swapping of Line-In, Line-Out, and Speaker.  They are simply analog pins out of a sound chip that can either read voltage in or put voltage out.

Besides asusmode switches, are there any other switches available?

A quick google search of:  "ALC663 linux module options"

Shows a host of bugs related to this chip:

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1040873](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/1040873)

---

### Post by Panterogas on 2013-01-21
but when i used windows in former times, my headphones worked well.  besides that I do not get how your link should help me. first of all I am not well versed with ubuntu and this link does not help me with my problem.

---

