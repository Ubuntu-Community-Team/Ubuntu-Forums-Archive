---
title: "no sound in 10.4 LTS ON  HP probook 4515s"
date: 2010-05-05
forum: Multimedia Software
---

### Post by airz1 on 2010-05-05
hi, i have no sound on my laptop help please

---

### Post by fh_scott on 2010-05-05
I'm having all kinds of sound issues, too. I have a Dell Vostro 1500.

I'm not recommending you do this, but I've had the best result so far by removing pulseaudio. when I do this the only thing that doesn't work is the system sounds (login, "boops" when launching apps from the gnome panel, etc). You tube, VNC, Slacker Widget all play fine.

When pulse is installed, the slacker widget is the only thing that works, everything else sounds mute. alsamixer did show the "Speaker" at 00 but I raised it, to no effect.

---

### Post by lidex on 2010-05-05
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#*
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

---

### Post by airz1 on 2010-05-06
its alright now i found libflashsupport_1.0~2219-2_i386.deb installed it and it works fine now =]:guitar:

---

