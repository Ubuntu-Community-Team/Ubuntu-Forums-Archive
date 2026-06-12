---
title: "Latest proprietary ATI drivers causes screensavers to freeze"
date: 2008-07-10
forum: Multimedia Software
---

### Post by swinky on 2008-07-10
I installed the latest ATI drivers (Version 8.6) on my Ubuntu 8.04 machine using a Radeon X1950. I was really, really happy with the new drivers, they finally allow me to run fullscreen video and 3d programs without the annoying flickering problem I used to have while running Compiz Fusion. 

However, I find that ever since I installed these new drivers, any time my screen shuts down, the screensaver (Flying Toasters) freezes and won't shut itself off to let me use the computer. Restarting the X server with Ctrl+Alt+Backspace will bring the desktop back up, but it is of course not the best solution since I lose anything I was working on at the time. The screensaver works fine while the monitor is on (though to be fair, I have not sat here for the twenty minutes it takes to turn off the monitor to make sure), and I have not (yet) tried other screensavers. 

I really have no idea where to start looking for problems, does anybody have any ideas?

---

### Post by Fire_Chief on 2008-07-10
I experienced the same problem. At the moment, I worked around the problem by installing xscreensaver and disabling gnome-screensaver. It's not a pretty fix nor desired as a permanent one but for the moment the freezing is gone. I too would like to see a resolution to the problem.

I've got Ubuntu 8.04 using an ATI x1400 Mobility (Thinkpad T60) also with the Catalyst 8.6 drivers.

---

### Post by soxs on 2008-07-10
using 8.6 and everything is going fine (RadeonHD 3870, ubuntu 8.04 AMD64)
Note: I installed it according to method to in that thread
[http://wiki.cchtml.com/index.php?title=Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php?title=Ubuntu_Hardy_Installation_Guide)

---

### Post by swinky on 2008-07-11
> **Fire_Chief said:**
> At the moment, I worked around the problem by installing xscreensaver and disabling gnome-screensaver.

I tried xscreensaver and oddly enough it only made problems worse. The screensaver would freeze during previews as soon as I tried to exit out of it. It is definitely an OpenGL issue though, because as soon as I switch to a screensaver that is not 3D (i.e. "Galaxy") I don't have problems, whereas anything that uses OpenGL crashes. For now I guess I'll just stick with Galaxy as my screensaver, though I really hope this gets fixed soon. Luckily I don't seem to have any problems with any other OpenGL applications, so I guess it is not a huge issue.

---

### Post by sjhilton on 2008-07-13
I have the same problem. I have my drivers installed by updates through EnvyNG (I'm assuming it's up to date with 8.6).

---

### Post by swinky on 2008-07-23
ATI released version 8.7 of the Catalyst drivers on Monday, and after updating I no longer have the problem with the screensaver freezing. I would suggest anybody having problems with 8.6 upgrade to 8.7.

---

