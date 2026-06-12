---
title: "[SOLVED] No flash player"
date: 2008-11-10
forum: Multimedia Software
---

### Post by coop0311emt on 2008-11-10
I went through the prompted install and searched this site and tried someone else's repair for the same problem but to no avail basically it keeps telling me that my java is not turned on or I don't have a flash player installed every time I try to watch youtube and the like

I am really new and appreciate any help you can give me thanks

---

### Post by gandaran on 2008-11-10
install this package **ubuntu-restricted-extras** in add/remove programs or use the command line to install
 **sudo apt-get install ubuntu-restricted-extras**
this package installs flash, java and codecs

---

### Post by coop0311emt on 2008-11-10
used the command line to install the package but I am still not up and running

---

### Post by gandaran on 2008-11-10
did you restart firefox?

---

### Post by coop0311emt on 2008-11-10
yes

---

### Post by gandaran on 2008-11-10
okay then, type this code in firefox url bar, post the full output here
```
about:plugins
```

---

### Post by aysiu on 2008-11-10
Can you paste these commands into the terminal and then post the output back here? ```
sudo updatedb
cat /etc/lsb-release
uname -m
locate flashplay
locate libflash
dpkg -s flashplugin-nonfree
dpkg -s mozilla-plugin-gnash
dpkg -s swfdec-mozilla
``` The first command may take a few minutes to execute. Just be patient.

---

### Post by coop0311emt on 2008-11-10
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
Java(TM) Plug-in 1.6.0_07-b06

    File name: libjavaplugin_oji.so
    Java(TM) Plug-in 1.6.0_07

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
application/x-java-applet;jpi-version=1.6.0_07 	Java 		Yes
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
application/x-java-bean;jpi-version=1.6.0_07 	Java 		Yes
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

    File name: libswfdecmozilla.so
    Shockwave Flash 9.0 r100

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Adobe Flash movie 	swf 	Yes
application/futuresplash 	FutureSplash movie 	spl 	Yes

---

