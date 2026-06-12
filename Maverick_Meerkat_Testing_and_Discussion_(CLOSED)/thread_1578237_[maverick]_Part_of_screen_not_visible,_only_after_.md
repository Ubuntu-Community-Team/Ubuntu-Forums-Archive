---
title: "[maverick] Part of screen not visible, only after reapplying resolution."
date: 2010-09-20
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Sh4wn on 2010-09-20
Hi guys,

I recently upgraded to Ubuntu maverick beta, and there's one thing that's quite annoying:

This is how my screen should look like after boot:

[[img]http://www.imgdumper.nl/uploads3/4c97262b6e1f3/4c97262b25f9f-Screenshot.thumb.jpg[/img]](http://www.imgdumper.nl/uploads3/4c97262b6e1f3/4c97262b25f9f-Screenshot.png)

This is how it looks like after a boot:
[[img]http://www.imgdumper.nl/uploads3/4c9727706642d/4c9727701e5a4-Screenshot.thumb.jpg[/img]](http://www.imgdumper.nl/uploads3/4c9727706642d/4c9727701e5a4-Screenshot.png)

As you can see, on the left side, there's a big part missing. Only after starting nvidia-settins, setting my resolution to something else, apply, and change it back to my original resolution (1280x1024) my screens look good again. 

As you probably know now: I'm using the nvidia restricted driver. It's a clean install (no update-manager -d), and if you need any more information, please say so.

Anyone got an idea how to fix this?

---

### Post by Iowan on 2010-09-20
Moved to Maverick Meerkat Testing and Discussion

---

### Post by cariboo on 2010-09-20
When you move your mouse to the left does the desktop move so that you an see what is there?

---

### Post by Sh4wn on 2010-09-20
Nope, it doesn't move when I put the mouse there. You can also see it at the login screen, the login dialog isn't properly aligned in the center (as you can imagine, it is a little bit moved to the left)

---

### Post by oasick on 2010-09-20
I have a similar problem. I explained here, but still not repaired...

[http://ubuntuforums.org/showthread.php?t=1575412](http://ubuntuforums.org/showthread.php?t=1575412)

---

### Post by pulpo69 on 2010-09-20
i can confirm this problem, i have since acouple of weeks.
Even a fresh install didn't solve the problem.

---

### Post by cariboo on 2010-09-20
Do you have the same problem when using the nouveau drivers?

---

### Post by pulpo69 on 2010-09-20
i forgot, i use an ati-card, monitor connected with an HDMI-cable.
All worked fine in Lucid Lynx.

---

### Post by oasick on 2010-09-20
> **cariboo907 said:**
> Do you have the same problem when using the nouveau drivers?

I use nouveau driver and I have the same problem

---

### Post by DevHead on 2010-09-20
> **pulpo69 said:**
> i can confirm this problem, i have since acouple of weeks.
Even a fresh install didn't solve the problem.

Ditto.

---

### Post by Sh4wn on 2010-09-21
Funny part: After installing the beta from the CD, it actually worked. But then, after installing the upgrades -> problems.

---

### Post by DevHead on 2010-09-21
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/641525](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/641525)

This is the problem I'm seeing.

---

### Post by Sh4wn on 2010-09-22
> **DevHead said:**
> [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/641525](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/641525)

This is the problem I'm seeing.

Yes, it's very likely it's the same bug, with the only differences I use nvidia driver, and with me everything is shifted to the left.

---

### Post by DevHead on 2010-09-22
Interesting.  ATI to the right and nVidia to the left.

---

### Post by oasick on 2010-09-22
I have a nvidia FX5900 with nouveau driver and my desktop before reapplying resolution look like this:
[[IMG]http://img227.imageshack.us/img227/3771/pantallazo2g.th.jpg[/IMG]](http://img227.imageshack.us/i/pantallazo2g.jpg/)

After reapplying resolution look like this:
[[IMG]http://img837.imageshack.us/img837/6715/pantallazor.th.jpg[/IMG]](http://img837.imageshack.us/i/pantallazor.jpg/)

You can see that a part of right and down screen is missing.

---

### Post by oasick on 2010-09-23
I fix it with this solution 

[http://ubuntuforums.org/showpost.php?p=9878880&postcount=5](http://ubuntuforums.org/showpost.php?p=9878880&postcount=5)

:):)

---

### Post by Sh4wn on 2010-09-24
With the proprietary driver that fix doesn't work.. (as you can't use gnome-display-properties)

---

