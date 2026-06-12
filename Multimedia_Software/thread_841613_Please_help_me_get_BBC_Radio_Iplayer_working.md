---
title: "Please help me get BBC Radio Iplayer working"
date: 2008-06-26
forum: Multimedia Software
---

### Post by ouchouchouch on 2008-06-26
OK, I have Ubuntu 8.04. I managed to get the BBC Radio iplayer working ages ago during beta after a lot of installing various stuff recommended on this forum. 

It stopped working several times but started again after updates. Now it has stopped working again only for streaming audio from the BBC Radio iplayer. 

Everything else (audio/video/flash) works just fine. This is making me really, really frustrated. No errors, no messages, no crash, it just does not work. 

Please take pity on me someone. This sort of stuff has worked for me in the past on the Windows platform, and I really, really don't want to go back after six months on Ubuntu only. But without streaming BBC radio I simply can't carry on. Help!

---

### Post by ouchouchouch on 2008-06-26
More information:

When I select play in the iplayer, it gives a few messages (getting playlist, connecting to some IP or URL) and then simply says "stopped"

If I say aboutplugins in firefox it returns a load of entries for all sorts of stuff. There look to be a number which might play iPlayer content (I've no idea what the streaming media format is though)

Is it possible to remove all the plugins, all the multimedia stuff etc and start again, in case there is some kind of conflict? 

Or do I have to zap the whole installation and start again. I really hope not, that is one of the beastly features of nameless proprietary O/S when they break is it not?

---

### Post by aeiah on 2008-06-26
have you tried both real player and windows media player streams? both work for me. i didnt even think i installed real player to be honest. i have the firefox mplayer plugin, which is used for the windows media version of the stream.

here's my plugin list from firefox
```
Windows Media Player Plugin

    File name: mplayerplug-in-wmp.so
    mplayerplug-in 3.40

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets


Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 9.0 r115


Java(TM) Plug-in 1.6.0_03-b05

    File name: libjavaplugin_oji.so
    Java(TM) Plug-in 1.6.0_03


DivX Browser Plug-In

    File name: mplayerplug-in-dvx.so
    mplayerplug-in 3.40

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets


QuickTime Plug-in 6.0 / 7

    File name: mplayerplug-in-qt.so
    mplayerplug-in 3.40

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets


RealPlayer 9

    File name: mplayerplug-in-rm.so
    mplayerplug-in 3.40

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets


mplayerplug-in 3.40

    File name: mplayerplug-in.so
    mplayerplug-in 3.40

    Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using MPlayer
    JavaScript Enabled and Using GTK2 Widgets

```

so yea. its all mplayer based. if you havent got mplayer firefox plugin then perhaps you could follow this and it'll help:
[http://ubuntuforums.org/showthread.php?t=540412](http://ubuntuforums.org/showthread.php?t=540412)

---

### Post by ouchouchouch on 2008-06-27
Hi there, thanks for the advice, well I tried everything in the thread...

[http://ubuntuforums.org/showthread.php?t=540412](http://ubuntuforums.org/showthread.php?t=540412)

...but still no streaming from the BBC Radio player, neither stream types work. When I inspect the plugins in firefox mplayerplug-in 3.50 seems to be loaded.

Does anyone know how I can remove **everything** to do with media, streaming, browsing, firefox, plugins, codecs and re-install all of it? Or is there a smarter way to de-bug this problem?

---

### Post by icheyne on 2008-06-27
I fixed this by reverting to Firefox 2.

[https://answers.launchpad.net/ubuntu/+faq/95](https://answers.launchpad.net/ubuntu/+faq/95)

sudo aptitude remove firefox-3.0
I clicked "n" to the first solution and accepted the second one that installed Firefox 2

---

### Post by ouchouchouch on 2008-06-28
Hi thanks for the advice. 

I tried this and still no result. Streaming from the BBC radio iplayer does not work still. I'm considering clean installing to verify whether my base system is broken in some mysterious way (it is gutsy, upgraded to hardy beta, and then hardy 8.04) so there could be nasty baggage on board.

I think I need to definitively establish whether x64 8.04, firefox 3, BBC Radio Iplayer, mplayer plugin combination is universally broken on my hardware or not.

I really resent having to go down this route, I'd prefer find out what is broken on the existing system, but I can't identify a method for trouble shooting it :(



> **icheyne said:**
> I fixed this by reverting to Firefox 2.

[https://answers.launchpad.net/ubuntu/+faq/95](https://answers.launchpad.net/ubuntu/+faq/95)

sudo aptitude remove firefox-3.0
I clicked "n" to the first solution and accepted the second one that installed Firefox 2

---

### Post by Pjotr123 on 2008-06-28
- do a clean installation of 32-bit generic Ubuntu 8.04 (therefore not 64-bit!). Easiest way:
[http://ubuntutip.googlepages.com/reinstall](http://ubuntutip.googlepages.com/reinstall)

- apply this to-do list straight after installation:
[http://ubuntutip.googlepages.com/thefirstthingstodo](http://ubuntutip.googlepages.com/thefirstthingstodo)

The multimedia part of that list should take care of this problem. :-)

---

### Post by ouchouchouch on 2008-06-28
OK thanks everyone, now fixed by a complete re-install of my system disk (I have /home on a different partition for exactly this circumstance)

I reinstalled 64 bit 8.04, then followed this recipe someone pointed me at;

apt-get remove totem-mozilla mozilla-plugin-vlc
apt-get install mozilla-mplayer
apt-get install ubuntu-restricted-extras

then; 

1.Edit /etc/apt/sources.list


sudo gedit /etc/apt/sources.list

2.Append the following lines to it:

## Medibuntu - Ubuntu 8.04 "hardy"
deb  [http://packages.medibuntu.org/](http://packages.medibuntu.org/) hardy free non-free

3.Import medibuntu's key and update the local package list

wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

4.Now install the codec we need:

sudo apt-get install non-free-codecs

While it is annoying to have to just blat the entire O/S to fix a streaming media problem, it was gratifying that my complete application environment functioned properly when I moved the new install /home to a scratch dir in root, mkdir /home, tweaked /etc/fstab to point to the correct /home disk and rebooted, job done! Absolutely all apps including email, firefox properly configured and functional in 1 minute. Try doing that with any of the M$ O/S! 

All I need to know now is how to mark this thread solved?



> **Pjotr123 said:**
> - do a clean installation of 32-bit generic Ubuntu 8.04 (therefore not 64-bit!). Easiest way:
[http://ubuntutip.googlepages.com/reinstall](http://ubuntutip.googlepages.com/reinstall)

- apply this to-do list straight after installation:
[http://ubuntutip.googlepages.com/thefirstthingstodo](http://ubuntutip.googlepages.com/thefirstthingstodo)

The multimedia part of that list should take care of this problem. :-)

---

### Post by xc3RnbFO8P on 2008-06-28
In Thread Tools on the top of the page.

---

### Post by ouchouchouch on 2008-06-29
ARRRRRRGGGGHHHH!!

OK the problem is back again. Once again no streaming BBC Radio from the Iplayer. Also the listen again content has ceased functioning this time. I've changed nothing at all. However, using the beta version for the new unified BBC Iplayer, the listen again stuff works, but not the streaming.

Yesterday (after a complete re-install) this all worked, persisted over reboots, was apparently robust. Today it is broken. Pretty much it is looking like bit rot 1, Ubuntu 0 here.

I'm more than disappointed. I'm going to post a rant on the Testimonials & Experiences discussion.

Should I switch to the 32 bit OS and try again and there is a high probability of success? Or is it unrealistic to expect Ubuntu to be able to stream BBC radio content at all and that I actually need to use a Microsoft platform to do this reliably :-(

---

### Post by icheyne on 2008-06-29
Sorry to hear it still does not work for you. It's fine here (in 32 bitland).

---

### Post by saltandwoodsmoke on 2008-07-18
JFTR, I too can't gat live streaming of Radio on the iPlayer either.

I have installed Gstream codecs, mplayer plugins, RealPlayer, Flash.

All archived content plays fine. No live streaming. I haven't done a clean install and, as I am a newbie with little spare time on my hand I don't intend to ;)

---

### Post by majabl on 2008-07-19
> **saltandwoodsmoke said:**
> JFTR, I too can't gat live streaming of Radio on the iPlayer either.

I have installed Gstream codecs, mplayer plugins, RealPlayer, Flash.

All archived content plays fine. No live streaming. I haven't done a clean install and, as I am a newbie with little spare time on my hand I don't intend to ;)

Is this through the new iPlayer radio streamer or through the BBC Radio player that the BBC has made available for the past through years?  For me, using just mplayer, the BBC Radio player works no problem, but if I try to play radio using the iPlayer then I get sound only if I have the iPlayer window in the foreground.

---

### Post by Jeztastic on 2008-07-25
I can't get iPlayer to stream at all. It seems that BBC radio is moving away from letting you use RealPlayer and Windows Media Player. It's a pain.

---

### Post by ash05 on 2008-07-25
do a clean installation of 32-bit generic Ubuntu 8.04

---

### Post by F W Adams on 2008-08-14
I have an 8.04 set up and just tried the advice given below from post #7, the TV and radio on iplayer worked fine.

---------------- 

- apply this to-do list straight after installation:
[http://ubuntutip.googlepages.com/thefirstthingstodo](http://ubuntutip.googlepages.com/thefirstthingstodo)

The multimedia part of that list should take care of this problem.

---

### Post by Andrew B. on 2008-09-04
I've been having similar problems with BBC iplayer.  Looking at the BBC website, they say that you can only use Adobe Flash Player, and no other Flash player, because of digital rights management.

I have tried and tried to get BBC iplayer working with Firefox.  I've done all the things in the (excellent) beginners multimedia tips on [http://ubuntutip.googlepages.com/](http://ubuntutip.googlepages.com/) but they haven't helped with this particular problem.

Firefox shows in its add ons that Shockwave Flash 9.0 r124 is enabled, but when I go to the "test flash player" page on the Adobe website, it doesn't work.

So I installed Opera, and BBC iplayer works just fine in Opera, but still doesn't work in Firefox!  It doesn't matter particularly that it doesn't work in Firefox, but I'm curious as to what I've done wrong, and also other users might have the same problem?

My ubuntu installation is v. simple, with nothing unusual.  As I say, I followed all the multimedia tips from the ubuntu tips.  

I've (hopefully completely) uninstalled and reinstalled Firefox, with no improvement.  Any ideas, anyone?  

(I'm not sure if I should have added this on this thread or started a new one -- sorry if I've done the wrong thing.)

---

### Post by gandaran on 2008-09-04
> Firefox shows in its add ons that Shockwave Flash 9.0 r124 is enabled, but when I go to the "test flash player" page on the Adobe website, it doesn't work.

do you have any other flash package installed? like gnash, swfdec or libflash-mozplugin?

type **about: plugins** (without spaces) in firefox url bar, post back here the full output.

note: went to the "test flash player" adobe site, didn't work, maybe because I have flash 10 beta installed.

---

### Post by Raffles10 on 2008-09-04
It must be a codec issue. I just tried it and it works fine for me. The only thing is I'm using Linux Mint, which is basically Ubuntu with a different theme, a few extra tools and it includes all the extra codecs that the default install of Ubuntu doesn't. One of which must be the one that gets Iplayer working in Firefox.

Sorry if doesn't help you very much, but at least it does work in linux, if you can find the right codec.

---

### Post by Andrew B. on 2008-09-04
Gandaran -- thanks for the help.  This is what about:plugins produces.  The entries for Flash are right at the end:

Installed plugins
Find more information about browser plugins at mozilla.org.
Help for installing plugins is available from plugindoc.mozdev.org.
VLC Multimedia Plugin

    File name: libvlcplugin.so
    Version 0.8.6e Janus, copyright 1996-2007 The VideoLAN Team
    [http://www.videolan.org/](http://www.videolan.org/)

MIME Type 	Description 	Suffixes 	Enabled
audio/mpeg 	MPEG audio 	mp2,mp3,mpga,mpega 	Yes
audio/x-mpeg 	MPEG audio 	mp2,mp3,mpga,mpega 	Yes
video/mpeg 	MPEG video 	mpg,mpeg,mpe 	Yes
video/x-mpeg 	MPEG video 	mpg,mpeg,mpe 	Yes
video/mpeg-system 	MPEG video 	mpg,mpeg,mpe,vob 	Yes
video/x-mpeg-system 	MPEG video 	mpg,mpeg,mpe,vob 	Yes
video/mpeg4 	MPEG-4 video 	mp4,mpg4 	Yes
audio/mpeg4 	MPEG-4 audio 	mp4,mpg4 	Yes
application/mpeg4-iod 	MPEG-4 video 	mp4,mpg4 	Yes
application/mpeg4-muxcodetable 	MPEG-4 video 	mp4,mpg4 	Yes
video/x-msvideo 	AVI video 	avi 	Yes
video/quicktime 	QuickTime video 	mov,qt 	Yes
application/x-ogg 	Ogg stream 	ogg 	Yes
application/ogg 	Ogg stream 	ogg 	Yes
application/x-vlc-plugin 	VLC plugin 	vlc 	Yes
video/x-ms-asf-plugin 	Windows Media Video 	asf,asx 	Yes
video/x-ms-asf 	Windows Media Video 	asf,asx 	Yes
application/x-mplayer2 	Windows Media 		Yes
video/x-ms-wmv 	Windows Media 	wmv 	Yes
application/x-google-vlc-plugin 	Google VLC plugin 		Yes
audio/wav 	WAV audio 	wav 	Yes
audio/x-wav 	WAV audio 	wav 	Yes
audio/3gpp 	3GPP audio 	3gp,3gpp 	Yes
video/3gpp 	3GPP video 	3gp,3gpp 	Yes
audio/3gpp2 	3GPP2 audio 	3g2,3gpp2 	Yes
video/3gpp2 	3GPP2 video 	3g2,3gpp2 	Yes
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
image/x-macInstalled plugins
Find more information about browser plugins at mozilla.org.
Help for installing plugins is available from plugindoc.mozdev.org.
VLC Multimedia Plugin

    File name: libvlcplugin.so
    Version 0.8.6e Janus, copyright 1996-2007 The VideoLAN Team
    [http://www.videolan.org/](http://www.videolan.org/)

MIME Type 	Description 	Suffixes 	Enabled
audio/mpeg 	MPEG audio 	mp2,mp3,mpga,mpega 	Yes
audio/x-mpeg 	MPEG audio 	mp2,mp3,mpga,mpega 	Yes
video/mpeg 	MPEG video 	mpg,mpeg,mpe 	Yes
video/x-mpeg 	MPEG video 	mpg,mpeg,mpe 	Yes
video/mpeg-system 	MPEG video 	mpg,mpeg,mpe,vob 	Yes
video/x-mpeg-system 	MPEG video 	mpg,mpeg,mpe,vob 	Yes
video/mpeg4 	MPEG-4 video 	mp4,mpg4 	Yes
audio/mpeg4 	MPEG-4 audio 	mp4,mpg4 	Yes
application/mpeg4-iod 	MPEG-4 video 	mp4,mpg4 	Yes
application/mpeg4-muxcodetable 	MPEG-4 video 	mp4,mpg4 	Yes
video/x-msvideo 	AVI video 	avi 	Yes
video/quicktime 	QuickTime video 	mov,qt 	Yes
application/x-ogg 	Ogg stream 	ogg 	Yes
application/ogg 	Ogg stream 	ogg 	Yes
application/x-vlc-plugin 	VLC plugin 	vlc 	Yes
video/x-ms-asf-plugin 	Windows Media Video 	asf,asx 	Yes
video/x-ms-asf 	Windows Media Video 	asf,asx 	Yes
application/x-mplayer2 	Windows Media 		Yes
video/x-ms-wmv 	Windows Media 	wmv 	Yes
application/x-google-vlc-plugin 	Google VLC plugin 		Yes
audio/wav 	WAV audio 	wav 	Yes
audio/x-wav 	WAV audio 	wav 	Yes
audio/3gpp 	3GPP audio 	3gp,3gpp 	Yes
video/3gpp 	3GPP video 	3gp,3gpp 	Yes
audio/3gpp2 	3GPP2 audio 	3g2,3gpp2 	Yes
video/3gpp2 	3GPP2 video 	3g2,3gpp2 	Yes
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
Java(TM) Plug-in 1.6.0_06-b02

    File name: libjavaplugin_oji.so
    Java(TM) Plug-in 1.6.0_06

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
application/x-java-applet;jpi-version=1.6.0_06 	Java 		Yes
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
application/x-java-bean;jpi-version=1.6.0_06 	Java 		Yes
Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 9.0 r124

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yespaint 	MacPaint Bitmap image 	pntg 	Yes
image/x-quicktime 	QuickTime image 	pict, pict1, pict2 	Yes
video/x-m4v 	MPEG-4 video 	m4v 	Yes
Java(TM) Plug-in 1.6.0_06-b02

    File name: libjavaplugin_oji.so
    Java(TM) Plug-in 1.6.0_06

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
application/x-java-applet;jpi-version=1.6.0_06 	Java 		Yes
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
application/x-java-bean;jpi-version=1.6.0_06 	Java 		Yes
Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 9.0 r124

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes

---

### Post by gandaran on 2008-09-04
> **Andrew B. said:**
> Gandaran -- thanks for the help.  This is what about:plugins produces.  The entries for Flash are right at the end:

Installed plugins
Find more information about browser plugins at mozilla.org.
Help for installing plugins is available from plugindoc.mozdev.org.
VLC Multimedia Plugin

    File name: libvlcplugin.so
    Version 0.8.6e Janus, copyright 1996-2007 The VideoLAN Team
    [http://www.videolan.org/](http://www.videolan.org/)

MIME Type 	Description 	Suffixes 	Enabled
audio/mpeg 	MPEG audio 	mp2,mp3,mpga,mpega 	Yes
audio/x-mpeg 	MPEG audio 	mp2,mp3,mpga,mpega 	Yes
video/mpeg 	MPEG video 	mpg,mpeg,mpe 	Yes
video/x-mpeg 	MPEG video 	mpg,mpeg,mpe 	Yes
video/mpeg-system 	MPEG video 	mpg,mpeg,mpe,vob 	Yes
video/x-mpeg-system 	MPEG video 	mpg,mpeg,mpe,vob 	Yes
video/mpeg4 	MPEG-4 video 	mp4,mpg4 	Yes
audio/mpeg4 	MPEG-4 audio 	mp4,mpg4 	Yes
application/mpeg4-iod 	MPEG-4 video 	mp4,mpg4 	Yes
application/mpeg4-muxcodetable 	MPEG-4 video 	mp4,mpg4 	Yes
video/x-msvideo 	AVI video 	avi 	Yes
video/quicktime 	QuickTime video 	mov,qt 	Yes
application/x-ogg 	Ogg stream 	ogg 	Yes
application/ogg 	Ogg stream 	ogg 	Yes
application/x-vlc-plugin 	VLC plugin 	vlc 	Yes
video/x-ms-asf-plugin 	Windows Media Video 	asf,asx 	Yes
video/x-ms-asf 	Windows Media Video 	asf,asx 	Yes
application/x-mplayer2 	Windows Media 		Yes
video/x-ms-wmv 	Windows Media 	wmv 	Yes
application/x-google-vlc-plugin 	Google VLC plugin 		Yes
audio/wav 	WAV audio 	wav 	Yes
audio/x-wav 	WAV audio 	wav 	Yes
audio/3gpp 	3GPP audio 	3gp,3gpp 	Yes
video/3gpp 	3GPP video 	3gp,3gpp 	Yes
audio/3gpp2 	3GPP2 audio 	3g2,3gpp2 	Yes
video/3gpp2 	3GPP2 video 	3g2,3gpp2 	Yes
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
image/x-macInstalled plugins
Find more information about browser plugins at mozilla.org.
Help for installing plugins is available from plugindoc.mozdev.org.
VLC Multimedia Plugin

    File name: libvlcplugin.so
    Version 0.8.6e Janus, copyright 1996-2007 The VideoLAN Team
    [http://www.videolan.org/](http://www.videolan.org/)

MIME Type 	Description 	Suffixes 	Enabled
audio/mpeg 	MPEG audio 	mp2,mp3,mpga,mpega 	Yes
audio/x-mpeg 	MPEG audio 	mp2,mp3,mpga,mpega 	Yes
video/mpeg 	MPEG video 	mpg,mpeg,mpe 	Yes
video/x-mpeg 	MPEG video 	mpg,mpeg,mpe 	Yes
video/mpeg-system 	MPEG video 	mpg,mpeg,mpe,vob 	Yes
video/x-mpeg-system 	MPEG video 	mpg,mpeg,mpe,vob 	Yes
video/mpeg4 	MPEG-4 video 	mp4,mpg4 	Yes
audio/mpeg4 	MPEG-4 audio 	mp4,mpg4 	Yes
application/mpeg4-iod 	MPEG-4 video 	mp4,mpg4 	Yes
application/mpeg4-muxcodetable 	MPEG-4 video 	mp4,mpg4 	Yes
video/x-msvideo 	AVI video 	avi 	Yes
video/quicktime 	QuickTime video 	mov,qt 	Yes
application/x-ogg 	Ogg stream 	ogg 	Yes
application/ogg 	Ogg stream 	ogg 	Yes
application/x-vlc-plugin 	VLC plugin 	vlc 	Yes
video/x-ms-asf-plugin 	Windows Media Video 	asf,asx 	Yes
video/x-ms-asf 	Windows Media Video 	asf,asx 	Yes
application/x-mplayer2 	Windows Media 		Yes
video/x-ms-wmv 	Windows Media 	wmv 	Yes
application/x-google-vlc-plugin 	Google VLC plugin 		Yes
audio/wav 	WAV audio 	wav 	Yes
audio/x-wav 	WAV audio 	wav 	Yes
audio/3gpp 	3GPP audio 	3gp,3gpp 	Yes
video/3gpp 	3GPP video 	3gp,3gpp 	Yes
audio/3gpp2 	3GPP2 audio 	3g2,3gpp2 	Yes
video/3gpp2 	3GPP2 video 	3g2,3gpp2 	Yes
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
Java(TM) Plug-in 1.6.0_06-b02

    File name: libjavaplugin_oji.so
    Java(TM) Plug-in 1.6.0_06

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
application/x-java-applet;jpi-version=1.6.0_06 	Java 		Yes
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
application/x-java-bean;jpi-version=1.6.0_06 	Java 		Yes
Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 9.0 r124

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yespaint 	MacPaint Bitmap image 	pntg 	Yes
image/x-quicktime 	QuickTime image 	pict, pict1, pict2 	Yes
video/x-m4v 	MPEG-4 video 	m4v 	Yes
Java(TM) Plug-in 1.6.0_06-b02

    File name: libjavaplugin_oji.so
    Java(TM) Plug-in 1.6.0_06

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
application/x-java-applet;jpi-version=1.6.0_06 	Java 		Yes
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
application/x-java-bean;jpi-version=1.6.0_06 	Java 		Yes
Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 9.0 r124

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes

Andrew B. 
        the flash looks okay, but remember, for BBC iplayer you need two things, flash and a real video compatible player, you have the default totem gstreamer plugin installed, this player doesn't player real video, 
(opera doesn't work with gtk apps, example, totem, thats why iplayer works in opera if you have another player plugin installed) so to get iplayer working in firefox you either remove the totem plugin and let the vlc or maplyer plugin (which one have you installed) take over the embedded firefox streaming.
another way you can keep the totem plugin (remove all other player plugins), install real player 11 **and run the commands to get realplayer embbeded as a plugin just for real video  ** totem will handle the rest.

edit: I can't  be 100% sure about this, I not in the UK, so i can't use the iplayer, only the iplayer radio service, for the radio service you need a real player, so I figured it's the same for videos, maybe I'm wrong it only uses flash.

---

### Post by gandaran on 2008-09-04
> **Raffles10 said:**
> It must be a codec issue. I just tried it and it works fine for me. The only thing is I'm using Linux Mint, which is basically Ubuntu with a different theme, a few extra tools and it includes all the extra codecs that the default install of Ubuntu doesn't. One of which must be the one that gets Iplayer working in Firefox.

Sorry if doesn't help you very much, but at least it does work in linux, if you can find the right codec.

it's not just a codec issue, Linux Mint comes with default mplayer plugin and the mplayer  codecs already installed, while ubuntu uses totem.

---

### Post by Andrew B. on 2008-09-04
>       the flash looks okay, but remember, for BBC iplayer you need two things, flash and a real video compatible player, you have the default totem gstreamer plugin installed, this player doesn't player real video, 
 so to get iplayer working in firefox you either remove the totem plugin and let the vlc or maplyer plugin (which one have you installed) take over the embedded firefox streaming.
another way you can keep the totem plugin (remove all other player plugins), install real player 11 **and run the commands to get realplayer embbeded as a plugin just for real video  ** totem will handle the rest.

Gandaran -- I'm sorry, but I'm stuck again!  I have tried both these routes, but without success.  

First, I went into Firefox > Tools > Add-ons and disabled all the Totem add-ons, leaving just Shockwave Flash and VLC.  BBC iplayer still didn't work.  Then I looked into RealPlayer.  Realplayer 11 doesn't seem to be in Synaptic.  So I have downloaded a ".bin" file from the RealPlayer website but I don't know what to do with that now!

I don't want to consume any more of your time -- especially since Opera works and I can use that! -- but if you could point me at idiot-proof instructions on how to get the right set up I'd be grateful!  Thanks.

---

### Post by gandaran on 2008-09-04
Andrew B.
just one question, does flash work in other sites, like youtube videos?

if firefox doesn't work with iplayer, forget installing real player. I don't recommend it.

---

### Post by Andrew B. on 2008-09-05
Flash (in Firefox) doesn't work on YouTube either.  Flash works fine in Opera still.

---

### Post by gandaran on 2008-09-05
> **Andrew B. said:**
> Flash (in Firefox) doesn't work on YouTube either.  Flash works fine in Opera still.

look, this is very strange, maybe you have a firefox addon installed that is blocking flash (flashblock, addblock or something else), try disabling them and restart firefox.

if it still doesn't work, then delete the hidden home .mozilla folder (backup the folder first) and restart firefox, go to youtube and try the videos.

---

### Post by Andrew B. on 2008-09-05
I am pretty sure I don't have the flash block or ad block add-ins.  

I deleted the hidden .mozilla folder.  It looks like it contained all the bookmarks and passwords etc because it was like going into Firefox for the first time.  But I still have the same problem with Flash.

I'm going to reinstall Ubuntu again from scratch and see if I can make it work!  I'll let you know how I get on.

---

### Post by Andrew B. on 2008-09-06
Here's what I did.  I re-installed Ubuntu from the 8.04 CD, a complete re-install.  I accepted all the updates (which came in two tranches).  I then selected the flashplayer nonfree plugin, which installed (eventually -- only a 3Kb/s connection) and then BBC iplayer worked.  So I don't know what the problem was, but whatever it was, it's fixed.  In fiddling about trying to solve it I must have damaged something.  Reinstalling Ubuntu is dead easy so in hindsight I should have tried it sooner, although in fiddling about I did learn a lot.

Live streaming of radio still didn't seem to work so I worked through the sticky in this forum (the comprehensive multimedia how-to) and now everything works except QuickTime.  The problem with the live radio was, in the end, a lack of patience: it took **forever** to start.

To fix the Quicktime problem I'm intending to uninstall Gecko and try a different program in its place.

Thank you again for your help.

---

### Post by sallywon on 2008-09-06
Thank u for ur advise buddy!

---

### Post by shaimaster1 on 2008-09-08
I can play the music in the BBC Iplayer but I cannot see the play seek slider. I had it before but now it just shows the controls and loads up.

---

### Post by kline on 2008-10-06
Sorry if I am beating a dead hourse, but under 8.04 and using firefox, the popup and selection High Speed is grayed out for the BBC iPlayer.  When I select Low quality, I can eventually get a realplay[er] to feed me at 20kbps.  The high speed says that it can find neither Windose nor Real, BTW.

If I use konqueror, something called "Kaffiene Player" works flawlessly, but only for 80-83 seconds before it quits.

I have *not* reverted to firefox-2; that may be part of the firefox snafu.    Regarding the konqueror browser, it always seems to want to use amarok if I choose an mp3 stream.  I have repeatedly tried to switch over to xine and-or kmplayer.  

Before, with 6.06 just about everything seemed to work.  (*sigh*)

---

### Post by icheyne on 2008-10-06
Ibex should make life easier:

[http://www.ubuntu.com/testing/intrepid/beta#Totem%20BBC%20plugin](http://www.ubuntu.com/testing/intrepid/beta#Totem%20BBC%20plugin)

---

### Post by kline on 2008-10-08
> **icheyne said:**
> Ibex should make life easier:

[http://www.ubuntu.com/testing/intrepid/beta#Totem%20BBC%20plugin](http://www.ubuntu.com/testing/intrepid/beta#Totem%20BBC%20plugin)

Hm.  Well, *this* time at least, I knew where to find the "Update Manager";
but all it did was pick up a bunch of perhaps 15 utilities.  So, altho this is not the place to ask this, it's important: how do I upgrade from 8.04 to 8.10?  [[ Previously, I stuck with 6.06 LTS for 2+ years and had to wait for somebody to take their time to do backports.  This time, using the update tool--which is a ++great GUI tool--I want to stay current.]]

Looks likt the Ubuntu volunteers and the BBC and probably others are fixing stuff quickly.  This is just one reason I'll be switching to Ubuntu.

thanks for any clues re 8.04 -> 8.10.  Else please tell me where else to ask! BTW, if the upgrade tool only works for completed releases, I can wait for 8.10 to get out of Beta.  ...Gotta have the BBC.

---

### Post by icheyne on 2008-10-08
[http://www.google.co.uk/search?hl=en&q=ubuntu+beta](http://www.google.co.uk/search?hl=en&q=ubuntu+beta)
[http://www.ubuntu.com/testing/intrepid/beta](http://www.ubuntu.com/testing/intrepid/beta)

**Upgrading from Ubuntu 8.04**
To upgrade from Ubuntu 8.04, press Alt+F2 and type in "update-manager -d" (without the quotes) into the command box. Update Manager should open up and tell you: New distribution release '8.10' is available. Click Upgrade and follow the on-screen instructions.

---

### Post by beercz on 2008-10-25
I am running Intrepid, with firefox 3.

Foolishly, I "experimented" with my plugins and have now lost my streaming media from the BBC website (I use them alot).

I can get streaming video from the [bbc news]("http://news.bbc.co.uk") website, but I cannot get sound from this site.

Nor can I get sound from any live streamed BBC radio station. 

If I try the BBC's iPlayer and attempt to watch/listen to any of their streaming services I get "This service is unavailable at this time".

I can watch/listen to any of the BBC's archived content with no problem, it's just their live streaming content I cannot pick up.

Anyone know which ff plugins I need to use for BBC streaming media?

Thanks in advance.

---

### Post by eternalnewbee on 2008-10-25
This is what solved my problem with the bbc player:
I went to Addons and typed "streaming" in the search bar, scrolled down to an Addon called "Media Connectivity", and installed it. Restarted FF, went to the BBC radio page and clicked on BBC World service. The usual player opened, but there was an extra button which I clicked, and then vlc appeared, and acouple of seconds later I was listening to the BBC.

It's not the ideal solution, but it works. I hope the explanation was clear enough.
Good luck.
EDIT: In the Preferences of Media Connectivity you can choose your default player of choice. Not necessarily vlc.

---

### Post by beercz on 2008-10-27
Thanks eternalnewbee

Seems to work now having installed Firefox's media connectivity plug in.

I must stop "experimenting" .... perhaps not :twisted:

---

### Post by ajgreeny on 2008-10-27
Going right back to the start of this thread, which I have just found, I would suggest you install totem-xine and get rid of totem-gstreamer.  Also uninstall the totem-mozilla plugin and make sure you have mozilla-mplayer.  This has always worked for me without problem on BBC sites for audio streams, and video is, of course, by flash, which is now fine with flash 10 installed; it always played, but not as smoothly as it does now.

---

### Post by eternalnewbee on 2008-10-28
> Thanks eternalnewbee

Seems to work now having installed Firefox's media connectivity plug in.
You're welcome.

---

### Post by linuxlab on 2008-10-28
have you installed VLC, I remember installing VLC awhile ago and it fixed a problem of a kind?

$ sudo -i
passwd
apt-get update
apt-get install vlc

---

### Post by kylea on 2008-11-24
> **ajgreeny said:**
> Going right back to the start of this thread, which I have just found, I would suggest you install totem-xine and get rid of totem-gstreamer.  Also uninstall the totem-mozilla plugin and make sure you have mozilla-mplayer.  This has always worked for me without problem on BBC sites for audio streams, and video is, of course, by flash, which is now fine with flash 10 installed; it always played, but not as smoothly as it does now.


After 4 weeks of hell I finally found your post - thanks very much - I cannot believe it but I can now stream the BBC and ABC (Australia) via Firefox 3.04.

Uninstalled the plugins as recommended, installed mozilla-mplayer and it just started :popcorn::lolflag:

---

