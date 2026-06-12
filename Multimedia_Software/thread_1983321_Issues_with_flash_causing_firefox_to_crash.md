---
title: "Issues with flash causing firefox to crash"
date: 2012-05-20
forum: Multimedia Software
---

### Post by hueyafrosamurai on 2012-05-20
Hey, so I'm new to this forum, but ain't new to linux/ubuntu, so I thought i could skip the "absolute beginner section".

Anyway, so I was trying to install flash debug, which I managed to do. I was trying to figure out the source of a video that was streaming. Gave up, so then tried to get rid of flash debug. I reinstalled normal flash. But then on certain sites, like one of flash video (myspace and dailymotion for example), firefox would crash. everytime, without fail. so then i tried installing flashaid for firefox. briefly, it seemed it may have done the trick. I was wrong. So basically firefox always crashes when i go to certain sites with flash. kinda sucks eh...

Anybody got any ideas of what to do? Maybe I didn't uninstall flash debug properly? My problem in general, is that I'm not very good in installing stuff manually, ie via the terminal, unless someone gives me a very detailed tutorial and holds my hand along the way.... 

Cheers

---

### Post by lovinglinux on 2012-05-20
Please click Flash-Aid menu, select Help >>> Generate Report and post the results here, so I can take a look.

---

### Post by hueyafrosamurai on 2012-05-20
Ok, this is what flashaid/help/generate report shows:

> [FONT=monospace]Ubuntu Architecture

Linux palmares-laptop 2.6.32-41-generic-pae #89-Ubuntu SMP Fri Apr 27 23:59:24 UTC 2012 i686 GNU/Linux

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

/usr/bin/firefox
/usr/bin/firefox: symbolic link to `../lib/firefox/firefox.sh'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)

Firefox divertion

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

Sources

elementaryart-ppa-lucid.list
elementaryart-ppa-lucid.list.save
iplist.list
libreoffice-ppa-lucid.list
libreoffice-ppa-lucid.list.save
ubuntugis-ubuntugis-unstable-lucid.list

Flash packages

flashplugin-installer                install
Plugin locations

/home/palmares/Documents/flashplayer_10_plugin_debug/libflashplayer.so
/home/palmares/Downloads/flash_player_10_linux_dev/plugin/debugger/libflashplayer.so.tar.gz
/usr/lib/firefox-addons/plugins/libflashplayer.so
/usr/lib/flashplugin-installer/libflashplayer.so
/usr/lib/mozilla/plugins/libflashplayer.so

/usr/lib/mozilla/plugins/flashplugin-alternative.so

Flash symlinks


/usr/lib/mozilla/plugins/libflashplayer.so: ELF 32-bit LSB shared object, Intel 80386, version 1 (SYSV), dynamically linked, stripped
/usr/lib/mozilla/plugins/flashplugin-alternative.so: symbolic link to `/etc/alternatives/mozilla-flashplugin'
/etc/alternatives/mozilla-flashplugin: symbolic link to `/usr/lib/flashplugin-installer/libflashplayer.so'
/usr/lib/flashplugin-installer/libflashplayer.so: ELF 32-bit LSB shared object, Intel 80386, version 1 (SYSV), dynamically linked, stripped
/usr/lib/flashplugin-nonfree/libflashplayer.so: ERROR: cannot open `/usr/lib/flashplugin-nonfree/libflashplayer.so' (No such file or directory)
/usr/lib/adobe-flashplugin/libflashplayer.so: ERROR: cannot open `/usr/lib/adobe-flashplugin/libflashplayer.so' (No such file or directory)
/usr/lib/lightspark/lightspark.so: ERROR: cannot open `/usr/lib/lightspark/lightspark.so' (No such file or directory)
/usr/lib/swfdec-mozilla/libswfdecmozilla.so: ERROR: cannot open `/usr/lib/swfdec-mozilla/libswfdecmozilla.so' (No such file or directory)
/usr/lib/gnash/libgnashplugin.so: ERROR: cannot open `/usr/lib/gnash/libgnashplugin.so' (No such file or directory)
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-installer/npwrapper.libflashplayer.so' (No such file or directory)
/var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so' (No such file or directory)

pluginreg.dat

Generated File. Do not edit.

[HEADER]
Version:0.15:$
Arch:x86-gcc3:$

[PLUGINS]
libflashplayer.so:$
/usr/lib/mozilla/plugins/libflashplayer.so:$
:$
1334182565000:1:1:$
Shockwave Flash 11.2 r202:$
Shockwave Flash:$
2
0:application/x-shockwave-flash:Shockwave Flash:swf:$
1:application/futuresplash:FutureSplash Player:spl:$
IcedTeaPlugin.so:$
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/IcedTeaPlugin.so:$
:$
1329507418000:1:5:$
The IcedTea NPR Web Browser Plugin (using IcedTea6 1.9.13 (6b20-1.9.13-0ubuntu1~10.04.1)) executes Java applets.:$
IcedTea NPR Web Browser Plugin (using IcedTea6 1.9.13 (6b20-1.9.13-0ubuntu1~10.04.1)):$
34[/FONT] [FONT=Ubuntu]

