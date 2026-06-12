---
title: "no dri with xgl"
date: 2006-09-10
forum: Multimedia &amp; Video
---

### Post by ghotra on 2006-09-10
Hi, I just installed xgl on my laptop with an intel 915 video card.  Everything seems to be working...just slowly.

# glxinfo | grep direct
direct rendering: No

Clearly, this is an issue.  Before I installed xgl, I did have direct rendering.  Is there something I can do so that I have direct rendering with xgl?  In my xorg.confg, I have

Option "DRI" "true"

under my video...this did not help.

Here is my .xsession

```

# Start up Xgl, compiz, and GNOME

# Run Xgl server on :1, on top of normal X
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &

# Tell subsequent X programs to access the Xgl server at :1
DISPLAY=:1

# Start Compiz window manager
gnome-window-decorator &
compiz gconf decoration fade cube rotate zoom scale move resize place menu switcher &

# Start GNOME
exec gnome-session

```

Any help is appreciated.dri

---

### Post by whatever on 2006-09-10
you cannot have dri in xgl. if you want dri - don't use xgl.

---

### Post by semakwetu on 2006-09-10
You need to edit the Module section of /etc/X11/xorg.conf look for Load "dri" and put a # in front of it

#	Load	"dri"

---

### Post by Ziox on 2006-09-10
you probably have DRI...if you run a normal Gnome/KDE/XFCE session, then it'll probably tell you that direct rendering is yes...XGL for some reason doesn't tell you it...so...if I were you, I wouldn't worry about it....

the slowness is probably because of your graphic card or some hardware insufficiency...

---

### Post by ghotra on 2006-09-10
So is AIGlx recommended instead of xgl?  This is a laptop with an Intel Graphics Accelerator 950.

---

### Post by Ziox on 2006-09-10
I'm not too clear on the differences between AIGLX and XGL, so it up to your what you want to do....

---

### Post by mgpower0 on 2006-09-10
AIglx is meant to be better for laptops and it does use the dri drivers. I have XGL on desktop and AIglx on lappy and both are pretty much identical.

If you don't want to go through installing it all again, first check that the blur plugin is disabled as this slows XGL and AI down quite significantly

---

