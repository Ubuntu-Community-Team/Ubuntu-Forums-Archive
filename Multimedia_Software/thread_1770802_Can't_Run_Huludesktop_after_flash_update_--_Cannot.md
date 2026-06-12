---
title: "Can't Run Huludesktop after flash update -- Cannot view hidden huludesktop folder"
date: 2011-05-29
forum: Multimedia Software
---

### Post by bep7987 on 2011-05-29
I am using Natty 11.04 64-bit desktop
Kernel Linux 2.6.38-8-generic
GNOME 2.23.1.

I have used huludesktop on Ubuntu for a while.  It was working until I updated flash with Flash-Aid because I was concerned about using outdated flash.

I am now using npwrapper flash plugin (/var/lib/flashplugin-installer/npwrapper.libflashplayer.so). 

When I start huludesktop, I get the following error message:
[INDENT]Huludesktop could not locate the flash plugin.  If you already have it installed, please modify ~/.huludesktop with the correct location of libflashplayer.so[/INDENT]
[[img]http://s2.postimage.org/dbmj69r8/huludesktop.jpg[/img]](http://postimage.org/image/dbmj69r8/)

I have never been able to view the ~/.huludesktop folder. I can see my other hidden folders, but not ~/.huludesktop. 

When I attempt to change directories to ~/.huludesktop in terminal, I get the error message "Not a directory".

If I try to create the ~/.huludesktop directory, I get the message that the directory exists.

When I try to create symbolic links to the flashplayer plugin, I get a message stating that the link already exists.

In the past, I was able to get huludesktop to run by updating the link to the flashplayer plugin in the /usr/lib/mozilla/plugins folder.

Is the problem that I'm using the npwrapper plugin and not the libflashplayer.so?

Any suggestions?

---

### Post by Yellow Pasque on 2011-05-29
~/.huludesktop would be the user's configuration file (not a directory) and the file probably doesn't exist, so you would have to create it. Using nspluginwrapper isn't as good as the native 64-bit Flash, unless you have an nvidia card that can take advantage of VDPAU/Stage Video, so let us know what video card you have:
```
lspci | grep VGA
```

---

### Post by lovinglinux on 2011-05-29
Make sure you have [Flash-Aid 2.1.1]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/"). Run Flash-Aid again, but instead of selecting the version from the repository in the installation options, choose the version from Adobe Labs.

If that doesn't work, then click Flash-Aid menu, select "Help", then "Generate Report" and attach the *firefox-report.txt* file created in your Desktop, so I can take a look at it.

---

### Post by bep7987 on 2011-05-29
Here's the result from lspci | grep VGA:

01:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 8300 GS] (rev a1)

---

### Post by bep7987 on 2011-05-29
lovinglinux,

The report is 36.5 kb and therefore, too large to attach, so I've posted it here. I hope that's ok.

I'm not sure where the report is pulling the "sources" from because some of those (clamav, sevenmachines, ubuntu-mozilla-security-ppa-lucid.list) are no longer in my software sources list, at least in synaptic package manager.

Thank you for looking at this.

Ubuntu Architecture

---

### Post by lovinglinux on 2011-05-29
You have a such a big mess of plugins there, that Flash-Aid is not being able to remove all of them.

Please make sure you have Flash-Aid 2.1.1, then run the Wizard Mode again, but instead of executing the script, use the export option. Send me the script. I will add all the additional commands you need to fix this mess and give it back to you, so you can run it on a terminal.

---

### Post by bep7987 on 2011-05-29
Yes, I have Flash-Aid 2.1.1.

---

### Post by lovinglinux on 2011-05-29
> **bep7987 said:**
> Yes, I have Flash-Aid 2.1.1.

You removed the report data, but I still need that info to customize your script :-)

---

### Post by bep7987 on 2011-05-29
Sorry, after I removed it, I thought perhaps that was premature.  I've put it back.  Thank you.

---

### Post by lovinglinux on 2011-05-29
> **bep7987 said:**
> Sorry, after I removed it, I thought perhaps that was premature.  I've put it back.  Thank you.

okay, here it is the modified script. Close Firefox, than drag the script to a terminal to execute it.

After executing the script, start Firefox generate a new report and post it here. Test if flash works fine.

EDIT: I did a mistake in two lines of the script, but it will work anyway.

---

### Post by bep7987 on 2011-05-29
I ran the script, but it doesn't look as though flash was installed.

---

### Post by lovinglinux on 2011-05-29
Looks like you have more than one profile with different plugins.

Please post the result of:

```
ls ~/.mozilla
```

Please run each of these commands separately and tell me if you get any errors:

```
sudo apt-get purge flashplugin64-installer
```

```
sudo apt-get purge flashplugin-installer
```

```
sudo rm -f /home/petey/libflashplayer.so
```
```
sudo rm -f /home/petey/.mozilla/plugins/npwrapper.libflashplayer.so
```

Then empty your trash, generate a new report and paste here.

---

### Post by bep7987 on 2011-05-29
Here's the result of ls ~/.mozilla:
eclipse  extensions  firefox  firefox.last-version  plugins

I received no errors when executing the other commands.

---

### Post by lovinglinux on 2011-05-29
> **bep7987 said:**
> Here's the result of ls ~/.mozilla:
eclipse  extensions  firefox  firefox.last-version  plugins

I suppose ~/.mozilla/firefox.last-version is a backup. Delete it or zip it, because it is polluting the report with multiple flash versions, making hard to pinpoint the problem.

> **bep7987 said:**
> I received no errors when executing the other commands.

Here's the report:
[HTML]Ubuntu Architecture

Linux petey-desktop 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"

Firefox Packages

firefox						install
firefox-globalmenu				install
firefox-gnome-support				install

Firefox binaries