-----con't-----[/FONT]

---

### Post by hueyafrosamurai on 2012-05-20
and:

> 0:application/x-java-vm:IcedTea:class,jar:$
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
16:application/x-java-applet;jpi-version=1.6.0_20:IcedTea:class,jar:$
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
32:application/x-java-bean;jpi-version=1.6.0_20:IcedTea:class,jar:$
33:application/x-java-vm-npruntime:::$
librhythmbox-itms-detection-plugin.so:$
/usr/lib/mozilla/plugins/librhythmbox-itms-detection-plugin.so:$
:$
1277463660000:1:5:$
This plug-in detects the presence of iTunes when opening iTunes Store URLs in a web page with Firefox.:$
iTunes Application Detector:$
1
0:application/itunes-plugin:::$
libtotem-narrowspace-plugin.so:$
/usr/lib/mozilla/plugins/libtotem-narrowspace-plugin.so:$
:$
1274279893000:1:5:$
The <a href="http://www.gnome.org/projects/totem/">Totem</a> 2.30.2 plugin handles video and audio streams.:$
QuickTime Plug-in 7.6.6:$
5
0:video/quicktime:QuickTime video:mov:$
1:video/mp4:MPEG-4 video:mp4:$
2:image/x-macpaint:MacPaint Bitmap image:pntg:$
3:image/x-quicktime:Macintosh Quickdraw/PICT drawing:pict, pict1, pict2:$
4:video/x-m4v:MPEG-4 video:m4v:$
libtotem-mully-plugin.so:$
/usr/lib/mozilla/plugins/libtotem-mully-plugin.so:$
:$
1274279893000:1:5:$
DivX Web Player version 1.4.0.233:$
DivX® Web Player:$
1
0:video/divx:AVI video:divx:$
libtotem-gmp-plugin.so:$
/usr/lib/mozilla/plugins/libtotem-gmp-plugin.so:$
:$
1274279893000:1:5:$
The <a href="http://www.gnome.org/projects/totem/">Totem</a> 2.30.2 plugin handles video and audio streams.:$
Windows Media Player Plug-in 10 (compatible; Totem):$
13
0:application/x-mplayer2:AVI video:avi, wma, wmv:$
1:video/x-ms-asf-plugin:ASF video:asf, wmv:$
2:video/x-msvideo:AVI video:asf, wmv:$
3:video/x-ms-asf:ASF video:asf:$
4:video/x-ms-wmv:Windows Media video:wmv:$
5:video/x-wmv:Windows Media video:wmv:$
6:video/x-ms-wvx:Windows Media video:wmv:$
7:video/x-ms-wm:Windows Media video:wmv:$
8:video/x-ms-wmp:Windows Media video:wmv:$
9:application/x-ms-wms:Windows Media video:wms:$
10:application/x-ms-wmp:Windows Media video:wmp:$
11:application/asx:Microsoft ASX playlist:asx:$
12:audio/x-ms-wma:Windows Media audio:wma:$
libtotem-cone-plugin.so:$
/usr/lib/mozilla/plugins/libtotem-cone-plugin.so:$
:$
1274279893000:1:5:$
The <a href="http://www.gnome.org/projects/totem/">Totem</a> 2.30.2 plugin handles video and audio streams.:$
VLC Multimedia Plugin (compatible Totem 2.30.2):$
19
0:application/x-vlc-plugin:VLC Multimedia Plugin::$
1:application/vlc:VLC Multimedia Plugin::$
2:video/x-google-vlc-plugin:VLC Multimedia Plugin::$
3:application/x-ogg:Ogg multimedia file:ogg:$
4:application/ogg:Ogg multimedia file:ogg:$
5:audio/ogg:Ogg Audio:oga:$
6:audio/x-ogg:Ogg Audio:ogg:$
7:video/ogg:Ogg Video:ogv:$
8:video/x-ogg:Ogg Video:ogg:$
9:application/annodex:Annodex exchange format:anx:$
10:audio/annodex:Annodex Audio:axa:$
11:video/annodex:Annodex Video:axv:$
12:video/mpeg:MPEG video:mpg, mpeg, mpe:$
13:audio/wav:WAV audio:wav:$
14:audio/x-wav:WAV audio:wav:$
15:audio/mpeg:MP3 audio:mp3:$
16:application/x-nsv-vp3-mp3:NullSoft video:nsv:$
17:video/flv:Flash video:flv:$
18:application/x-totem-plugin:Totem Multimedia plugin::$

[INVALID]Had to split in two due to smiley face limit, haha.

I'll try posting this same thing, but post crash aswell if that would help. But tell me if it would make a difference, I don't wanna spam this thread.

Cheers!

---

### Post by hueyafrosamurai on 2012-05-23
No?

And for now, since noone can help me perhaps, I'm using greasemonkey for certain flash and video sites...

---

### Post by lovinglinux on 2012-05-24
I don't see anything wrong in your report.

Try to disable hardware acceleration.

See [http://ubuntuforums.org/showthread.php?t=1953796](http://ubuntuforums.org/showthread.php?t=1953796)

---

### Post by hueyafrosamurai on 2012-06-01
Cheers. Will suss that out.

---

