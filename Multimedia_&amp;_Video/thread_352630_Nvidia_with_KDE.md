---
title: "Nvidia with KDE"
date: 2007-02-03
forum: Multimedia &amp; Video
---

### Post by Patrick K on 2007-02-03
I have the Nvidia driver installed and running with Ubuntu Gnome. I just installed KDE and noticed in the KDE configuration editor that the card is using the "nv" drivers. Xorg.conf has "nvidia" for the driver to use. GL screensavers refuse to run so I think the "nv" drive is actually in use. The Nvidia control panel launches from the menus the same as in Gnome. I didn't see any options for disabling or enabling Open GL. There are a few GL setting available. 

Does KDE use the same xorg.conf file as Gnome? If not, where does it get it's driver settings?

The KDE config applet doesn't have a change driver option. So how do I get the "nvidia" driver working, or at least get GL working.

---

### Post by taurus on 2007-02-03
There is only one /etc/X11/xorg.conf so doesn't matter if you run Gnome, KDE, XFce4, fluxbox, etc.  So look in there to make sure the Drive is nvidia.

```
kdesu kate /etc/X11/xorg.conf
```

---

### Post by Patrick K on 2007-02-03
> **taurus said:**
> There is only one /etc/X11/xorg.conf so doesn't matter if you run Gnome, KDE, XFce4, fluxbox, etc.  So look in there to make sure the Drive is nvidia.

```
kdesu kate /etc/X11/xorg.conf
```

That's what I thought. And yes, nvidia is the driver in xorg.conf. 

I wonder why the GL screensavers don't work. Not that I'm that interested in the screensavers as such, but I'd like OpenGL to work.

---

