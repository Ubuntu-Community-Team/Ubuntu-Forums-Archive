---
title: "opengl makes screen flicker (ati)"
date: 2005-10-26
forum: Multimedia &amp; Video
---

### Post by barongas on 2005-10-26
I've installed the fglrx-packages on my hoary system, like so:
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 XT Generic
OpenGL version string: 1.3.4769 (X4.3.0-8.8.25)

But whenever I load an opengl app (like glgears) I get small horizontal flickery disturbing things over my screen.
I tried editing my HorizSync and VertRefresh but that resulted in X loading mesa (without the flicker though).

So anyone know what to do or where to start looking for it?

---

### Post by RSX311 on 2005-10-26
I kinda get the same thing after I installed the fglrx drivers. when I play a movie the screen tears horizontally like in games where vertical sync is off.  I've tried changing my refresh rate but that didn't help.  Or when I try to move a window really fast the window gets torn up and it looks like the rest of the window is trying to catch up with my movement.  Any ideas?

---

### Post by pepolez on 2006-08-12
i have the same issue on my system, it occurs on any opengl application, even if the application is not currently visible.

quite annoying when playing games such as enemy territory (natively)

---

### Post by pudgypaw on 2006-09-30
over here i'm getting vertical tearing whenever i move any window to the right side of my widescreen monitor (dell 20.1" fpw; ATI X1800)

login screen has insane tearing/flickering. FVWM-Crystal also has insane tearing.

---

### Post by pudgypaw on 2006-09-30
sorry to double post but i just found a solution, use this code:

sudo dpkg-reconfigure -phigh xserver-xorg

after that all the tearing stopped, they detected the proper sync rates.

---

### Post by winallsys on 2008-06-01
Sorry for this question but...

how exactly do you enter the code? I have the exact same promlem and it really bugs me. :sad: I haven't seen the problem in videos, but it really annoys me in 3d games.

---

### Post by CalvinAnderson on 2008-06-04
Seems to be that it is Compiz.  Turn that off and then there are no problems.

Worked for me.  Macbook Pro 1.8ghz with ATI x1600

---

### Post by Soo on 2008-06-13
> **pudgypaw said:**
> sorry to double post but i just found a solution, use this code:

sudo dpkg-reconfigure -phigh xserver-xorg

after that all the tearing stopped, they detected the proper sync rates.

Seems that in doing this I can only launch GNOME in failsafe mode.

---

