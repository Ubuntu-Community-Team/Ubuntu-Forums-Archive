---
title: "My Flash is not working ?"
date: 2012-04-19
forum: Multimedia Software
---

### Post by jaho22 on 2012-04-19
I have Ubuntu 11.10, and i have problem with flash player, it works with only some of the youtube videos.

How to fix, i may have installed some extra flash players and they may be causing conflicts to my flash videos ?

How to fix ?

---

### Post by oboedad55 on 2012-04-19
> **jaho22 said:**
> I have Ubuntu 11.10, and i have problem with flash player, it works with only some of the youtube videos.

How to fix, i may have installed some extra flash players and they may be causing conflicts to my flash videos ?

How to fix ?

How did you install "extra flash players"? In Firefox, if you're using it, look under tools/addons and tell us what's listed in "plugins".

---

### Post by Windoze Refugee on 2012-04-19
IM having a lot of trouble with flash too. I get an error/timeout from the repository (Connecting to fpdownload.macromedia.com|1.0.0.0|:80... timed out ) and none of the BBC i=player works, many of the youtube and other sites using flash/swf.
Bizarrely, i also dont seem to be able to fix it by upgrading to Oneric Ocelot as the upgrade button is missing in update manager...

---

### Post by lovinglinux on 2012-04-19
> **jaho22 said:**
> I have Ubuntu 11.10, and i have problem with flash player, it works with only some of the youtube videos.

How to fix, i may have installed some extra flash players and they may be causing conflicts to my flash videos ?

How to fix ?

First, install [Flash-Aid](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/) and execute it's Wizard. It will remove conflicting plugins and install flash properly. Restart the browser. If the problem persists, click Flash_Aid menu, select "Help > Generate Report" and paste the report here.

---

### Post by Paddy Landau on 2012-04-19
I installed Flash Aid.

Firefox > Tools > Flash-Aid > Quick Mode > Install beta flash. Restart Firefox.

That worked for me, thank you.

**EDIT:** Some sites did not work properly unti I rebooted.

---

### Post by Windoze Refugee on 2012-04-19
Hi, and many thanks for the help.
Still having trouble even with Flash Aid, not least as the connection to Macromedia server seems to er...well..not connect (Timed out every time so far)

heres the flash aid help report

```
Ubuntu Architecture  Linux jonathan-desktop 2.6.38-14-generic #58-Ubuntu SMP Tue Mar 27 18:48:46 UTC 2012 i686 i686 i386 GNU/Linux  

Ubuntu Version  

DISTRIB_ID=Ubuntu 
DISTRIB_RELEASE=11.04 
DISTRIB_CODENAME=natty 
DISTRIB_DESCRIPTION="Ubuntu 11.04"  

Firefox Packages

firefox                        install 
firefox-3.5                    deinstall 
firefox-branding                install 
firefox-globalmenu                install 
firefox-gnome-support                install 
firefox-locale-en                install  

Firefox binaries  

/usr/bin/firefox 
/usr/bin/firefox: symbolic link to `../lib/firefox-11.0/firefox.sh' 
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory) 
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)  

Firefox divertion  

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)  

Sources  

dropbox.list 
dropbox.list.distUpgrade 
dropbox.list.save 
google-chrome.list 
google-chrome.list.save 
karmic-partner.list 
karmic-partner.list.distUpgrade 
karmic-partner.list.save 
mozillateam-thunderbird-stable-natty.list 
mozillateam-thunderbird-stable-natty.list.save 
natty-partner.list natty-partner.list.save  

Flash packages  

flashplugin-installer                deinstall 

Plugin locations  

/home/jonathan/usr/lib/flash-plugin/libflashplayer.so 
/opt/Adobe AIR/Versions/1.0/Resources/libflashplayer.so   

Flash symlinks   

