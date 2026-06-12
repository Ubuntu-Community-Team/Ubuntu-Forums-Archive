---
title: "mplayer errors"
date: 2006-08-13
forum: Multimedia &amp; Video
---

### Post by vista on 2006-08-13
When i want to watch streaming videos using mplayer I get:
couldn't resolve name for AF_INET6:

And when i want to watch .wmv files i've downloaded to
the desktop i only hear audio but no video (also mplayer).

Why is that?

---

### Post by simonn on 2006-08-13
You probably need to install the Windows codecs. 

[https://help.ubuntu.com/community/RestrictedFormats#head-6c942d1939d97331f96e42b63774003fde7daed5](https://help.ubuntu.com/community/RestrictedFormats#head-6c942d1939d97331f96e42b63774003fde7daed5)

---

### Post by vista on 2006-08-14
But I've allready installed the codecs, what have I missed?
I looked in firefox about plugins, this is what's installed.

> Shockwave Flash

    Filnamn: libflashplayer.so
    Shockwave Flash 7.0 r63

MIME-typ 	Beskrivning 	Filändelse 	Aktiverad
application/x-shockwave-flash 	Shockwave Flash 	swf 	Ja
application/futuresplash 	FutureSplash Player 	spl 	Ja
Helix DNA Plugin: RealPlayer G2 Plug-In Compatible

    Filnamn: nphelix.so
    Helix DNA Plugin: RealPlayer G2 Plug-In Compatible version 0.4.0.592 built with gcc 3.3.5 on Mar 9 2006

MIME-typ 	Beskrivning 	Filändelse 	Aktiverad
audio/x-pn-realaudio-plugin 	RealPlayer Plugin Metafile 	rpm 	Ja
Google VLC multimedia plugin 1.0

    Filnamn: mplayerplug-in-gmp.so
    mplayerplug-in 3.17

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

MIME-typ 	Beskrivning 	Filändelse 	Aktiverad
application/x-google-vlc-plugin 	Google Video 		Ja
QuickTime Plug-in 6.0

    Filnamn: mplayerplug-in-qt.so
    mplayerplug-in 3.17

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

MIME-typ 	Beskrivning 	Filändelse 	Aktiverad
video/quicktime 	Quicktime 	mov 	Ja
video/x-quicktime 	Quicktime 	mov 	Ja
image/x-quicktime 	Quicktime 	mov 	Ja
video/quicktime 	Quicktime 	mp4 	Ja
video/quicktime 	Quicktime - Session Description Protocol 	sdp 	Ja
application/x-quicktimeplayer 	Quicktime 	mov 	Ja
application/smil 	SMIL 	smil 	Ja
Windows Media Player Plugin

    Filnamn: mplayerplug-in-wmp.so
    mplayerplug-in 3.17

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

MIME-typ 	Beskrivning 	Filändelse 	Aktiverad
application/asx 	Media Files 	* 	Ja
video/x-ms-asf-plugin 	Media Files 	* 	Ja
video/x-msvideo 	AVI 	avi,* 	Ja
video/msvideo 	AVI 	avi,* 	Ja
application/x-mplayer2 	Media Files 	* 	Ja
application/x-ms-wmv 	Microsoft WMV video 	wmv,* 	Ja
video/x-ms-asf 	Media Files 	asf,asx,* 	Ja
video/x-ms-wm 	Media Files 	wm,* 	Ja
video/x-ms-wmv 	Microsoft WMV video 	wmv,* 	Ja
audio/x-ms-wmv 	Windows Media 	wmv,* 	Ja
video/x-ms-wmp 	Windows Media 	wmp,* 	Ja
video/x-ms-wvx 	Windows Media 	wvx,* 	Ja
audio/x-ms-wax 	Windows Media 	wax,* 	Ja
audio/x-ms-wma 	Windows Media 	wma,* 	Ja
application/x-drm-v2 	Windows Media 	asx,* 	Ja
audio/wav 	Microsoft wave file 	wav,* 	Ja
audio/x-wav 	Microsoft wave file 	wav,* 	Ja
mplayerplug-in 3.17

    Filnamn: mplayerplug-in.so
    mplayerplug-in 3.17

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

MIME-typ 	Beskrivning 	Filändelse 	Aktiverad
video/mpeg 	MPEG 	mpg,mpeg 	Ja
audio/mpeg 	MPEG 	mpg,mpeg 	Ja
video/x-mpeg 	MPEG 	mpg,mpeg 	Ja
video/x-mpeg2 	MPEG2 	mpv2,mp2ve 	Ja
audio/mpeg 	MPEG 	mpg,mpeg 	Ja
audio/x-mpeg 	MPEG 	mpg,mpeg 	Ja
audio/mpeg2 	MPEG audio 	mp2 	Ja
audio/x-mpeg2 	MPEG audio 	mp2 	Ja
video/mp4 	MPEG 4 Video 	mp4 	Ja
audio/mpeg3 	MPEG audio 	mp3 	Ja
audio/x-mpeg3 	MPEG audio 	mp3 	Ja
audio/mp3 	MPEG audio 	mp3 	Ja
application/x-ogg 	Ogg Vorbis Media 	ogg 	Ja
audio/ogg 	Ogg Vorbis Audio 	ogg 	Ja
application/ogg 	Ogg Vorbis / Ogg Theora 	ogg 	Ja
video/fli 	FLI animation 	fli,flc 	Ja
video/x-fli 	FLI animation 	fli,flc 	Ja
video/vnd.vivo 	VivoActive 	viv,vivo 	Ja
application/x-nsv-vp3-mp3 	Nullsoft Streaming Video 	nsv 	Ja
video/vnd.divx 	DivX Media Format 	divx 	Ja
audio/basic 	Basic Audio File 	au,snd 	Ja
audio/x-basic 	Basic Audio File 	au,snd 	Ja
Java(TM) Plug-in 1.5.0_06-b05

    Filnamn: libjavaplugin_oji.so
    Java(TM) Plug-in 1.5.0_06

MIME-typ 	Beskrivning 	Filändelse 	Aktiverad
application/x-java-vm 	Java 		Ja
application/x-java-applet 	Java 		Ja
application/x-java-applet;version=1.1 	Java 		Ja
application/x-java-applet;version=1.1.1 	Java 		Ja
application/x-java-applet;version=1.1.2 	Java 		Ja
application/x-java-applet;version=1.1.3 	Java 		Ja
application/x-java-applet;version=1.2 	Java 		Ja
application/x-java-applet;version=1.2.1 	Java 		Ja
application/x-java-applet;version=1.2.2 	Java 		Ja
application/x-java-applet;version=1.3 	Java 		Ja
application/x-java-applet;version=1.3.1 	Java 		Ja
application/x-java-applet;version=1.4 	Java 		Ja
application/x-java-applet;version=1.4.1 	Java 		Ja
application/x-java-applet;version=1.4.2 	Java 		Ja
application/x-java-applet;version=1.5 	Java 		Ja
application/x-java-applet;jpi-version=1.5.0_06 	Java 		Ja
application/x-java-bean 	Java 		Ja
application/x-java-bean;version=1.1 	Java 		Ja
application/x-java-bean;version=1.1.1 	Java 		Ja
application/x-java-bean;version=1.1.2 	Java 		Ja
application/x-java-bean;version=1.1.3 	Java 		Ja
application/x-java-bean;version=1.2 	Java 		Ja
application/x-java-bean;version=1.2.1 	Java 		Ja
application/x-java-bean;version=1.2.2 	Java 		Ja
application/x-java-bean;version=1.3 	Java 		Ja
application/x-java-bean;version=1.3.1 	Java 		Ja
application/x-java-bean;version=1.4 	Java 		Ja
application/x-java-bean;version=1.4.1 	Java 		Ja
application/x-java-bean;version=1.4.2 	Java 		Ja
application/x-java-bean;version=1.5 	Java 		Ja
application/x-java-bean;jpi-version=1.5.0_06 	Java 		Ja

---

