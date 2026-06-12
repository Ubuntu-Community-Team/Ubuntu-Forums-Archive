---
title: "how to watch fullscreen using mplayer"
date: 2008-09-22
forum: Multimedia Software
---

### Post by Daniel_wang on 2008-09-22
very strange is my mplayer can not watch the rmvb file in fullscreen even though I turn on it,

any idea will be appreciated.

---

### Post by shirilover on 2008-09-22
What video output method are you using?
If it's X11, you need to use the -zoom switch as well to display full screen.

---

### Post by Daniel_wang on 2008-09-23
sorry how to use -zoom to switch?

---

### Post by shirilover on 2008-09-23
One of the following ways:
```

mplayer -vo x11 -fs -zoom yourvideo.rmvb

```
or by adding the following to ~/.mplayer/config
```

# Use the following video output method
#vo=xv # This is the preferred video output
vo=x11

# Enable full screen when using X11/XShm output
fs=yes
zoom=yes

```

---

### Post by Daniel_wang on 2008-09-24
yes, it's done, thank you.

can you tell me why by default it can not watch in full screen

but, i need to configure it mannually?

---