/usr/lib/mozilla/plugins/libflashplayer.so: ERROR: cannot open `/usr/lib/mozilla/plugins/libflashplayer.so' (No such file or directory) 
/usr/lib/mozilla/plugins/flashplugin-alternative.so: ERROR: cannot open `/usr/lib/mozilla/plugins/flashplugin-alternative.so' (No such file or directory) 
/etc/alternatives/mozilla-flashplugin: ERROR: cannot open `/etc/alternatives/mozilla-flashplugin' (No such file or directory) 
/usr/lib/flashplugin-installer/libflashplayer.so: ERROR: cannot open `/usr/lib/flashplugin-installer/libflashplayer.so' (No such file or directory) 
/usr/lib/flashplugin-nonfree/libflashplayer.so: ERROR: cannot open `/usr/lib/flashplugin-nonfree/libflashplayer.so' (No such file or directory) 
/usr/lib/adobe-flashplugin/libflashplayer.so: ERROR: cannot open `/usr/lib/adobe-flashplugin/libflashplayer.so' (No such file or directory) 
/usr/lib/lightspark/lightspark.so: ERROR: cannot open `/usr/lib/lightspark/lightspark.so' (No such file or directory) 
/usr/lib/swfdec-mozilla/libswfdecmozilla.so: ERROR: cannot open `/usr/lib/swfdec-mozilla/libswfdecmozilla.so' (No such file or directory) 
/usr/lib/gnash/libgnashplugin.so: ERROR: cannot open `/usr/lib/gnash/libgnashplugin.so' (No such file or directory) 
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-installer/npwrapper.libflashplayer.so' (No such file or directory) 
/var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so' (No such file or directory)  

pluginreg.dat  

Generated File. Do not edit.  

[HEADER] Version:0.15:$ Arch:x86-gcc3:$  [PLUGINS] IcedTeaPlugin.so:$ /usr/lib/jvm/java-6-openjdk/jre/lib/i386/IcedTeaPlugin.so:$ :$ 1320797432000:1:5:$ The <a href="http://icedtea.classpath.org/wiki/IcedTea-Web">IcedTea-Web Plugin</a> executes Java applets.:$ IcedTea-Web Plugin (using IcedTea-Web 1.1.1 (1.1.1-0ubuntu1~11.04.2)):$ 34 0:application/x-java-vm:IcedTea:class,jar:$ 1:application/x-java-applet:IcedTea:class,jar:$ 2:application/x-java-applet;version=1.1:IcedTea:class,jar:$ 3:application/x-java-applet;version=1.1.1:IcedTea:class,jar:$ 4:application/x-java-applet;version=1.1.2:IcedTea:class,jar:$ 5:application/x-java-applet;version=1.1.3:IcedTea:class,jar:$ 6:application/x-java-applet;version=1.2:IcedTea:class,jar:$ 7:application/x-java-applet;version=1.2.1:IcedTea:class,jar:$ 8:application/x-java-applet;version=1.2.2:IcedTea:class,jar:$ 9:application/x-java-applet;version=1.3:IcedTea:class,jar:$ 10:application/x-java-applet;version=1.3.1:IcedTea:class,jar:$ 11:application/x-java-applet;version=1.4:IcedTea:class,jar:$ 12:application/x-java-applet;version=1.4.1:IcedTea:class,jar:$ 13:application/x-java-applet;version=1.4.2:IcedTea:class,jar:$ 14:application/x-java-applet;version=1.5:IcedTea:class,jar:$ 15:application/x-java-applet;version=1.6:IcedTea:class,jar:$ 16:application/x-java-applet;jpi-version=1.6.0_50:IcedTea:class,jar:$ 17:application/x-java-bean:IcedTea:class,jar:$ 18:application/x-java-bean;version=1.1:IcedTea:class,jar:$ 19:application/x-java-bean;version=1.1.1:IcedTea:class,jar:$ 20:application/x-java-bean;version=1.1.2:IcedTea:class,jar:$ 21:application/x-java-bean;version=1.1.3:IcedTea:class,jar:$ 22:application/x-java-bean;version=1.2:IcedTea:class,jar:$ 23:application/x-java-bean;version=1.2.1:IcedTea:class,jar:$ 24:application/x-java-bean;version=1.2.2:IcedTea:class,jar:$ 25:application/x-java-bean;version=1.3:IcedTea:class,jar:$ 26:application/x-java-bean;version=1.3.1:IcedTea:class,jar:$ 27:application/x-java-bean;version=1.4:IcedTea:class,jar:$ 28:application/x-java-bean;version=1.4.1:IcedTea:class,jar:$ 29:application/x-java-bean;version=1.4.2:IcedTea:class,jar:$ 30:application/x-java-bean;version=1.5:IcedTea:class,jar:$ 31:application/x-java-bean;version=1.6:IcedTea:class,jar:$ 32:application/x-java-bean;jpi-version=1.6.0_50:IcedTea:class,jar:$ 33:application/x-java-vm-npruntime:::$ libvlcplugin.so:$ /usr/lib/mozilla/plugins/libvlcplugin.so:$ :$ 1311248968000:1:5:$ Version 1.1.9 The Luggage, copyright 1996-2007 The VideoLAN Team<br><a href="http://www.videolan.org/">http://www.videolan.org/</a>:$ VLC Multimedia Plug-in:$ 39 0:audio/mpeg:MPEG audio:mp2,mp3,mpga,mpega:$ 1:audio/x-mpeg:MPEG audio:mp2,mp3,mpga,mpega:$ 2:video/mpeg:MPEG video:mpg,mpeg,mpe:$ 3:video/x-mpeg:MPEG video:mpg,mpeg,mpe:$ 4:video/mpeg-system:MPEG video:mpg,mpeg,mpe,vob:$ 5:video/x-mpeg-system:MPEG video:mpg,mpeg,mpe,vob:$ 6:audio/x-mpegurl:MPEG audio:m3u:$ 7:video/mp4:MPEG-4 video:mp4,mpg4:$ 8:audio/mp4:MPEG-4 audio:mp4,mpg4:$ 9:audio/x-m4a:MPEG-4 audio:m4a:$ 10:application/mpeg4-iod:MPEG-4 video:mp4,mpg4:$ 11:application/mpeg4-muxcodetable:MPEG-4 video:mp4,mpg4:$ 12:video/x-msvideo:AVI video:avi:$ 13:video/quicktime:QuickTime video:mov,qt:$ 14:application/x-ogg:Ogg stream gg:$ 15:application/ogg:Ogg stream gg:$ 16:application/x-vlc-plugin:VLC plug-in:vlc:$ 17:video/x-ms-asf-plugin:Windows Media Video:asf,asx:$ 18:video/x-ms-asf:Windows Media Video:asf,asx:$ 19:application/x-mplayer2:Windows Media::$ 20:video/x-ms-wmv:Windows Media:wmv:$ 21:video/x-ms-wvx:Windows Media Video:wvx:$ 22:audio/x-ms-wma:Windows Media Audio:wma:$ 23:application/x-google-vlc-plugin:Google VLC plug-in::$ 24:audio/wav:WAV audio:wav:$ 25:audio/x-wav:WAV audio:wav:$ 26:audio/3gpp:3GPP audio:3gp,3gpp:$ 27:video/3gpp:3GPP video:3gp,3gpp:$ 28:audio/3gpp2:3GPP2 audio:3g2,3gpp2:$ 29:video/3gpp2:3GPP2 video:3g2,3gpp2:$ 30:video/divx ivX video:divx:$ 31:video/flv:FLV video:flv:$ 32:video/x-flv:FLV video:flv:$ 33:video/x-matroska:Matroska video:mkv:$ 34:audio/x-matroska:Matroska audio:mka:$ 35:application/xspf+xml:Playlist xspf:xspf:$ 36:video/webm:WebM video:webm:$ 37:audio/webm:WebM audio:webm:$ 38:audio/amr:AMR audio:amr:$ librhythmbox-itms-detection-plugin.so:$ /usr/lib/mozilla/plugins/librhythmbox-itms-detection-plugin.so:$ :$ 1304575418000:1:5:$ This plug-in detects the presence of iTunes when opening iTunes Store URLs in a web page with Firefox.:$ iTunes Application Detector:$ 1 0:application/itunes-plugin:::$ libtotem-narrowspace-plugin.so:$ /usr/lib/mozilla/plugins/libtotem-narrowspace-plugin.so:$ :$ 1300218695000:1:5:$ The <a href="http://www.gnome.org/projects/totem/">Totem</a> 2.32.0 plugin handles video and audio streams.:$ QuickTime Plug-in 7.6.6:$ 5 0:video/quicktime:QuickTime video:mov:$ 1:video/mp4:MPEG-4 video:mp4:$ 2:image/x-macpaint:MacPaint Bitmap image ntg:$ 3:image/x-quicktime:Macintosh Quickdraw/PICT drawing ict, pict1, pict2:$ 4:video/x-m4v:MPEG-4 video:m4v:$ libtotem-gmp-plugin.so:$ /usr/lib/mozilla/plugins/libtotem-gmp-plugin.so:$ :$ 1300218695000:1:5:$ The <a href="http://www.gnome.org/projects/totem/">Totem</a> 2.32.0 plugin handles video and audio streams.:$ Windows Media Player Plug-in 10 (compatible; Totem):$ 13 0:application/x-mplayer2:AVI video:avi, wma, wmv:$ 1:video/x-ms-asf-plugin:ASF video:asf, wmv:$ 2:video/x-msvideo:AVI video:asf, wmv:$ 3:video/x-ms-asf:ASF video:asf:$ 4:video/x-ms-wmv:Windows Media video:wmv:$ 5:video/x-wmv:Windows Media video:wmv:$ 6:video/x-ms-wvx:Windows Media video:wmv:$ 7:video/x-ms-wm:Windows Media video:wmv:$ 8:video/x-ms-wmp:Windows Media video:wmv:$ 9:application/x-ms-wms:Windows Media video:wms:$ 10:application/x-ms-wmp:Windows Media video:wmp:$ 11:application/asx:Microsoft ASX playlist:asx:$ 12:audio/x-ms-wma:Windows Media audio:wma:$ libtotem-mully-plugin.so:$ /usr/lib/mozilla/plugins/libtotem-mully-plugin.so:$ :$ 1300218695000:1:5:$ DivX Web Player version 1.4.0.233:$ DivXÂ® Web Player:$ 1 0:video/divx:AVI video:divx:$ libtotem-cone-plugin.so:$ /usr/lib/mozilla/plugins/libtotem-cone-plugin.so:$ :$ 1300218695000:1:5:$ The <a href="http://www.gnome.org/projects/totem/">Totem</a> 2.32.0 plugin handles video and audio streams.:$ VLC Multimedia Plugin (compatible Totem 2.32.0):$ 20 0:application/x-vlc-plugin:VLC Multimedia Plugin::$ 1:application/vlc:VLC Multimedia Plugin::$ 2:video/x-google-vlc-plugin:VLC Multimedia Plugin::$ 3:application/x-ogg:Ogg multimedia file gg:$ 4:application/ogg:Ogg multimedia file gg:$ 5:audio/ogg:Ogg Audio ga:$ 6:audio/x-ogg:Ogg Audio gg:$ 7:video/ogg:Ogg Video gv:$ 8:video/x-ogg:Ogg Video gg:$ 9:application/annodex:Annodex exchange format:anx:$ 10:audio/annodex:Annodex Audio:axa:$ 11:video/annodex:Annodex Video:axv:$ 12:video/mpeg:MPEG video:mpg, mpeg, mpe:$ 13:audio/wav:WAV audio:wav:$ 14:audio/x-wav:WAV audio:wav:$ 15:audio/mpeg:MP3 audio:mp3:$ 16:application/x-nsv-vp3-mp3:NullSoft video:nsv:$ 17:video/flv:Flash video:flv:$ 18:video/webm:WebM video:webm:$ 19:application/x-totem-plugin:Totem Multimedia plugin::$  [INVALID]
```

