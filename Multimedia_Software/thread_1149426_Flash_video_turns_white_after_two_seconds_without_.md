---
title: "Flash video turns white after two seconds without sound"
date: 2009-05-05
forum: Multimedia Software
---

### Post by 0liv on 2009-05-05
Hi there!

When I'm trying to watch some flash video (YouTube but not only)
on Opera (9.64) or Firefox 3:
-- it plays only for two seconds
-- it then turns white
-- there is no sound

There is no problem when I try to watch the same videos on Epiphany.

I'm on Jaunty and I have "adobe-flashplugin 10.0.22.87-2jaunty1".

Reading a few forum suggestions, I tried to
-- reinstall adobe-flashplugin
-- reinstall pulseaudio
-- install libflashsupport
-- change every sound settings to pulseaudio
-- change every sound settings to something not pulseaudio (eg. alsa)

Nothing changed.

So ... :confused: ... HELP!

---

### Post by trash on 2009-05-05
Same problem here, thought same flash plugin works fine in firefox.

---

### Post by 0liv on 2009-05-07
up

---

### Post by trash on 2009-05-07
for amd64 this fixed it for me.. but i don't know if you are 32 or 64bit

[http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.22.87.linux-x86_64.so.tar.gz)

basically you need to create a .mozilla/plugins folder in you home directory, extract files to it and then point Opera to it.

hope you get it sorted!

---

### Post by gandaran on 2009-05-07
> **0liv said:**
> Hi there!

When I'm trying to watch some flash video (YouTube but not only)
on Opera (9.64) or Firefox 3:
-- it plays only for two seconds
-- it then turns white
-- there is no sound

There is no problem when I try to watch the same videos on Epiphany.

I'm on Jaunty and I have "adobe-flashplugin 10.0.22.87-2jaunty1".

Reading a few forum suggestions, I tried to
-- reinstall adobe-flashplugin
-- reinstall pulseaudio
-- install libflashsupport
-- change every sound settings to pulseaudio
-- change every sound settings to something not pulseaudio (eg. alsa)

Nothing changed.

So ... :confused: ... HELP!

libflashsupport or flashplugin-nonfree-extrasound is for use with flash 9 only, it's known to cause the white flash window with flash 10.
and ensure you don't have any open source flash like gnash or swfdec installed, these two won't let firefox use adobe flash if installed
only install one adobe flash plugin either the adobe-flashplugin or flashplugin-nonfree (flashplugin-installer in jaunty 9.04)

---

### Post by psyke83 on 2009-05-08
The issue is caused by libflashsupport, as gandaran suggested. This library is obsolete and shouldn't be used. 

This is the bug report: [#192888]("https://bugs.launchpad.net/bugs/192888")

---

### Post by 0liv on 2009-05-08
Thanks for your answers but as I said in my original post,
I installed libflashsupport **after** this problem first occured
as a try to solve it...

And now, it is uninstalled but the problem remains.

So, any idea ?

---

### Post by gandaran on 2009-05-08
> **0liv said:**
> Thanks for your answers but as I said in my original post,
I installed libflashsupport **after** this problem first occured
as a try to solve it...

And now, it is uninstalled but the problem remains.

So, any idea ?
you removed the flashplugin-nonfree-extrasound?
which ubuntu 9.04 - 32-bits or 64-bits?
post the output of **locate libflash**
and also the output of typing this code in firefox url bar
```
about:plugins
```

---

### Post by 0liv on 2009-05-08
> you removed the flashplugin-nonfree-extrasound?

I never had it installed before. ;-)

> which ubuntu 9.04 - 32-bits or 64-bits?

32bits

> post the output of locate libflash

/home/username/.mozilla/plugins/libflashplayer.so
/usr/lib/flashplugin-installer/libflashplayer.so
/usr/lib/openoffice/basis3.0/program/libflashli.so
/usr/lib/opera/plugins/libflashplayer.so

>and also the output of typing this code in firefox url bar about: plugins

