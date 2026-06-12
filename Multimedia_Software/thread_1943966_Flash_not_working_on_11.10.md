---
title: "Flash not working on 11.10"
date: 2012-03-20
forum: Multimedia Software
---

### Post by adityanihar on 2012-03-20
I am able to play videos only on youtube.com.

Tried google-chrome, chromium and firefox but no luck. 
even tried flash-aid. funny part is I can play youtube videos but not other videos from metacafe.com, southparkstudios.com and some other streaming videos. 

Can any one help me out on this. I read and found lot of posts but no help.

Thanks
Aditya

---

### Post by lovinglinux on 2012-03-21
Please generate a Report using Flash-Aid Help menu and post here.

---

### Post by adityanihar on 2012-03-21
Thanks for the reply 
Here is the report generated 

```
Ubuntu Architecture

Linux ################ 3.0.0-16-generic #29-Ubuntu SMP Tue Feb 14 12:48:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"

Firefox Packages

firefox						install
firefox-globalmenu				install
firefox-gnome-support				install
firefox-locale-en				install

Firefox binaries

/usr/bin/firefox
/usr/bin/firefox: symbolic link to `../lib/firefox-11.0/firefox.sh'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)

Firefox divertion

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

Sources

caffeine-developers-ppa-oneiric.list
caffeine-developers-ppa-oneiric.list.save
google-chrome.list
google-talkplugin.list
google-talkplugin.list.save
medibuntu.list
medibuntu.list.save
oneiric-partner.list
oneiric-partner.list.save
team-xbmc-ppa-oneiric.list
team-xbmc-ppa-oneiric.list.save
webupd8team-gnome3-oneiric.list
webupd8team-gnome3-oneiric.list.save
webupd8team-jupiter-oneiric.list
webupd8team-jupiter-oneiric.list.save
xbmc.list
xbmc.list.save

Flash packages

adobe-flash-properties-gtk			install
adobe-flashplugin				install
Plugin locations


/usr/lib/firefox/plugins/flashplugin-alternative.so
/usr/lib/iceape/plugins/flashplugin-alternative.so
/usr/lib/iceweasel/plugins/flashplugin-alternative.so
/usr/lib/midbrowser/plugins/flashplugin-alternative.so
/usr/lib/mozilla/plugins/flashplugin-alternative.so
/usr/lib/xulrunner/plugins/flashplugin-alternative.so
/usr/lib/xulrunner-addons/plugins/flashplugin-alternative.so

Flash symlinks


/usr/lib/mozilla/plugins/libflashplayer.so: ERROR: cannot open `/usr/lib/mozilla/plugins/libflashplayer.so' (No such file or directory)
/usr/lib/mozilla/plugins/flashplugin-alternative.so: symbolic link to `/etc/alternatives/mozilla-flashplugin'
/etc/alternatives/mozilla-flashplugin: symbolic link to `/usr/lib/adobe-flashplugin/libflashplayer.so'
/usr/lib/flashplugin-installer/libflashplayer.so: ERROR: cannot open `/usr/lib/flashplugin-installer/libflashplayer.so' (No such file or directory)
/usr/lib/flashplugin-nonfree/libflashplayer.so: ERROR: cannot open `/usr/lib/flashplugin-nonfree/libflashplayer.so' (No such file or directory)
/usr/lib/adobe-flashplugin/libflashplayer.so: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, stripped
/usr/lib/lightspark/lightspark.so: ERROR: cannot open `/usr/lib/lightspark/lightspark.so' (No such file or directory)
/usr/lib/swfdec-mozilla/libswfdecmozilla.so: ERROR: cannot open `/usr/lib/swfdec-mozilla/libswfdecmozilla.so' (No such file or directory)
/usr/lib/gnash/libgnashplugin.so: ERROR: cannot open `/usr/lib/gnash/libgnashplugin.so' (No such file or directory)
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-installer/npwrapper.libflashplayer.so' (No such file or directory)
/var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so' (No such file or directory)

pluginreg.dat

Generated File. Do not edit.

[HEADER]
Version:0.15:$
Arch:x86_64-gcc3:$