PS Ive had to edit this report a little, as it was seeing some of the entries as smilies etc and not allowing them all to be posted. Hope this doesnt cause too much confusion
WR

---

### Post by lovinglinux on 2012-04-19
> **Windoze Refugee said:**
> Hi, and many thanks for the help.
Still having trouble even with Flash Aid, not least as the connection to Macromedia server seems to er...well..not connect (Timed out every time so far)

heres the flash aid help report

```
Ubuntu Architecture  Linux jonathan-desktop 2.6.38-14-generic #58-Ubuntu SMP Tue Mar 27 18:48:46 UTC 2012 i686 i686 i386 GNU/Linux  

Ubuntu Version  

DISTRIB_ID=Ubuntu 
DISTRIB_RELEASE=11.04 
DISTRIB_CODENAME=natty 
DISTRIB_DESCRIPTION="Ubuntu 11.04"  

Firefox Packages

firefox                        install 
firefox-3.5                    deinstall 
firefox-branding                install 
firefox-globalmenu                install 
firefox-gnome-support                install 
firefox-locale-en                install  

Firefox binaries  

/usr/bin/firefox 
/usr/bin/firefox: symbolic link to `../lib/firefox-11.0/firefox.sh' 
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory) 
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)  

Firefox divertion  

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)  

Sources  

dropbox.list 
dropbox.list.distUpgrade 
dropbox.list.save 
google-chrome.list 
google-chrome.list.save 
karmic-partner.list 
karmic-partner.list.distUpgrade 
karmic-partner.list.save 
mozillateam-thunderbird-stable-natty.list 
mozillateam-thunderbird-stable-natty.list.save 
natty-partner.list natty-partner.list.save  

Flash packages  

flashplugin-installer                deinstall 

Plugin locations  

/home/jonathan/usr/lib/flash-plugin/libflashplayer.so 
/opt/Adobe AIR/Versions/1.0/Resources/libflashplayer.so   

Flash symlinks   

