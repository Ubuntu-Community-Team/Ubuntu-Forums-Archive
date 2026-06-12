---
title: "Ubuntu Hardy, Flash in Firefox 3"
date: 2008-08-19
forum: Multimedia Software
---

### Post by minstn on 2008-08-19
hi group,
i'm using ubuntu hardy for quite a while now, i have to say i like it a lot! the only thing which is kind of annoying is Flash support for Firefox 3.0. every time after loading youtube.com Firefox shows a grey box with a big Play button, it plays the video as it should, however if there are several flash areas on the screen (example Google Analytics) Firefox just freezes! any idea how to fix that? am i missing something here?
thanks in advance!

---

### Post by gandaran on 2008-08-19
you have swfdec flash installed! open your synaptic package manager, look for swfdec and mark for complete removal, then find the **flashplugin-nonfree** package (adobe flash) check-mark for install and click the apply button, that's all.

---

### Post by minstn on 2008-08-20
works as charm! thanks!

---

### Post by botezuma on 2008-08-23
i had the same problem and did so but after about a week got the same grey screen. Opened synaptic and looked for "flash" and looked like i had two versions of "flashplugin-nonfree", one was the Adobe Flash Player Plugin Installer and the other one the "flashplugin-nonfree" standalone player by Macromedia which i've completely removed. Thanks for the inspiration :).

Running Linux Mint based on Hardy and Firefox 3.0.1
Peace and love!

---

### Post by pjizz on 2008-09-16
hi.  as far as i can tell, i don't have swfdec installed and did install flashplugin-nonfree.  it doesn't appear that i have the 2 isntances, as botezuma did.

however, i still get the grey check marks to play flash.  any suggestions?

---

### Post by gandaran on 2008-09-16
> however, i still get the grey check marks to play flash. any suggestions?

type **about: plugins** (without spaces) in firefox url bar, post the full output back here.

---

### Post by Orlsend on 2008-09-16
make sure you got "Gnash" uninstalled

---

### Post by pjizz on 2008-09-16
here ya go...tell me what you think

```
Shockwave Flash

    File name: libswfdecmozilla.so
    Shockwave Flash 9.0 r100

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Adobe Flash movie 	swf 	Yes
application/futuresplash 	FutureSplash movie 	spl 	Yes
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
```

---

### Post by pjizz on 2008-09-16
> **Orlsend said:**
> make sure you got "Gnash" uninstalled

i do not have Gnash installed

---

### Post by gandaran on 2008-09-16
> **pjizz said:**
> i do not have Gnash installed

but you do have swfdec installed and I don't see adobe flash, flashplugin-nonfree!

> Shockwave Flash

    File name: libswfdecmozilla.so
    Shockwave Flash 9.0 r100

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Adobe Flash movie 	swf 	Yes
application/futuresplash 	FutureSplash movie 	spl 	Yes
Default Plugin


---

### Post by pjizz on 2008-09-16
i removed swfdec earlier, and i tried to install flashplugin-nonfree, but maybe it didn't work.  however, when i look in synaptic it looks like it is there but i'm not sure.  maybe remove and redo it?

ill post an image to show you what i mean

---

### Post by gandaran on 2008-09-16
> **pjizz said:**
> i removed swfdec earlier, and i tried to install flashplugin-nonfree, but maybe it didn't work.  however, when i look in synaptic it looks like it is there but i'm not sure.  maybe remove and redo it?

ill post an image to show you what i mean

use synaptic to remove and install, use the search box for swfdec, mark all packages installed that begin with swfdec for removal (choose complete removal) then find the flashplugin-nonfree and mark for install, next just click the apply button. should fix it.

---

### Post by pjizz on 2008-09-16
okay i was lil confused on what synaptic was...i'm in there now and have swfdec marked for complete removal and flashplugin-nonfree marked for reinstallation (i guess it was there).

however, the apply button is greyed out???

---

### Post by gandaran on 2008-09-16
> **pjizz said:**
> okay i was lil confused on what synaptic was...i'm in there now and have swfdec marked for complete removal and flashplugin-nonfree marked for reinstallation (i guess it was there).

