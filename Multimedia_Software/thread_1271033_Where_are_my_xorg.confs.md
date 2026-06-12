---
title: "Where are my xorg.confs?"
date: 2009-09-20
forum: Multimedia Software
---

### Post by MalphasWats on 2009-09-20
Hi,

  I was running my UNR eee on an external projector and I wanted to actually give the display a name (rather than just UNKNOWN) and add in an extra resolution I knew it supported but when I edit my /etc/X11/xorg.conf file, all I have is:

```
Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        SubSection "Display"
                Virtual 1360 1368
        EndSubSection
EndSection

Section "Device"
        Identifier      "Configured Video Device"
EndSection

```

Which was a little disappointing. I'm an 'intermediateNoob' with linux, so I'm not entirely sure where else to look, I did try grepping for the name of the primary panel (LAPTOP 10") to see if I could find where it was defined but I couldn't find it.

Anyone know where I can look?

Thanks
-Malphas

---

### Post by jorgemarmo on 2009-09-20
possibly it has something to do with xrandr

[http://www.thinkwiki.org/wiki/Xorg_RandR_1.2](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2)

I have a problem with that too, the device section for the mouse is not there anymore...

Anybody can clarify this?

---

### Post by raboofje on 2009-09-20
I really don't know, but 'Xorg -configure' can auto-generate an xorg.conf for you. Perhaps that yields a config that is easier to tweak?

---

### Post by MalphasWats on 2009-09-20
Thanks for the replies,

  looking at that xrandr page, my xorg conf is way simpler than even the examples they give, all the mouse stuff is missing too.

I may well try re-generating it, although everything is working fine so I'm reluctant to mess with it for now :)

---

### Post by jorgemarmo on 2009-09-20
> I may well try re-generating it, although everything is working fine so I'm reluctant to mess with it for now :smile:

Easy... I have messed up my xorg.conf several times.... just be sure to back uo the one u have right now, it should be something like

terminal way 
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

in the worst case Ubuntu will start in "low resolution mode" or something like that... and u just have to back to your old xorg.conf file....

---