/usr/lib/mozilla/plugins/libflashplayer.so: ERROR: cannot open `/usr/lib/mozilla/plugins/libflashplayer.so' (No such file or directory) 
/usr/lib/mozilla/plugins/flashplugin-alternative.so: ERROR: cannot open `/usr/lib/mozilla/plugins/flashplugin-alternative.so' (No such file or directory) 
/etc/alternatives/mozilla-flashplugin: ERROR: cannot open `/etc/alternatives/mozilla-flashplugin' (No such file or directory) 
/usr/lib/flashplugin-installer/libflashplayer.so: ERROR: cannot open `/usr/lib/flashplugin-installer/libflashplayer.so' (No such file or directory) 
/usr/lib/flashplugin-nonfree/libflashplayer.so: ERROR: cannot open `/usr/lib/flashplugin-nonfree/libflashplayer.so' (No such file or directory) 
/usr/lib/adobe-flashplugin/libflashplayer.so: ERROR: cannot open `/usr/lib/adobe-flashplugin/libflashplayer.so' (No such file or directory) 
/usr/lib/lightspark/lightspark.so: ERROR: cannot open `/usr/lib/lightspark/lightspark.so' (No such file or directory) 
/usr/lib/swfdec-mozilla/libswfdecmozilla.so: ERROR: cannot open `/usr/lib/swfdec-mozilla/libswfdecmozilla.so' (No such file or directory) 
/usr/lib/gnash/libgnashplugin.so: ERROR: cannot open `/usr/lib/gnash/libgnashplugin.so' (No such file or directory) 
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-installer/npwrapper.libflashplayer.so' (No such file or directory) 
/var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so' (No such file or directory)  

pluginreg.dat  

Generated File. Do not edit.  

[HEADER] Version:0.15:$ Arch:x86-gcc3:$  [PLUGINS] IcedTeaPlugin.so:$ /usr/lib/jvm/java-6-openjdk/jre/lib/i386/IcedTeaPlugin.so:$ :$ 1320797432000:1:5:$ The <a href="http://icedtea.classpath.org/wiki/IcedTea-Web">IcedTea-Web Plugin</a> executes Java applets.:$ IcedTea-Web Plugin (using IcedTea-Web 1.1.1 (1.1.1-0ubuntu1~11.04.2)):$ 34 0:application/x-java-vm:IcedTea:class,jar:$ 1:application/x-java-applet:IcedTea:class,jar:$ 2:application/x-java-applet;version=1.1:IcedTea:class,jar:$ 3:application/x-java-applet;version=1.1.1:IcedTea:class,jar:$ 4:application/x-java-applet;version=1.1.2:IcedTea:class,jar:$ 5:application/x-java-applet;version=1.1.3:IcedTea:class,jar:$ 6:application/x-java-applet;version=1.2:IcedTea:class,jar:$ 7:application/x-java-applet;version=1.2.1:IcedTea:class,jar:$ 8:application/x-java-applet;version=1.2.2:IcedTea:class,jar:$ 9:application/x-java-applet;version=1.3:IcedTea:class,jar:$ 10:application/x-java-applet;version=1.3.1:IcedTea:class,jar:$ 11:application/x-java-applet;version=1.4:IcedTea:class,jar:$ 12:application/x-java-applet;version=1.4.1:IcedTea:class,jar:$ 13:application/x-java-applet;version=1.4.2:IcedTea:class,jar:$ 14:application/x-java-applet;version=1.5:IcedTea:class,jar:$ 15:application/x-java-applet;version=1.6:IcedTea:class,jar:$ 16:application/x-java-applet;jpi-version=1.6.0_50:IcedTea:class,jar:$ 17:application/x-java-bean:IcedTea:class,jar:$ 18:application/x-java-bean;version=1.1:IcedTea:class,jar:$ 19:application/x-java-bean;version=1.1.1:IcedTea:class,jar:$ 20:application/x-java-bean;version=1.1.2:IcedTea:class,jar:$ 21:application/x-java-bean;version=1.1.3:IcedTea:class,jar:$ 22:application/x-java-bean;version=1.2:IcedTea:class,jar:$ 23:application/x-java-bean;version=1.2.1:IcedTea:class,jar:$ 24:application/x-java-bean;version=1.2.2:IcedTea:class,jar:$ 25:application/x-java-bean;version=1.3:IcedTea:class,jar:$ 26:application/x-java-bean;version=1.3.1:IcedTea:class,jar:$ 27:application/x-java-bean;version=1.4:IcedTea:class,jar:$ 28:application/x-java-bean;version=1.4.1:IcedTea:class,jar:$ 29:application/x-java-bean;version=1.4.2:IcedTea:class,jar:$ 30:application/x-java-bean;version=1.5:IcedTea:class,jar:$ 31:application/x-java-bean;version=1.6:IcedTea:class,jar:$ 32:application/x-java-bean;jpi-version=1.6.0_50:IcedTea:class,jar:$ 33:application/x-java-vm-npruntime:::$ libvlcplugin.so:$ /usr/lib/mozilla/plugins/libvlcplugin.so:$ :$ 1311248968000:1:5:$ Version 1.1.9 The Luggage, copyright 1996-2007 The VideoLAN Team<br><a href="http://www.videolan.org/">http://www.videolan.org/</a>:$ VLC Multimedia Plug-in:$ 39 0:audio/mpeg:MPEG audio:mp2,mp3,mpga,mpega:$ 1:audio/x-mpeg:MPEG audio:mp2,mp3,mpga,mpega:$ 2:video/mpeg:MPEG video:mpg,mpeg,mpe:$ 3:video/x-mpeg:MPEG video:mpg,mpeg,mpe:$ 4:video/mpeg-system:MPEG video:mpg,mpeg,mpe,vob:$ 5:video/x-mpeg-system:MPEG video:mpg,mpeg,mpe,vob:$ 6:audio/x-mpegurl:MPEG audio:m3u:$ 7:video/mp4:MPEG-4 video:mp4,mpg4:$ 8:audio/mp4:MPEG-4 audio:mp4,mpg4:$ 9:audio/x-m4a:MPEG-4 audio:m4a:$ 10:application/mpeg4-iod:MPEG-4 video:mp4,mpg4:$ 11:application/mpeg4-muxcodetable:MPEG-4 video:mp4,mpg4:$ 12:video/x-msvideo:AVI video:avi:$ 13:video/quicktime:QuickTime video:mov,qt:$ 14:application/x-ogg:Ogg stream gg:$ 15:application/ogg:Ogg stream gg:$ 16:application/x-vlc-plugin:VLC plug-in:vlc:$ 17:video/x-ms-asf-plugin:Windows Media Video:asf,asx:$ 18:video/x-ms-asf:Windows Media Video:asf,asx:$ 19:application/x-mplayer2:Windows Media::$ 20:video/x-ms-wmv:Windows Media:wmv:$ 21:video/x-ms-wvx:Windows Media Video:wvx:$ 22:audio/x-ms-wma:Windows Media Audio:wma:$ 23:application/x-google-vlc-plugin:Google VLC plug-in::$ 24:audio/wav:WAV audio:wav:$ 25:audio/x-wav:WAV audio:wav:$ 26:audio/3gpp:3GPP audio:3gp,3gpp:$ 27:video/3gpp:3GPP video:3gp,3gpp:$ 28:audio/3gpp2:3GPP2 audio:3g2,3gpp2:$ 29:video/3gpp2:3GPP2 video:3g2,3gpp2:$ 30:video/divx ivX video:divx:$ 31:video/flv:FLV video:flv:$ 32:video/x-flv:FLV video:flv:$ 33:video/x-matroska:Matroska video:mkv:$ 34:audio/x-matroska:Matroska audio:mka:$ 35:application/xspf+xml:Playlist xspf:xspf:$ 36:video/webm:WebM video:webm:$ 37:audio/webm:WebM audio:webm:$ 38:audio/amr:AMR audio:amr:$ librhythmbox-itms-detection-plugin.so:$ /usr/lib/mozilla/plugins/librhythmbox-itms-detection-plugin.so:$ :$ 1304575418000:1:5:$ This plug-in detects the presence of iTunes when opening iTunes Store URLs in a web page with Firefox.:$ iTunes Application Detector:$ 1 0:application/itunes-plugin:::$ libtotem-narrowspace-plugin.so:$ /usr/lib/mozilla/plugins/libtotem-narrowspace-plugin.so:$ :$ 1300218695000:1:5:$ The <a href="http://www.gnome.org/projects/totem/">Totem</a> 2.32.0 plugin handles video and audio streams.:$ QuickTime Plug-in 7.6.6:$ 5 0:video/quicktime:QuickTime video:mov:$ 1:video/mp4:MPEG-4 video:mp4:$ 2:image/x-macpaint:MacPaint Bitmap image ntg:$ 3:image/x-quicktime:Macintosh Quickdraw/PICT drawing ict, pict1, pict2:$ 4:video/x-m4v:MPEG-4 video:m4v:$ libtotem-gmp-plugin.so:$ /usr/lib/mozilla/plugins/libtotem-gmp-plugin.so:$ :$ 1300218695000:1:5:$ The <a href="http://www.gnome.org/projects/totem/">Totem</a> 2.32.0 plugin handles video and audio streams.:$ Windows Media Player Plug-in 10 (compatible; Totem):$ 13 0:application/x-mplayer2:AVI video:avi, wma, wmv:$ 1:video/x-ms-asf-plugin:ASF video:asf, wmv:$ 2:video/x-msvideo:AVI video:asf, wmv:$ 3:video/x-ms-asf:ASF video:asf:$ 4:video/x-ms-wmv:Windows Media video:wmv:$ 5:video/x-wmv:Windows Media video:wmv:$ 6:video/x-ms-wvx:Windows Media video:wmv:$ 7:video/x-ms-wm:Windows Media video:wmv:$ 8:video/x-ms-wmp:Windows Media video:wmv:$ 9:application/x-ms-wms:Windows Media video:wms:$ 10:application/x-ms-wmp:Windows Media video:wmp:$ 11:application/asx:Microsoft ASX playlist:asx:$ 12:audio/x-ms-wma:Windows Media audio:wma:$ libtotem-mully-plugin.so:$ /usr/lib/mozilla/plugins/libtotem-mully-plugin.so:$ :$ 1300218695000:1:5:$ DivX Web Player version 1.4.0.233:$ DivXÂ® Web Player:$ 1 0:video/divx:AVI video:divx:$ libtotem-cone-plugin.so:$ /usr/lib/mozilla/plugins/libtotem-cone-plugin.so:$ :$ 1300218695000:1:5:$ The <a href="http://www.gnome.org/projects/totem/">Totem</a> 2.32.0 plugin handles video and audio streams.:$ VLC Multimedia Plugin (compatible Totem 2.32.0):$ 20 0:application/x-vlc-plugin:VLC Multimedia Plugin::$ 1:application/vlc:VLC Multimedia Plugin::$ 2:video/x-google-vlc-plugin:VLC Multimedia Plugin::$ 3:application/x-ogg:Ogg multimedia file gg:$ 4:application/ogg:Ogg multimedia file gg:$ 5:audio/ogg:Ogg Audio ga:$ 6:audio/x-ogg:Ogg Audio gg:$ 7:video/ogg:Ogg Video gv:$ 8:video/x-ogg:Ogg Video gg:$ 9:application/annodex:Annodex exchange format:anx:$ 10:audio/annodex:Annodex Audio:axa:$ 11:video/annodex:Annodex Video:axv:$ 12:video/mpeg:MPEG video:mpg, mpeg, mpe:$ 13:audio/wav:WAV audio:wav:$ 14:audio/x-wav:WAV audio:wav:$ 15:audio/mpeg:MP3 audio:mp3:$ 16:application/x-nsv-vp3-mp3:NullSoft video:nsv:$ 17:video/flv:Flash video:flv:$ 18:video/webm:WebM video:webm:$ 19:application/x-totem-plugin:Totem Multimedia plugin::$  [INVALID]
```

