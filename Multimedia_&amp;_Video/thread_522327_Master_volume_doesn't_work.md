---
title: "Master volume doesn't work"
date: 2007-08-10
forum: Multimedia &amp; Video
---

### Post by Chris_huh on 2007-08-10
My master volume in the taskbar doesn't make any difference to the volume. The only way i can change the volume is from within each individual program. Even if it gets put on mute sound still comes out.

Anyone know what might be happening?

---

### Post by phetre on 2007-08-13
> **Chris_huh said:**
> My master volume in the taskbar doesn't make any difference to the volume. The only way i can change the volume is from within each individual program. Even if it gets put on mute sound still comes out.

Anyone know what might be happening?

If you're running Gnome (i.e., regular Ubuntu), you can right-click on the taskbar's volume control, choose Preferences, and change the default channel (or whatever it's called) from "Master" to "PCM." At least you could on Feisty -- I'm using Kubuntu Gutsy now.

Unfortunately the global keyboard shortcuts deal only with the Master channel, so if you have volume-controlling keys on your keyboard, they still won't work. This older post ([http://ubuntuforums.org/showthread.php?p=1318003](http://ubuntuforums.org/showthread.php?p=1318003)) suggests one solution using xbindkeys, but it's really ugly. Before I try that, does anybody know a safe, sane way to change the which channel the volume keys control, especially in KDE? Thanks!

---

### Post by huzzak on 2007-10-21
I had the same problem and went to System>Preferences>Sound and then set Master and PCM as the default mixer tracks.  Now it done be fine.

---

### Post by phetre on 2007-10-22
> **huzzak said:**
> I had the same problem and went to System>Preferences>Sound and then set Master and PCM as the default mixer tracks.  Now it done be fine.

Perfect, thanks!

---