[PLUGINS]
libgnome-shell-browser-plugin.so:$
/usr/lib/mozilla/plugins/libgnome-shell-browser-plugin.so:$
:$
1327898169000:1:5:$
This plugin provides integration with Gnome Shell for live extension enabling and disabling. It can be used only by extensions.gnome.org:$
Gnome Shell Integration:$
1
0:application/x-gnome-shell-integration:Gnome Shell Integration Dummy Content-Type::$
libnpgoogletalk.so:$
/opt/google/talkplugin/libnpgoogletalk.so:$
:$
1323737910000:1:5:$
Version: 2.6.1.0:$
Google Talk Plugin:$
1
0:application/googletalk:Google Talk Plugin:googletalk:$
libnpgtpo3dautoplugin.so:$
/opt/google/talkplugin/libnpgtpo3dautoplugin.so:$
:$
1323737910000:1:5:$
Google Talk Plugin Video Accelerator version:0.1.44.14:$
Google Talk Plugin Video Accelerator:$
1
0:application/vnd.gtpo3d.auto:O3D MIME::$
IcedTeaPlugin.so:$
/usr/lib/jvm/java-6-openjdk/jre/lib/amd64/IcedTeaPlugin.so:$
:$
1320721707000:1:5:$
The <a href="http://icedtea.classpath.org/wiki/IcedTea-Web">IcedTea-Web Plugin</a> executes Java applets.:$
IcedTea-Web Plugin (using IcedTea-Web 1.1.3 (1.1.3-1ubuntu1.1)):$
34
0:application/x-java-vm:IcedTea:class,jar:$
1:application/x-java-applet:IcedTea:class,jar:$
2:application/x-java-applet;version=1.1:IcedTea:class,jar:$
3:application/x-java-applet;version=1.1.1:IcedTea:class,jar:$
4:application/x-java-applet;version=1.1.2:IcedTea:class,jar:$
5:application/x-java-applet;version=1.1.3:IcedTea:class,jar:$
6:application/x-java-applet;version=1.2:IcedTea:class,jar:$
7:application/x-java-applet;version=1.2.1:IcedTea:class,jar:$
8:application/x-java-applet;version=1.2.2:IcedTea:class,jar:$
9:application/x-java-applet;version=1.3:IcedTea:class,jar:$
10:application/x-java-applet;version=1.3.1:IcedTea:class,jar:$
11:application/x-java-applet;version=1.4:IcedTea:class,jar:$
12:application/x-java-applet;version=1.4.1:IcedTea:class,jar:$
13:application/x-java-applet;version=1.4.2:IcedTea:class,jar:$
14:application/x-java-applet;version=1.5:IcedTea:class,jar:$
15:application/x-java-applet;version=1.6:IcedTea:class,jar:$
16:application/x-java-applet;jpi-version=1.6.0_50:IcedTea:class,jar:$
17:application/x-java-bean:IcedTea:class,jar:$
18:application/x-java-bean;version=1.1:IcedTea:class,jar:$
19:application/x-java-bean;version=1.1.1:IcedTea:class,jar:$
20:application/x-java-bean;version=1.1.2:IcedTea:class,jar:$
21:application/x-java-bean;version=1.1.3:IcedTea:class,jar:$
22:application/x-java-bean;version=1.2:IcedTea:class,jar:$
23:application/x-java-bean;version=1.2.1:IcedTea:class,jar:$
24:application/x-java-bean;version=1.2.2:IcedTea:class,jar:$
25:application/x-java-bean;version=1.3:IcedTea:class,jar:$
26:application/x-java-bean;version=1.3.1:IcedTea:class,jar:$
27:application/x-java-bean;version=1.4:IcedTea:class,jar:$
28:application/x-java-bean;version=1.4.1:IcedTea:class,jar:$
29:application/x-java-bean;version=1.4.2:IcedTea:class,jar:$
30:application/x-java-bean;version=1.5:IcedTea:class,jar:$
31:application/x-java-bean;version=1.6:IcedTea:class,jar:$
32:application/x-java-bean;jpi-version=1.6.0_50:IcedTea:class,jar:$
33:application/x-java-vm-npruntime:::$