/usr/bin/firefox
/usr/bin/firefox: symbolic link to `../lib/firefox-4.0.1/firefox.sh'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)

Firefox divertion

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

Sources

chromium-daily-ppa-maverick.list
chromium-daily-ppa-maverick.list.save
chromium-daily-stable-maverick.list
chromium-daily-stable-maverick.list.save
google-talkplugin.list
google-talkplugin.list.distUpgrade
google-talkplugin.list.save
medibuntu.list
medibuntu.list.distUpgrade
medibuntu.list.save
mozillateam-firefox-stable-maverick.list
mozillateam-firefox-stable-maverick.list.distUpgrade
mozillateam-firefox-stable-maverick.list.save
mozillateam-firefox-stable-natty.list
mozillateam-firefox-stable-natty.list.save
rvm-mplayer-maverick.list
rvm-mplayer-maverick.list.save
rvm-smplayer-maverick.list
rvm-smplayer-maverick.list.save
screenlets-ppa-natty.list
screenlets-ppa-natty.list.save
sevenmachines-flash-natty.list
sevenmachines-flash-natty.list.save
ubuntu-clamav-ppa-lucid.list
ubuntu-clamav-ppa-lucid.list.distUpgrade
ubuntu-clamav-ppa-lucid.list.save
ubuntu-mozilla-security-ppa-lucid.list
ubuntu-mozilla-security-ppa-lucid.list.distUpgrade
ubuntu-mozilla-security-ppa-lucid.list.save

Flash packages

flashplugin64-installer				deinstall
Plugin locations

/home/petey/libflashplayer.so
/home/petey/.local/share/Trash/files/libflashplayer.so
/home/petey/.local/share/Trash/info/libflashplayer.so.trashinfo
/home/petey/.mozilla/plugins/libflashplayer.so
/root/.local/share/Trash/files/libflashplayer.so
/root/.local/share/Trash/files/npwrapper.2.libflashplayer.so
/root/.local/share/Trash/files/npwrapper.libflashplayer.so
/root/.local/share/Trash/files/pluginslibflashplayer.so
/root/.local/share/Trash/files/flash.2/libflashplayer.so
/root/.local/share/Trash/info/libflashplayer.so.trashinfo
/root/.local/share/Trash/info/npwrapper.2.libflashplayer.so.trashinfo
/root/.local/share/Trash/info/npwrapper.libflashplayer.so.trashinfo
/root/.local/share/Trash/info/pluginslibflashplayer.so.trashinfo
/usr/lib/chromium-browser/plugins/libflashplayer.so

/usr/lib/chromium-browser/plugins/flashplugin-alternative.so
/usr/lib/firefox/plugins/flashplugin-alternative.so
/usr/lib/iceape/plugins/flashplugin-alternative.so
/usr/lib/iceweasel/plugins/flashplugin-alternative.so
/usr/lib/midbrowser/plugins/flashplugin-alternative.so
/usr/lib/mozilla/plugins/flashplugin-alternative.so
/usr/lib/xulrunner/plugins/flashplugin-alternative.so
/usr/lib/xulrunner-addons/plugins/flashplugin-alternative.so

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

[HEADER]
Version:0.15:$
Arch:x86_64-gcc3:$

[PLUGINS]
libnpgtpo3dautoplugin.so:$
/opt/google/talkplugin/libnpgtpo3dautoplugin.so:$
:$
1303321917000:1:5:$
Google Talk Plugin Video Accelerator version:0.1.43.7:$
Google Talk Plugin Video Accelerator:$
1
0:application/vnd.gtpo3d.auto:O3D MIME::$
libnpgoogletalk64.so:$
/opt/google/talkplugin/libnpgoogletalk64.so:$
:$
1303321917000:1:5:$
Version: 2.0.6.0:$
Google Talk Plugin:$
1
0:application/googletalk:Google Talk Plugin:googletalk:$
librhythmbox-itms-detection-plugin.so:$
/usr/lib/mozilla/plugins/librhythmbox-itms-detection-plugin.so:$
:$
1301673552000:1:5:$
This plug-in detects the presence of iTunes when opening iTunes Store URLs in a web page with Firefox.:$
iTunes Application Detector:$
1
0:application/itunes-plugin:::$
nsdejavu.so:$
/usr/lib/netscape/plugins-libc6/nsdejavu.so:$
:$
1301006797000:1:5:$
This is the <a href="http://djvu.sourceforge.net">DjVuLibre-3.5.23</a> version of the DjVu plugin.<br>See <a href="http://djvu.sourceforge.net">DjVuLibre</a>.:$
DjVuLibre-3.5.23:$
6
0:image/x-djvu:DjVu File:djvu,djv:$
1:image/x.djvu:DjVu File::$
2:image/djvu:DjVu File::$
3:image/x-dejavu:DjVu File::$
4:image/x-iw44:DjVu File::$
5:image/vnd.djvu:DjVu File::$
libtotem-narrowspace-plugin.so:$
/usr/lib/mozilla/plugins/libtotem-narrowspace-plugin.so:$
:$
1300218622000:1:5:$
The <a href="http://www.gnome.org/projects/totem/">Totem</a> 2.32.0 plugin handles video and audio streams.:$
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
1300218622000:1:5:$
DivX Web Player version 1.4.0.233:$
DivXÂ® Web Player:$
1
0:video/divx:AVI video:divx:$
libtotem-gmp-plugin.so:$
/usr/lib/mozilla/plugins/libtotem-gmp-plugin.so:$
:$
1300218622000:1:5:$
The <a href="http://www.gnome.org/projects/totem/">Totem</a> 2.32.0 plugin handles video and audio streams.:$
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
1300218622000:1:5:$
The <a href="http://www.gnome.org/projects/totem/">Totem</a> 2.32.0 plugin handles video and audio streams.:$
VLC Multimedia Plugin (compatible Totem 2.32.0):$
20
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
18:video/webm:WebM video:webm:$
19:application/x-totem-plugin:Totem Multimedia plugin::$
xineplugin.so:$
/usr/lib/xine-plugin/xineplugin.so:$
:$
1298398613000:1:5:$
Xine Plugin version 1.0.2, (c) <a href=http://www.xinehq.de>The Xine Project</a>.<br>Windows Media Player / RealPlayer / QuickTime compatible.:$
Xine Plugin:$
91
0:application/annodex: Annodex media: anx:$
1:application/x-annodex: Annodex media: anx:$
2:audio/annodex: Annodex audio: axa:$
3:audio/x-annodex: Annodex audio: axa:$
4:video/annodex: Annodex video: axv:$
5:video/x-annodex: Annodex video: axv:$
6:audio/x-realaudio: RealAudio File: ra:$
7:audio/basic: ULAW: snd,au:$
8:audio/x-basic: ULAW: snd,au:$
9:audio/x-pn-au: ULAW: snd,au:$
10:audio/x-tta: True Audio: tta:$
11:audio/tta: True Audio: tta:$
12:audio/x-mod: SoundTracker/NoiseTracker/ProTracker Module: mod:$
13:audio/mod: SoundTracker/NoiseTracker/ProTracker Module: mod:$
14:audio/it: ImpulseTracker Module: it:$
15:audio/x-it: ImpulseTracker Module: it:$
16:audio/x-stm: ScreamTracker 2 Module: stm:$
17:audio/x-s3m: ScreamTracker 3 Module: s3m:$
18:audio/s3m: ScreamTracker 3 Module: s3m:$
19:application/playerpro: 669 Tracker Module: 669:$
20:application/adrift: ADRIFT Module File: amf:$
21:audio/med: Amiga MED/OctaMED Tracker Module Sound File: med:$
22:audio/x-amf: ADRIFT Module File: amf:$
23:audio/x-xm: FastTracker II Audio: xm:$
24:audio/xm: FastTracker II Audio: xm:$
25:audio/x-aiff: AIFF audio: aif, aiff:$
26:audio/aiff: AIFF audio: aif, aiff:$
27:audio/x-pn-aiff: AIFF audio: aif, aiff:$
28:audio/x-flac: FLAC Audio: flac:$
29:audio/flac: FLAC Audio: flac:$
30:video/msvideo: AVI video: avi:$
31:video/x-msvideo: AVI video: avi:$
32:video/mkv: matroska: mkv:$
33:video/x-matroska: matroska: mkv:$
34:video/webm: WebM: wbm,webm:$
35:video/x-flic: Autodesk FLIC files: fli,flc:$
36:video/quicktime: Quicktime animation: mov,qt:$
37:video/x-quicktime: Quicktime animation: mov,qt:$
38:audio/x-m4a: MPEG-4 audio: m4a,m4b:$
39:application/x-quicktimeplayer: Quicktime list: qtl:$
40:video/mp4: MPEG-4 video: mp4,mpg4:$
41:audio/mp4: MPEG-4 audio: mp4,mpg4:$
42:audio/x-8svx: IFF-8SVX Audio: 8svx:$
43:audio/8svx: IFF-8SVX Audio: 8svx:$
44:audio/x-16sv: IFF-16SV Audio: 16sv:$
45:audio/168sv: IFF-16SV Audio: 16sv:$
46:image/x-ilbm: IFF-ILBM Picture: ilbm:$
47:image/ilbm: IFF-ILBM Picture: ilbm:$
48:video/x-anim: IFF-ANIM Video: anim:$
49:video/anim: IFF-ANIM Video: anim:$
50:video/x-flv: Flash video: flv:$
51:video/flv: Flash video: flv:$
52:application/x-flash-video: Flash video: flv:$
53:image/png: PNG image: png:$
54:image/x-png: PNG image: png:$
55:video/mng: MNG animation: mng:$
56:video/x-mng: MNG animation: mng:$
57:application/ogg: Ogg Stream: ogx:$
58:application/x-ogg: Ogg Stream: ogx:$
59:application/x-ogm: Ogg Stream: ogx:$
60:application/x-ogm-audio: Ogg Audio: oga:$
61:application/x-ogm-video: Ogg Video: ogv:$
62:audio/ogg: Ogg Audio: oga:$
63:audio/x-ogg: Ogg Audio: oga:$
64:video/ogg: Ogg Video: ogv:$
65:video/x-ogg: Ogg Video: ogv:$
66:video/x-ms-asf: ASF stream: asf:$
67:video/x-ms-wmv: Windows Media Video: wmv:$
68:audio/x-ms-wma: Windows Media Audio: wma:$
69:application/vnd.ms-asf: ASF stream: asf:$
70:application/x-mplayer2: mplayer2: asf,asx,asp:$
71:video/x-ms-asf-plugin: mms animation: asf,asx,asp:$
72:video/x-ms-wvx: wmv metafile: wvx:$
73:video/x-ms-wax: wma metafile: wva:$
74:audio/x-pn-realaudio: Real Media file: ra, rm, ram:$
75:audio/x-pn-realaudio-plugin: Real Media plugin file: rpm:$
76:audio/x-real-audio: Real Media file: ra, rm, ram:$
77:application/vnd.rn-realmedia: Real Media file: ra, rm, ram:$
78:audio/ac3: Dolby Digital audio: ac3:$
79:audio/x-wav: WAV audio: wav:$
80:audio/wav: WAV audio: wav:$
81:audio/x-pn-wav: WAV audio: wav:$
82:audio/x-pn-windows-acm: WAV audio: wav:$
83:audio/musepack: Musepack audio: mpc, mp+, mpp:$
84:audio/x-musepack: Musepack audio: mpc, mp+, mpp:$
85:audio/x-flac: FLAC Audio: flac:$
86:audio/flac: FLAC Audio: flac:$
87:audio/x-wavpack: WavPack audioaudio/x-scpls: pls: Winamp playlist: wv,wvp:$
88:application/smil: SMIL playlist: smi, smil:$
89:application/xspf+xml: XSPF playlist: xspf:$
90:application/x-xine-plugin: Xine plugin: :$
libnpjp2.so:$
/opt/java/64/jre1.6.0_25/lib/amd64/libnpjp2.so:$
:$
1302771481000:1:5:$
The next generation <a href="http://java.sun.com">Java</a> plug-in for Mozilla browsers.:$
Java(TM) Plug-in 1.6.0_25:$
34
0:application/x-java-vm:Java&#8482; Plug-in::$
1:application/x-java-applet:Java&#8482; Plug-in Applet::$
2:application/x-java-applet;version=1.1:Java&#8482; Plug-in::$
3:application/x-java-applet;version=1.1.1:Java&#8482; Plug-in::$
4:application/x-java-applet;version=1.1.2:Java&#8482; Plug-in::$
5:application/x-java-applet;version=1.1.3:Java&#8482; Plug-in::$
6:application/x-java-applet;version=1.2:Java&#8482; Plug-in::$
7:application/x-java-applet;version=1.2.1:Java&#8482; Plug-in::$
8:application/x-java-applet;version=1.2.2:Java&#8482; Plug-in::$
9:application/x-java-applet;version=1.3:Java&#8482; Plug-in::$
10:application/x-java-applet;version=1.3.1:Java&#8482; Plug-in::$
11:application/x-java-applet;version=1.4:Java&#8482; Plug-in::$
12:application/x-java-applet;version=1.4.1:Java&#8482; Plug-in::$
13:application/x-java-applet;version=1.4.2:Java&#8482; Plug-in::$
14:application/x-java-applet;version=1.5:Java&#8482; Plug-in::$
15:application/x-java-applet;version=1.6:Java&#8482; Plug-in::$
16:application/x-java-applet;jpi-version=1.6.0_25:Java&#8482; Plug-in::$
17:application/x-java-bean:Java&#8482; Plug-in JavaBeans::$
18:application/x-java-bean;version=1.1:Java&#8482; Plug-in::$
19:application/x-java-bean;version=1.1.1:Java&#8482; Plug-in::$
20:application/x-java-bean;version=1.1.2:Java&#8482; Plug-in::$
21:application/x-java-bean;version=1.1.3:Java&#8482; Plug-in::$
22:application/x-java-bean;version=1.2:Java&#8482; Plug-in::$
23:application/x-java-bean;version=1.2.1:Java&#8482; Plug-in::$
24:application/x-java-bean;version=1.2.2:Java&#8482; Plug-in::$
25:application/x-java-bean;version=1.3:Java&#8482; Plug-in::$
26:application/x-java-bean;version=1.3.1:Java&#8482; Plug-in::$
27:application/x-java-bean;version=1.4:Java&#8482; Plug-in::$
28:application/x-java-bean;version=1.4.1:Java&#8482; Plug-in::$
29:application/x-java-bean;version=1.4.2:Java&#8482; Plug-in::$
30:application/x-java-bean;version=1.5:Java&#8482; Plug-in::$
31:application/x-java-bean;version=1.6:Java&#8482; Plug-in::$
32:application/x-java-bean;jpi-version=1.6.0_25:Java&#8482; Plug-in::$
33:application/x-java-vm-npruntime:::$
libmoonloaderxpi.so:$
/home/petey/.mozilla/firefox/apzq6gn6.Default/extensions/moonlight@novell.com/plugins/libmoonloaderxpi.so:$
:$
1298584176000:1:5:$
4.0.51204.0:$
Silverlight Plug-In:$
2
0:application/x-silverlight:Novell Moonlight:xaml:$
1:application/x-silverlight-2:Novell Moonlight::$

[INVALID]
Generated File. Do not edit.

[HEADER]
Version:0.15:$
Arch:x86_64-gcc3:$

[PLUGINS]
libnpgtpo3dautoplugin.so:$
/opt/google/talkplugin/libnpgtpo3dautoplugin.so:$
:$
1303321917000:1:5:$
Google Talk Plugin Video Accelerator version:0.1.43.7:$
Google Talk Plugin Video Accelerator:$
1
0:application/vnd.gtpo3d.auto:O3D MIME::$
libnpgoogletalk64.so:$
/opt/google/talkplugin/libnpgoogletalk64.so:$
:$
1303321917000:1:5:$
Version: 2.0.6.0:$
Google Talk Plugin:$
1
0:application/googletalk:Google Talk Plugin:googletalk:$
librhythmbox-itms-detection-plugin.so:$
/usr/lib/mozilla/plugins/librhythmbox-itms-detection-plugin.so:$
:$
1301673552000:1:5:$
This plug-in detects the presence of iTunes when opening iTunes Store URLs in a web page with Firefox.:$
iTunes Application Detector:$
1
0:application/itunes-plugin:::$
nsdejavu.so:$
/usr/lib/netscape/plugins-libc6/nsdejavu.so:$
:$
1301006797000:1:5:$
This is the <a href="http://djvu.sourceforge.net">DjVuLibre-3.5.23</a> version of the DjVu plugin.<br>See <a href="http://djvu.sourceforge.net">DjVuLibre</a>.:$
DjVuLibre-3.5.23:$
6
0:image/x-djvu:DjVu File:djvu,djv:$
1:image/x.djvu:DjVu File::$
2:image/djvu:DjVu File::$
3:image/x-dejavu:DjVu File::$
4:image/x-iw44:DjVu File::$
5:image/vnd.djvu:DjVu File::$
libtotem-narrowspace-plugin.so:$
/usr/lib/mozilla/plugins/libtotem-narrowspace-plugin.so:$
:$
1300218622000:1:5:$
The <a href="http://www.gnome.org/projects/totem/">Totem</a> 2.32.0 plugin handles video and audio streams.:$
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
1300218622000:1:5:$
DivX Web Player version 1.4.0.233:$
DivXÂ® Web Player:$
1
0:video/divx:AVI video:divx:$
libtotem-gmp-plugin.so:$
/usr/lib/mozilla/plugins/libtotem-gmp-plugin.so:$
:$
1300218622000:1:5:$
The <a href="http://www.gnome.org/projects/totem/">Totem</a> 2.32.0 plugin handles video and audio streams.:$
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
1300218622000:1:5:$
The <a href="http://www.gnome.org/projects/totem/">Totem</a> 2.32.0 plugin handles video and audio streams.:$
VLC Multimedia Plugin (compatible Totem 2.32.0):$
20
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
18:video/webm:WebM video:webm:$
19:application/x-totem-plugin:Totem Multimedia plugin::$
xineplugin.so:$
/usr/lib/xine-plugin/xineplugin.so:$
:$
1298398613000:1:5:$
Xine Plugin version 1.0.2, (c) <a href=http://www.xinehq.de>The Xine Project</a>.<br>Windows Media Player / RealPlayer / QuickTime compatible.:$
Xine Plugin:$
91
0:application/annodex: Annodex media: anx:$
1:application/x-annodex: Annodex media: anx:$
2:audio/annodex: Annodex audio: axa:$
3:audio/x-annodex: Annodex audio: axa:$
4:video/annodex: Annodex video: axv:$
5:video/x-annodex: Annodex video: axv:$
6:audio/x-aiff: AIFF audio: aif, aiff:$
7:audio/aiff: AIFF audio: aif, aiff:$
8:audio/x-pn-aiff: AIFF audio: aif, aiff:$
9:audio/x-flac: FLAC Audio: flac:$
10:audio/flac: FLAC Audio: flac:$
11:audio/x-realaudio: RealAudio File: ra:$
12:audio/basic: ULAW: snd,au:$
13:audio/x-basic: ULAW: snd,au:$
14:audio/x-pn-au: ULAW: snd,au:$
15:audio/x-tta: True Audio: tta:$
16:audio/tta: True Audio: tta:$
17:audio/x-mod: SoundTracker/NoiseTracker/ProTracker Module: mod:$
18:audio/mod: SoundTracker/NoiseTracker/ProTracker Module: mod:$
19:audio/it: ImpulseTracker Module: it:$
20:audio/x-it: ImpulseTracker Module: it:$
21:audio/x-stm: ScreamTracker 2 Module: stm:$
22:audio/x-s3m: ScreamTracker 3 Module: s3m:$
23:audio/s3m: ScreamTracker 3 Module: s3m:$
24:application/playerpro: 669 Tracker Module: 669:$
25:application/adrift: ADRIFT Module File: amf:$
26:audio/med: Amiga MED/OctaMED Tracker Module Sound File: med:$
27:audio/x-amf: ADRIFT Module File: amf:$
28:audio/x-xm: FastTracker II Audio: xm:$
29:audio/xm: FastTracker II Audio: xm:$
30:video/msvideo: AVI video: avi:$
31:video/x-msvideo: AVI video: avi:$
32:video/mkv: matroska: mkv:$
33:video/x-matroska: matroska: mkv:$
34:video/webm: WebM: wbm,webm:$
35:video/x-flic: Autodesk FLIC files: fli,flc:$
36:video/quicktime: Quicktime animation: mov,qt:$
37:video/x-quicktime: Quicktime animation: mov,qt:$
38:audio/x-m4a: MPEG-4 audio: m4a,m4b:$
39:application/x-quicktimeplayer: Quicktime list: qtl:$
40:video/mp4: MPEG-4 video: mp4,mpg4:$
41:audio/mp4: MPEG-4 audio: mp4,mpg4:$
42:audio/x-8svx: IFF-8SVX Audio: 8svx:$
43:audio/8svx: IFF-8SVX Audio: 8svx:$
44:audio/x-16sv: IFF-16SV Audio: 16sv:$
45:audio/168sv: IFF-16SV Audio: 16sv:$
46:image/x-ilbm: IFF-ILBM Picture: ilbm:$
47:image/ilbm: IFF-ILBM Picture: ilbm:$
48:video/x-anim: IFF-ANIM Video: anim:$
49:video/anim: IFF-ANIM Video: anim:$
50:video/x-flv: Flash video: flv:$
51:video/flv: Flash video: flv:$
52:application/x-flash-video: Flash video: flv:$
53:image/png: PNG image: png:$
54:image/x-png: PNG image: png:$
55:video/mng: MNG animation: mng:$
56:video/x-mng: MNG animation: mng:$
57:application/ogg: Ogg Stream: ogx:$
58:application/x-ogg: Ogg Stream: ogx:$
59:application/x-ogm: Ogg Stream: ogx:$
60:application/x-ogm-audio: Ogg Audio: oga:$
61:application/x-ogm-video: Ogg Video: ogv:$
62:audio/ogg: Ogg Audio: oga:$
63:audio/x-ogg: Ogg Audio: oga:$
64:video/ogg: Ogg Video: ogv:$
65:video/x-ogg: Ogg Video: ogv:$
66:video/x-ms-asf: ASF stream: asf:$
67:video/x-ms-wmv: Windows Media Video: wmv:$
68:audio/x-ms-wma: Windows Media Audio: wma:$
69:application/vnd.ms-asf: ASF stream: asf:$
70:application/x-mplayer2: mplayer2: asf,asx,asp:$
71:video/x-ms-asf-plugin: mms animation: asf,asx,asp:$
72:video/x-ms-wvx: wmv metafile: wvx:$
73:video/x-ms-wax: wma metafile: wva:$
74:audio/x-pn-realaudio: Real Media file: ra, rm, ram:$
75:audio/x-pn-realaudio-plugin: Real Media plugin file: rpm:$
76:audio/x-real-audio: Real Media file: ra, rm, ram:$
77:application/vnd.rn-realmedia: Real Media file: ra, rm, ram:$
78:audio/ac3: Dolby Digital audio: ac3:$
79:audio/x-wav: WAV audio: wav:$
80:audio/wav: WAV audio: wav:$
81:audio/x-pn-wav: WAV audio: wav:$
82:audio/x-pn-windows-acm: WAV audio: wav:$
83:audio/musepack: Musepack audio: mpc, mp+, mpp:$
84:audio/x-musepack: Musepack audio: mpc, mp+, mpp:$
85:audio/x-flac: FLAC Audio: flac:$
86:audio/flac: FLAC Audio: flac:$
87:audio/x-wavpack: WavPack audioaudio/x-scpls: pls: Winamp playlist: wv,wvp:$
88:application/smil: SMIL playlist: smi, smil:$
89:application/xspf+xml: XSPF playlist: xspf:$
90:application/x-xine-plugin: Xine plugin: :$
libflashplayer.so:$
/usr/lib/flashplugin-installer/libflashplayer.so:$
:$
1305514526000:1:1:$
Shockwave Flash 10.3 d162:$
Shockwave Flash:$
2
0:application/x-shockwave-flash:Shockwave Flash:swf:$
1:application/futuresplash:FutureSplash Player:spl:$
libnpjp2.so:$
/opt/java/64/jre1.6.0_25/lib/amd64/libnpjp2.so:$
:$
1302771481000:1:5:$
The next generation <a href="http://java.sun.com">Java</a> plug-in for Mozilla browsers.:$
Java(TM) Plug-in 1.6.0_25:$
34
0:application/x-java-vm:Java&#8482; Plug-in::$
1:application/x-java-applet:Java&#8482; Plug-in Applet::$
2:application/x-java-applet;version=1.1:Java&#8482; Plug-in::$
3:application/x-java-applet;version=1.1.1:Java&#8482; Plug-in::$
4:application/x-java-applet;version=1.1.2:Java&#8482; Plug-in::$
5:application/x-java-applet;version=1.1.3:Java&#8482; Plug-in::$
6:application/x-java-applet;version=1.2:Java&#8482; Plug-in::$
7:application/x-java-applet;version=1.2.1:Java&#8482; Plug-in::$
8:application/x-java-applet;version=1.2.2:Java&#8482; Plug-in::$
9:application/x-java-applet;version=1.3:Java&#8482; Plug-in::$
10:application/x-java-applet;version=1.3.1:Java&#8482; Plug-in::$
11:application/x-java-applet;version=1.4:Java&#8482; Plug-in::$
12:application/x-java-applet;version=1.4.1:Java&#8482; Plug-in::$
13:application/x-java-applet;version=1.4.2:Java&#8482; Plug-in::$
14:application/x-java-applet;version=1.5:Java&#8482; Plug-in::$
15:application/x-java-applet;version=1.6:Java&#8482; Plug-in::$
16:application/x-java-applet;jpi-version=1.6.0_25:Java&#8482; Plug-in::$
17:application/x-java-bean:Java&#8482; Plug-in JavaBeans::$
18:application/x-java-bean;version=1.1:Java&#8482; Plug-in::$
19:application/x-java-bean;version=1.1.1:Java&#8482; Plug-in::$
20:application/x-java-bean;version=1.1.2:Java&#8482; Plug-in::$
21:application/x-java-bean;version=1.1.3:Java&#8482; Plug-in::$
22:application/x-java-bean;version=1.2:Java&#8482; Plug-in::$
23:application/x-java-bean;version=1.2.1:Java&#8482; Plug-in::$
24:application/x-java-bean;version=1.2.2:Java&#8482; Plug-in::$
25:application/x-java-bean;version=1.3:Java&#8482; Plug-in::$
26:application/x-java-bean;version=1.3.1:Java&#8482; Plug-in::$
27:application/x-java-bean;version=1.4:Java&#8482; Plug-in::$
28:application/x-java-bean;version=1.4.1:Java&#8482; Plug-in::$
29:application/x-java-bean;version=1.4.2:Java&#8482; Plug-in::$
30:application/x-java-bean;version=1.5:Java&#8482; Plug-in::$
31:application/x-java-bean;version=1.6:Java&#8482; Plug-in::$
32:application/x-java-bean;jpi-version=1.6.0_25:Java&#8482; Plug-in::$
33:application/x-java-vm-npruntime:::$
libmoonloaderxpi.so:$
/home/petey/.mozilla/firefox/hgr7824a.emusic/extensions/moonlight@novell.com/plugins/libmoonloaderxpi.so:$
:$
1302543314000:1:5:$
4.0.51204.0:$
Silverlight Plug-In:$
2
0:application/x-silverlight:Novell Moonlight:xaml:$
1:application/x-silverlight-2:Novell Moonlight::$
libflashplayer.so:$
/usr/lib/mozilla/plugins/libflashplayer.so:$
:$
0:1:13:$
Shockwave Flash 10.2 d161:$
Shockwave Flash:$
2
0:application/x-shockwave-flash:Shockwave Flash:swf:$
1:application/futuresplash:FutureSplash Player:spl:$

[INVALID]
Generated File. Do not edit.

[HEADER]
Version:0.15:$
Arch:x86_64-gcc3:$

[PLUGINS]
libflashplayer.so:$
/usr/lib/flashplugin-installer/libflashplayer.so:$
:$
1305514526000:1:1:$
Shockwave Flash 10.3 d162:$
Shockwave Flash:$
2
0:application/x-shockwave-flash:Shockwave Flash:swf:$
1:application/futuresplash:FutureSplash Player:spl:$
libnpgtpo3dautoplugin.so:$
/opt/google/talkplugin/libnpgtpo3dautoplugin.so:$
:$
1303321917000:1:5:$
Google Talk Plugin Video Accelerator version:0.1.43.7:$
Google Talk Plugin Video Accelerator:$
1
0:application/vnd.gtpo3d.auto:O3D MIME::$
libnpgoogletalk64.so:$
/opt/google/talkplugin/libnpgoogletalk64.so:$
:$
1303321917000:1:5:$
Version: 2.0.6.0:$
Google Talk Plugin:$
1
0:application/googletalk:Google Talk Plugin:googletalk:$
librhythmbox-itms-detection-plugin.so:$
/usr/lib/mozilla/plugins/librhythmbox-itms-detection-plugin.so:$
:$
1301673552000:1:5:$
This plug-in detects the presence of iTunes when opening iTunes Store URLs in a web page with Firefox.:$
iTunes Application Detector:$
1
0:application/itunes-plugin:::$
nsdejavu.so:$
/usr/lib/netscape/plugins-libc6/nsdejavu.so:$
:$
1301006797000:1:5:$
This is the <a href="http://djvu.sourceforge.net">DjVuLibre-3.5.23</a> version of the DjVu plugin.<br>See <a href="http://djvu.sourceforge.net">DjVuLibre</a>.:$
DjVuLibre-3.5.23:$
6
0:image/x-djvu:DjVu File:djvu,djv:$
1:image/x.djvu:DjVu File::$
2:image/djvu:DjVu File::$
3:image/x-dejavu:DjVu File::$
4:image/x-iw44:DjVu File::$
5:image/vnd.djvu:DjVu File::$
libtotem-narrowspace-plugin.so:$
/usr/lib/mozilla/plugins/libtotem-narrowspace-plugin.so:$
:$
1300218622000:1:5:$
The <a href="http://www.gnome.org/projects/totem/">Totem</a> 2.32.0 plugin handles video and audio streams.:$
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
1300218622000:1:5:$
DivX Web Player version 1.4.0.233:$
DivXÂ® Web Player:$
1
0:video/divx:AVI video:divx:$
libtotem-gmp-plugin.so:$
/usr/lib/mozilla/plugins/libtotem-gmp-plugin.so:$
:$
1300218622000:1:5:$
The <a href="http://www.gnome.org/projects/totem/">Totem</a> 2.32.0 plugin handles video and audio streams.:$
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
1300218622000:1:5:$
The <a href="http://www.gnome.org/projects/totem/">Totem</a> 2.32.0 plugin handles video and audio streams.:$
VLC Multimedia Plugin (compatible Totem 2.32.0):$
20
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
18:video/webm:WebM video:webm:$
19:application/x-totem-plugin:Totem Multimedia plugin::$
xineplugin.so:$
/usr/lib/xine-plugin/xineplugin.so:$
:$
1298398613000:1:5:$
Xine Plugin version 1.0.2, (c) <a href=http://www.xinehq.de>The Xine Project</a>.<br>Windows Media Player / RealPlayer / QuickTime compatible.:$
Xine Plugin:$
91
0:application/annodex: Annodex media: anx:$
1:application/x-annodex: Annodex media: anx:$
2:audio/annodex: Annodex audio: axa:$
3:audio/x-annodex: Annodex audio: axa:$
4:video/annodex: Annodex video: axv:$
5:video/x-annodex: Annodex video: axv:$
6:audio/x-mod: SoundTracker/NoiseTracker/ProTracker Module: mod:$
7:audio/mod: SoundTracker/NoiseTracker/ProTracker Module: mod:$
8:audio/it: ImpulseTracker Module: it:$
9:audio/x-it: ImpulseTracker Module: it:$
10:audio/x-stm: ScreamTracker 2 Module: stm:$
11:audio/x-s3m: ScreamTracker 3 Module: s3m:$
12:audio/s3m: ScreamTracker 3 Module: s3m:$
13:application/playerpro: 669 Tracker Module: 669:$
14:application/adrift: ADRIFT Module File: amf:$
15:audio/med: Amiga MED/OctaMED Tracker Module Sound File: med:$
16:audio/x-amf: ADRIFT Module File: amf:$
17:audio/x-xm: FastTracker II Audio: xm:$
18:audio/xm: FastTracker II Audio: xm:$
19:audio/x-aiff: AIFF audio: aif, aiff:$
20:audio/aiff: AIFF audio: aif, aiff:$
21:audio/x-pn-aiff: AIFF audio: aif, aiff:$
22:audio/x-flac: FLAC Audio: flac:$
23:audio/flac: FLAC Audio: flac:$
24:audio/x-realaudio: RealAudio File: ra:$
25:audio/basic: ULAW: snd,au:$
26:audio/x-basic: ULAW: snd,au:$
27:audio/x-pn-au: ULAW: snd,au:$
28:audio/x-tta: True Audio: tta:$
29:audio/tta: True Audio: tta:$
30:video/msvideo: AVI video: avi:$
31:video/x-msvideo: AVI video: avi:$
32:video/mkv: matroska: mkv:$
33:video/x-matroska: matroska: mkv:$
34:video/webm: WebM: wbm,webm:$
35:video/x-flic: Autodesk FLIC files: fli,flc:$
36:video/quicktime: Quicktime animation: mov,qt:$
37:video/x-quicktime: Quicktime animation: mov,qt:$
38:audio/x-m4a: MPEG-4 audio: m4a,m4b:$
39:application/x-quicktimeplayer: Quicktime list: qtl:$
40:video/mp4: MPEG-4 video: mp4,mpg4:$
41:audio/mp4: MPEG-4 audio: mp4,mpg4:$
42:audio/x-8svx: IFF-8SVX Audio: 8svx:$
43:audio/8svx: IFF-8SVX Audio: 8svx:$
44:audio/x-16sv: IFF-16SV Audio: 16sv:$
45:audio/168sv: IFF-16SV Audio: 16sv:$
46:image/x-ilbm: IFF-ILBM Picture: ilbm:$
47:image/ilbm: IFF-ILBM Picture: ilbm:$
48:video/x-anim: IFF-ANIM Video: anim:$
49:video/anim: IFF-ANIM Video: anim:$
50:video/x-flv: Flash video: flv:$
51:video/flv: Flash video: flv:$
52:application/x-flash-video: Flash video: flv:$
53:image/png: PNG image: png:$
54:image/x-png: PNG image: png:$
55:video/mng: MNG animation: mng:$
56:video/x-mng: MNG animation: mng:$
57:application/ogg: Ogg Stream: ogx:$
58:application/x-ogg: Ogg Stream: ogx:$
59:application/x-ogm: Ogg Stream: ogx:$
60:application/x-ogm-audio: Ogg Audio: oga:$
61:application/x-ogm-video: Ogg Video: ogv:$
62:audio/ogg: Ogg Audio: oga:$
63:audio/x-ogg: Ogg Audio: oga:$
64:video/ogg: Ogg Video: ogv:$
65:video/x-ogg: Ogg Video: ogv:$
66:video/x-ms-asf: ASF stream: asf:$
67:video/x-ms-wmv: Windows Media Video: wmv:$
68:audio/x-ms-wma: Windows Media Audio: wma:$
69:application/vnd.ms-asf: ASF stream: asf:$
70:application/x-mplayer2: mplayer2: asf,asx,asp:$
71:video/x-ms-asf-plugin: mms animation: asf,asx,asp:$
72:video/x-ms-wvx: wmv metafile: wvx:$
73:video/x-ms-wax: wma metafile: wva:$
74:audio/x-pn-realaudio: Real Media file: ra, rm, ram:$
75:audio/x-pn-realaudio-plugin: Real Media plugin file: rpm:$
76:audio/x-real-audio: Real Media file: ra, rm, ram:$
77:application/vnd.rn-realmedia: Real Media file: ra, rm, ram:$
78:audio/ac3: Dolby Digital audio: ac3:$
79:audio/x-wav: WAV audio: wav:$
80:audio/wav: WAV audio: wav:$
81:audio/x-pn-wav: WAV audio: wav:$
82:audio/x-pn-windows-acm: WAV audio: wav:$
83:audio/musepack: Musepack audio: mpc, mp+, mpp:$
84:audio/x-musepack: Musepack audio: mpc, mp+, mpp:$
85:audio/x-flac: FLAC Audio: flac:$
86:audio/flac: FLAC Audio: flac:$
87:audio/x-wavpack: WavPack audioaudio/x-scpls: pls: Winamp playlist: wv,wvp:$
88:application/smil: SMIL playlist: smi, smil:$
89:application/xspf+xml: XSPF playlist: xspf:$
90:application/x-xine-plugin: Xine plugin: :$
libnpjp2.so:$
/opt/java/64/jre1.6.0_25/lib/amd64/libnpjp2.so:$
:$
1302771481000:1:5:$
The next generation <a href="http://java.sun.com">Java</a> plug-in for Mozilla browsers.:$
Java(TM) Plug-in 1.6.0_25:$
34
0:application/x-java-vm:Java&#8482; Plug-in::$
1:application/x-java-applet:Java&#8482; Plug-in Applet::$
2:application/x-java-applet;version=1.1:Java&#8482; Plug-in::$
3:application/x-java-applet;version=1.1.1:Java&#8482; Plug-in::$
4:application/x-java-applet;version=1.1.2:Java&#8482; Plug-in::$
5:application/x-java-applet;version=1.1.3:Java&#8482; Plug-in::$
6:application/x-java-applet;version=1.2:Java&#8482; Plug-in::$
7:application/x-java-applet;version=1.2.1:Java&#8482; Plug-in::$
8:application/x-java-applet;version=1.2.2:Java&#8482; Plug-in::$
9:application/x-java-applet;version=1.3:Java&#8482; Plug-in::$
10:application/x-java-applet;version=1.3.1:Java&#8482; Plug-in::$
11:application/x-java-applet;version=1.4:Java&#8482; Plug-in::$
12:application/x-java-applet;version=1.4.1:Java&#8482; Plug-in::$
13:application/x-java-applet;version=1.4.2:Java&#8482; Plug-in::$
14:application/x-java-applet;version=1.5:Java&#8482; Plug-in::$
15:application/x-java-applet;version=1.6:Java&#8482; Plug-in::$
16:application/x-java-applet;jpi-version=1.6.0_25:Java&#8482; Plug-in::$
17:application/x-java-bean:Java&#8482; Plug-in JavaBeans::$
18:application/x-java-bean;version=1.1:Java&#8482; Plug-in::$
19:application/x-java-bean;version=1.1.1:Java&#8482; Plug-in::$
20:application/x-java-bean;version=1.1.2:Java&#8482; Plug-in::$
21:application/x-java-bean;version=1.1.3:Java&#8482; Plug-in::$
22:application/x-java-bean;version=1.2:Java&#8482; Plug-in::$
23:application/x-java-bean;version=1.2.1:Java&#8482; Plug-in::$
24:application/x-java-bean;version=1.2.2:Java&#8482; Plug-in::$
25:application/x-java-bean;version=1.3:Java&#8482; Plug-in::$
26:application/x-java-bean;version=1.3.1:Java&#8482; Plug-in::$
27:application/x-java-bean;version=1.4:Java&#8482; Plug-in::$
28:application/x-java-bean;version=1.4.1:Java&#8482; Plug-in::$
29:application/x-java-bean;version=1.4.2:Java&#8482; Plug-in::$
30:application/x-java-bean;version=1.5:Java&#8482; Plug-in::$
31:application/x-java-bean;version=1.6:Java&#8482; Plug-in::$
32:application/x-java-bean;jpi-version=1.6.0_25:Java&#8482; Plug-in::$
33:application/x-java-vm-npruntime:::$
libmoonloaderxpi.so:$
/home/petey/.mozilla/firefox/t3n73r7b.Bank/extensions/moonlight@novell.com/plugins/libmoonloaderxpi.so:$
:$
1302543314000:1:5:$
4.0.51204.0:$
Silverlight Plug-In:$
2
0:application/x-silverlight:Novell Moonlight:xaml:$
1:application/x-silverlight-2:Novell Moonlight::$
libflashplayer.so:$
/usr/lib/mozilla/plugins/libflashplayer.so:$
:$
0:1:13:$
Shockwave Flash 10.2 d161:$
Shockwave Flash:$
2
0:application/x-shockwave-flash:Shockwave Flash:swf:$
1:application/futuresplash:FutureSplash Player:spl:$

[INVALID]
/home/petey/.mozilla/plugins/libflashplayer.so:$
0:$
[/HTML]


The files /home/petey/libflashplayer.so and /home/petey/.mozilla/plugins/libflashplayer.so need to be deleted, but the command I gave you should have done that. Try to delete them manually. Also there are several plugins in the user Trash and the root trash. Please clean up your trashes.

After that, run the wizard again, then paste a new report.

Sorry for asking this so many times, but for some reason things are not being deleted as expected, even with direct commands to do that.

---

### Post by bep7987 on 2011-05-29
I don't know why these files are showing up in the report.  

I ran gksudo nautilus and entered the paths but could not find the files.  I searched for them too, but could not find them.  I manually deleted all the files in the /home/petey/.local/share/Trash/ folder. 

Using Synaptic Package Manager, I completely removed/uninstalled Firefox.

I deleted the profiles and reinstalled Firefox.

Created a new profile and installed Flash-Aid.

I currently have the old version of flash installed.
    File: /usr/lib/mozilla/plugins/libflashplayer.so
    Version: Shockwave Flash 10.3 d162

The only extensions installed are: 
[INDENT]Flash-Aid 2.1.1, 
Global Menu Bar integration 1.0.3 and 
Ubuntu Firefox Modifications 0.9.[/INDENT]

Plugins installed:

[INDENT]Shockwave Flash 10.3 d162 	

Totem 2.32.0 plugin 

Google Talk Plugin Video Accelerator version:0.1.43.7 	

Google Talk Plugin
Version: 2.0.6.0 	

DjVuLibre-3.5.23

Xine Plugin version 1.0.2, (c) The Xine Project.

iTunes Application Detector[/INDENT]

---

### Post by bep7987 on 2011-05-29
I corrected the path to the flash plugin in the ~/.huludesktop file and huludesktop works again except the picture is extremely jerky in full-screen mode, less so if I watch in almost full-screen mode.

---

### Post by lovinglinux on 2011-05-30
You have the latest beta 64bit version of flash now.

About the jerkiness, please watch if the CPU usage is increasing too much while playing the video in almost full screen.

Unfortunately, since I don't live in US I can't get Hulu desktop to test it.

---

### Post by bep7987 on 2011-05-30
Ok. Thank you for your help.

From a security standpoint, should I be concerned that the latest 64bit version of flash is out-of-date?

---

### Post by lovinglinux on 2011-05-30
> **bep7987 said:**
> Ok. Thank you for your help.

From a security standpoint, should I be concerned that the latest 64bit version of flash is out-of-date?

Well, if you follow Adobe security announcements, you will notice that virtually any version they make have a critical security vulnerability. So, from a security standpoint, you shouldn't even be using flash :-)

Unfortunately, the version you are using is the last one released by Adobe and they haven't changed it since last November.

If you want to be secure, you could use AppArmor to limit what the mozilla plugin container and firefox can do on your system.

---

### Post by bep7987 on 2011-05-31
Thank you. I use AppArmor already. :)

---

