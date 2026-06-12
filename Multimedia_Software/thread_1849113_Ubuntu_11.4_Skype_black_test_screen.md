---
title: "Ubuntu 11.4 Skype black test screen"
date: 2011-09-23
forum: Multimedia Software
---

### Post by TheBlueMelon on 2011-09-23
Earlier this week, I was given this small handled PC.

The model is: **Sony VAIO VGN-UX390N**

So far, I finally got the webcam built in to work with Ubuntu. The webcam being a:[B]
 Ricoh Camera VGP-VCC8 [R5U870][/B]

After installing Cheese onto Ubuntu, the detects the webcam, and there is video. Skype also detects the webcam, but there is no video for the Skype Video Test Screen. Is there any fix for this? I keep looking around to find nothing that works, and I would really like to use this thing :(

---

### Post by TheBlueMelon on 2011-09-25
Help bump D:

---

### Post by fjanos on 2011-10-08
I have Genius Webcam e-messenger 112 on a desktop with the same problem any solution yet?

---

### Post by BigBananaMan on 2012-02-01
Bump again, I think everybody is having this problem and I've reached the conclusion of reasonable troubleshooting on two systems with no solution.  I'm seeing a lot of questions on Skype's forums but they keep making "windows tech support" styled answers like to plug the camera in :-|
Camera operates in cheese and is detected in skype at /dev/video0 but only displays a black screen and does not show up to the other person.  I can accept video from them.

When running skype it prints the following to both stdout and stderr:
```
/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(<unknown>:8144): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(<unknown>:8144): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so


(<unknown>:8144): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:8144): Gtk-WARNING **: Loading IM context type 'ibus' failed

(<unknown>:8144): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:8144): Gtk-WARNING **: Loading IM context type 'ibus' failed
/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(<unknown>:8144): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(<unknown>:8144): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so


(<unknown>:8144): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:8144): Gtk-WARNING **: Loading IM context type 'ibus' failed

```


2.6.38-13-generic x86_64 GNU/Linux

---

