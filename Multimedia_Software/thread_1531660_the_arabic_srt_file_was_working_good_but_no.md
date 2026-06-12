---
title: "the arabic srt file was working good but no"
date: 2010-07-15
forum: Multimedia Software
---

### Post by magiclinux on 2010-07-15
[SIZE=4]hello ...
the arabic srt file was working fine with vlc & movie player 
the  setting at ( [/SIZE][SIZE=4]Arabic Windows 1256)
and i have ( [/SIZE][SIZE=4]libfribidi0 )

but now the translation didn't appear at movie player and with vlc the [COLOR=#000000]Character [/COLOR]Separated[COLOR=#000000] 

[/COLOR][/SIZE][SIZE=4] 
for smplayer and kmplayer the [COLOR=#000000]Character [/COLOR]Separated[/SIZE][SIZE=4] and from the left to right 

i try to edit the config for mplayer to add this line[/SIZE] 
[PHP]fontconfig=1
font='Sans'
flip-hebrew=1
subcp=WINDOWS-1256 [/PHP][SIZE=4]but i got error when i try to open smplayer or kmplayer [/SIZE]

[PHP]The flip-hebrew option can't be used in a config file.
 Error parsing option flip-hebrew=1 at line 5  [/PHP][SIZE=4]what i can do i hope to get some help here [/SIZE]

---

### Post by rvm4000 on 2010-07-17
Maybe mplayer wasn't compiled with fribidi support.

Try this build:
[https://launchpad.net/~rvm/+archive/mplayer](https://launchpad.net/~rvm/+archive/mplayer)

---