### Post by coop0311emt on 2008-11-10
administrator@administrator-desktop:~$ sudo updatedb
administrator@administrator-desktop:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.04
DISTRIB_CODENAME=hardy
DISTRIB_DESCRIPTION="Ubuntu 8.04.1"
administrator@administrator-desktop:~$ uname -m
i686
administrator@administrator-desktop:~$ locate flashplay
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#adaptv.vo.llnwd.net
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#adcontent.videoegg.com
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#adknowledge.com
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#as1.suitesmart.com
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#bandtools.nabbr.com
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#bc.newsweek.com
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#bin.clearspring.com
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#blutube.com
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#blutube.policeone.com
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#cdn.gigya.com
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#cdn.liveleak.com
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#cdn.lookery.com
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#cdnl3.liveleak.com
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#core.videoegg.com
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#d.yimg.com
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#ff0000.com
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#flash.gydget.com
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#flash.quantserve.com
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#flash.revver.com
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#grouper.com
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#iamlegend.warnerbros.com
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#illumenix.com
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#images.video.msn.com
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#include.classistatic.com
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#interclick.com
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#l.yimg.com
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#lads.myspace.com
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#layouts1.lovemyflash.com
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#llnw.jibjab.com
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#m.uk.2mdn.net
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#m1.2mdn.net
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#media.scanscout.com
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#media.tattomedia.com
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#media1.break.com
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#mpsnare.iesnare.com
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#myoutdoortv.com
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#natalie.feedroom.com
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#oddcast.com
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#pagead2.googlesyndication.com
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#panthercustomer.com
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#peanutlabs.com
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#player.hulu.com
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#quantserve.com
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#rutube.ru
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#s.mcstatic.com
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#s.ytimg.com
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#s9.addthis.com
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#slide.com
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#ssl-images-amazon.com
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#static.scanscout.com
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#static.userplane.com
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#static.youporn.com
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#stuff.pyzam.com
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#suitesmart.com
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#us.js2.yimg.com
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#vhss-a.oddcast.com
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#video.flashtalking.com
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#video.google.com
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#video.nbcuni.com
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#void.snocap.com
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#widgets.clearspring.com
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#widgets.nbcuni.com
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#[www.cbs.com](www.cbs.com)
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#[www.cmt.com](www.cmt.com)
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#[www.comedycentral.com](www.comedycentral.com)
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#[www.dumpalink.com](www.dumpalink.com)
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#[www.filecabi.net](www.filecabi.net)
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#[www.hulu.com](www.hulu.com)
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#[www.ifilm.com](www.ifilm.com)
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#[www.liveleak.com](www.liveleak.com)
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#[www.livevideo.com](www.livevideo.com)
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#[www.lovemyflash.com](www.lovemyflash.com)
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#[www.maxim.com](www.maxim.com)
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#[www.redtube.com](www.redtube.com)
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#[www.reuters.com](www.reuters.com)
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#[www.reverbnation.com](www.reverbnation.com)
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#[www.spike.com](www.spike.com)
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#[www.theboondocksaints.com](www.theboondocksaints.com)
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#[www.thedailyshow.com](www.thedailyshow.com)
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#[www.time.com](www.time.com)
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#[www.timmcgraw.com](www.timmcgraw.com)
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#[www.trucktrend.com](www.trucktrend.com)
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#[www.xatech.com](www.xatech.com)
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#[www.youtube.com](www.youtube.com)
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#youtube.com
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/settings.sol
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#adaptv.vo.llnwd.net/settings.sol
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#adcontent.videoegg.com/settings.sol
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#adknowledge.com/settings.sol
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#as1.suitesmart.com/settings.sol
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#bandtools.nabbr.com/settings.sol
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#bc.newsweek.com/settings.sol
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#bin.clearspring.com/settings.sol
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#blutube.com/settings.sol
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#blutube.policeone.com/settings.sol
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#cdn.gigya.com/settings.sol
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#cdn.liveleak.com/settings.sol
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#cdn.lookery.com/settings.sol
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#cdnl3.liveleak.com/settings.sol
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#core.videoegg.com/settings.sol
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#d.yimg.com/settings.sol
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#ff0000.com/settings.sol
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#flash.gydget.com/settings.sol
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#flash.quantserve.com/settings.sol
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#flash.revver.com/settings.sol
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#grouper.com/settings.sol
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#iamlegend.warnerbros.com/settings.sol
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#illumenix.com/settings.sol
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#images.video.msn.com/settings.sol
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#include.classistatic.com/settings.sol
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#interclick.com/settings.sol
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#l.yimg.com/settings.sol
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#lads.myspace.com/settings.sol
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#layouts1.lovemyflash.com/settings.sol
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#llnw.jibjab.com/settings.sol
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#m.uk.2mdn.net/settings.sol
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#m1.2mdn.net/settings.sol
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#media.scanscout.com/settings.sol
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#media.tattomedia.com/settings.sol
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#media1.break.com/settings.sol
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#mpsnare.iesnare.com/settings.sol
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#myoutdoortv.com/settings.sol
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#natalie.feedroom.com/settings.sol
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#oddcast.com/settings.sol
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#pagead2.googlesyndication.com/settings.sol
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#panthercustomer.com/settings.sol
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#peanutlabs.com/settings.sol
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#player.hulu.com/settings.sol
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#quantserve.com/settings.sol
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#rutube.ru/settings.sol
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#s.mcstatic.com/settings.sol
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#s.ytimg.com/settings.sol
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#s9.addthis.com/settings.sol
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#slide.com/settings.sol
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#ssl-images-amazon.com/settings.sol
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#static.scanscout.com/settings.sol
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#static.userplane.com/settings.sol
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#static.youporn.com/settings.sol
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#stuff.pyzam.com/settings.sol
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#suitesmart.com/settings.sol
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#us.js2.yimg.com/settings.sol
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#vhss-a.oddcast.com/settings.sol
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#video.flashtalking.com/settings.sol
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#video.google.com/settings.sol
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#video.nbcuni.com/settings.sol
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#void.snocap.com/settings.sol
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#widgets.clearspring.com/settings.sol
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#widgets.nbcuni.com/settings.sol
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#[www.cbs.com/settings.sol](www.cbs.com/settings.sol)
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#[www.cmt.com/settings.sol](www.cmt.com/settings.sol)
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#[www.comedycentral.com/settings.sol](www.comedycentral.com/settings.sol)
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#[www.dumpalink.com/settings.sol](www.dumpalink.com/settings.sol)
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#[www.filecabi.net/settings.sol](www.filecabi.net/settings.sol)
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#[www.hulu.com/settings.sol](www.hulu.com/settings.sol)
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#[www.ifilm.com/settings.sol](www.ifilm.com/settings.sol)
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#[www.liveleak.com/settings.sol](www.liveleak.com/settings.sol)
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#[www.livevideo.com/settings.sol](www.livevideo.com/settings.sol)
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#[www.lovemyflash.com/settings.sol](www.lovemyflash.com/settings.sol)
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#[www.maxim.com/settings.sol](www.maxim.com/settings.sol)
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#[www.redtube.com/settings.sol](www.redtube.com/settings.sol)
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#[www.reuters.com/settings.sol](www.reuters.com/settings.sol)
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#[www.reverbnation.com/settings.sol](www.reverbnation.com/settings.sol)
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#[www.spike.com/settings.sol](www.spike.com/settings.sol)
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#[www.theboondocksaints.com/settings.sol](www.theboondocksaints.com/settings.sol)
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#[www.thedailyshow.com/settings.sol](www.thedailyshow.com/settings.sol)
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#[www.time.com/settings.sol](www.time.com/settings.sol)
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#[www.timmcgraw.com/settings.sol](www.timmcgraw.com/settings.sol)
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#[www.trucktrend.com/settings.sol](www.trucktrend.com/settings.sol)
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#[www.xatech.com/settings.sol](www.xatech.com/settings.sol)
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#[www.youtube.com/settings.sol](www.youtube.com/settings.sol)
/host/Documents and Settings/Administrator/Application Data/Macromedia/Flash Player/macromedia.com/support/flashplayer/sys/#youtube.com/settings.sol
/host/WINDOWS/system32/Macromed/Flash/flashplayer.xpt
/usr/lib/flashplugin-nonfree/libflashplayer.so
administrator@administrator-desktop:~$ locate libflash
/usr/lib/flashplugin-nonfree/libflashplayer.so
/usr/lib/openoffice/program/libflash680li.so
administrator@administrator-desktop:~$ dpkg -s flashplugin-nonfree
Package: flashplugin-nonfree
Status: install ok installed
Priority: optional
Section: contrib/web
Installed-Size: 164
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Architecture: i386
Version: 9.0.124.0ubuntu2
Replaces: flashplugin (<< 6)
Depends: debconf | debconf-2.0, fontconfig, libatk1.0-0, libc6, libcairo2, libexpat1, libfontconfig1, libfreetype6, libglib2.0-0, libgtk2.0-0, libice6, libpango1.0-0, libpng12-0, libsm6, libx11-6, libxau6, libxcursor1, libxdmcp6, libxext6, libxfixes3, libxi6, libxinerama1, libxrandr2, libxrender1, libxt6, wget, zlib1g
Suggests: firefox, firefox-3.0, konqueror-nsplugins, libflashsupport, msttcorefonts, ttf-bitstream-vera | ttf-dejavu, ttf-xfree86-nonfree, x-ttcidfont-conf, xfs (>= 1:1.0.1-5), xulrunner-1.9
Conflicts: flashplayer-mozilla, flashplugin (<< 6), xfs (<< 1:1.0.1-5)
Description: Adobe Flash Player plugin installer
 This package will download the Flash Player from Adobe.  It is a
 Netscape/Mozilla type plugin.  Any browser based on Netscape or Mozilla can
 use the Flash plugin.  This package currently supports the following browsers:
 Mozilla, Mozilla-Firefox, Firefox, Iceweasel, and Iceape.  Also Galeon and
 Epiphany can use the Flash plugin.  Konqueror can also use the Flash plugin if
 konqueror-nsplugins is installed.
 .
 WARNING: Installing this Ubuntu package causes the Adobe flash plugin to be
 downloaded from [www.adobe.com](www.adobe.com).  The distribution license of the Adobe flash
 plugin is available at [www.adobe.com](www.adobe.com).  Installing this Ubuntu package implies
 that you have accepted the terms of that license.
 .
  Homepage: [http://wiki.ubuntu.com/FlashPlayer9](http://wiki.ubuntu.com/FlashPlayer9)
Npp-Applications: ec8030f7-c20a-464f-9b0e-13a3a9e97384, 92650c4d-4b8e-4d2a-b7eb-24ecf4f6b63a, aa5ca914-c309-495d-91cf-3141bbb04115
Npp-Mimetype: application/x-shockwave-flash
Npp-Name: Adobe Flash Player (installer)
Original-Maintainer: Bart Martens <bartm@knars.be>
administrator@administrator-desktop:~$ dpkg -s mozilla-plugin-gnash
Package: mozilla-plugin-gnash
Status: install ok installed
Priority: optional
Section: utils
Installed-Size: 308
Maintainer: Alexander Sack <asac@ubuntu.com>
Architecture: i386
Source: gnash
Version: 0.8.2-0ubuntu3
Depends: gnash (= 0.8.2-0ubuntu3), libc6 (>= 2.7-1), libgcc1 (>= 1:4.1.1-21), libstdc++6 (>= 4.2.1-4), libx11-6, libxi6
Description: free SWF movie player - Plugin for Mozilla and derivatives
 Gnash is a free Flash movie player, which works either standalone, or as
 plugin for Firefox/Mozilla or Konqueror.
 .
 This package includes the plugin for Firefox/Mozilla Web Browser.
 .
 Homepage: [http://www.gnu.org/software/gnash/](http://www.gnu.org/software/gnash/)
Npp-Applications: ec8030f7-c20a-464f-9b0e-13a3a9e97384,92650c4d-4b8e-4d2a-b7eb-24ecf4f6b63a,aa5ca914-c309-495d-91cf-3141bbb04115
Npp-Mimetype: application/x-shockwave-flash
Npp-Name: Gnash SWF Player
Original-Maintainer: Miriam Ruiz <little_miry@yahoo.es>
administrator@administrator-desktop:~$ dpkg -s swfdec-mozilla

---

### Post by gandaran on 2008-11-10
theres a package you have to remove, open synaptic find the swfdec-mozilla (swfdec flash) package and mark for complete removal, click the apply button

remove the mozilla-plugin-gnash too

---

### Post by aysiu on 2008-11-10
I didn't see the output for the last command, but you should definitely remove the Gnash plugin: ```
sudo apt-get remove mozilla-plugin-gnash && sudo apt-get install --reinstall flashplugin-nonfree
``` and then restart Firefox.

---

### Post by coop0311emt on 2008-11-10
thanks removing gnash took care of it

---

