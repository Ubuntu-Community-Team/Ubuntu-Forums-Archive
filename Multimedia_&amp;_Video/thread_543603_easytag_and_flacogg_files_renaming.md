---
title: "easytag and flac/ogg files renaming"
date: 2007-09-05
forum: Multimedia &amp; Video
---

### Post by biblonchk on 2007-09-05
Dear All,

Using Ubuntu 7.04 with fr_FR.UTF-8@euro locale set,
I can't get correct file rename (UTF-8 ) operations on hand of tags content (UTF-8 or ISO ).

For both flac and ogg taged files (mp3 not used), if an involved tag has accented characters, file is renamed with ISO-8859 encoding :confused:

EasyTag Settings:

[LIST]
[*]Use system enconding: enabled
[*]ID3 in flac: enabled or disabled
[*]ID3v2: enabled
[*]ID3 encoding: UTF-8 or ISO-8859
[/LIST]

This happens with both easytag versions:  native 2.0-0ubuntu1, as well as fresh compiled 2.1-1. Maybe a library problem ?

May someone give me an hint in order to resolve this issue ?

Many thanks in advance for your help
Kindest regards

---

### Post by biblonchk on 2007-09-05
My system has locales and i18n set for french, english, german and spanish.
It offers Gnome, KDE and fluxbox trough the gdm login screen.

Playing further at gdm's language selection level, i found out:
[LIST]
[*]Renaming behaviour (i.e: accented filenames are handled UTF) is OK when login in in french or english UTF without '@euro' extension. 
[*]Filename is handled wrong (i.e: ISO) when selecting french.UTF-8@euro
[/LIST]

---

