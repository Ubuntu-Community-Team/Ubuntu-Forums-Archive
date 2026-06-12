---
title: "[SOLVED] no flash play in firefox"
date: 2009-01-05
forum: Multimedia Software
---

### Post by GlennW on 2009-01-05
Happy New Year!

My happiness has rapidly faded the last couple of days when youtube and any other flash (vimeo, bbc news, even small flash applets on web pages) display as a black box with a little gray box in the middle and an arrow in the midst of that. 

Clicking that produces all sorts of Mplayer windows and errors popping up saying that there's this error and when closing that there's another with a different error. The error messages differ with the sites. Sometimes, though, I can wade through it all and get it to play but even the tiny window is terribly pixelated and the playback is choppy in the extreme. The sound is even worse. 

The thing that is so very frustrating is that everything was doing so very well just a couple of days ago. I had vlc handling everything and it was doing a bang up job. Youtube would play in its own window and so would every other flash site. Now it's just really screwed up.

I've run through ubuntu-freak's how-to several times to make sure that I hadn't missed something but to no avail. I'm still stuck with nothing. 

I need some help. I'm sure that it's a simple fix but I have no idea where to look.

Thanks in advance.

Oh, I'm still a nOOb so keep it simple.

---

### Post by 2hot6ft2 on 2009-01-05
put this in a terminal and hit Enter
Applications>Accessories>Terminal

```
sudo apt-get install ubuntu-restricted-extras
```

Then your password and Enter (your password will not be displayed)

It will fix that as well as other multimedia problems you haven't found out about yet.

When it gets to the agreement hit Tab then Enter to accept the Java agreement.

---

### Post by GlennW on 2009-01-05
Thanks 2hot6ft2 for the quick response. I pasted the code you provided into terminal and it said that it was already installed and that everything was already the newest version. I went to youtube just in case and still the same old issues. 

The error message this time was:

ffdemux_swf: Element doesn't implement handling of this stream. Please file a bug.

This is ridiculous! How can this be a bug when, obviously, the vast majority of linux users don't have this problem!

Help!

---

### Post by wolfen69 on 2009-01-05
i make no promises, but the following has worked for me several times. go to synaptic and completely remove flash. then in terminal: ```
sudo apt-get clean && sudo apt-get autoremove
``` then go [here]("http://get.adobe.com/flashplayer/") and download the .deb flash file for ubuntu, close firefox, and click to install.

---

### Post by sendblink23 on 2009-01-06
reality is  after doing what last mentioned before posted

Remove all Flash  in Synaptic Package Manager

And only simply you need is

Applications
Add/Remove...
Show: All available applications
Search: flash
Mark: Macromedia Flash Plugin

Install it..  thats it just test: [www.youtube.com](www.youtube.com)

hope it helps

---

### Post by gandaran on 2009-01-06
GlennW
> My happiness has rapidly faded the last couple of days when youtube and any other flash (vimeo, bbc news, even small flash applets on web pages) display as a black box with a little gray box in the middle and an arrow in the midst of that.
what else have you bean installing for flash? there are many flash packages but you must only have one package installed, firefox can only use one, check with your synaptic package manager for flash, the other flash plugins are gnash, swfdec, and libflash, remove any of them if they are installed and just keep the adobe flash.

also check firefox » edit » preferences » applications tab » shockwave file, see if it is set to open with  shockwave flash (firefox) and not some player like vlc or mplayer

---

### Post by GlennW on 2009-01-06
> **gandaran said:**
> GlennW

what else have you bean installing for flash? there are many flash packages but you must only have one package installed, firefox can only use one, check with your synaptic package manager for flash, the other flash plugins are gnash, swfdec, and libflash, remove any of them if they are installed and just keep the adobe flash.

also check firefox » edit » preferences » applications tab » shockwave file, see if it is set to open with  shockwave flash (firefox) and not some player like vlc or mplayer

I've implemented precisely what you and sendblink23 have specified. No change! Shockwave was already set to be used by firefox. 

I would think that something is obviously overriding this but I have no clue.

---

### Post by gandaran on 2009-01-06
can you post the full output of this code, enter the code in firefox urlbar
```
about:plugins
```
and also this **locate libflash**, type this on the terminal/console

---

### Post by GlennW on 2009-01-07
> **gandaran said:**
> can you post the full output of this code, enter the code in firefox urlbar
```
about:plugins
```
and also this **locate libflash**, type this on the terminal/console