however, the apply button is greyed out???

you haven't selected the package for install or was it already installed?
if installed try removing it first.

---

### Post by pjizz on 2008-09-16
got it...i just wasn't running synaptic as root.  all is working now.  now, if only i could get my trash to change it's image when there is something in it...

---

### Post by pjizz on 2008-09-17
hey...i have a new issue..

when i try to open menus on some sites, they are often obscured by flash animations.  i'll attach a picture of this in action.

any ideas?

---

### Post by gandaran on 2008-09-17
I'm not sure if that is a flash problem, I tried the same page and didn't see any flash objects there, but then the page keeps changing every time
worked fine here with flash 10, adobe linux flash 9 sometimes doesn't display flash objects correctly on some webpages, flash 10 is a little better, but still in alpha testing, and won't work with many flash videos pages yet.

---

### Post by change_mode on 2009-03-20
The menu thing is a bug in flash-nonfree. It puts flash on top of javascript items.
If I remember correctly, installing the latest flash from the adobe site will fix that.

Oh sorry, I didn't see how old this topic was.

---

### Post by digbickman on 2009-04-12
I cant get flash to work
Ubuntu 8.04 Hardy Heron

about:plugin in firefox:
```
Installed plugins
Find more information about browser plugins at mozilla.org.
Help for installing plugins is available from plugindoc.mozdev.org.
iTunes Application Detector

    File name: librhythmbox-itms-detection-plugin.so
    This plug-in detects the presence of iTunes when opening iTunes Store URLs in a web page with Firefox.

MIME Type 	Description 	Suffixes 	Enabled
application/itunes-plugin 			Yes
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

```

I removed everything gnash and swfdec and installed the non free in synaptic

---

### Post by gandaran on 2009-04-12
> **digbickman said:**
> I cant get flash to work
Ubuntu 8.04 Hardy Heron

about:plugin in firefox:
```
Installed plugins
Find more information about browser plugins at mozilla.org.
Help for installing plugins is available from plugindoc.mozdev.org.
iTunes Application Detector

    File name: librhythmbox-itms-detection-plugin.so
    This plug-in detects the presence of iTunes when opening iTunes Store URLs in a web page with Firefox.

MIME Type 	Description 	Suffixes 	Enabled
application/itunes-plugin 			Yes
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

```

I removed everything gnash and swfdec and installed the non free in synaptic

according to this output you don't have flash installed, if you just installed ubuntu 8.04 you have to install all updates for flash to work, what you have installed is a broken flash package, remove it completely, update and update synaptic too (sudo apt-get update) then reinstall.

---

### Post by digbickman on 2009-04-12
Ok my system says it is up to date and did sudo apt-get update

This time when i installed flushplugin-nonfree i clicked details and noticed it says "download fail" at the end

Any clues?

Thanks

---

### Post by gandaran on 2009-04-13
> **digbickman said:**
> Ok my system says it is up to date and did sudo apt-get update

This time when i installed flushplugin-nonfree i clicked details and noticed it says "download fail" at the end

Any clues?

Thanks
download it directly from adobe then, get the .deb 8.04 ubuntu package [here]("http://get.adobe.com/flashplayer/")

---

### Post by digbickman on 2009-04-13
> **gandaran said:**
> download it directly from adobe then, get the .deb 8.04 ubuntu package [here]("http://get.adobe.com/flashplayer/")

This was the first thing i tried following a tutorial from 
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

i downloaded .deb 8.04 
but the "install package" was grayed out.

I installed ubuntu 7 then did a system upgrage to 8.04.  I also recently installed xubuntu desktop following this
[http://www.psychocats.net/ubuntu/xfce](http://www.psychocats.net/ubuntu/xfce)

---

### Post by Motorhead Kaze on 2009-04-23
Thanks for this. "swfdec" and "Gnash" are totally vile. After reinstalling Hardy fresh for the first time in a long time I had forgotten about getting rid of Gnash...why they put this crap in here in the first place...gah!

Thanks gandaran!

---

