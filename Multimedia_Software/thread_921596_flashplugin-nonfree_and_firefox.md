---
title: "flashplugin-nonfree and firefox"
date: 2008-09-16
forum: Multimedia Software
---

### Post by demios on 2008-09-16
I had flash working well, perfectly, no complaints. I updated today with apt-get and installed flashplugin-nonfree (which made me quite confused, but I'm no pro so I figured what the hell. that being said, this whole thing is probably my fault).

Then the flash players in myspace and purevolume started sucking. I didn't test the audio, but they have all sorts of visual glitches and the text is all blurry (it was clear before I installed it).

So I removed it with apt-get (sudo apt-get remove flashplugin-nonfree) and the flash players still suck. I don't know what I had working before, but is there a simple way to get the new flash plugin to perform better?

---

### Post by wolfen69 on 2008-09-16
```
sudo apt-get *purge* flashplugin-nonfree
```
then
```
sudo apt-get clean
```then
```
sudo apt-get autoremove
```then
```
sudo apt-get install flashplugin-nonfree
```then
```
sudo apt-get install libflashsupport
``` let us know what happens.

---

### Post by demios on 2008-09-16
perfect, thanks a ton. keep kicking ***.

---

### Post by demios on 2008-09-18
wait a sec, after a reboot, the blurryness and image glitches are back.

---

### Post by gandaran on 2008-09-18
> **demios said:**
> wait a sec, after a reboot, the blurryness and image glitches are back.
check if you have installed any other flash package besides adobe flash
open synaptic, use the search box for flash, other packages are gnash, swfdec and libflash.

---

### Post by demios on 2008-09-18
none of those are installed, just (after redoing that list of apt-get commands) only flashplugin-nonfree and libflashsupport

---

### Post by gandaran on 2008-09-19
> **demios said:**
> none of those are installed, just (after redoing that list of apt-get commands) only flashplugin-nonfree and libflashsupport

can you post the full output here by typing **about: plugins** (without spaces) in the firefox url bar

---

### Post by demios on 2008-09-19
sorry it's not all table-ey like in the page.
this is it after a reboot, and with the blurry/glitchey flash.

Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 10.0 r12

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
Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 9.0 r124

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes

---

### Post by gandaran on 2008-09-19
demios 
you have two versions of adobe flash installed, flash 10 and 9
if you want to keep flash 10, just remove the flashplugin-nonfree (do a complete removal, use synaptic for that) also remove libflashsupport, you don't need it, it's only needed if there's  a flash sound problem with flash 9.

---

### Post by demios on 2008-09-19
doing this leaves me with the blurry flash. maybe flash 9 works better than 10? should I revert to 9 to try that?
Thanks for helping me out man

---

### Post by gandaran on 2008-09-19
well, you'll have to keep trying everything until the problem is fixed
do you know where flash 10 is installed and how to remove it?

---

### Post by demios on 2008-09-19
er, no...

---

### Post by gandaran on 2008-09-20
flash 10 should be installed in home/user/.mozilla/plugins or /usr/lib/mozilla/plugins, if not then use this command **locate libflashplayer.so** to find, then just go to that folder and delete the libflashplayer.so file.

heres what I think you should do next, open synaptic package manager, make sure the flashplugin-nonfree is complete removed from the system (this is important, there are two options, remove and complete removal) now try firefox on a flash webpage, if you get the missing plugins messages it means no flash is installed, good, reboot the computer.
install the flashplugin-nonfree now, if you still have the same problem then all I can do is recommend you do a ubuntu reinstall.

---

### Post by chucknoz on 2008-09-20
> **demios said:**
> doing this leaves me with the blurry flash. maybe flash 9 works better than 10? should I revert to 9 to try that?
Thanks for helping me out man

9 is as bad imo. I can see a marked difference viewing vids thru windows, and in ubuntu, using the same ver ff and flash plugin for both

---

### Post by demios on 2008-09-20
k, I did everything you said there, got the no flash messages, installed flashplugin-nonfree and libflashsupport, and it's still blurry. guess I'll just keep messing with it, don't really feel like doing a full reinstall of ubuntu -- took some time to get audio and wireless working. thanks though.

---