PS Ive had to edit this report a little, as it was seeing some of the entries as smilies etc and not allowing them all to be posted. Hope this doesnt cause too much confusion
WR

First delete /home/jonathan/usr/lib/flash-plugin/libflashplayer.so. I don't know why you have such directory structure in your home, so delete the /home/jonathan/usr/ folder as well, if you don't need it to something else.

Then, click "Check Update" in Flash-Aid menu and wait for the warning about new version of Flash Beta. After that run the Flash-Aid Wizard again to install flash, because you don't have any flash version installed.

---

### Post by Windoze Refugee on 2012-04-19
H and thanks again for your help.
Im still hitting the same problem in that the macromedia server wont connect so cant download/upgrade anything :(

from terminal:
"--2012-04-19 13:09:23--  (try:11)  [http://fpdownload.macromedia.com/get/flashplayer/pdc/11.2.202.233/install_flash_player_11_linux.i386.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/pdc/11.2.202.233/install_flash_player_11_linux.i386.tar.gz)
Connecting to fpdownload.macromedia.com|1.0.0.0|:80... failed: Connection timed out.
Retrying.
"

etc etc etc ad nauseum

---

### Post by Paddy Landau on 2012-04-19
> **Windoze Refugee said:**
> Ive had to edit this report a little, as it was seeing some of the entries as smilies etc
There are three different ways to get around this.

[LIST]
[*]Under where you type your post, there are three "Miscellaneous Options". One of them is "Disable smilies in text". Select it.
[/LIST]

[LIST]
[*]Anything surrounded by [noparse]```
[/noparse] and [noparse]
```[/noparse] (or highlight the text and press the "#" button in your toolbar) will not show any smilies.
[/LIST]

[LIST]
[*]Likewise, anything surrounded by  [noparse][noparse][/noparse] and [/noparse] will not show any smilies.
[/LIST]

---

### Post by lovinglinux on 2012-04-19
> **Windoze Refugee said:**
> H and thanks again for your help.
Im still hitting the same problem in that the macromedia server wont connect so cant download/upgrade anything :(

from terminal:
"--2012-04-19 13:09:23--  (try:11)  [http://fpdownload.macromedia.com/get/flashplayer/pdc/11.2.202.233/install_flash_player_11_linux.i386.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/pdc/11.2.202.233/install_flash_player_11_linux.i386.tar.gz)
Connecting to fpdownload.macromedia.com|1.0.0.0|:80... failed: Connection timed out.
Retrying.
"

etc etc etc ad nauseum

It is connecting from here.

Anyway, instead of the Beta install option, select the stable from repositories. It is the same version.

---

### Post by Windoze Refugee on 2012-04-20
Hi. And once more, continued thanks for the input. Ive now successfully installed flash, and functionality appears to have returned to Youtube (the ones Ive looked at so far anyway) but the BBC iplayer (and presumably some others) is still not working. This includes both the live radio stream and the 'watch again' VOD returning the error: "this content doesnt seem to be working. Try again later'. Any ideas?

---

### Post by Windoze Refugee on 2012-04-23
I've now manage to upgrade to Oneric Ocelot, as much as anything in the hope that it would solve the flash streaming problem. It hasnt :(. Does ANYONE know whats wrong?

---

### Post by LittleDeb on 2012-04-23
Also having youtube Video playback problems, Only Some Videos Play.

Here is my Flash Aid Report:

```
Ubuntu Architecture  Linux bob-desktop 2.6.32-41-generic #88-Ubuntu SMP Thu Mar 29 13:08:43 UTC 2012 i686 GNU/Linux  

Ubuntu Version  

DISTRIB_ID=Ubuntu 
DISTRIB_RELEASE=10.04 
DISTRIB_CODENAME=lucid 
DISTRIB_DESCRIPTION="Ubuntu 10.04.4 LTS"  

Firefox Packages  

firefox                        install 
firefox-branding                install 
firefox-gnome-support                install 
firefox-locale-en                install  

Firefox binaries  
/usr/bin/firefox /usr/bin/firefox: symbolic link to `../lib/firefox-11.0/firefox.sh' 
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory) 
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)  

Firefox divertion  

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)  

Sources  

danielrichter2007-grub-customizer-lucid.list 
danielrichter2007-grub-customizer-lucid.list.save 
lucid-partner.list 
lucid-partner.list.save 
medibuntu.list 
medibuntu.list.save  

Flash packages  

Plugin locations   

/usr/lib/mozilla/plugins/flashplugin-alternative.so  

Flash symlinks   

/usr/lib/mozilla/plugins/libflashplayer.so: ELF 32-bit LSB shared object, Intel 80386, version 1 (SYSV), dynamically linked, stripped 
/usr/lib/mozilla/plugins/flashplugin-alternative.so: ERROR: cannot open `/usr/lib/mozilla/plugins/flashplugin-alternative.so' (No such file or directory) 
/etc/alternatives/mozilla-flashplugin: ERROR: cannot open `/etc/alternatives/mozilla-flashplugin' (No such file or directory) 
/usr/lib/flashplugin-installer/libflashplayer.so: ERROR: cannot open `/usr/lib/flashplugin-installer/libflashplayer.so' (No such file or directory) 
/usr/lib/flashplugin-nonfree/libflashplayer.so: ERROR: cannot open `/usr/lib/flashplugin-nonfree/libflashplayer.so' (No such file or directory) 
/usr/lib/adobe-flashplugin/libflashplayer.so: ERROR: cannot open `/usr/lib/adobe-flashplugin/libflashplayer.so' (No such file or directory) 
/usr/lib/lightspark/lightspark.so: ERROR: cannot open `/usr/lib/lightspark/lightspark.so' (No such file or directory) 
/usr/lib/swfdec-mozilla/libswfdecmozilla.so: ERROR: cannot open `/usr/lib/swfdec-mozilla/libswfdecmozilla.so' (No such file or directory) 
/usr/lib/gnash/libgnashplugin.so: ERROR: cannot open `/usr/lib/gnash/libgnashplugin.so' (No such file or directory) 
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-installer/npwrapper.libflashplayer.so' (No such file or directory) 
/var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so' (No such file or directory)  

pluginreg.dat  Generated File. Do not edit.  [HEADER] Version:0.15:$ Arch:x86-gcc3:$  

[PLUGINS] 