I've removed and purged, reinstalled adobe flash 10 (again!) but to no avail. Everytime I come upon a page with flash (youtube, vimeo, bbc, any streaming video) there's nothing but a big black box with the mediaplayerconnectivity icon in the middle of it. Hope that helps.

Here's the output from about:plugins.

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
DivX Browser Plug-In

    File name: gecko-mediaplayer-dvx.so
    Gecko Media Player 0.7.0

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer

MIME Type 	Description 	Suffixes 	Enabled
video/divx 	DivX Media Format 	divx 	Yes
video/vnd.divx 	DivX Media Format 	divx 	Yes
QuickTime Plug-in 7.4.5

    File name: gecko-mediaplayer-qt.so
    Gecko Media Player 0.7.0

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer

MIME Type 	Description 	Suffixes 	Enabled
video/quicktime 	Quicktime 	mov 	Yes
video/x-quicktime 	Quicktime 	mov 	Yes
image/x-quicktime 	Quicktime 	mov 	Yes
video/quicktime 	Quicktime 	mp4 	Yes
video/quicktime 	Quicktime - Session Description Protocol 	sdp 	Yes
application/x-quicktimeplayer 	Quicktime 	mov 	Yes
RealPlayer 9

    File name: gecko-mediaplayer-rm.so
    Gecko Media Player 0.7.0

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer

MIME Type 	Description 	Suffixes 	Enabled
audio/x-pn-realaudio 	RealAudio 	ram,rm 	Yes
application/vnd.rn-realmedia 	RealMedia 	rm 	Yes
application/vnd.rn-realaudio 	RealAudio 	ra,ram 	Yes
video/vnd.rn-realvideo 	RealVideo 	rv 	Yes
audio/x-realaudio 	RealAudio 	ra 	Yes
audio/x-pn-realaudio-plugin 	RealAudio 	rpm 	Yes
application/smil 	SMIL 	smil 	Yes
Windows Media Player Plug-in

    File name: gecko-mediaplayer-wmp.so
    Gecko Media Player 0.7.0

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer

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
application/x-ms-wmp 	Windows Media 	wmp,* 	Yes
video/x-ms-wvx 	Windows Media 	wvx,* 	Yes
audio/x-ms-wax 	Windows Media 	wax,* 	Yes
audio/x-ms-wma 	Windows Media 	wma,* 	Yes
application/x-drm-v2 	Windows Media 	asx,* 	Yes
audio/wav 	Microsoft wave file 	wav,* 	Yes
audio/x-wav 	Microsoft wave file 	wav,* 	Yes
gecko-mediaplayer 0.7.0

    File name: gecko-mediaplayer.so
    Gecko Media Player 0.7.0

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer

MIME Type 	Description 	Suffixes 	Enabled
video/mpeg 	MPEG 	mpg,mpeg 	Yes
audio/mpeg 	MPEG 	mpg,mpeg 	Yes
video/x-mpeg 	MPEG 	mpg,mpeg 	Yes
video/x-mpeg2 	MPEG2 	mpv2,mp2ve 	Yes
audio/mpeg 	MPEG 	mpg,mpeg 	Yes
audio/x-mpeg 	MPEG 	mpg,mpeg 	Yes
audio/mpeg2 	MPEG audio 	mp2 	Yes
audio/x-mpeg2 	MPEG audio 	mp2 	Yes
audio/mp4 	MPEG 4 audio 	mp4 	Yes
audio/x-mp4 	MPEG 4 audio 	mp4 	Yes
video/mp4 	MPEG 4 Video 	mp4 	Yes
video/x-m4v 	MPEG 4 Video 	m4v 	Yes
video/3gpp 	MPEG 4 Video 	mp4,3gp 	Yes
audio/mpeg3 	MPEG audio 	mp3 	Yes
audio/x-mpeg3 	MPEG audio 	mp3 	Yes
audio/x-mpegurl 	MPEG url 	m3u 	Yes
audio/mp3 	MPEG audio 	mp3 	Yes
application/x-ogg 	Ogg Vorbis Media 	ogg 	Yes
audio/ogg 	Ogg Vorbis Audio 	ogg 	Yes
audio/x-ogg 	Ogg Vorbis Audio 	ogg 	Yes
application/ogg 	Ogg Vorbis / Ogg Theora 	ogg 	Yes
audio/flac 	FLAC Audio 	flac 	Yes
audio/x-flac 	FLAC Audio 	flac 	Yes
video/fli 	FLI animation 	fli,flc 	Yes
video/x-fli 	FLI animation 	fli,flc 	Yes
video/x-flv 	Flash Video 	flv 	Yes
video/vnd.vivo 	VivoActive 	viv,vivo 	Yes
application/x-nsv-vp3-mp3 	Nullsoft Streaming Video 	nsv 	Yes
audio/x-mod 	Soundtracker 	mod 	Yes
audio/basic 	Basic Audio File 	au,snd 	Yes
audio/x-basic 	Basic Audio File 	au,snd 	Yes
audio/midi 	MIDI Audio 	mid,midi,kar 	Yes
audio/x-scpls 	Shoutcast Playlist 	pls 	Yes
Java(TM) Plug-in 1.6.0_10-b33

    File name: libjavaplugin_oji.so
    Java(TM) Plug-in 1.6.0_10

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
application/x-java-applet;version=1.6 	Java 		Yes
application/x-java-applet;jpi-version=1.6.0_10 	Java 		Yes
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
application/x-java-bean;version=1.6 	Java 		Yes
application/x-java-bean;jpi-version=1.6.0_10 	Java 		Yes
Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 10.0 r15

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
Helix DNA Plugin: RealPlayer G2 Plug-In Compatible

    File name: nphelix.so
    Helix DNA Plugin: RealPlayer G2 Plug-In Compatible version 0.4.0.4434 built with gcc 3.4.6 on Oct 1 2008

