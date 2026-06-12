---
title: "Nvidia monitor dpi causing white fringing on text"
date: 2007-08-07
forum: Multimedia &amp; Video
---

### Post by scaaryfast on 2007-08-07
After installing the nvidia-glx-new drivers, text in KDE on my 1280x1024 LCD screen now has a white aliased effect around it.

This did not occur with the default nv driver, but also occurs with the nvidia-glx drivers.

The aliasing effect is very subtle and is sub-pixel sized on both sides of text characters on a grey/mid coloured background. It only appears in the horizontal plane (e.g. is not around the top and bottom of characters, only the vertical sides).

The Nvidia settings tool indicates that the screen resolution is 95x96 dots per inch and I have a hunch that this is what's causing the problem.

Can anyone help?

---

### Post by nick_h on 2007-08-07
I don't use KDE myself so perhaps someone could confirm this.

You can pass the option *-dpi 96* to the X server by changing the *ServerCmd* line in */etc/kde3/kdm/kdmrc* file.

You can check the result by typing:
```
xdpyinfo | grep resolution
```

---

### Post by scaaryfast on 2007-08-08
Thanks for the reply.

I tried adding the -dpi 96 option and 
```
xdpyinfo | grep resolution
```
Returns:
```
resolution:    96x96 dots per inch
```
However, the fringing/aliasing is still there :(

This may be my eyes here, but the root desktop environment seems to look ok.

Any more ideas?

---

### Post by uluman on 2008-02-07
Did you ever find a solution to this?

---

