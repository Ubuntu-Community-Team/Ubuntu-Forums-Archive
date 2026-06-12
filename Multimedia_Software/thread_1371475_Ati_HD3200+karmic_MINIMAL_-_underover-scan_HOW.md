---
title: "Ati HD3200+karmic MINIMAL - under/over-scan HOW????"
date: 2010-01-03
forum: Multimedia Software
---

### Post by pricinosus on 2010-01-03
1.Instaled Ubuntu minimal
2.download and instaled ATI/AMD drivers (via envy)
3.Primary display DELL 2007FPb (SVGA cable) cloned with secondary display PANASONIC TH-42PV80PA (DVI/HDMI cable)
4.PANASONIC TH-42PV80PA have black borders, the image is underscaned (left, right, top, bottom)
5. In Full install of ubuntu 9.10 (not MINIMAL) in Gnome when run amdcccle the solution was very simple. Just drag the slider to the maximum and image was overscaned to the full surface of the screen.

How to do point 5. from shell in UBUNTU MINIMAL (the light version without gnome)?????? Tried already from shell:
```
sudo amdcccle
``` but the Catalyst control Panel doesn't start. Say something bad about x server.

aticonfig ???
xrandr ???? 
xorg.conf ????
something else ???

---

### Post by pricinosus on 2010-01-04
[IMG]http://img121.imageshack.us/img121/9215/ccce.jpg[/IMG]

This is what i'm talking about!!!

How to change under/over-scan (_without using the Catalyst Control Panel_) from shell, _without gnome instaled_. Just keyboard input, Ubuntu Minimal. See here:
[[FONT="Arial"][COLOR="DarkOrchid"]https://help.ubuntu.com/community/Installation/MinimalCD[/COLOR][/FONT]]("https://help.ubuntu.com/community/Installation/MinimalCD")

---

### Post by pricinosus on 2010-01-06
The solution is about to rise
:guitar:

seems the "/etc/ati/amdpcsdb" file is involved in any change that user make in Catalyst Control Panel

[[IMG]http://img63.imageshack.us/img63/912/amdpcsdb.png[/IMG]](http://img63.imageshack.us/i/amdpcsdb.png/)

This is the file I'm loking for tweaking.

in this moment i'm running gnome.

I will install karmic minimal and try to rewrite the /etc/ati/amdpcsdb file with tweaked one.

Stay tuned for the results.
8-)

---