libflashplayer.so:$ /usr/lib/mozilla/plugins/libflashplayer.so:$ :$ 1334182565000:1:1:$ Shockwave Flash 11.2 r202:$ Shockwave Flash:$ 2 0:application/x-shockwave-flash:Shockwave Flash:swf:$ 1:application/futuresplash:FutureSplash Player:spl:$ 

IcedTeaPlugin.so:$ /usr/lib/jvm/java-6-openjdk/jre/lib/i386/IcedTeaPlugin.so:$ :$ 1329507418000:1:5:$ The IcedTea NPR Web Browser Plugin (using IcedTea6 1.9.13 (6b20-1.9.13-0ubuntu1~10.04.1)) executes Java applets.:$ IcedTea NPR Web Browser Plugin (using IcedTea6 1.9.13 (6b20-1.9.13-0ubuntu1~10.04.1)):$ 34 0:application/x-java-vm:IcedTea:class,jar:$ 1:application/x-java-applet:IcedTea:class,jar:$ 2:application/x-java-applet;version=1.1:IcedTea:class,jar:$ 3:application/x-java-applet;version=1.1.1:IcedTea:class,jar:$ 4:application/x-java-applet;version=1.1.2:IcedTea:class,jar:$ 5:application/x-java-applet;version=1.1.3:IcedTea:class,jar:$ 6:application/x-java-applet;version=1.2:IcedTea:class,jar:$ 7:application/x-java-applet;version=1.2.1:IcedTea:class,jar:$ 8:application/x-java-applet;version=1.2.2:IcedTea:class,jar:$ 9:application/x-java-applet;version=1.3:IcedTea:class,jar:$ 10:application/x-java-applet;version=1.3.1:IcedTea:class,jar:$ 11:application/x-java-applet;version=1.4:IcedTea:class,jar:$ 12:application/x-java-applet;version=1.4.1:IcedTea:class,jar:$ 13:application/x-java-applet;version=1.4.2:IcedTea:class,jar:$ 14:application/x-java-applet;version=1.5:IcedTea:class,jar:$ 15:application/x-java-applet;version=1.6:IcedTea:class,jar:$ 16:application/x-java-applet;jpi-version=1.6.0_20:IcedTea:class,jar:$ 17:application/x-java-bean:IcedTea:class,jar:$ 18:application/x-java-bean;version=1.1:IcedTea:class,jar:$ 19:application/x-java-bean;version=1.1.1:IcedTea:class,jar:$ 20:application/x-java-bean;version=1.1.2:IcedTea:class,jar:$ 21:application/x-java-bean;version=1.1.3:IcedTea:class,jar:$ 22:application/x-java-bean;version=1.2:IcedTea:class,jar:$ 23:application/x-java-bean;version=1.2.1:IcedTea:class,jar:$ 24:application/x-java-bean;version=1.2.2:IcedTea:class,jar:$ 25:application/x-java-bean;version=1.3:IcedTea:class,jar:$ 26:application/x-java-bean;version=1.3.1:IcedTea:class,jar:$ 27:application/x-java-bean;version=1.4:IcedTea:class,jar:$ 28:application/x-java-bean;version=1.4.1:IcedTea:class,jar:$ 29:application/x-java-bean;version=1.4.2:IcedTea:class,jar:$ 30:application/x-java-bean;version=1.5:IcedTea:class,jar:$ 31:application/x-java-bean;version=1.6:IcedTea:class,jar:$ 32:application/x-java-bean;jpi-version=1.6.0_20:IcedTea:class,jar:$ 33:application/x-java-vm-npruntime:::$ librhythmbox-itms-detection-plugin.so:$ /usr/lib/mozilla/plugins/librhythmbox-itms-detection-plugin.so:$ :$ 1277463660000:1:5:$ This plug-in detects the presence of iTunes when opening iTunes Store URLs in a web page with Firefox.:$ iTunes Application Detector:$ 1 0:application/itunes-plugin:::$ libtotem-narrowspace-plugin.so:$ /usr/lib/mozilla/plugins/libtotem-narrowspace-plugin.so:$ :$ 1274279893000:1:5:$ The <a href="http://www.gnome.org/projects/totem/">Totem</a> 2.30.2 plugin handles video and audio streams.:$ QuickTime Plug-in 7.6.6:$ 5 0:video/quicktime:QuickTime video:mov:$ 1:video/mp4:MPEG-4 video:mp4:$ 2:image/x-macpaint:MacPaint Bitmap image:pntg:$ 3:image/x-quicktime:Macintosh Quickdraw/PICT drawing:pict, pict1, pict2:$ 4:video/x-m4v:MPEG-4 video:m4v:$ libtotem-mully-plugin.so:$ /usr/lib/mozilla/plugins/libtotem-mully-plugin.so:$ :$ 1274279893000:1:5:$ DivX Web Player version 1.4.0.233:$ DivXÂ® Web Player:$ 1 0:video/divx:AVI video:divx:$ libtotem-gmp-plugin.so:$ /usr/lib/mozilla/plugins/libtotem-gmp-plugin.so:$ :$ 1274279893000:1:5:$ The <a href="http://www.gnome.org/projects/totem/">Totem</a> 2.30.2 plugin handles video and audio streams.:$ Windows Media Player Plug-in 10 (compatible; Totem):$ 13 0:application/x-mplayer2:AVI video:avi, wma, wmv:$ 1:video/x-ms-asf-plugin:ASF video:asf, wmv:$ 2:video/x-msvideo:AVI video:asf, wmv:$ 3:video/x-ms-asf:ASF video:asf:$ 4:video/x-ms-wmv:Windows Media video:wmv:$ 5:video/x-wmv:Windows Media video:wmv:$ 6:video/x-ms-wvx:Windows Media video:wmv:$ 7:video/x-ms-wm:Windows Media video:wmv:$ 8:video/x-ms-wmp:Windows Media video:wmv:$ 9:application/x-ms-wms:Windows Media video:wms:$ 10:application/x-ms-wmp:Windows Media video:wmp:$ 11:application/asx:Microsoft ASX playlist:asx:$ 12:audio/x-ms-wma:Windows Media audio:wma:$ libtotem-cone-plugin.so:$ /usr/lib/mozilla/plugins/libtotem-cone-plugin.so:$ :$ 1274279893000:1:5:$ The <a href="http://www.gnome.org/projects/totem/">Totem</a> 2.30.2 plugin handles video and audio streams.:$ VLC Multimedia Plugin (compatible Totem 2.30.2):$ 19 0:application/x-vlc-plugin:VLC Multimedia Plugin::$ 1:application/vlc:VLC Multimedia Plugin::$ 2:video/x-google-vlc-plugin:VLC Multimedia Plugin::$ 3:application/x-ogg:Ogg multimedia file:ogg:$ 4:application/ogg:Ogg multimedia file:ogg:$ 5:audio/ogg:Ogg Audio:oga:$ 6:audio/x-ogg:Ogg Audio:ogg:$ 7:video/ogg:Ogg Video:ogv:$ 8:video/x-ogg:Ogg Video:ogg:$ 9:application/annodex:Annodex exchange format:anx:$ 10:audio/annodex:Annodex Audio:axa:$ 11:video/annodex:Annodex Video:axv:$ 12:video/mpeg:MPEG video:mpg, mpeg, mpe:$ 13:audio/wav:WAV audio:wav:$ 14:audio/x-wav:WAV audio:wav:$ 15:audio/mpeg:MP3 audio:mp3:$ 16:application/x-nsv-vp3-mp3:NullSoft video:nsv:$ 17:video/flv:Flash video:flv:$ 18:application/x-totem-plugin:Totem Multimedia plugin::$  [INVALID] 
```


Any help would be greatly appreciated!

---

### Post by lovinglinux on 2012-04-23
> **Windoze Refugee said:**
> I've now manage to upgrade to Oneric Ocelot, as much as anything in the hope that it would solve the flash streaming problem. It hasnt :(. Does ANYONE know whats wrong?

YouTube works, but BBC iPlayer doesn't? Then I can't be much helpful, because I don't have access to BBC. I would test other video sites, to see if the problem is exclusive to BBC.

---

### Post by lovinglinux on 2012-04-23
> **LittleDeb said:**
> Also having youtube Video playback problems, Only Some Videos Play.

Here is my Flash Aid Report:

```
Ubuntu Architecture  Linux bob-desktop 2.6.32-41-generic #88-Ubuntu SMP Thu Mar 29 13:08:43 UTC 2012 i686 GNU/Linux  