MIME Type 	Description 	Suffixes 	Enabled
audio/x-pn-realaudio-plugin 	RealPlayer Plugin Metafile 	rpm 	Yes


Here's the output from terminal>locate libflash

/home/glenn/.mozilla/extensions/libflashplayer.so
/home/glenn/.mozilla/firefox/libflashplayer.so
/home/glenn/.mozilla/plugins/libflashplayer.so
/usr/lib/iceweasel/libflashsupport.so
/usr/lib/openoffice/program/libflash680li.so
/usr/lib/xulrunner/libflashsupport.so

Thanks for your input.

---

### Post by gandaran on 2009-01-07
> I've removed and purged, reinstalled adobe flash 10 (again!) but to no avail. Everytime I come upon a page with flash (youtube, vimeo, bbc, any streaming video) there's nothing but a big black box with the mediaplayerconnectivity icon in the middle of it. Hope that helps.
have you tried disabling the media player connectivity addon? or check the flash option in the media player connectivity preferences, what player is set to run it!
> /home/glenn/.mozilla/extensions/libflashplayer.so
/home/glenn/.mozilla/firefox/libflashplayer.so
/home/glenn/.mozilla/plugins/libflashplayer.so
/usr/lib/iceweasel/libflashsupport.so
/usr/lib/xulrunner/libflashsupport.so
why is flash also installed in /home/glenn/.mozilla/firefox/libflashplayer.so and /home/glenn/.mozilla/extensions/libflashplayer.so?
should be only on /home/glenn/.mozilla/plugins/libflashplayer.so!
this flash was installed from the adobe .tar.gz (tarball) package, have you also installed the adobe-flashplugin .deb package? and the flashplugin-nonfree?
are you running ubuntu 8.04 and do you need libflashsupport installed? libflashsupport is only needed for flash 9 sound problems and possibly conflicts with flash 10.

---

### Post by GlennW on 2009-01-07
> **gandaran said:**
> have you tried disabling the media player connectivity addon? or check the flash option in the media player connectivity preferences, what player is set to run it!

why is flash also installed in /home/glenn/.mozilla/firefox/libflashplayer.so and /home/glenn/.mozilla/extensions/libflashplayer.so?
should be only on /home/glenn/.mozilla/plugins/libflashplayer.so!
this flash was installed from the adobe .tar.gz (tarball) package, have you also installed the adobe-flashplugin .deb package? and the flashplugin-nonfree?
are you running ubuntu 8.04 and do you need libflashsupport installed? libflashsupport is only needed for flash 9 sound problems and possibly conflicts with flash 10.

Thanks for your time! The mediaplayerconnectivity addon has totem running the flash media. That doesn't sound right at all!

I have disabled the mediaplayerconnectivity addon and will restart X now. I have also removed libflash from all but the folder you specified.

I'll post shortly.

---

### Post by GlennW on 2009-01-07
That did it gandaran! I disabled the mediaplayerconnectivity addon as mentioned in the previous post. It would be nice to know exactly what the issue was but for now I'm thrilled that things are working as they did previously.

Thanks.

---

