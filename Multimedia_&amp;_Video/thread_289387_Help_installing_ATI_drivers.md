---
title: "Help installing ATI drivers"
date: 2006-10-30
forum: Multimedia &amp; Video
---

### Post by Whitebread1 on 2006-10-30
I'm following the instructions provided [here]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI") and I've run into a problem.  I'm trying to configure xorg, and I'm getting this error:
Warning: Could not find configuration file
Please copy configuration file template to /etc/X11

Help anyone?

---

### Post by Whitebread1 on 2006-10-30
Guys, I've gotten past this problem, but I now have a new one.
When I run fglrxinfo to see if it was installed correctly, I get this error:

Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1)

I read the trouble shooting section, but it doesn't comment on how to deal with the missing XFree86-DRI error.

Help?

---

### Post by Bloged on 2006-10-31
This is because Edgy has Composite on by default and DRI + Composite isn't a good combination you have to disable the composite by putting this at the end of /etc/X11/xorg.conf
```

Section "Extensions"
        Option "Composite" "false"
EndSection

```

After that reload the fglrx module for the kernel with:
```

sudo rmmod -f fglrx
sudo depmod -a
sudo modprobe fglrx

```

Restart your X-server. If everything has gone well you now should have it all working.

Grtz,

Bloged

---

### Post by dakini on 2006-11-02
^ Thanks for that, Bloged.  I had the same error and your solution worked perfectly.  :)

---