Ubuntu Version  

DISTRIB_ID=Ubuntu 
DISTRIB_RELEASE=10.04 
DISTRIB_CODENAME=lucid 
DISTRIB_DESCRIPTION="Ubuntu 10.04.4 LTS"  

Firefox Packages  

firefox                        install 
firefox-branding                install 
firefox-gnome-support                install 
firefox-locale-en                install  

Firefox binaries  
/usr/bin/firefox /usr/bin/firefox: symbolic link to `../lib/firefox-11.0/firefox.sh' 
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory) 
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)  

Firefox divertion  

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)  

Sources  

danielrichter2007-grub-customizer-lucid.list 
danielrichter2007-grub-customizer-lucid.list.save 
lucid-partner.list 
lucid-partner.list.save 
medibuntu.list 
medibuntu.list.save  

Flash packages  

Plugin locations   

/usr/lib/mozilla/plugins/flashplugin-alternative.so  

Flash symlinks   

/usr/lib/mozilla/plugins/libflashplayer.so: ELF 32-bit LSB shared object, Intel 80386, version 1 (SYSV), dynamically linked, stripped 
/usr/lib/mozilla/plugins/flashplugin-alternative.so: ERROR: cannot open `/usr/lib/mozilla/plugins/flashplugin-alternative.so' (No such file or directory) 
/etc/alternatives/mozilla-flashplugin: ERROR: cannot open `/etc/alternatives/mozilla-flashplugin' (No such file or directory) 
/usr/lib/flashplugin-installer/libflashplayer.so: ERROR: cannot open `/usr/lib/flashplugin-installer/libflashplayer.so' (No such file or directory) 
/usr/lib/flashplugin-nonfree/libflashplayer.so: ERROR: cannot open `/usr/lib/flashplugin-nonfree/libflashplayer.so' (No such file or directory) 
/usr/lib/adobe-flashplugin/libflashplayer.so: ERROR: cannot open `/usr/lib/adobe-flashplugin/libflashplayer.so' (No such file or directory) 
/usr/lib/lightspark/lightspark.so: ERROR: cannot open `/usr/lib/lightspark/lightspark.so' (No such file or directory) 
/usr/lib/swfdec-mozilla/libswfdecmozilla.so: ERROR: cannot open `/usr/lib/swfdec-mozilla/libswfdecmozilla.so' (No such file or directory) 
/usr/lib/gnash/libgnashplugin.so: ERROR: cannot open `/usr/lib/gnash/libgnashplugin.so' (No such file or directory) 
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-installer/npwrapper.libflashplayer.so' (No such file or directory) 
/var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so' (No such file or directory)  

pluginreg.dat  Generated File. Do not edit.  [HEADER] Version:0.15:$ Arch:x86-gcc3:$  

[PLUGINS] 

libflashplayer.so:$ /usr/lib/mozilla/plugins/libflashplayer.so:$ :$ 1334182565000:1:1:$ Shockwave Flash 11.2 r202:$ Shockwave Flash:$ 2 0:application/x-shockwave-flash:Shockwave Flash:swf:$ 1:application/futuresplash:FutureSplash Player:spl:$ 

IcedTeaPlugin.so:$ /usr/lib/jvm/java-6-openjdk/jre/lib/i386/IcedTeaPlugin.so:$ :$ 1329507418000:1:5:$ The IcedTea NPR Web Browser Plugin (using IcedTea6 1.9.13 (6b20-1.9.13-0ubuntu1~10.04.1)) executes Java applets.:$ IcedTea NPR Web Browser Plugin (using IcedTea6 1.9.13 (6b20-1.9.13-0ubuntu1~10.04.1)):$ 34 0:application/x-java-vm:IcedTea:class,jar:$ 1:application/x-java-applet:IcedTea:class,jar:$ 2:application/x-java-applet;version=1.1:IcedTea:class,jar:$ 3:application/x-java-applet;version=1.1.1:IcedTea:class,jar:$ 4:application/x-java-applet;version=1.1.2:IcedTea:class,jar:$ 5:application/x-java-applet;version=1.1.3:IcedTea:class,jar:$ 6:application/x-java-applet;version=1.2:IcedTea:class,jar:$ 7:application/x-java-applet;version=1.2.1:IcedTea:class,jar:$ 8:application/x-java-applet;version=1.2.2:IcedTea:class,jar:$ 9:application/x-java-applet;version=1.3:IcedTea:class,jar:$ 10:application/x-java-applet;version=1.3.1:IcedTea:class,jar:$ 11:application/x-java-applet;version=1.4:IcedTea:class,jar:$ 12:application/x-java-applet;version=1.4.1:IcedTea:class,jar:$ 13:application/x-java-applet;version=1.4.2:IcedTea:class,jar:$ 14:application/x-java-applet;version=1.5:IcedTea:class,jar:$ 15:application/x-java-applet;version=1.6:IcedTea:class,jar:$ 16:application/x-java-applet;jpi-version=1.6.0_20:IcedTea:class,jar:$ 17:application/x-java-bean:IcedTea:class,jar:$ 18:application/x-java-bean;version=1.1:IcedTea:class,jar:$ 19:application/x-java-bean;version=1.1.1:IcedTea:class,jar:$ 20:application/x-java-bean;version=1.1.2:IcedTea:class,jar:$ 21:application/x-java-bean;version=1.1.3:IcedTea:class,jar:$ 22:application/x-java-bean;version=1.2:IcedTea:class,jar:$ 23:application/x-java-bean;version=1.2.1:IcedTea:class,jar:$ 24:application/x-java-bean;version=1.2.2:IcedTea:class,jar:$ 25:application/x-java-bean;version=1.3:IcedTea:class,jar:$ 26:application/x-java-bean;version=1.3.1:IcedTea:class,jar:$ 27:application/x-java-bean;version=1.4:IcedTea:class,jar:$ 28:application/x-java-bean;version=1.4.1:IcedTea:class,jar:$ 29:application/x-java-bean;version=1.4.2:IcedTea:class,jar:$ 30:application/x-java-bean;version=1.5:IcedTea:class,jar:$ 31:application/x-java-bean;version=1.6:IcedTea:class,jar:$ 32:application/x-java-bean;jpi-version=1.6.0_20:IcedTea:class,jar:$ 33:application/x-java-vm-npruntime:::$ librhythmbox-itms-detection-plugin.so:$ /usr/lib/mozilla/plugins/librhythmbox-itms-detection-plugin.so:$ :$ 1277463660000:1:5:$ This plug-in detects the presence of iTunes when opening iTunes Store URLs in a web page with Firefox.:$ iTunes Application Detector:$ 1 0:application/itunes-plugin:::$ libtotem-narrowspace-plugin.so:$ /usr/lib/mozilla/plugins/libtotem-narrowspace-plugin.so:$ :$ 1274279893000:1:5:$ The <a href="http://www.gnome.org/projects/totem/">Totem</a> 2.30.2 plugin handles video and audio streams.:$ QuickTime Plug-in 7.6.6:$ 5 0:video/quicktime:QuickTime video:mov:$ 1:video/mp4:MPEG-4 video:mp4:$ 2:image/x-macpaint:MacPaint Bitmap image:pntg:$ 3:image/x-quicktime:Macintosh Quickdraw/PICT drawing:pict, pict1, pict2:$ 4:video/x-m4v:MPEG-4 video:m4v:$ libtotem-mully-plugin.so:$ /usr/lib/mozilla/plugins/libtotem-mully-plugin.so:$ :$ 1274279893000:1:5:$ DivX Web Player version 1.4.0.233:$ DivXÂ® Web Player:$ 1 0:video/divx:AVI video:divx:$ libtotem-gmp-plugin.so:$ /usr/lib/mozilla/plugins/libtotem-gmp-plugin.so:$ :$ 1274279893000:1:5:$ The <a href="http://www.gnome.org/projects/totem/">Totem</a> 2.30.2 plugin handles video and audio streams.:$ Windows Media Player Plug-in 10 (compatible; Totem):$ 13 0:application/x-mplayer2:AVI video:avi, wma, wmv:$ 1:video/x-ms-asf-plugin:ASF video:asf, wmv:$ 2:video/x-msvideo:AVI video:asf, wmv:$ 3:video/x-ms-asf:ASF video:asf:$ 4:video/x-ms-wmv:Windows Media video:wmv:$ 5:video/x-wmv:Windows Media video:wmv:$ 6:video/x-ms-wvx:Windows Media video:wmv:$ 7:video/x-ms-wm:Windows Media video:wmv:$ 8:video/x-ms-wmp:Windows Media video:wmv:$ 9:application/x-ms-wms:Windows Media video:wms:$ 10:application/x-ms-wmp:Windows Media video:wmp:$ 11:application/asx:Microsoft ASX playlist:asx:$ 12:audio/x-ms-wma:Windows Media audio:wma:$ libtotem-cone-plugin.so:$ /usr/lib/mozilla/plugins/libtotem-cone-plugin.so:$ :$ 1274279893000:1:5:$ The <a href="http://www.gnome.org/projects/totem/">Totem</a> 2.30.2 plugin handles video and audio streams.:$ VLC Multimedia Plugin (compatible Totem 2.30.2):$ 19 0:application/x-vlc-plugin:VLC Multimedia Plugin::$ 1:application/vlc:VLC Multimedia Plugin::$ 2:video/x-google-vlc-plugin:VLC Multimedia Plugin::$ 3:application/x-ogg:Ogg multimedia file:ogg:$ 4:application/ogg:Ogg multimedia file:ogg:$ 5:audio/ogg:Ogg Audio:oga:$ 6:audio/x-ogg:Ogg Audio:ogg:$ 7:video/ogg:Ogg Video:ogv:$ 8:video/x-ogg:Ogg Video:ogg:$ 9:application/annodex:Annodex exchange format:anx:$ 10:audio/annodex:Annodex Audio:axa:$ 11:video/annodex:Annodex Video:axv:$ 12:video/mpeg:MPEG video:mpg, mpeg, mpe:$ 13:audio/wav:WAV audio:wav:$ 14:audio/x-wav:WAV audio:wav:$ 15:audio/mpeg:MP3 audio:mp3:$ 16:application/x-nsv-vp3-mp3:NullSoft video:nsv:$ 17:video/flv:Flash video:flv:$ 18:application/x-totem-plugin:Totem Multimedia plugin::$  [INVALID] 
```


