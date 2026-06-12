---
title: "unable to compie mplayer in gui mode"
date: 2007-08-14
forum: Multimedia &amp; Video
---

### Post by feistybee on 2007-08-14
Hi

I have Ubuntu Edgy and I dont have internet connection :(.

So I used to download somewhere and install the same in m/c.

The additional packages installation are done thru apt-get. So I can't do anything in offline. Who made it like this? There sud be a way to do in offline also.

I have downloaded the mplayer source and tried to compile. It compiled fine in normal mode. But when I tried to compile in GUI mode, it throws error.

/usr/include/X11/Xlib.h:60:19: error: X11/X.h: No such file or directory
/usr/include/X11/Xlib.h:63:28: error: X11/Xfuncproto.h: No such file or directory
/usr/include/X11/Xlib.h:64:25: error: X11/Xosdefs.h: No such file or dir

I found that there is no file called X.h in the /usr/include/X11/.

Somebody can guide me, how I can do this offline?

Regards,
bee

---

### Post by deadgobby on 2007-08-14
You may be better off DL the deb file from
[http://packages.debian.org/stable/graphics/mplayer](http://packages.debian.org/stable/graphics/mplayer)
 However that VLC player is better, not too cool as looks go, but it does the job very very well.
[http://packages.debian.org/stable/graphics/vlc](http://packages.debian.org/stable/graphics/vlc)
Gobby

---

### Post by Gremlinzzz on 2007-08-14
You can get other deb packages for edgy here
[http://packages.ubuntu.com/edgy/allpackages](http://packages.ubuntu.com/edgy/allpackages)

---