[INVALID]
```

---

### Post by lovinglinux on 2012-03-22
Flash seems to be installed properly, but it doesn't show in pluginreg.dat.

The type **[noparse]about:plugins[/noparse]** in the address bar. Check if you see a Flash plugin listed. It should be just one.

---

### Post by fonsi2099 on 2012-03-26
I have the same problem, thanks for the solution.

Ubuntu 11.10 64Bit
Ultrabook, Acer

---

### Post by haggus71 on 2012-03-29
I had no flash in chromium with all video plugins selected, and firefox freezes the computer in lubuntu 11.10.  When I downloaded the Chrome browser, however, flash was no problem.  

This has been a continuing problem.  Most people using software shouldn't have to browse 5 different threads and get 5 different answers...none of which work.

---

### Post by TBABill on 2012-03-29
Flash is built into Chrome. Sometimes just reinstalling the plugin will solve the issue and it takes only a few moments via terminal, software center or synaptic.

---

### Post by fonsi2099 on 2012-03-29
This has worked for me with firefox 11.00,
quote: 
sudo apt-get remove --purge adobe-flashplugin flashplugin* nspluginwrapper

sudo apt-get install --reinstall adobe-flashplugin

_or_

reinstall flash plugin from ubuntu sofware center.
end quote.

:guitar:

---

### Post by ihasbedhead on 2012-03-29
install flash-aid on firefox
its a add-on

---

### Post by mojo risin on 2012-03-29
Interestingly enough I have the same problem. 
It only occurred after I updated this morning, and since, I can't get any flash content to play in any browser. 
Flash is properly installed, and I tried all installers (adobe installer, gnash and lightspark)separately, and none work. Youtube works, because the videos are in HTML 5.(tried in firefox , epiphany, and chromium)
```