```

Shockwave Flash

    Nom de fichier : libflashplayer.so
    Shockwave Flash 10.0 r22

Type MIME 	Description 	Suffixes 	Autorisé
application/x-shockwave-flash 	Shockwave Flash 	swf 	Oui
application/futuresplash 	FutureSplash Player 	spl 	Oui

Default Plugin

    Nom de fichier : libnullplugin.so
    The default plugin handles plugin data for mimetypes and extensions that are not specified and facilitates downloading of new plugins.

Type MIME 	Description 	Suffixes 	Autorisé
* 	All types 	.* 	Non

Demo Print Plugin for unix/linux

    Nom de fichier : libunixprintplugin.so
    The demo print plugin for unix.

Type MIME 	Description 	Suffixes 	Autorisé
application/x-print-unix-nsplugin 	Demo Print Plugin for Unix/Linux 	.pnt 	Oui

Java(TM) Plug-in 1.6.0_13-b03

    Nom de fichier : libjavaplugin_oji.so
    Java(TM) Plug-in 1.6.0_13

Type MIME 	Description 	Suffixes 	Autorisé
application/x-java-vm 	Java 		Oui
application/x-java-applet 	Java 		Oui
application/x-java-applet;version=1.1 	Java 		Oui
application/x-java-applet;version=1.1.1 	Java 		Oui
application/x-java-applet;version=1.1.2 	Java 		Oui
application/x-java-applet;version=1.1.3 	Java 		Oui
application/x-java-applet;version=1.2 	Java 		Oui
application/x-java-applet;version=1.2.1 	Java 		Oui
application/x-java-applet;version=1.2.2 	Java 		Oui
application/x-java-applet;version=1.3 	Java 		Oui
application/x-java-applet;version=1.3.1 	Java 		Oui
application/x-java-applet;version=1.4 	Java 		Oui
application/x-java-applet;version=1.4.1 	Java 		Oui
application/x-java-applet;version=1.4.2 	Java 		Oui
application/x-java-applet;version=1.5 	Java 		Oui
application/x-java-applet;version=1.6 	Java 		Oui
application/x-java-applet;jpi-version=1.6.0_13 	Java 		Oui
application/x-java-bean 	Java 		Oui
application/x-java-bean;version=1.1 	Java 		Oui
application/x-java-bean;version=1.1.1 	Java 		Oui
application/x-java-bean;version=1.1.2 	Java 		Oui
application/x-java-bean;version=1.1.3 	Java 		Oui
application/x-java-bean;version=1.2 	Java 		Oui
application/x-java-bean;version=1.2.1 	Java 		Oui
application/x-java-bean;version=1.2.2 	Java 		Oui
application/x-java-bean;version=1.3 	Java 		Oui
application/x-java-bean;version=1.3.1 	Java 		Oui
application/x-java-bean;version=1.4 	Java 		Oui
application/x-java-bean;version=1.4.1 	Java 		Oui
application/x-java-bean;version=1.4.2 	Java 		Oui
application/x-java-bean;version=1.5 	Java 		Oui
application/x-java-bean;version=1.6 	Java 		Oui
application/x-java-bean;jpi-version=1.6.0_13 	Java 		Oui

DivX Browser Plug-In

    Nom de fichier : mplayerplug-in-dvx.so
    mplayerplug-in 3.55

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

Type MIME 	Description 	Suffixes 	Autorisé
video/divx 	DivX Media Format 	divx 	Oui
video/vnd.divx 	DivX Media Format 	divx 	Oui

QuickTime Plug-in 7.4.5

    Nom de fichier : mplayerplug-in-qt.so
    mplayerplug-in 3.55

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

Type MIME 	Description 	Suffixes 	Autorisé
video/quicktime 	Quicktime 	mov 	Oui
video/x-quicktime 	Quicktime 	mov 	Oui
image/x-quicktime 	Quicktime 	mov 	Oui
video/quicktime 	Quicktime 	mp4 	Oui
video/quicktime 	Quicktime - Session Description Protocol 	sdp 	Oui
application/x-quicktimeplayer 	Quicktime 	mov 	Oui
application/smil 	SMIL 	smil 	Oui

RealPlayer 9

    Nom de fichier : mplayerplug-in-rm.so
    mplayerplug-in 3.55

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

Type MIME 	Description 	Suffixes 	Autorisé
audio/x-pn-realaudio 	RealAudio 	ram,rm 	Oui
application/vnd.rn-realmedia 	RealMedia 	rm 	Oui
application/vnd.rn-realaudio 	RealAudio 	ra,ram 	Oui
video/vnd.rn-realvideo 	RealVideo 	rv 	Oui
audio/x-realaudio 	RealAudio 	ra 	Oui
audio/x-pn-realaudio-plugin 	RealAudio 	rpm 	Oui
application/smil 	SMIL 	smil 	Oui

Windows Media Player Plug-in

    Nom de fichier : mplayerplug-in-wmp.so
    mplayerplug-in 3.55

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

Type MIME 	Description 	Suffixes 	Autorisé
application/asx 	Media Files 	* 	Oui
video/x-ms-asf-plugin 	Media Files 	* 	Oui
video/x-msvideo 	AVI 	avi,* 	Oui
video/msvideo 	AVI 	avi,* 	Oui
application/x-mplayer2 	Media Files 	* 	Oui
application/x-ms-wmv 	Microsoft WMV video 	wmv,* 	Oui
video/x-ms-asf 	Media Files 	asf,asx,* 	Oui
video/x-ms-wm 	Media Files 	wm,* 	Oui
video/x-ms-wmv 	Microsoft WMV video 	wmv,* 	Oui
audio/x-ms-wmv 	Windows Media 	wmv,* 	Oui
video/x-ms-wmp 	Windows Media 	wmp,* 	Oui
application/x-ms-wmp 	Windows Media 	wmp,* 	Oui
video/x-ms-wvx 	Windows Media 	wvx,* 	Oui
audio/x-ms-wax 	Windows Media 	wax,* 	Oui
audio/x-ms-wma 	Windows Media 	wma,* 	Oui
application/x-drm-v2 	Windows Media 	asx,* 	Oui
audio/wav 	Microsoft wave file 	wav,* 	Oui
audio/x-wav 	Microsoft wave file 	wav,* 	Oui

mplayerplug-in 3.55

    Nom de fichier : mplayerplug-in.so
    mplayerplug-in 3.55

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

Type MIME 	Description 	Suffixes 	Autorisé
video/mpeg 	MPEG 	mpg,mpeg 	Oui
audio/mpeg 	MPEG 	mpg,mpeg 	Oui
video/x-mpeg 	MPEG 	mpg,mpeg 	Oui
video/x-mpeg2 	MPEG2 	mpv2,mp2ve 	Oui
audio/mpeg 	MPEG 	mpg,mpeg 	Oui
audio/x-mpeg 	MPEG 	mpg,mpeg 	Oui
audio/mpeg2 	MPEG audio 	mp2 	Oui
audio/x-mpeg2 	MPEG audio 	mp2 	Oui
audio/mp4 	MPEG 4 audio 	mp4 	Oui
audio/x-mp4 	MPEG 4 audio 	mp4 	Oui
video/mp4 	MPEG 4 Video 	mp4 	Oui
video/3gpp 	MPEG 4 Video 	mp4,3gp 	Oui
audio/mpeg3 	MPEG audio 	mp3 	Oui
audio/x-mpeg3 	MPEG audio 	mp3 	Oui
audio/x-mpegurl 	MPEG url 	m3u 	Oui
audio/mp3 	MPEG audio 	mp3 	Oui
application/x-ogg 	Ogg Vorbis Media 	ogg 	Oui
audio/ogg 	Ogg Vorbis Audio 	ogg 	Oui
audio/x-ogg 	Ogg Vorbis Audio 	ogg 	Oui
application/ogg 	Ogg Vorbis / Ogg Theora 	ogg 	Oui
audio/flac 	FLAC Audio 	flac 	Oui
audio/x-flac 	FLAC Audio 	flac 	Oui
video/fli 	FLI animation 	fli,flc 	Oui
video/x-fli 	FLI animation 	fli,flc 	Oui
video/x-flv 	Flash Video 	flv 	Oui
video/vnd.vivo 	VivoActive 	viv,vivo 	Oui
application/x-nsv-vp3-mp3 	Nullsoft Streaming Video 	nsv 	Oui
audio/x-mod 	Soundtracker 	mod 	Oui
audio/basic 	Basic Audio File 	au,snd 	Oui
audio/x-basic 	Basic Audio File 	au,snd 	Oui
audio/x-scpls 	Shoutcast Playlist 	pls 	Oui

Shockwave Flash

    Nom de fichier : libflashplayer.so
    Shockwave Flash 9.0 r48

Type MIME 	Description 	Suffixes 	Autorisé
application/x-shockwave-flash 	Shockwave Flash 	swf 	Oui
application/futuresplash 	FutureSplash Player 	spl 	Oui

```

