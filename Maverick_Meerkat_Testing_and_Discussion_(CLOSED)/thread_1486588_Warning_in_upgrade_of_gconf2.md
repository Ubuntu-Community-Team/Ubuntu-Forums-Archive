---
title: "Warning in upgrade of gconf2"
date: 2010-05-18
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by zika on 2010-05-18
Processing triggers for gconf2 ...
WARNING: Failed to parse default value `[????????? ???????;gnome-appearance-properties.desktop,????????? ???????????? ???????????;gnome-default-applications.desktop,?????????? ??????????;system-config-printer.desktop] ' for schema (/schemas/apps/control-center/cc_actions_list)

---

### Post by dino99 on 2010-05-18
i've had too and cant boot with lastest ricotz kernel (2-10)

---

### Post by ranch hand on 2010-05-18
I got that warning.  Didn't pay too much attention to it as it does not seem to effect my performance at all.

I also assumed it was the OS finally catching on that printing just is not right at all with my old HP Deskjet 832C (yep it sure is a serial port printer).  Works fine on all versions up to 10.10.

Maybe I have been silly not to look into that warning more.

---

### Post by zika on 2010-05-18
> **dino99 said:**
> i've had too and cant boot with lastest ricotz kernel (2-10)I have no problem boot-ing with ricotz kernel, just get that warning whenever gconf2 is upgraded...

---

### Post by Kevbert on 2010-05-24
Do you get all this when upgrading to meercat?
```
Setting up gconf2 (2.28.1-3ubuntu1) ...
WARNING: Failed to parse default value `' for schema (/schemas/desktop/gnome/f-spot/ui/main_window_x)
WARNING: Failed to parse default value `' for schema (/schemas/desktop/gnome/f-spot/ui/main_window_y)
WARNING: Failed to parse default value `' for schema (/schemas/desktop/gnome/f-spot/ui/viewer_x)
WARNING: Failed to parse default value `' for schema (/schemas/desktop/gnome/f-spot/ui/viewer_y)
WARNING: Failed to parse default value `[????????? ???????;gnome-appearance-properties.desktop,????????? ???????????? ???????????;gnome-default-applications.desktop,?????????? ??????????;system-config-printer.desktop] ' for schema (/schemas/apps/control-center/cc_actions_list)
Setting up libgnomevfs2-common (1:2.24.3-1ubuntu1) ...

```
If you try running f-spot from terminal you may get [[COLOR="Red"]this error[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/585020").

---

### Post by jppr on 2010-05-24
updated  f-spot already 4 hours ago without any problems, and i can open, use and close f-spot normal way...

---

### Post by philinux on 2010-05-24
Yep plenty of warnings.

Old bug [https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/276272](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/276272)

---

### Post by dino99 on 2010-05-24
is it really gconf2 to blame ?

---

### Post by philinux on 2010-05-24
/usr/share/applications/gnome-appearance-properties.desktop

Well the first file it complains about has exactly the same contents in lucid as maverick.

---

### Post by xeizo on 2010-05-24
I've had those warnings too, but the box works and is able to reboot. I've used both Ricotz 2.10 and now 34-3.  Plymouth is fubar though, I have to disable splash every time I boot( grub, "e", uncomment splash, ctrl-x).

---

### Post by ronacc on 2010-05-24
could this be more of the libgtk2 mess ?

---

### Post by ranch hand on 2010-05-24
> **xeizo said:**
> I've had those warnings too, but the box works and is able to reboot. I've used both Ricotz 2.10 and now 34-3.  Plymouth is fubar though, I have to disable splash every time I boot( grub, "e", uncomment splash, ctrl-x).
You can change that to not have the splash in your /ect/default.grub file.

---

