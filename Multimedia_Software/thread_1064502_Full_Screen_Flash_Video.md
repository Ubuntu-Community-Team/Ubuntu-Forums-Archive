---
title: "Full Screen Flash Video"
date: 2009-02-08
forum: Multimedia Software
---

### Post by jlabomb on 2009-02-08
I was wondering if there was a fix for this issue. I have not found any info on it at all. Some websites I watch video on I can view in full screen like youtube. But the majority of the sites I watch video on will not work in full screen. If I hit the full screen button the video gets smaller and is surrounded by a white border. This website is an example [http://watchxonline.com/media/95-futurama-307-the-day-the-earth-stood-stupid.php]("http://watchxonline.com/media/95-futurama-307-the-day-the-earth-stood-stupid.php") The video works in full screen on windows just not on Ubuntu. Looking forward to any help. Thanks.

---

### Post by empthollow on 2009-02-08
i am able to play that video fullscreen with firefox 3.0.5 and flashplayer10 from the adobe website on both arch linux and ubuntu intrepid.  Are you using different versions of these programs?

---

### Post by jlabomb on 2009-02-09
I have firefox 3.0.5 and my Flash shows Shockwave Flash 10.0 r15. This has been a problem since I had 7.10 I kept hoping upgrades would fix it.

---

### Post by redroad55 on 2009-02-09
I'm not so sure what you have is a flash problem .. Be more specific: what graphics interface do you have and list plugins listed under add ons > plugins in your browser .. post back ..best to you

---

### Post by empthollow on 2009-02-09
my working setup has the same version 10.0 r15, so i would have go with redroad55 and say look elsewhere.

---

### Post by redroad55 on 2009-02-09
this may be a long shot but look at this..
  [http://ubuntuforums.org/showthread.php?t=1034369&highlight=full+screen]("http://ubuntuforums.org/showthread.php?t=1034369&highlight=full+screen")
Post back

---

### Post by jlabomb on 2009-02-09
My video card is Gigabyte Nvidia 6600 LE I am using the Nvidia driver Version 177 and I use it in a dual monitor display at 1024 x 768 each. The plugins for Firefox are Default Plugin, Demo print, Divx Web Player, GCJ Web Browser, IcedTea, Quicktime, Shockwave Flash, Totem Web, VLC Multimedia, and Windows Media Player. My extensions in case you need those are Adblock plus, Bugmenot, Digg, Download Statusbar, Download Helper, DownThemAll, Foxmarks, PDF Download, Stumble, Ubuntu Firefox Mod, and WOT. I tried to disable the sound you suggested from that other post but it didn't help. I thought about reinstalling Flash but I don't guess I will since you don't think thats the problem. I just don't understand why some sites work with fullscreen and others don't. Thanks again for the help.

---

### Post by redroad55 on 2009-02-09
after looking at your post I think the issue is totem ... there is no java or realplayer each of which have a part to play..

first go here if you have not already and follow the steps and then post back..

[https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories]("https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories")

---

### Post by jlabomb on 2009-02-10
I went through adding the repository and installed real player and some other codecs I think I already have then updated. It is still not playing fullscreen. I did not see how to install Java but I have 

> java version "1.6.0_0"
IcedTea6 1.3.1 (6b12-0ubuntu6.1) Runtime Environment (build 1.6.0_0-b12)
OpenJDK 64-Bit Server VM (build 1.6.0_0-b12, mixed mode)


Also here is more info about my plugins.

> Installed plugins
Find more information about browser plugins at mozilla.org.
Help for installing plugins is available from plugindoc.mozdev.org.
Shockwave Flash

    File name: /var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so
    Shockwave Flash 10.0 r15

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
IcedTea Web Browser Plugin

    File name: /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/IcedTeaPlugin.so
    The IcedTea Web Browser Plugin executes Java applets.

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
Default Plugin

    File name: /usr/lib/xulrunner-addons/plugins/libnullplugin.so
    The default plugin handles plugin data for mimetypes and extensions that are not specified and facilitates downloading of new plugins.

MIME Type 	Description 	Suffixes 	Enabled
* 	All types 	.* 	No
Demo Print Plugin for unix/linux

    File name: /usr/lib/xulrunner-addons/plugins/libunixprintplugin.so
    The demo print plugin for unix.

MIME Type 	Description 	Suffixes 	Enabled
application/x-print-unix-nsplugin 	Demo Print Plugin for Unix/Linux 	.pnt 	Yes
Totem Web Browser Plugin 2.24.3

    File name: /usr/lib/totem/gstreamer/libtotem-basic-plugin.so
    The Totem 2.24.3 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
application/x-ogg 	Ogg multimedia file 	ogg 	Yes
application/ogg 	Ogg multimedia file 	ogg 	Yes
audio/ogg 	Ogg Audio 	oga 	Yes
audio/x-ogg 	Ogg Audio 	ogg 	Yes
video/ogg 	Ogg Video 	ogv 	Yes
video/x-ogg 	Ogg Video 	ogg 	Yes
application/annodex 	application/annodex type 	anx 	Yes
audio/annodex 	audio/annodex type 	axa 	Yes
video/annodex 	video/annodex type 	axv 	Yes
video/mpeg 	MPEG video 	mpg, mpeg, mpe 	Yes
audio/wav 	WAV audio 	wav 	Yes
audio/x-wav 	WAV audio 	wav 	Yes
audio/mpeg 	MP3 audio 	mp3 	Yes
application/x-nsv-vp3-mp3 	NullSoft video 	nsv 	Yes
video/flv 	Flash video 	flv 	Yes
application/x-totem-plugin 	Totem Multimedia plugin 		Yes
Windows Media Player Plug-in 10 (compatible; Totem)

    File name: /usr/lib/totem/gstreamer/libtotem-gmp-plugin.so
    The Totem 2.24.3 plugin handles video and audio streams.

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
DivX® Web Player

    File name: /usr/lib/totem/gstreamer/libtotem-mully-plugin.so
    DivX Web Player version 1.4.0.233

MIME Type 	Description 	Suffixes 	Enabled
video/divx 	AVI video 	divx 	Yes
QuickTime Plug-in 7.2.0

    File name: /usr/lib/totem/gstreamer/libtotem-narrowspace-plugin.so
    The Totem 2.24.3 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
video/quicktime 	QuickTime video 	mov 	Yes
video/mp4 	MPEG-4 video 	mp4 	Yes
image/x-macpaint 	MacPaint Bitmap image 	pntg 	Yes
image/x-quicktime 	Macintosh Quickdraw/PICT drawing 	pict, pict1, pict2 	Yes
video/x-m4v 	MPEG-4 video 	m4v 	Yes
VLC Multimedia Plug-in

    File name: /usr/lib/mozilla/plugins/libvlcplugin.so
    Version 0.9.4 Grishenko, copyright 1996-2007 The VideoLAN Team
    [http://www.videolan.org/](http://www.videolan.org/)

MIME Type 	Description 	Suffixes 	Enabled
audio/mpeg 	MPEG audio 	mp2,mp3,mpga,mpega 	Yes
audio/x-mpeg 	MPEG audio 	mp2,mp3,mpga,mpega 	Yes
video/mpeg 	MPEG video 	mpg,mpeg,mpe 	Yes
video/x-mpeg 	MPEG video 	mpg,mpeg,mpe 	Yes
video/mpeg-system 	MPEG video 	mpg,mpeg,mpe,vob 	Yes
video/x-mpeg-system 	MPEG video 	mpg,mpeg,mpe,vob 	Yes
video/mp4 	MPEG-4 video 	mp4,mpg4 	Yes
audio/mp4 	MPEG-4 audio 	mp4,mpg4 	Yes
application/mpeg4-iod 	MPEG-4 video 	mp4,mpg4 	Yes
application/mpeg4-muxcodetable 	MPEG-4 video 	mp4,mpg4 	Yes
video/x-msvideo 	AVI video 	avi 	Yes
video/quicktime 	QuickTime video 	mov,qt 	Yes
application/x-ogg 	Ogg stream 	ogg 	Yes
application/ogg 	Ogg stream 	ogg 	Yes
application/x-vlc-plugin 	VLC plug-in 	vlc 	Yes
video/x-ms-asf-plugin 	Windows Media Video 	asf,asx 	Yes
video/x-ms-asf 	Windows Media Video 	asf,asx 	Yes
application/x-mplayer2 	Windows Media 		Yes
video/x-ms-wmv 	Windows Media 	wmv 	Yes
video/x-ms-wvx 	Windows Media Video 	wvx 	Yes
application/x-google-vlc-plugin 	Google VLC plug-in 		Yes
audio/wav 	WAV audio 	wav 	Yes
audio/x-wav 	WAV audio 	wav 	Yes
audio/3gpp 	3GPP audio 	3gp,3gpp 	Yes
video/3gpp 	3GPP video 	3gp,3gpp 	Yes
audio/3gpp2 	3GPP2 audio 	3g2,3gpp2 	Yes
video/3gpp2 	3GPP2 video 	3g2,3gpp2 	Yes
video/divx 	DivX video 	divx 	Yes
video/flv 	FLV video 	flv 	Yes
video/x-flv 	FLV video 	flv 	Yes
video/x-matroska 	Matroska video 	mkv 	Yes
audio/x-matroska 	Matroska audio 	mka 	Yes
GCJ Web Browser Plugin 0.96.1

    File name: /usr/lib/classpath/libgcjwebplugin.so
    The GCJ Web Browser Plugin executes Java applets.

MIME Type 	Description 	Suffixes 	Enabled
application/x-java-vm 	GCJ 	class,jar 	Yes
application/x-java-applet 	GCJ 	class,jar 	Yes
application/x-java-applet;version=1.1 	GCJ 	class,jar 	Yes
application/x-java-applet;version=1.1.1 	GCJ 	class,jar 	Yes
application/x-java-applet;version=1.1.2 	GCJ 	class,jar 	Yes
application/x-java-applet;version=1.1.3 	GCJ 	class,jar 	Yes
application/x-java-applet;version=1.2 	GCJ 	class,jar 	Yes
application/x-java-applet;version=1.2.1 	GCJ 	class,jar 	Yes
application/x-java-applet;version=1.2.2 	GCJ 	class,jar 	Yes
application/x-java-applet;version=1.3 	GCJ 	class,jar 	Yes
application/x-java-applet;version=1.3.1 	GCJ 	class,jar 	Yes
application/x-java-applet;version=1.4 	GCJ 	class,jar 	Yes
application/x-java-applet;version=1.4.1 	GCJ 	class,jar 	Yes
application/x-java-applet;version=1.4.2 	GCJ 	class,jar 	Yes
application/x-java-applet;jpi-version=1.4.2_01 	GCJ 	class,jar 	Yes
application/x-java-bean 	GCJ 	class,jar 	Yes
application/x-java-bean;version=1.1 	GCJ 	class,jar 	Yes
application/x-java-bean;version=1.1.1 	GCJ 	class,jar 	Yes
application/x-java-bean;version=1.1.2 	GCJ 	class,jar 	Yes
application/x-java-bean;version=1.1.3 	GCJ 	class,jar 	Yes
application/x-java-bean;version=1.2 	GCJ 	class,jar 	Yes
application/x-java-bean;version=1.2.1 	GCJ 	class,jar 	Yes
application/x-java-bean;version=1.2.2 	GCJ 	class,jar 	Yes
application/x-java-bean;version=1.3 	GCJ 	class,jar 	Yes
application/x-java-bean;version=1.3.1 	GCJ 	class,jar 	Yes
application/x-java-bean;version=1.4 	GCJ 	class,jar 	Yes
application/x-java-bean;version=1.4.1 	GCJ 	class,jar 	Yes
application/x-java-bean;version=1.4.2 	GCJ 	class,jar 	Yes
application/x-java-bean;jpi-version=1.4.2_01 	GCJ 	class,jar 	Yes


I think this is the right track, I appreciate the help.

---

### Post by redroad55 on 2009-02-10
Just a quick question are you running a 64 bit OS ? Post back

---

### Post by jlabomb on 2009-02-10
Yes I am running 64 bit Ubuntu 8.10

---

### Post by redroad55 on 2009-02-10
It looks like in your post above Iced tea has taken care of java ..Try logging in under another account and test full screen and post back with results

---

### Post by redroad55 on 2009-02-10
In further investigating your problem Flash may be an issue in this way .. If you have a 64 bit browser installed and 32 bit flash .. and since 64 bit linux flash wasn't released until recently that might be the case .. So this link is the new release of 64 bit flash ..
 [http://labs.adobe.com/downloads/flashplayer10.html]("http://labs.adobe.com/downloads/flashplayer10.html")
one of the requirements to install is to uninstall all other flash that is done like this:
```
sudo apt-get purge adobe-flashplugin flashplugin-nonfree gnash gnash-common libflashsupport mozilla-plugin-gnash nspluginwrapper swfdec-mozilla && sudo apt-get install flashplugin-nonfree
```

The only issue I have is determining browser 64 bit or 32 bit or

whether a conflict is presented ?
That's what I have for now ..Post back any thoughts results and or questions ..Best to you

---

### Post by jlabomb on 2009-02-10
That would make sense. I haven't installed flash since I first got Ubuntu so it probably is the 32 bit one. I will try that when I get home from work and let you know how it went. Thanks again.

---

### Post by jlabomb on 2009-02-10
I tried to run the code you provided and I got this error  E: Couldn't find package adobe-flashplugin  I went into synaptic and tried to remove the packages their. Then I installed flash again and I guess I made things worse cause youtube doesn't play video fullscreen. Also I am using a 64 bit browser. Thanks

Shockwave Flash

    File name: /var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so
    Shockwave Flash 10.0 r15

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes

---

### Post by redroad55 on 2009-02-10
So you run this : 
 > sudo apt-get purge adobe-flashplugin flashplugin-nonfree gnash gnash-common libflashsupport mozilla-plugin-gnash nspluginwrapper swfdec-mozilla
 then go here to the bottom of page for your 64 bit flash..
[http://labs.adobe.com/downloads/flashplayer10.html]("http://labs.adobe.com/downloads/flashplayer10.html")

Post back with any results and or questions.. Best to you

---

### Post by redroad55 on 2009-02-10
Once downloaded, simply open the Tar archive, look for a file named "libflashplayer.so", copy that file to your desktop, then execute the following command in the terminal:

> sudo mkdir /usr/lib/flashplugin-nonfree && sudo cp -f ~/Desktop/libflashplayer.so /usr/lib/flashplugin-nonfree/ && sudo ln -sf /usr/lib/flashplugin-nonfree/libflashplayer.so /usr/lib/firefox/plugins/libflashplayer.so

You may now restart your web browser and use the plugin.

Post back with any results and or questions .. Best to you

---

### Post by jlabomb on 2009-02-10
Well I got it installed. Still not sure the install worked. I still got that error when I ran that but I check the packages in synaptic and I removed the ones that were there. The player still does not play in full screen. It works in full screen on hulu but not youtube or watchx.

Shockwave Flash

    File name: /home/james/.mozilla/plugins/libflashplayer.so
    Shockwave Flash 10.0 d21

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes

---

### Post by redroad55 on 2009-02-10
ok so You got the 64 bit flash installed ..That's great .. We can put that behind us .. Let's look at the player next.. Try logging in another account and try your video test utube etc.full screen and post back .. That wil tell

---

### Post by jlabomb on 2009-02-10
Well it does not work on the other name either. I had to install Flash on this name separate not sure if that is normal but it reads the same info the other does now.

Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 10.0 d21

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes

I wont be able to try anything on this computer till I get home from school tomorrow night but I can answer questions throughout the day. Sorry it is such a hassle but appreciate the help. Thanks.

---

### Post by redroad55 on 2009-02-10
now lets go with this it will only install them if they are not there :
> sudo apt-get install alsa-oss faac faad gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse ia32-libs icedtea6-plugin libavcodec-unstripped-51 libmp3lame0 non-free-codecs 
then:
> sudo apt-get remove kaffeine-mozilla mozilla-helix-player mozilla-mplayer mozilla-plugin-vlc totem-mozilla xine-plugin
and finally:
> sudo apt-get install gnome-mplayer gecko-mediaplayer
you should now be able to stream anything you want
Best to you ..Post back any results and or questions





Post back

---

### Post by jlabomb on 2009-02-11
All the installs went fine, there were a few that I was missing. The videos still do not play full screen on some websites. They do work on others. There must be something strange in my system. There isn't a setting for full screen video in the nvidia settings is there. Thanks again.

---

### Post by redroad55 on 2009-02-11
When you say full screen please specify streamed video content or dvd playback .. I'll look thru your previous posts and see what else can be done .. be back tomorrow ..Post back ..Best to you

---

### Post by jlabomb on 2009-02-11
Full screen video from flash player. It plays DVD's fine and some flash video fine in full screen. I am just making guesses not really anything I can put my finger on.

---

### Post by Ibbelz on 2009-02-12
Hi, I have the same problem with my ubuntu setup. I am running Ubuntu 8.10 and flash (flv) videos won't play in full screen, in full screen mode the video is small and surrounded by a white border (similar to jlabomb's case).. Strange thing is that for some other flash videos full screen works great....

I see two similarities between my setup and jlabomb's. I also have the proprietary drivers from nividia, only I have version 173 installed. And the other similarity is that my system is also dual screen. 

This is my about plugins in Firefox:

```

Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 10.0 r15

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
Totem Web Browser Plugin 2.24.3

    File name: libtotem-basic-plugin.so
    The Totem 2.24.3 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
application/x-ogg 	Ogg multimedia file 	ogg 	Yes
application/ogg 	Ogg multimedia file 	ogg 	Yes
audio/ogg 	Ogg Audio 	oga 	Yes
audio/x-ogg 	Ogg Audio 	ogg 	Yes
video/ogg 	Ogg Video 	ogv 	Yes
video/x-ogg 	Ogg Video 	ogg 	Yes
application/annodex 	application/annodex type 	anx 	Yes
audio/annodex 	audio/annodex type 	axa 	Yes
video/annodex 	video/annodex type 	axv 	Yes
video/mpeg 	MPEG video 	mpg, mpeg, mpe 	Yes
audio/wav 	WAV audio 	wav 	Yes
audio/x-wav 	WAV audio 	wav 	Yes
audio/mpeg 	MP3 audio 	mp3 	Yes
application/x-nsv-vp3-mp3 	NullSoft video 	nsv 	Yes
video/flv 	Flash video 	flv 	Yes
application/x-totem-plugin 	Totem Multimedia plugin 		Yes
Windows Media Player Plug-in 10 (compatible; Totem)

    File name: libtotem-gmp-plugin.so
    The Totem 2.24.3 plugin handles video and audio streams.

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
DivX® Web Player

    File name: libtotem-mully-plugin.so
    DivX Web Player version 1.4.0.233

MIME Type 	Description 	Suffixes 	Enabled
video/divx 	AVI video 	divx 	Yes
QuickTime Plug-in 7.2.0

    File name: libtotem-narrowspace-plugin.so
    The Totem 2.24.3 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
video/quicktime 	QuickTime video 	mov 	Yes
video/mp4 	MPEG-4 video 	mp4 	Yes
image/x-macpaint 	MacPaint Bitmap image 	pntg 	Yes
image/x-quicktime 	Macintosh Quickdraw/PICT drawing 	pict, pict1, pict2 	Yes
video/x-m4v 	MPEG-4 video 	m4v 	Yes
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

```

I really hope there is a fix!

---

### Post by Ibbelz on 2009-02-15
Any thoughts on this?

---

### Post by jlabomb on 2009-02-15
I am wondering if it has something to do with the dual monitor. I have no explanation to support this because some websites do play full screen while others don't. I just remembered that I don't have a Nvidia 6600 LE in this system its a 7300 GT. I swap with the one in my Dad's computer when he thinks its not working. I never have a problem with either one myself.

---

### Post by jlabomb on 2009-04-27
The new nvidia driver did nothing to help with this nor upgrading to Jaunty. I am going to assume it is a glitch due to the dual monitors.

---

