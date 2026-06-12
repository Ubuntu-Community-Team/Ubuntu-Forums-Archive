---
title: "mplayer config file subtitle encoding"
date: 2009-07-14
forum: Multimedia Software
---

### Post by c001os on 2009-07-14
I have set up my mplayer in a config file (/home/.../.mplayer/config) , everything fine, but i dont know how i can set up subtitle font preferences and encoding, int the config file. I'm using hungarian subtitles (iso-8859-2). In gmplayer everything fine, but i want to use mplayer.

---

### Post by SyL on 2009-07-14
Have a look at [http://ubuntuforums.org/showpost.php?p=543322&postcount=2](http://ubuntuforums.org/showpost.php?p=543322&postcount=2)
```
# Set font.
font=/home/osmo/.fonts/microsoft-vista/calibri.ttf

# Set font encoding.
subfont-encoding=unicode

# Set subtitle file encoding.
unicode=yes
utf8=yes

```

Or directly here: [http://www.mplayerhq.hu/DOCS/man/en/mplayer.1.html](http://www.mplayerhq.hu/DOCS/man/en/mplayer.1.html) at the OSD/SUBTITLE OPTIONS section.
[B][SIZE=1]
[/SIZE][/B]

HTH

---

### Post by c001os on 2009-07-22
Thy everything fixed.

my config for Hungarian language:

--------------

font=/home/c001os/.mplayer/subfont.ttf
# Set font encoding.
subcp=latin2
subfont-text-scale=3
subfont-osd-scale=3

---------------

---

### Post by SyL on 2009-07-27
> **c001os said:**
> Thy everything fixed.

my config for Hungarian language:

--------------

font=/home/c001os/.mplayer/subfont.ttf
# Set font encoding.
subcp=latin2
subfont-text-scale=3
subfont-osd-scale=3

---------------


thx for sharing ;-)
If i remember SMPlayer offers an easy going wizard to configure the subtitle preferences.

---

