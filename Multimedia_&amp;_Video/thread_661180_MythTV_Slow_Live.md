---
title: "MythTV Slow Live"
date: 2008-01-07
forum: Multimedia &amp; Video
---

### Post by thomaspember on 2008-01-07
Hi (1st time post)

when i view live TV in mythTV the video is slow and jumpy but if i rec it then play it back its ok

My Spec

P4 3.06 @ 4.12Ghz
3GB DDR Ram
160GB 3G/bs SATA HDD
Sapphire 1650Pro 512Mb PCI-E
Kworld DVB-T 100

i think my spec is ok right?

---

### Post by mihai.ile on 2008-01-14
just installed mythtv on gusty and happens the same thing!

If I play the saved video in totem or vlc is very fast.

---

### Post by Scorpuk on 2008-01-15
What video drivers do you have installed?

---

### Post by mihai.ile on 2008-01-15
The drivers I use are fglrx for an ati radeon 9600xt.

I solved the problem by ading the line in xorg.conf and reboot:
```

sudo gedit /etc/X11/xorg.conf

```
and in section:
```

Section "Device"
        Identifier  "ATI Technologies Inc Radeon 9600XT"
        Driver      "fglrx"
        BusID       "PCI:1:0:0"
EndSection

```
added the line:
```
Option      "VideoOverlay" "on"
```

So the final result:
```

Section "Device"
        Identifier  "ATI Technologies Inc Radeon Mobility X700 (PCIE)"
        Driver      "fglrx"
        Option      "VideoOverlay" "on"
        BusID       "PCI:1:0:0"
EndSection

```

Just reboot (or maybe a CTRL-ALT-BACKSPACE will work also) and it will be ok.

If you also have an ATI card, make sure you have the fglrx drivers installed and test it out and if it works pu a [SOLVED] tag in the post name ;)

---

