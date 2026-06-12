---
title: "Updating/Installing Adobe Flash?"
date: 2008-05-16
forum: Multimedia Software
---

### Post by raynedanser on 2008-05-16
Online video streaming. 

Youtube is fine, but I'm a huge newbie and basically need someone to hold my hand as I do this. 

There's some stuff I want to watch, but I'm being prompted to update my Adobe Flash Player and a download screen pops up along with some Linux options... Except I can't figure out what to do with them from there. 

Help?

---

### Post by DieB on 2008-05-16
well the package flashplugin-nonfree in the repositories is normally on the newest state just install that via add/remove or synaptic.

plus for other codec problems install ubuntu-restricted-extras.

hope that helps

---

### Post by raynedanser on 2008-05-16
> **DieB said:**
> well the package flashplugin-nonfree in the repositories is normally on the newest state just install that via add/remove or synaptic.

plus for other codec problems install ubuntu-restricted-extras.

hope that helps

I just checked and I have that flash plug in installed. Is there anything that might be conflicting with it, perhaps?

Still poking around, thanks for the help. ;-)

---

### Post by DieB on 2008-05-16
are you using the NoScript addon in firefox?

cause if: 

you have to allow "ytimg.com" and "youtube.com"

hope that helps?

if not, what flashplugin-nonfree a/o ubuntu version are u using?

---

### Post by raynedanser on 2008-05-16
> **DieB said:**
> are you using the NoScript addon in firefox?

if not, what flashplugin-nonfree a/o ubuntu version are u using?

No I'm not. It's installed, but disabled (and why won't it let me uninstall it completely? It's grayed out.)

And how do I check that?

---

### Post by gandaran on 2008-05-16
> **raynedanser said:**
> No I'm not. It's installed, but disabled (and why won't it let me uninstall it completely? It's grayed out.)

And how do I check that?

to find out the flash firefox is using, just type **about: plugins**(without spaces) on firefox navigator bar, post the results back here.

---

### Post by raynedanser on 2008-05-16
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
Shockwave Flash

    File name: libgnashplugin.so
    Shockwave Flash 8.0 r99. Gnash 0.8.2, the GNU Flash Player. Copyright © 2006, 2007, 2008 Free Software Foundation, Inc.
    Gnash comes with NO WARRANTY, to the extent permitted by law. You may redistribute copies of Gnash under the terms of the GNU General Public License. For more information about Gnash, see [http://www.gnu.org/software/gnash](http://www.gnu.org/software/gnash). Compatible Shockwave Flash 8.0 r99.

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
GCJ Web Browser Plugin (using IcedTea) 1.0

    File name: gcjwebplugin.so
    The GCJ Web Browser Plugin (using IcedTea) executes Java applets.

MIME Type 	Description 	Suffixes 	Enabled
application/x-java-vm 	IcedTea 	class,jar 	Yes
application/x-java-applet 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.1.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.1.2 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.1.3 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.2 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.2.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.2.2 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.3 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.3.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.4 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.4.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.4.2 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.5 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.6 	IcedTea 	class,jar 	Yes
application/x-java-applet;jpi-version=1.6.0_00 	IcedTea 	class,jar 	Yes
application/x-java-bean 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.1.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.1.2 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.1.3 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.2 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.2.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.2.2 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.3 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.3.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.4 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.4.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.4.2 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.5 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.6 	IcedTea 	class,jar 	Yes
application/x-java-bean;jpi-version=1.6.0_00 	IcedTea 	class,jar 	Yes

---

### Post by gandaran on 2008-05-16
you have the gnash flash installed, go to synaptic, remove it (complete removal) then install the flashplugin-nonfree package (adobe flash).


edit:
you are also using open java, if you have any problems with java, un-install the open java and install the sun-java6-plugin!

---

### Post by raynedanser on 2008-05-16
(I REALLY appreciate all this help.)

Do I need to remove open Java through Synaptic as well? And how do I install the java 6 plug in? same way?

---

### Post by cor2y on 2008-05-16
Theres nothing wrong with open java it works.
Just remove gnash.
Search via Synaptic for gnash and mozilla-plugin-gnash.
And install flashplugin-nonfree (search via Synaptic for it) if you can't find it be sure to enable the restricted repos in Ubuntu.
In Synaptic Settings->Repositories and then check off Universe, Multiverse, Restricted and update then search again.

---

### Post by raynedanser on 2008-05-16
> **cor2y said:**
> Theres nothing wrong with open java it works.
And install flashplugin-nonfree (search via Synaptic for it) if you can't find it be sure to enable the restricted repos in Ubuntu.

gnash is removed. The flash plug in is installed. I think. That's what the green square means, right? Should I uninstall and reinstall?

---

### Post by cor2y on 2008-05-16
check about:plugins again see if adobe flash is listed instead of gnash.

---

### Post by raynedanser on 2008-05-17
> **cor2y said:**
> check about:plugins again see if adobe flash is listed instead of gnash.

*If* I'm reading it right, it's not installed. Except when I go to Synaptic, the options are to reinstall or uninstall - so should I remove it then readd it and see if that works?

---