Ubuntu Architecture  Linux schrabbelkiste 3.0.0-17-generic #30-Ubuntu SMP Thu Mar 8 17:34:21 UTC 2012 i686 i686 i386 GNU/Linux  Ubuntu Version  DISTRIB_ID=Ubuntu DISTRIB_RELEASE=11.10 DISTRIB_CODENAME=oneiric DISTRIB_DESCRIPTION="Ubuntu 11.10"  Firefox Packages  firefox                        install firefox-locale-af                install firefox-locale-en                install firefox-locale-id                install firefox-locale-ja                install firefox-locale-mn                install firefox-locale-vi                install  Firefox binaries  /usr/bin/firefox /usr/bin/firefox: symbolic link to `../lib/firefox-11.0/firefox.sh' /usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory) /opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)  Firefox divertion  /usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)  Sources  ddebs.list ddebs.list.distUpgrade ddebs.list.save lubuntu-desktop-ppa-oneiric.list lubuntu-desktop-ppa-oneiric.list.save mozillateam-firefox-stable-oneiric.list mozillateam-firefox-stable-oneiric.list.save pdfmod-team-ppa-oneiric.list pdfmod-team-ppa-oneiric.list.save  Flash packages  Plugin locations   /usr/lib/mozilla/plugins/flashplugin-alternative.so  Flash symlinks   /usr/lib/mozilla/plugins/libflashplayer.so: ELF 32-bit LSB shared object, Intel 80386, version 1 (SYSV), dynamically linked, stripped /usr/lib/mozilla/plugins/flashplugin-alternative.so: broken symbolic link to `/etc/alternatives/mozilla-flashplugin' /etc/alternatives/mozilla-flashplugin: broken symbolic link to `/usr/lib/gnash/libgnashplugin.so' /usr/lib/flashplugin-installer/libflashplayer.so: ERROR: cannot open `/usr/lib/flashplugin-installer/libflashplayer.so' (No such file or directory) /usr/lib/flashplugin-nonfree/libflashplayer.so: ERROR: cannot open `/usr/lib/flashplugin-nonfree/libflashplayer.so' (No such file or directory) /usr/lib/adobe-flashplugin/libflashplayer.so: ERROR: cannot open `/usr/lib/adobe-flashplugin/libflashplayer.so' (No such file or directory) /usr/lib/lightspark/lightspark.so: ERROR: cannot open `/usr/lib/lightspark/lightspark.so' (No such file or directory) /usr/lib/swfdec-mozilla/libswfdecmozilla.so: ERROR: cannot open `/usr/lib/swfdec-mozilla/libswfdecmozilla.so' (No such file or directory) /usr/lib/gnash/libgnashplugin.so: ERROR: cannot open `/usr/lib/gnash/libgnashplugin.so' (No such file or directory) /var/lib/flashplugin-installer/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-installer/npwrapper.libflashplayer.so' (No such file or directory) /var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so' (No such file or directory)  pluginreg.dat  Generated File. Do not edit.  [HEADER] Version:0.15:$ Arch:x86-gcc3:$  [PLUGINS] libflashplayer.so:$ /usr/lib/mozilla/plugins/libflashplayer.so:$ :$ 1329955048000:1:1:$ Shockwave Flash 11.2 r202:$ Shockwave Flash:$ 2 0:application/x-shockwave-flash:Shockwave Flash:swf:$ 1:application/futuresplash:FutureSplash Player:spl:$ IcedTeaPlugin.so:$ /usr/lib/jvm/java-6-openjdk/jre/lib/i386/IcedTeaPlugin.so:$ :$ 1320721957000:1:5:$ The <a href="http://icedtea.classpath.org/wiki/IcedTea-Web">IcedTea-Web Plugin</a> executes Java applets.:$ IcedTea-Web Plugin (using IcedTea-Web 1.1.3 (1.1.3-1ubuntu1.1)):$ 34 0:application/x-java-vm:IcedTea:class,jar:$ 1:application/x-java-applet:IcedTea:class,jar:$ 2:application/x-java-applet;version=1.1:IcedTea:class,jar:$ 3:application/x-java-applet;version=1.1.1:IcedTea:class,jar:$ 4:application/x-java-applet;version=1.1.2:IcedTea:class,jar:$ 5:application/x-java-applet;version=1.1.3:IcedTea:class,jar:$ 6:application/x-java-applet;version=1.2:IcedTea:class,jar:$ 7:application/x-java-applet;version=1.2.1:IcedTea:class,jar:$ 8:application/x-java-applet;version=1.2.2:IcedTea:class,jar:$ 9:application/x-java-applet;version=1.3:IcedTea:class,jar:$ 10:application/x-java-applet;version=1.3.1:IcedTea:class,jar:$ 11:application/x-java-applet;version=1.4:IcedTea:class,jar:$ 12:application/x-java-applet;version=1.4.1:IcedTea:class,jar:$ 13:application/x-java-applet;version=1.4.2:IcedTea:class,jar:$ 14:application/x-java-applet;version=1.5:IcedTea:class,jar:$ 15:application/x-java-applet;version=1.6:IcedTea:class,jar:$ 16:application/x-java-applet;jpi-version=1.6.0_50:IcedTea:class,jar:$ 17:application/x-java-bean:IcedTea:class,jar:$ 18:application/x-java-bean;version=1.1:IcedTea:class,jar:$ 19:application/x-java-bean;version=1.1.1:IcedTea:class,jar:$ 20:application/x-java-bean;version=1.1.2:IcedTea:class,jar:$ 21:application/x-java-bean;version=1.1.3:IcedTea:class,jar:$ 22:application/x-java-bean;version=1.2:IcedTea:class,jar:$ 23:application/x-java-bean;version=1.2.1:IcedTea:class,jar:$ 24:application/x-java-bean;version=1.2.2:IcedTea:class,jar:$ 25:application/x-java-bean;version=1.3:IcedTea:class,jar:$ 26:application/x-java-bean;version=1.3.1:IcedTea:class,jar:$ 27:application/x-java-bean;version=1.4:IcedTea:class,jar:$ 28:application/x-java-bean;version=1.4.1:IcedTea:class,jar:$ 29:application/x-java-bean;version=1.4.2:IcedTea:class,jar:$ 30:application/x-java-bean;version=1.5:IcedTea:class,jar:$ 31:application/x-java-bean;version=1.6:IcedTea:class,jar:$ 32:application/x-java-bean;jpi-version=1.6.0_50:IcedTea:class,jar:$ 33:application/x-java-vm-npruntime:::$ gecko-mediaplayer-wmp.so:$ /usr/lib/mozilla/plugins/gecko-mediaplayer-wmp.so:$ :$ 1313849555000:1:5:$ <a href="http://kdekorte.googlepages.com/gecko-mediaplayer">Gecko Media Player</a> 1.0.4<br><br>Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using <a href="http://mplayerhq.hu">MPlayer</a>:$ Windows Media Player Plug-in:$ 20 0:application/asx:Media Files:*:$ 1:video/x-ms-asf-plugin:Media Files:*:$ 2:video/x-msvideo:AVI:avi,*:$ 3:video/msvideo:AVI:avi,*:$ 4:application/x-mplayer2:Media Files:*:$ 5:video/x-mplayer2:Media Files:*:$ 6:application/x-ms-wmv:Microsoft WMV video:wmv,*:$ 7:video/x-ms-asf:Media Files:asf,asx,*:$ 8:video/x-ms-asx:Media Files:asx,*:$ 9:video/x-ms-wm:Media Files:wm,*:$ 10:video/x-ms-wmv:Microsoft WMV video:wmv,*:$ 11:audio/x-ms-wmv:Windows Media:wmv,*:$ 12:video/x-ms-wmp:Windows Media:wmp,*:$ 13:application/x-ms-wmp:Windows Media:wmp,*:$ 14:video/x-ms-wvx:Windows Media:wvx,*:$ 15:audio/x-ms-wax:Windows Media:wax,*:$ 16:audio/x-ms-wma:Windows Media:wma,*:$ 17:application/x-drm-v2:Windows Media:asx,*:$ 18:audio/wav:Microsoft wave file:wav,*:$ 19:audio/x-wav:Microsoft wave file:wav,*:$ gecko-mediaplayer-dvx.so:$ /usr/lib/mozilla/plugins/gecko-mediaplayer-dvx.so:$ :$ 1313849555000:1:5:$ <a href="http://kdekorte.googlepages.com/gecko-mediaplayer">Gecko Media Player</a> 1.0.4<br><br>Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using <a href="http://mplayerhq.hu">MPlayer</a>:$ DivX Browser Plug-In:$ 2 0:video/divx:DivX Media Format:divx:$ 1:video/vnd.divx:DivX Media Format:divx:$ gecko-mediaplayer.so:$ /usr/lib/mozilla/plugins/gecko-mediaplayer.so:$ :$ 1313849555000:1:5:$ <a href="http://kdekorte.googlepages.com/gecko-mediaplayer">Gecko Media Player</a> 1.0.4<br><br>Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using <a href="http://mplayerhq.hu">MPlayer</a>:$ mplayerplug-in is now gecko-mediaplayer 1.0.4:$ 46 0:audio/x-mpegurl:MPEG Playlist:m3u:$ 1:video/mpeg:MPEG:mpg,mpeg:$ 2:audio/mpeg:MPEG:mpg,mpeg:$ 3:video/x-mpeg:MPEG:mpg,mpeg:$ 4:video/x-mpeg2:MPEG2:mpv2,mp2ve:$ 5:audio/mpeg:MPEG:mpg,mpeg:$ 6:audio/x-mpeg:MPEG:mpg,mpeg:$ 7:audio/mpeg2:MPEG audio:mp2:$ 8:audio/x-mpeg2:MPEG audio:mp2:$ 9:audio/mp4:MPEG 4 audio:mp4:$ 10:audio/x-mp4:MPEG 4 audio:mp4:$ 11:video/mp4:MPEG 4 Video:mp4:$ 12:video/x-m4v:MPEG 4 Video:m4v:$ 13:video/3gpp:MPEG 4 Video:mp4,3gp:$ 14:audio/mpeg3:MPEG audio:mp3:$ 15:audio/x-mpeg3:MPEG audio:mp3:$ 16:audio/x-mpegurl:MPEG url:m3u:$ 17:audio/mp3:MPEG audio:mp3:$ 18:application/x-ogg:Ogg Vorbis Media:ogg,oga,ogm:$ 19:application/ogg:Ogg Vorbis Media:ogg,oga,ogm:$ 20:audio/x-ogg:Ogg Vorbis Audio:ogg,oga:$ 21:audio/ogg:Ogg Vorbis Audio:ogg,oga:$ 22:video/x-ogg:Ogg Vorbis Video:ogg,ogm:$ 23:video/ogg:Ogg Vorbis Video:ogg,ogm:$ 24:application/x-vlc-plugin:VLC plug-in:vlc:$ 25:application/x-google-vlc-plugin:Google VLC plug-in::$ 26:audio/flac:FLAC Audio:flac:$ 27:audio/x-flac:FLAC Audio:flac:$ 28:video/fli:FLI animation:fli,flc:$ 29:video/x-fli:FLI animation:fli,flc:$ 30:video/x-flv:Flash Video:flv:$ 31:video/flv:Flash Video:flv:$ 32:video/vnd.vivo:VivoActive:viv,vivo:$ 33:audio/x-matroska:Matroska Audio:mka:$ 34:video/x-matroska:Matroska Video:mkv:$ 35:application/x-nsv-vp3-mp3:Nullsoft Streaming Video:nsv:$ 36:audio/x-mod:Soundtracker:mod:$ 37:audio/x-aiff:AIFF Audio:aif:$ 38:audio/basic:Basic Audio File:au,snd:$ 39:audio/x-basic:Basic Audio File:au,snd:$ 40:audio/x-scpls:Shoutcast Playlist:pls:$ 41:video/x-mng:Multiple-Image Network Graphics:mng:$ 42:audio/webm:WEBM audio File:webm:$ 43:audio/x-webm:WEBM audio File:webm:$ 44:video/webm:WEBM video File:webm:$ 45:video/x-webm:WEBM video File:webm:$ gecko-mediaplayer-rm.so:$ /usr/lib/mozilla/plugins/gecko-mediaplayer-rm.so:$ :$ 1313849555000:1:5:$ <a href="http://kdekorte.googlepages.com/gecko-mediaplayer">Gecko Media Player</a> 1.0.4<br><br>Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using <a href="http://mplayerhq.hu">MPlayer</a>:$ RealPlayer 9:$ 7 0:audio/x-pn-realaudio:RealAudio:ram,rm:$ 1:application/vnd.rn-realmedia:RealMedia:rm:$ 2:application/vnd.rn-realaudio:RealAudio:ra,ram:$ 3:video/vnd.rn-realvideo:RealVideo:rv:$ 4:audio/x-realaudio:RealAudio:ra:$ 5:audio/x-pn-realaudio-plugin:RealAudio:rpm:$ 6:application/smil:SMIL:smil:$ gecko-mediaplayer-qt.so:$ /usr/lib/mozilla/plugins/gecko-mediaplayer-qt.so:$ :$ 1313849555000:1:5:$ <a href="http://kdekorte.googlepages.com/gecko-mediaplayer">Gecko Media Player</a> 1.0.4<br><br>Video Player Plug-in for QuickTime, RealPlayer and Windows Media Player streams using <a href="http://mplayerhq.hu">MPlayer</a>:$ QuickTime Plug-in 7.6.9:$ 6 0:video/quicktime:Quicktime:mov:$ 1:video/x-quicktime:Quicktime:mov:$ 2:image/x-quicktime:Quicktime:mov:$ 3:video/quicktime:Quicktime:mp4:$ 4:video/quicktime:Quicktime - Session Description Protocol:sdp:$ 5:application/x-quicktimeplayer:Quicktime:mov:$  [INVALID] /usr/lib/mozilla/plugins/flashplugin-alternative.so:$ 0:$ 
```

---

### Post by cainmark on 2012-03-29
I have the exact problem.  Installed and listed and enabled, just not working.

---

### Post by Lucidmez on 2012-03-29
Agreed, same problem here as well.  It appears to have happened after updating earlier today.  Everything looks to be installed properly.

---

### Post by r.stiltskin on 2012-03-29
My 10.05 is completely broken after today's "upgrade", and it doesn't seem possible to revert to the previous version.

I "completely removed" it in Synaptic, and then tried to install the previous one:
```
sudo apt-get install flashplugin-nonfree version=11.1.102.63ubuntu0
```
but it reinstalled the new one (11-2-202-228).  I don't understand why that happened.

As of now, nothing that uses flash works.

I'm using an old Nvidia-based card (I don't remember exactly which one) and Nvidia driver.

---

### Post by r.stiltskin on 2012-03-29
You can find solutions in [this thread]("http://ubuntuforums.org/showthread.php?p=11803068#post11803068").

---