Any help would be greatly appreciated!


I don't see anything wrong in your report. Please provide links to videos that work and to videos that doesn't work.

---

### Post by Windoze Refugee on 2012-05-01
this works just fine
[http://www.youtube.com/watch?v=1d6bUd9q45E&list=UUMffZS4_Fp-e-xG1u1IXoNg&index=9&feature=plcp](http://www.youtube.com/watch?v=1d6bUd9q45E&list=UUMffZS4_Fp-e-xG1u1IXoNg&index=9&feature=plcp)

The preliminary commercials work on this but the main item doesn't.
[http://www.youtube.com/watch?v=nabwiyhkhw4&list=SL&feature=sh_e_se&oref=http%3A%2F%2Fwww.youtube.com%2Fshow%2Ftheitcrowd%3Ffeature%3Dsh_e_pop&has_verified=1](http://www.youtube.com/watch?v=nabwiyhkhw4&list=SL&feature=sh_e_se&oref=http%3A%2F%2Fwww.youtube.com%2Fshow%2Ftheitcrowd%3Ffeature%3Dsh_e_pop&has_verified=1)

cheers
WR

---

### Post by lovinglinux on 2012-05-01
> **Windoze Refugee said:**
> this works just fine
[http://www.youtube.com/watch?v=1d6bUd9q45E&list=UUMffZS4_Fp-e-xG1u1IXoNg&index=9&feature=plcp](http://www.youtube.com/watch?v=1d6bUd9q45E&list=UUMffZS4_Fp-e-xG1u1IXoNg&index=9&feature=plcp)

The preliminary commercials work on this but the main item doesn't.
[http://www.youtube.com/watch?v=nabwiyhkhw4&list=SL&feature=sh_e_se&oref=http%3A%2F%2Fwww.youtube.com%2Fshow%2Ftheitcrowd%3Ffeature%3Dsh_e_pop&has_verified=1](http://www.youtube.com/watch?v=nabwiyhkhw4&list=SL&feature=sh_e_se&oref=http%3A%2F%2Fwww.youtube.com%2Fshow%2Ftheitcrowd%3Ffeature%3Dsh_e_pop&has_verified=1)

cheers
WR

The second video is not available in my country. I suppose the problem is probably DRM issue. I can't test it tho.

---

### Post by The Rnegade on 2012-05-01
> **jaho22 said:**
> I have Ubuntu 11.10, and i have problem with flash player, it works with only some of the youtube videos.

How to fix, i may have installed some extra flash players and they may be causing conflicts to my flash videos ?

How to fix ?

by extra flash players i assume you mean you tried to install some non proprietry adobe alternatives, uninstall them, then go on youre web browser and type about:plugins into the address bar, read through the list make sure none of them are listed. you may have to restart your computer to completely uninstall them. if that doesnt work you could uninstall the adobe flash package in the ubuntu repose and install the version from the adobe website

---

