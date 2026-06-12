---
title: "problem using led vu meter skin on xmms"
date: 2012-04-09
forum: Multimedia Software
---

### Post by linux14 on 2012-04-09
hi everyone:

i'm using ubuntu 10.04 lts, 3.2.6, x86_64.
i've, allready installed and 100% functional:

-xmms player 1.2.11 and all dependencies.
-analog vu meter 0.9.2 and all dependencies.
-eqxmms 0.7 (graphic equalizer) and all dependencies.



[IMG]http://img641.imageshack.us/img641/2959/screenshotfyh.png[/IMG]

i've downloaded, from gnome-look.org, debian packages, those skins, for the vu meter:

[IMG]http://img96.imageshack.us/img96/2246/screenshot1lo.png[/IMG]

...,  but the vu meter skin browser doesn't seems to be abble to load  them.skins are correctly loaded in ".xmms/VU_Meter_skins".
does anybody know why?
are they compatible?
are there any more dependencies to install?
any changes to be made?
thanks to all.

rcc

---

### Post by linux14 on 2012-04-11
hi again:

This post is made in desperation...
i've been "googling" a lot...for nothing.there is little information about this, or i'm not able to found it.
i've send an email to the author, asking for help, but have no reply...for the moment!
i've given all the information that I thought important...never the less..

[IMG]http://img713.imageshack.us/img713/8573/m1462861.png[/IMG]
[SIZE=2]
[/SIZE][SIZE=1]Depends on Gnome 2.x
Downloads:  574
[/SIZE][SIZE=2]Submitted:  Oct 26 2011
[/SIZE][SIZE=2]
[/SIZE][SIZE=1]
Description:
[/SIZE][B][SIZE=1]LED VU meter with many leds
Skin for VU meter plugin for XMMS and Audacious found here: [http://vumeterplugin.sourceforge.net/](http://vumeterplugin.sourceforge.net/)[/SIZE][/B]

[SIZE=1]


Changelog:
[/SIZE][B][SIZE=1]Small modifications of size and scale.
Added two more skins, small, horizontal.

Comments and suggestions are welcome.[/SIZE] [/B]

[SIZE=1]


License: [GPL]("http://www.fsf.org/licenses/gpl.html")
[/SIZE][SIZE=2][[IMG]http://gnome-look.org/img/arrows/download.png[/IMG]]("http://gnome-look.org/content/download.php?content=146286&id=1&tan=77631923")[/SIZE][SIZE=2](VUm_skins.tar.gz)

...that's the rest of it.
i would really like to get those skins working.
anybody???
thanks.


linux14:confused:
[/SIZE]

---

### Post by linux14 on 2012-04-16
hello again:

anybody?
any indication?
thanks.

linux14

---

### Post by shantiq on 2012-04-16
not sure it will help [probably not]  but i keep my skins


in .xmms/[COLOR="Red"]Skins[/COLOR]/nameofskin



i have to create a Skins folder i think that is where XMMS [still the best music player:KS] seems to expect them to be


But i think you might be trying to do something more evolved here :]

---

### Post by eddier on 2012-04-16
As far as I know the skins should be in ~/.local//share/XMMS/VU_Meter_skins.

Thats where I had them working for Audacious in 11.04

The VU-meter plugin I installed was version 1.0.0 that was downloaded from Gnome looks.(./configure/make/make install etc)

You need the appropriate .dev and Build-essential installed first.

Sadly the version offered in the 11.10 repos doesnt work and the 1.0.0 wont build either.

Sadly there is page after page of references to indexes on the net but nothing that resolves the current problem.:-k

eddie

---