And, here, as a special bonus, the opera: plugins

```

Shockwave Flash
application/futuresplash	spl
application/x-shockwave-flash	swf
/usr/lib/mozilla/plugins/flashplugin-alternative.so

Shockwave Flash
application/futuresplash	spl
application/x-shockwave-flash	swf
/usr/lib/opera/plugins/libflashplayer.so

DivX Browser Plug-In
video/divx	divx
video/vnd.divx	divx
/usr/lib/mozilla/plugins/mplayerplug-in-dvx.so

mplayerplug-in 3.55
video/mpeg	mpeg,mpg,mpe,m2v,m1v,mpa
video/mp4	mp4,mpg4
audio/mpeg	mp3,mp2,mpga,mpg,mpeg
audio/mp3	mp3
audio/x-mpegurl	m3u
audio/basic	au,snd
video/3gpp	3gp,mp4
video/x-mpeg	mpg,mpeg
video/x-mpeg2	mpv2,mp2ve
audio/x-mpeg	mpg,mpeg
audio/mpeg2	mp2
audio/x-mpeg2	mp2
audio/mpeg3	mp3
audio/x-mpeg3	mp3
application/x-ogg	ogg
audio/ogg	ogg
audio/x-ogg	ogg
application/ogg	ogg
audio/flac	flac
audio/x-flac	flac
video/fli	fli,flc
video/x-fli	fli,flc
video/x-flv	flv
video/vnd.vivo	viv,vivo
application/x-nsv-vp3-mp3	nsv
audio/x-mod	mod
audio/x-basic	au,snd
audio/x-scpls	pls
audio/mp4	mp4
audio/x-mp4	mp4
/usr/lib/mozilla/plugins/mplayerplug-in.so

QuickTime Plug-in 7.4.5
video/quicktime	qt,mov,mp4,sdp
application/smil	smi,smil
video/x-quicktime	mov
image/x-quicktime	mov
application/x-quicktimeplayer	mov
/usr/lib/mozilla/plugins/mplayerplug-in-qt.so

RealPlayer 9
application/smil	smi,smil
audio/x-pn-realaudio	ram,ra,rm
video/vnd.rn-realvideo	rv
application/vnd.rn-realmedia	rm
application/vnd.rn-realaudio	ra,ram
audio/x-realaudio	ra
audio/x-pn-realaudio-plugin	rpm
/usr/lib/mozilla/plugins/mplayerplug-in-rm.so

Windows Media Player Plug-in
audio/wav	wav
audio/x-wav	wav
video/x-msvideo	avi
application/asx	
video/x-ms-asf-plugin	
application/x-mplayer2	
video/x-ms-wm	wm
audio/x-ms-wma	wma
audio/x-ms-wax	wax
video/x-ms-wvx	wvx
video/x-ms-wmv	wmv,wmx
video/x-ms-asf	asf,asx
video/msvideo	avi
application/x-ms-wmv	wmv
audio/x-ms-wmv	wmv
video/x-ms-wmp	wmp
application/x-ms-wmp	wmp
application/x-drm-v2	asx
/usr/lib/mozilla/plugins/mplayerplug-in-wmp.so

```

---

### Post by gandaran on 2009-05-08
remove the flash 9 you have installed here
> /home/username/.mozilla/plugins/libflashplayer.so
just delete the libflashplayer.so file
restart firefox and try the youtube videos now, everything else looks okay.
you also need to remove the same file from /usr/lib/opera/plugins, opera will work fine with the flashplugin-installer flash.

---

### Post by 0liv on 2009-05-08
It works! Many many thanks!

---

