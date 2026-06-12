---
title: "flash"
date: 2008-07-26
forum: Multimedia Software
---

### Post by 0perator on 2008-07-26
when trying to view flash, it displays for about 2 seconds and turns grey, i have the non-free plugin and libflash-support

please help.

thanks.

---

### Post by gandaran on 2008-07-26
can you post a shot?
also type **about: plugins** (without spaces) in firefox and post the output here.
why did you install libflashsupport, do you know what's it for?

---

### Post by 0perator on 2008-07-26
i installed it cos the sound wasnt working, and my friend told me to, so i did and it worked.

[http://rvaf.co.uk/Screenshot.png](http://rvaf.co.uk/Screenshot.png)

also, here is the content of about:plugins

> Installed plugins
Find more information about browser plugins at mozilla.org.
Help for installing plugins is available from plugindoc.mozdev.org.
Shockwave Flash

    File name: npwrapper.libflashplayer.so
    Shockwave Flash 9.0 r124

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
Default Plugin

    File name: libnullplugin.so
    The default plugin handles plugin data for mimetypes and extensions that are not specified and facilitates downloading of new plugins.

MIME Type 	Description 	Suffixes 	Enabled
* 	All types 	.* 	No
Demo Print Plugin for unix/linux

    File name: libunixprintplugin.so
    The demo print plugin for unix.

MIME Type 	Description 	Suffixes 	Enabled
application/x-print-unix-nsplugin 	Demo Print Plugin for Unix/Linux 	.pnt 	Yes
iTunes Application Detector

    File name: librhythmbox-itms-detection-plugin.so
    This plug-in detects the presence of iTunes when opening iTunes Store URLs in a web page with Firefox.

MIME Type 	Description 	Suffixes 	Enabled
application/itunes-plugin 			Yes
Totem Web Browser Plugin 2.22.1

    File name: libtotem-basic-plugin.so
    The Totem 2.22.1 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
application/x-ogg 	- 	ogg 	Yes
application/ogg 	Ogg multimedia 	ogg 	Yes
audio/ogg 	Ogg Audio 	oga 	Yes
audio/x-ogg 	Ogg Audio 	ogg 	Yes
video/ogg 	Ogg Video 	ogv 	Yes
video/x-ogg 	Ogg Video 	ogg 	Yes
application/annodex 	- 	anx 	Yes
audio/annodex 	- 	axa 	Yes
video/annodex 	- 	axv 	Yes
video/mpeg 	MPEG video 	mpg, mpeg, mpe 	Yes
audio/wav 	WAV audio 	wav 	Yes
audio/x-wav 	WAV audio 	wav 	Yes
audio/mpeg 	MP3 audio 	mp3 	Yes
application/x-nsv-vp3-mp3 	NullSoft video 	nsv 	Yes
video/flv 	Flash video 	flv 	Yes
Helix DNA Plugin: RealPlayer G2 Plug-In Compatible (compatible; Totem)

    File name: libtotem-complex-plugin.so
    The Totem 2.22.1 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
audio/x-pn-realaudio-plugin 	RealAudio document 	rpm 	Yes
VLC Multimedia Plugin (compatible Totem 2.22.1)

    File name: libtotem-cone-plugin.so
    The Totem 2.22.1 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
application/x-vlc-plugin 	unknown 		Yes
application/vlc 	unknown 		Yes
video/x-google-vlc-plugin 	unknown 		Yes
Windows Media Player Plug-in 10 (compatible; Totem)

    File name: libtotem-gmp-plugin.so
    The Totem 2.22.1 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
application/x-mplayer2 	AVI video 	avi, wma, wmv 	Yes
video/x-ms-asf-plugin 	ASF video 	asf, wmv 	Yes
video/x-msvideo 	AVI video 	asf, wmv 	Yes
video/x-ms-asf 	ASF video 	asf 	Yes
video/x-ms-wmv 	Windows Media video 	wmv 	Yes
video/x-wmv 	Windows Media video 	wmv 	Yes
video/x-ms-wvx 	Microsoft ASX playlist 	wmv 	Yes
video/x-ms-wm 	ASF video 	wmv 	Yes
application/x-ms-wms 	Windows Media video 	wms 	Yes
application/asx 	Microsoft ASX playlist 	asx 	Yes
audio/x-ms-wma 	Windows Media audio 	wma 	Yes
DivX® Web Player

    File name: libtotem-mully-plugin.so
    DivX Web Player version 1.4.0.233

MIME Type 	Description 	Suffixes 	Enabled
video/divx 	AVI video 	divx 	Yes
QuickTime Plug-in 7.2.0

    File name: libtotem-narrowspace-plugin.so
    The Totem 2.22.1 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
video/quicktime 	QuickTime video 	mov 	Yes
video/mp4 	MPEG-4 video 	mp4 	Yes
image/x-macpaint 	MacPaint Bitmap image 	pntg 	Yes
image/x-quicktime 	QuickTime image 	pict, pict1, pict2 	Yes
video/x-m4v 	MPEG-4 video 	m4v 	Yes


---

### Post by gandaran on 2008-07-26
looks all-right, but you get sound and no flash, correct?
how about your firefox settings? flash blocked or a addon like flashblock installed?

---

### Post by 0perator on 2008-07-26
yeah thats right, i used to get flash and no sound, but after libflashsupport i get the opposite, sound, but no flash.

erm no nothing is blocking it either...

---

### Post by gandaran on 2008-07-26
I believe you running 64-bits ubuntu, correct? and you did install the flashplugin-nonfree with synaptic or a manual install?
maybe the solution for you is flash 10, flash 10 fixes the sound problem, no need to install libflashsupport, the problem is how to install flash 10 in 64-bits systems! it can be done, I have seen some posts about that.

---

### Post by 0perator on 2008-07-26
im not running 64 bits...

will it be easy to do in x86

---

### Post by gandaran on 2008-07-26
then why in the plugins list you get this 
File name: npwrapper.libflashplayer.so
Shockwave Flash 9.0 r124
it should only list liflashplayer.so without 'npwrapper' did you install this?
yes for 32-bits systems it easy to install flash 10
just wait full instructions coming up!

---

### Post by 0perator on 2008-07-26
i dont know why that comes up i duno if i installed it or not...

---

### Post by gandaran on 2008-07-26
download the flash 10 tar.gz package here [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)
open synaptic, remove the flashplugin-nonfree and libflashsupport (complete removal)
unpack/extract the tar package, copy/paste the libflashplayer.so file to either /usr/lib/mozilla/plugins folder (root permission needed) or hidden home .mozilla/plugins folder, I prefer this one, you don't like the flash, you just delete, no root permission need here, if you don't find a plugins folder in .mozilla then just make one!
next, type the about thing in firefox, it should show flash 10.

---

### Post by 0perator on 2008-07-26
ok, i moved it to /usr/lib/mozilla/plugins and it still doesnt work

also there is no such directory as /home/.mozilla

---

### Post by gandaran on 2008-07-26
> also there is no such directory as /home/.mozilla

its a hidden directory you have to enable in nautilus to see it

> ok, i moved it to /usr/lib/mozilla/plugins and it still doesnt work

does the flash 10 show up in about:plugins/firefox

---

### Post by 0perator on 2008-07-26
no i mean, when i try

cd /home/.mozilla

it says no such directory

and

application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes

is at the bottom...

---

### Post by gandaran on 2008-07-26
well if firefox list's  something like this and doesn't work, you must have something blocking flash.

File name: libflashplayer.so
Shockwave Flash 10.0 b

---

### Post by 0perator on 2008-07-26
i dont

---

### Post by gandaran on 2008-07-26
still one thing more to do for flash 10
delete the xpti.dat file in you hidden home .mozilla and reboot your computer.

---

### Post by 0perator on 2008-07-26
there is no /home/.mozilla though

---

### Post by gandaran on 2008-07-26
home/**user**/.mozilla
your home folder

nautilus » view » enable show hidden files

---

