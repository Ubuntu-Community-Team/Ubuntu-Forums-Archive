---
title: "Window is too far right"
date: 2007-02-28
forum: Multimedia &amp; Video
---

### Post by eschamp on 2007-02-28
I just installed 6.10 on a Dell 2400 with Intel 845 video and a Viewsonic VX900 monitor.

The Ubuntu window is too far to the right - is there a way to shift it in Ubuntu? I already have shifted it and resized it with the Viewsonic controls.

Thanks.

---

### Post by Ferrat on 2007-02-28
> **eschamp said:**
> I just installed 6.10 on a Dell 2400 with Intel 845 video and a Viewsonic VX900 monitor.

The Ubuntu window is too far to the right - is there a way to shift it in Ubuntu? I already have shifted it and resized it with the Viewsonic controls.

Thanks.

You need to mess around with your xorg.conf but yes you can move it and sometimes (often) it's just some setting that's wrong and that pushes/distorts the picture, had the same problem with Dual Screen on my LCD widescreen.

---

### Post by eschamp on 2007-02-28
> **Ferrat said:**
> You need to mess around with your xorg.conf but yes you can move it and sometimes (often) it's just some setting that's wrong and that pushes/distorts the picture, had the same problem with Dual Screen on my LCD widescreen.

Where is xorg.conf located?

Thanks.

---

### Post by christhemonkey on 2007-02-28
/etc/X11/xorg.conf

(obviously you need to be root to edit it:))
```
sudo nano /etc/X11/xorg.conf
```

---

### Post by eschamp on 2007-02-28
Found it but I don't see anything in it that deals with positioning. ???

---

### Post by christhemonkey on 2007-02-28
Ok, its a bit hacky, but you need to add a Mode option to the Monitor section and then add the mode to your display subsection.

See here:
[http://www.die.net/doc/linux/man/man5/xorg.conf.5.html](http://www.die.net/doc/linux/man/man5/xorg.conf.5.html)
(or type man xorg.conf on your machine)

---

### Post by eschamp on 2007-02-28
> **christhemonkey said:**
> Ok, its a bit hacky, but you need to add a Mode option to the Monitor section and then add the mode to your display subsection.

See here:
[http://www.die.net/doc/linux/man/man5/xorg.conf.5.html](http://www.die.net/doc/linux/man/man5/xorg.conf.5.html)
(or type man xorg.conf on your machine)

Yuck! If Ubuntu recognizes the video hardware and the monitor, why is there a need to do this?

Is it possible to damage my monitor if I give xorg.conf wrong data?

---

