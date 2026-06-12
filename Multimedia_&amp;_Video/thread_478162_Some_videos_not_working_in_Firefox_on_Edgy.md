---
title: "Some videos not working in Firefox on Edgy"
date: 2007-06-19
forum: Multimedia &amp; Video
---

### Post by molo on 2007-06-19
Hello,

I'm having a problem getting embedded videos to play in some web pages.  I'm not sure exactly which format is messing up, but here's an example of a site that doesn't work:  [http://www.freelicks.net/Littlewing1.htm](http://www.freelicks.net/Littlewing1.htm)

All I see is a grey box where the movie should be.  I've followed the instructions on installing the w32codecs and other packages, and I believe that video used to work, but at some point along the way something broke.  I'm attaching my "about:plugins" output for Firefox, in case it helps.

Anyone know what I can do about this?  I've been wrangling with this problem for a while, and it's getting pretty annoying, so if anyone has any ideas, I'd love to hear them.

Thanks,
molo


About:plugins:

```

Installed plug-ins
Find more information about browser plug-ins at mozilla.org.
Help for installing plug-ins is available from plugindoc.mozdev.org.

Windows Media Player Plug-in 10 (compatible; Totem)

    File name: /usr/lib/totem/libtotem-gmp-plugin.so
    The Totem 2.16.2 plugin handles video and audio streams.

MIME Type 	                  Description 	Suffixes 	         Enabled
application/x-mplayer2            AVI video 	avi, wma, wmv 	         Yes
video/x-ms-asf-plugin 	          ASF video 	asf, wmv 	         Yes
video/x-msvideo 	          AVI video 	asf, wmv 	         Yes
video/x-ms-asf 	                  ASF video     asf 	                 Yes
video/x-ms-wmv                    WMV video 	wmv 	                 Yes
video/x-wmv 	                  WMV video     wmv 	                 Yes


Shockwave Flash

    File name: /usr/lib/firefox/plugins/libflashplayer.so
    Shockwave Flash 9.0 r31

MIME Type 	                Description 	        Suffixes   Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	   Yes
application/futuresplash 	FutureSplash Player 	spl 	   Yes


Totem Web Browser Plugin 2.16.2

    File name: /usr/lib/totem/libtotem-basic-plugin.so
    The Totem 2.16.2 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes       Enabled
application/ogg Ogg multimedia 	ogg 	       Yes
video/mpeg 	MPEG video 	mpg, mpeg, mpe Yes
audio/wav 	WAV audio 	wav 	       Yes
audio/mpeg 	MP3 audio 	mp3 	       Yes


Helix DNA Plugin: RealPlayer G2 Plug-In Compatible (compatible; Totem)

    File name: /usr/lib/totem/libtotem-complex-plugin.so
    The Totem 2.16.2 plugin handles video and audio streams.

MIME Type 	                Description 	        Suffixes Enabled
audio/x-pn-realaudio-plugin 	RealAudio document 	rpm 	 Yes


DivX® Web Player

    File name: /usr/lib/totem/libtotem-mully-plugin.so
    The Totem 2.16.2 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
video/divx 	AVI video 	divx 	            Yes


QuickTime Plug-in 7.0 (compatible; Totem)

    File name: /usr/lib/totem/libtotem-narrowspace-plugin.so
    The Totem 2.16.2 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
video/quicktime QT video 	mov 	      Yes


Adobe Reader 7.0

    File name: /usr/lib/Adobe/Acrobat7.0/Browser/intellinux/nppdf.so
    The Adobe Reader plugin is used to enable viewing of PDF and FDF files from within the browser.

MIME Type 	                        Description 	Suffixes 	Enabled
application/pdf 	Portable Document Format 	pdf 	Yes
application/vnd.fdf 	Acrobat Forms Data Format 	fdf 	Yes
application/vnd.adobe.xfdf 	XML Version of Acrobat Forms Data Format 	xfdf 	Yes
application/vnd.adobe.xdp+xml 	Acrobat XML Data Package 	xdp 	Yes
application/vnd.adobe.xfd+xml 	Adobe FormFlow99 Data File 	xfd 	Yes


QuickTime Plug-in 6.0 / 7

    File name: /usr/lib/mozilla/plugins/mplayerplug-in-qt.so
    mplayerplug-in 3.31

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

MIME Type 	Description 	Suffixes 	Enabled
video/quicktime 	Quicktime 	mov 	Yes
video/x-quicktime 	Quicktime 	mov 	Yes
image/x-quicktime 	Quicktime 	mov 	Yes
video/quicktime 	Quicktime 	mp4 	Yes
video/quicktime 	Quicktime - Session Description Protocol 	sdp 	Yes
application/x-quicktimeplayer 	Quicktime 	mov 	Yes
application/smil 	SMIL 	smil 	Yes


RealPlayer 9

    File name: /usr/lib/mozilla/plugins/mplayerplug-in-rm.so
    mplayerplug-in 3.31

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

MIME Type 	Description 	Suffixes 	Enabled
audio/x-pn-realaudio 	RealAudio 	ram,rm 	Yes
application/vnd.rn-realmedia 	RealMedia 	rm 	Yes
application/vnd.rn-realaudio 	RealAudio 	ra,ram 	Yes
video/vnd.rn-realvideo 	RealVideo 	rv 	Yes
audio/x-realaudio 	RealAudio 	ra 	Yes
audio/x-pn-realaudio-plugin 	RealAudio 	rpm 	Yes
application/smil 	SMIL 	smil 	Yes


Windows Media Player Plugin

    File name: /usr/lib/mozilla/plugins/mplayerplug-in-wmp.so
    mplayerplug-in 3.31

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

MIME Type 	Description 	Suffixes 	Enabled
application/asx 	Media Files 	* 	Yes
video/x-ms-asf-plugin 	Media Files 	* 	Yes
video/x-msvideo 	AVI 	avi,* 	Yes
video/msvideo 	AVI 	avi,* 	Yes
application/x-mplayer2 	Media Files 	* 	Yes
application/x-ms-wmv 	Microsoft WMV video 	wmv,* 	Yes
video/x-ms-asf 	Media Files 	asf,asx,* 	Yes
video/x-ms-wm 	Media Files 	wm,* 	Yes
video/x-ms-wmv 	Microsoft WMV video 	wmv,* 	Yes
audio/x-ms-wmv 	Windows Media 	wmv,* 	Yes
video/x-ms-wmp 	Windows Media 	wmp,* 	Yes
video/x-ms-wvx 	Windows Media 	wvx,* 	Yes
audio/x-ms-wax 	Windows Media 	wax,* 	Yes
audio/x-ms-wma 	Windows Media 	wma,* 	Yes
application/x-drm-v2 	Windows Media 	asx,* 	Yes
audio/wav 	Microsoft wave file 	wav,* 	Yes
audio/x-wav 	Microsoft wave file 	wav,* 	Yes


mplayerplug-in 3.31

    File name: /usr/lib/mozilla/plugins/mplayerplug-in.so
    mplayerplug-in 3.31

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

MIME Type 	Description 	Suffixes 	Enabled
video/mpeg 	MPEG 	mpg,mpeg 	Yes
audio/mpeg 	MPEG 	mpg,mpeg 	Yes
video/x-mpeg 	MPEG 	mpg,mpeg 	Yes
video/x-mpeg2 	MPEG2 	mpv2,mp2ve 	Yes
audio/mpeg 	MPEG 	mpg,mpeg 	Yes
audio/x-mpeg 	MPEG 	mpg,mpeg 	Yes
audio/mpeg2 	MPEG audio 	mp2 	Yes
audio/x-mpeg2 	MPEG audio 	mp2 	Yes
video/mp4 	MPEG 4 Video 	mp4 	Yes
audio/mpeg3 	MPEG audio 	mp3 	Yes
audio/x-mpeg3 	MPEG audio 	mp3 	Yes
audio/x-mpegurl 	MPEG url 	m3u 	Yes
audio/mp3 	MPEG audio 	mp3 	Yes
application/x-ogg 	Ogg Vorbis Media 	ogg 	Yes
audio/ogg 	Ogg Vorbis Audio 	ogg 	Yes
application/ogg 	Ogg Vorbis / Ogg Theora 	ogg 	Yes
video/fli 	FLI animation 	fli,flc 	Yes
video/x-fli 	FLI animation 	fli,flc 	Yes
video/vnd.vivo 	VivoActive 	viv,vivo 	Yes
application/x-nsv-vp3-mp3 	Nullsoft Streaming Video 	nsv 	Yes
audio/x-mod 	Soundtracker 	mod 	Yes
audio/basic 	Basic Audio File 	au,snd 	Yes
audio/x-basic 	Basic Audio File 	au,snd 	Yes


Shockwave Flash

    File name: /usr/lib/mozilla/plugins/libflash-mozplugin.so
    Flash Movie player Version 0.4.12 compatible with Shockwave Flash 4.0

    Shockwave is a trademark of Macromedia®

    GPLFLash homepage : gplflash.sf.net

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Flash Plugin 	swf 	Yes
application/futuresplash 	Future Splash 	spl 	Yes


Helix DNA Plugin: RealPlayer G2 Plug-In Compatible

    File name: /usr/local/HelixPlayer/mozilla/nphelix.so
    Helix DNA Plugin: RealPlayer G2 Plug-In Compatible version 0.4.0.623 built with gcc 3.2.0 on Jul 18 2006

MIME Type 	Description 	Suffixes 	Enabled
audio/x-pn-realaudio-plugin 	RealPlayer Plugin Metafile 	rpm 	Yes


Java(TM) Plug-in 1.5.0_08-b03

    File name: /usr/lib/jvm/java-1.5.0-sun-1.5.0.08/jre/plugin/i386/ns7/libjavaplugin_oji.so
    Java(TM) Plug-in 1.5.0_08

MIME Type 	Description 	Suffixes 	Enabled
application/x-java-vm 	Java 		Yes
application/x-java-applet 	Java 		Yes
application/x-java-applet;version=1.1 	Java 		Yes
application/x-java-applet;version=1.1.1 	Java 		Yes
application/x-java-applet;version=1.1.2 	Java 		Yes
application/x-java-applet;version=1.1.3 	Java 		Yes
application/x-java-applet;version=1.2 	Java 		Yes
application/x-java-applet;version=1.2.1 	Java 		Yes
application/x-java-applet;version=1.2.2 	Java 		Yes
application/x-java-applet;version=1.3 	Java 		Yes
application/x-java-applet;version=1.3.1 	Java 		Yes
application/x-java-applet;version=1.4 	Java 		Yes
application/x-java-applet;version=1.4.1 	Java 		Yes
application/x-java-applet;version=1.4.2 	Java 		Yes
application/x-java-applet;version=1.5 	Java 		Yes
application/x-java-applet;jpi-version=1.5.0_08 	Java 		Yes
application/x-java-bean 	Java 		Yes
application/x-java-bean;version=1.1 	Java 		Yes
application/x-java-bean;version=1.1.1 	Java 		Yes
application/x-java-bean;version=1.1.2 	Java 		Yes
application/x-java-bean;version=1.1.3 	Java 		Yes
application/x-java-bean;version=1.2 	Java 		Yes
application/x-java-bean;version=1.2.1 	Java 		Yes
application/x-java-bean;version=1.2.2 	Java 		Yes
application/x-java-bean;version=1.3 	Java 		Yes
application/x-java-bean;version=1.3.1 	Java 		Yes
application/x-java-bean;version=1.4 	Java 		Yes
application/x-java-bean;version=1.4.1 	Java 		Yes
application/x-java-bean;version=1.4.2 	Java 		Yes
application/x-java-bean;version=1.5 	Java 		Yes
application/x-java-bean;jpi-version=1.5.0_08 	Java 		Yes

```

---

### Post by frodon on 2007-06-19
Save your time and install the "media player connectivity" firefox extension, it just send the stream to the player of you choice :
[https://addons.mozilla.org/en-US/firefox/addon/446](https://addons.mozilla.org/en-US/firefox/addon/446)

---

### Post by rfurman24 on 2007-06-19
It looks like you have conflicting plugins. I would start by unistalling totem plugin and see what happens. Also make sure you have chosen a output for mplayer, when the video window pops up right click and check output setting.

---

### Post by Gremlinzzz on 2007-06-19
Go to synaptic uninstall totem plugin  make sure mplayer plugin is installed  when the video window pops up right click and check output setting. mine are set to X11 video oss audio and i just watched the video your not missing much.

---

### Post by molo on 2007-06-19
Well, the suggestions worked great, uninstalling the totem plugin and reconfiguring the MPlayer plugin (to X11 video and ALSA audio output, in my case) did the trick.

Thanks a lot, guys!

molo

---

### Post by Gremlinzzz on 2007-06-19
Yeah sorry about the oss miss info.Had to set mine back to alsa when i started to watch a online  divx movie and there was no sound.l go figure dont know how it got to oss.

---

