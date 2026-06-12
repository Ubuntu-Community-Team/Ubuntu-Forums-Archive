---
title: "Ubuntu Jaunty (or any other) + Firefox 3.5.4pre (or any other) + Flash player = SLOW"
date: 2009-10-14
forum: Multimedia Software
---

### Post by DexterLB on 2009-10-14
I've got flashplugin-nonfree-10.0.32.18ubuntu0.9.04.1, but it was the same with all previous verions, Ubuntu Jaunty, but the problem was also in gutsy, hardy and intrepid, and firefox-3.5.4pre, but the problem was also in 3.0

I now want to watch BBC Iplayer, but I'm limited to the small screen, low quality, which takes 90% cpu (My processor is Intel Pentium 4 on 2.0GHz). If I switch to high quality or full screen the CPU is 100% and the framerate is choppy. Gnash and SWFdec don't work for Iplayer at all.

So, Is there a solution to the problem? Any help will be deeply apreciated... Doctor Who epizodes start soon and I want to be able to watch them on Iplayer without switching to windoze (which I installed exactly for that purpose by the way)

---

### Post by DexterLB on 2009-10-15
BuMp

---

### Post by TenPlus1 on 2009-10-15
Do you have your graphics card driver installed ok (nvidia/ati) as running gfx intensive processes without it will eat cpu time...

---

### Post by DexterLB on 2009-10-15
> **TenPlus1 said:**
> Do you have your graphics card driver installed ok (nvidia/ati) as running gfx intensive processes without it will eat cpu time...

Yes, it's nvidia-glx-96.40.10-0ubuntu1 32bit

My videocard is NVidia MX-440

I am also running compiz. But turning off compiz doesn't speed flash player up.

---

### Post by masux594 on 2009-10-15
The flash performance depends of what plugin u use flash videos.. What plugin have u installed?

Sysc, A

---

### Post by masux594 on 2009-10-15
go in the firefox page about:Plugins .. and tell us what plugin are u currently using..

Sysc, A

---

### Post by DexterLB on 2009-10-15
about:plugins
```
Installed plugins
Find more information about browser plugins at mozilla.org.
Help for installing plugins is available from plugindoc.mozdev.org.
Default Plugin

    File name: /usr/lib/xulrunner-addons/plugins/libnullplugin.so
    The default plugin handles plugin data for mimetypes and extensions that are not specified and facilitates downloading of new plugins.

MIME Type 	Description 	Suffixes 	Enabled
* 	All types 	.* 	No
Java(TM) Plug-in 1.6.0_16-b01

    File name: /usr/lib/jvm/java-6-sun-1.6.0.16/jre/plugin/i386/ns7/libjavaplugin_oji.so
    Java(TM) Plug-in 1.6.0_16

MIME Type 	Description 	Suffixes 	Enabled
application/x-java-vm 	Java™ Plug-in 		Yes
application/x-java-applet 	Java™ Plug-in Applet 		Yes
application/x-java-applet;version=1.1 	Java™ Plug-in 		Yes
application/x-java-applet;version=1.1.1 	Java™ Plug-in 		Yes
application/x-java-applet;version=1.1.2 	Java™ Plug-in 		Yes
application/x-java-applet;version=1.1.3 	Java™ Plug-in 		Yes
application/x-java-applet;version=1.2 	Java™ Plug-in 		Yes
application/x-java-applet;version=1.2.1 	Java™ Plug-in 		Yes
application/x-java-applet;version=1.2.2 	Java™ Plug-in 		Yes
application/x-java-applet;version=1.3 	Java™ Plug-in 		Yes
application/x-java-applet;version=1.3.1 	Java™ Plug-in 		Yes
application/x-java-applet;version=1.4 	Java™ Plug-in 		Yes
application/x-java-applet;version=1.4.1 	Java™ Plug-in 		Yes
application/x-java-applet;version=1.4.2 	Java™ Plug-in 		Yes
application/x-java-applet;version=1.5 	Java™ Plug-in 		Yes
application/x-java-applet;version=1.6 	Java™ Plug-in 		Yes
application/x-java-applet;jpi-version=1.6.0_16 	Java™ Plug-in 		Yes
application/x-java-bean 	Java™ Plug-in JavaBeans 		Yes
application/x-java-bean;version=1.1 	Java™ Plug-in 		Yes
application/x-java-bean;version=1.1.1 	Java™ Plug-in 		Yes
application/x-java-bean;version=1.1.2 	Java™ Plug-in 		Yes
application/x-java-bean;version=1.1.3 	Java™ Plug-in 		Yes
application/x-java-bean;version=1.2 	Java™ Plug-in 		Yes
application/x-java-bean;version=1.2.1 	Java™ Plug-in 		Yes
application/x-java-bean;version=1.2.2 	Java™ Plug-in 		Yes
application/x-java-bean;version=1.3 	Java™ Plug-in 		Yes
application/x-java-bean;version=1.3.1 	Java™ Plug-in 		Yes
application/x-java-bean;version=1.4 	Java™ Plug-in 		Yes
application/x-java-bean;version=1.4.1 	Java™ Plug-in 		Yes
application/x-java-bean;version=1.4.2 	Java™ Plug-in 		Yes
application/x-java-bean;version=1.5 	Java™ Plug-in 		Yes
application/x-java-bean;version=1.6 	Java™ Plug-in 		Yes
application/x-java-bean;jpi-version=1.6.0_16 	Java™ Plug-in 		Yes
Shockwave Flash

    File name: /usr/lib/adobe-flashplugin/libflashplayer.so
    Shockwave Flash 10.0 r32

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
Windows Media Player Plug-in 10 (compatible; Totem)

    File name: /usr/lib/totem/gstreamer/libtotem-gmp-plugin.so
    The Totem 2.26.1 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
application/x-mplayer2 	AVI video 	avi, wma, wmv 	Yes
video/x-ms-asf-plugin 	ASF video 	asf, wmv 	Yes
video/x-msvideo 	AVI video 	asf, wmv 	Yes
video/x-ms-asf 	ASF video 	asf 	Yes
video/x-ms-wmv 	Windows Media video 	wmv 	Yes
video/x-wmv 	Windows Media video 	wmv 	Yes
video/x-ms-wvx 	Windows Media video 	wmv 	Yes
video/x-ms-wm 	Windows Media video 	wmv 	Yes
video/x-ms-wmp 	Windows Media video 	wmv 	Yes
application/x-ms-wms 	Windows Media video 	wms 	Yes
application/x-ms-wmp 	Windows Media video 	wmp 	Yes
application/asx 	Microsoft ASX playlist 	asx 	Yes
audio/x-ms-wma 	Windows Media audio 	wma 	Yes

```

---

### Post by DexterLB on 2009-10-16
***_[size="7"][color="darkred"]bump[/color][/size]_***

---

### Post by masux594 on 2009-10-19
I'm sorry but this week-end i was too busy.. this evening i'll see in my pc..

Sysc, A

---

### Post by DexterLB on 2009-10-19
Ok. I'll be waiting... :)

---

### Post by masux594 on 2009-10-21
Oki, I'm here.. I'm sorry for the delay.. Well.. You have a very slow performance because u currently use the gstreamer plugin instead of the abobe one.. So.. u may uninstall all the plugins for flash and then install the right one..
Uninstall all the flsh plugin that u might have installed, and then install one that i currently use 
```
sudo apt-get remove swfdec-mozilla mozilla-plugin-gnash adobe-flashplugin flashplugin-nonfree && sudo apt-get install flashplugin-installer flashplugin-nonfree
```

Sysc, A

---

