---
title: "Gnome loads manually, but not at boot..."
date: 2006-07-15
forum: Multimedia &amp; Video
---

### Post by SFDD on 2006-07-15
I've messed something up, but I'm not sure what. When I boot up I get an error when X tries to load that the following file cannot be accessed:

/usr/lib/xorg/modules/xgl/libxglx.so

But the file is there; I can (at least) see it when I manually go to the directory. It's permissions are set to "-rw-r--r--" (It's owned by root.)

But if I log in and then manually run 'startx' I still get an error, but then Gnome loads and seems to work fine.

I have an nVidia card and I have installed the nVidia driver using the "envy" script.

When I check using Synaptic Package manager, it says that the GLX packages is installed. 

Perhaps a link has died or something that's confusing X when it loads on its own? Anyone have any fix ideas?

Thanks!

---

