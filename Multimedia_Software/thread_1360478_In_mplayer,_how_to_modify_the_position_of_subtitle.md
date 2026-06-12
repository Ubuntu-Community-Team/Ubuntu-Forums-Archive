---
title: "In mplayer, how to modify the position of subtitle?"
date: 2009-12-20
forum: Multimedia Software
---

### Post by wxlug on 2009-12-20
As the title said? I tried to search in the preferences, but failed. Only options for the font of subtitle.

Thanks.

---

### Post by lovinglinux on 2009-12-21
If you want a simple solution, then I recommend installing [smplayer](apt:smplayer). It is another front-end for mplayer, with great subtitle support, including ssa. 

You can also specify subtitle position in mplayer config file, which is located at ~/.mplayer/config. See [this page](http://www.mplayerhq.hu/DOCS/man/en/mplayer.1.html#OSD/SUBTITLE%20OPTIONS) for instructions. My configuration file looks like this:
```

[default]

alang=English,eng,en
slang=Portuguese,por,pt
ao=pulse
vo=xv
zoom=1
vf=eq2
#af=volume=10:0
double="yes"
font=/usr/share/fonts/truetype/msttcorefonts/arial.ttf
***="yes"
embeddedfonts="yes"
***-color="FFFF0000"
subfont-text-scale="7"
subfont-outline="3"
[COLOR="Red"]subpos="0"[/COLOR]
subalign="1"

[gnome-mplayer]
alang=English,eng,en
slang=Portuguese,por,pt
ao=pulse
vo=xv
#af=volume=10:0
double="yes"
font=/usr/share/fonts/truetype/msttcorefonts/arial.ttf
***="yes"
embeddedfonts="yes"
***-color="FFFF0000"
subfont-autoscale=1
subfont-text-scale="7"
subfont-encoding="ISO-8859-1"
subfont-outline="3"
[COLOR="Red"]subpos="0"[/COLOR]
subalign="1"

msglevel=all=5
vf=eq2
```

The lines in red are those that determine the position. The number ranges from 0 (bottom) to 100 (top). Nevertheless, this ain't working for me recently. The *** are blocked by the site, because it thinks I'm talking other people's buts, when in fact its **ssa** inverted, wich is another subtitle format. 

Another option would be to convert the subtitle to ssa, specifying the position. You can do that with [jubler](http://www.jubler.org/).

---

