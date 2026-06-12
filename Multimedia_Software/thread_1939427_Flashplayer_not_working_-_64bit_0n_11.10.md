---
title: "Flashplayer not working - 64bit 0n 11.10"
date: 2012-03-11
forum: Multimedia Software
---

### Post by bwallum on 2012-03-11
Hi

My flash player stopped working towards the end of February. I've waited for an update to fix it, no luck.

What is the best way to get 64bit flashplugin (on Firefox) running again, please?

Thanks

---

### Post by winh8r on 2012-03-11
You can try clicking on the "help with flash" link in my sig and installing Flash Aid, then run the wizard and let it sort out any conflicts.

Hope this helps you.

---

### Post by bwallum on 2012-03-11
Thanks winh8r, tried the flash-aid fix but it didn't work.

---

### Post by shantiq on 2012-03-12
maybe try this


[ATTACH]214173[/ATTACH]


[SIZE="3"]
**or**[/SIZE]



First, remove old, unnecessary packages.

```
sudo apt-get remove --purge adobe-flashplugin flashplugin* nspluginwrapper
```

Install 32 or 64-bit Flash. Answer "Y" to confirm this operation.

```
sudo apt-get install --reinstall adobe-flashplugin
```

---

### Post by lovinglinux on 2012-03-13
> **shantiq said:**
> maybe try this


[ATTACH]214173[/ATTACH]


[SIZE="3"]
**or**[/SIZE]



First, remove old, unnecessary packages.

```
sudo apt-get remove --purge adobe-flashplugin flashplugin* nspluginwrapper
```

Install 32 or 64-bit Flash. Answer "Y" to confirm this operation.

```
sudo apt-get install --reinstall adobe-flashplugin
```


Flash-Aid does that. It removes installed plugins from several locations and install again, so probably not that issue.


Please click "Help >> Generate Report" in Flash-Aid menu and post here.

---

### Post by eclectica on 2012-03-19
I had the same problem.  Flash-aid extension fixed it for me.

---

### Post by bwallum on 2012-03-26
> Please click "Help >> Generate Report" in Flash-Aid menu and post here.Thanks LovingLinux, sorry about delay, I have been trying to use the report to work it out but without success. Your help would be most welcome. I upgraded to Precise to see if that might help but it remains the same. The red revolving circle appears in flash streams but no content shows.

EDIT
Cracked it...I think. I tried Shantiq's solution but still no joy. After some trial and error I right clicked on a piece of flash media, and chose Global Settings from the menu that appeared. When the Global Settings window opened I chose the Advanced tab and under the Browsing Data and Settings section I left clicked on the Delete All.. button. Flash then worked.

---

### Post by hacker_nk on 2012-03-27
I have the same problem here. I posted a thread already but nobody seemed to care so I will join here. This is my report from FlashAid, I tried everything you mentioned in the above posts.
```

Ubuntu Architecture  Linux marko-Inspiron-N5110 3.0.0-16-generic #29-Ubuntu SMP Tue Feb 14 12:48:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux  Ubuntu Version  DISTRIB_ID=Ubuntu DISTRIB_RELEASE=11.10 DISTRIB_CODENAME=oneiric DISTRIB_DESCRIPTION="Ubuntu 11.10"  Firefox Packages  firefox						install firefox-globalmenu				install firefox-locale-en				install  Firefox binaries  /usr/bin/firefox /usr/bin/firefox: symbolic link to `../lib/firefox-11.0/firefox.sh' /usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory) /opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)  Firefox divertion  /usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)  Sources  oneiric-partner.list opera.list  Flash packages  adobe-flash-properties-gtk			install adobe-flashplugin				install Plugin locations  /home/marko/.mozilla/firefox/xpfj8oo1.default/extensions/flashlight@stephennolan.com.au/archive/11/libflashplayer.so /home/marko/.mozilla/firefox/xpfj8oo1.default/extensions/flashlight@stephennolan.com.au/plugins/libflashplayer.so /usr/lib/adobe-flashplugin/libflashplayer.so /usr/lib/chromium-browser/plugins/libflashplayer.so /usr/lib/firefox-addons/plugins/libflashplayer.so /usr/lib/mozilla/plugins/libflashplayer.so  /usr/lib/firefox/plugins/flashplugin-alternative.so /usr/lib/iceape/plugins/flashplugin-alternative.so /usr/lib/iceweasel/plugins/flashplugin-alternative.so /usr/lib/midbrowser/plugins/flashplugin-alternative.so /usr/lib/mozilla/plugins/flashplugin-alternative.so /usr/lib/xulrunner/plugins/flashplugin-alternative.so /usr/lib/xulrunner-addons/plugins/flashplugin-alternative.so  Flash symlinks   /usr/lib/mozilla/plugins/libflashplayer.so: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, stripped /usr/lib/mozilla/plugins/flashplugin-alternative.so: symbolic link to `/etc/alternatives/mozilla-flashplugin' /etc/alternatives/mozilla-flashplugin: symbolic link to `/usr/lib/adobe-flashplugin/libflashplayer.so' /usr/lib/flashplugin-installer/libflashplayer.so: ERROR: cannot open `/usr/lib/flashplugin-installer/libflashplayer.so' (No such file or directory) /usr/lib/flashplugin-nonfree/libflashplayer.so: ERROR: cannot open `/usr/lib/flashplugin-nonfree/libflashplayer.so' (No such file or directory) /usr/lib/adobe-flashplugin/libflashplayer.so: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, stripped /usr/lib/lightspark/lightspark.so: ERROR: cannot open `/usr/lib/lightspark/lightspark.so' (No such file or directory) /usr/lib/swfdec-mozilla/libswfdecmozilla.so: ERROR: cannot open `/usr/lib/swfdec-mozilla/libswfdecmozilla.so' (No such file or directory) /usr/lib/gnash/libgnashplugin.so: ERROR: cannot open `/usr/lib/gnash/libgnashplugin.so' (No such file or directory) /var/lib/flashplugin-installer/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-installer/npwrapper.libflashplayer.so' (No such file or directory) /var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so' (No such file or directory)  pluginreg.dat  Generated File. Do not edit.  [HEADER] Version:0.15:$ Arch:x86_64-gcc3:$  [PLUGINS] libflashplayer.so:$ /home/marko/.mozilla/firefox/xpfj8oo1.default/extensions/flashlight@stephennolan.com.au/plugins/libflashplayer.so:$ :$ 1332795981000:1:5:$ Shockwave Flash 11.2 r202:$ Shockwave Flash:$ 2 0:application/x-shockwave-flash:Shockwave Flash:swf:$ 1:application/futuresplash:FutureSplash Player:spl:$ libflashplayer.so:$ /usr/lib/adobe-flashplugin/libflashplayer.so:$ :$ 1330400964000:1:1:$ Shockwave Flash 11.1 r102:$ Shockwave Flash:$ 2 0:application/x-shockwave-flash:Shockwave Flash:swf:$ 1:application/futuresplash:FutureSplash Player:spl:$ IcedTeaPlugin.so:$ /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/IcedTeaPlugin.so:$ :$ 1320721707000:1:5:$ The <a href="http://icedtea.classpath.org/wiki/IcedTea-Web">IcedTea-Web Plugin</a> executes Java applets.:$ IcedTea-Web Plugin (using IcedTea-Web 1.1.3 (1.1.3-1ubuntu1.1)):$ 34 0:application/x-java-vm:IcedTea:class,jar:$ 1:application/x-java-applet:IcedTea:class,jar:$ 2:application/x-java-applet;version=1.1:IcedTea:class,jar:$ 3:application/x-java-applet;version=1.1.1:IcedTea:class,jar:$ 4:application/x-java-applet;version=1.1.2:IcedTea:class,jar:$ 5:application/x-java-applet;version=1.1.3:IcedTea:class,jar:$ 6:application/x-java-applet;version=1.2:IcedTea:class,jar:$ 7:application/x-java-applet;version=1.2.1:IcedTea:class,jar:$ 8:application/x-java-applet;version=1.2.2:IcedTea:class,jar:$ 9:application/x-java-applet;version=1.3:IcedTea:class,jar:$ 10:application/x-java-applet;version=1.3.1:IcedTea:class,jar:$ 11:application/x-java-applet;version=1.4:IcedTea:class,jar:$ 12:application/x-java-applet;version=1.4.1:IcedTea:class,jar:$ 13:application/x-java-applet;version=1.4.2:IcedTea:class,jar:$ 14:application/x-java-applet;version=1.5:IcedTea:class,jar:$ 15:application/x-java-applet;version=1.6:IcedTea:class,jar:$ 16:application/x-java-applet;jpi-version=1.6.0_50:IcedTea:class,jar:$ 17:application/x-java-bean:IcedTea:class,jar:$ 18:application/x-java-bean;version=1.1:IcedTea:class,jar:$ 19:application/x-java-bean;version=1.1.1:IcedTea:class,jar:$ 20:application/x-java-bean;version=1.1.2:IcedTea:class,jar:$ 21:application/x-java-bean;version=1.1.3:IcedTea:class,jar:$ 22:application/x-java-bean;version=1.2:IcedTea:class,jar:$ 23:application/x-java-bean;version=1.2.1:IcedTea:class,jar:$ 24:application/x-java-bean;version=1.2.2:IcedTea:class,jar:$ 25:application/x-java-bean;version=1.3:IcedTea:class,jar:$ 26:application/x-java-bean;version=1.3.1:IcedTea:class,jar:$ 27:application/x-java-bean;version=1.4:IcedTea:class,jar:$ 28:application/x-java-bean;version=1.4.1:IcedTea:class,jar:$ 29:application/x-java-bean;version=1.4.2:IcedTea:class,jar:$ 30:application/x-java-bean;version=1.5:IcedTea:class,jar:$ 31:application/x-java-bean;version=1.6:IcedTea:class,jar:$ 32:application/x-java-bean;jpi-version=1.6.0_50:IcedTea:class,jar:$ 33:application/x-java-vm-npruntime:::$ libtotem-cone-plugin.so:$ /usr/lib/mozilla/plugins/libtotem-cone-plugin.so:$ :$ 1318915705000:1:5:$ The <a href="http://www.gnome.org/projects/totem/">Totem</a> 3.0.1 plugin handles video and audio streams.:$ VLC Multimedia Plugin (compatible Totem 3.0.1):$ 21 0:application/x-vlc-plugin:VLC Multimedia Plugin::$ 1:application/vlc:VLC Multimedia Plugin::$ 2:video/x-google-vlc-plugin:VLC Multimedia Plugin::$ 3:application/x-ogg:Ogg multimedia file:ogg:$ 4:application/ogg:Ogg multimedia file:ogg:$ 5:audio/ogg:Ogg Audio:oga:$ 6:audio/x-ogg:Ogg Audio:ogg:$ 7:video/ogg:Ogg Video:ogv:$ 8:video/x-ogg:Ogg Video:ogg:$ 9:application/annodex:Annodex exchange format:anx:$ 10:audio/annodex:Annodex Audio:axa:$ 11:video/annodex:Annodex Video:axv:$ 12:video/mpeg:MPEG video:mpg, mpeg, mpe:$ 13:audio/wav:WAV audio:wav:$ 14:audio/x-wav:WAV audio:wav:$ 15:audio/mpeg:MP3 audio:mp3:$ 16:application/x-nsv-vp3-mp3:NullSoft video:nsv:$ 17:video/flv:Flash video:flv:$ 18:video/webm:WebM video:webm:$ 19:application/x-totem-plugin:Totem Multimedia plugin::$ 20:audio/midi:MIDI audio:mid, midi:$ libtotem-mully-plugin.so:$ /usr/lib/mozilla/plugins/libtotem-mully-plugin.so:$ :$ 1318915705000:1:5:$ DivX Web Player version 1.4.0.233:$ DivXÂ® Web Player:$ 1 0:video/divx:AVI video:divx:$ libtotem-gmp-plugin.so:$ /usr/lib/mozilla/plugins/libtotem-gmp-plugin.so:$ :$ 1318915705000:1:5:$ The <a href="http://www.gnome.org/projects/totem/">Totem</a> 3.0.1 plugin handles video and audio streams.:$ Windows Media Player Plug-in 10 (compatible; Totem):$ 13 0:application/x-mplayer2:AVI video:avi, wma, wmv:$ 1:video/x-ms-asf-plugin:ASF video:asf, wmv:$ 2:video/x-msvideo:AVI video:asf, wmv:$ 3:video/x-ms-asf:ASF video:asf:$ 4:video/x-ms-wmv:Windows Media video:wmv:$ 5:video/x-wmv:Windows Media video:wmv:$ 6:video/x-ms-wvx:Windows Media video:wmv:$ 7:video/x-ms-wm:Windows Media video:wmv:$ 8:video/x-ms-wmp:Windows Media video:wmv:$ 9:application/x-ms-wms:Windows Media video:wms:$ 10:application/x-ms-wmp:Windows Media video:wmp:$ 11:application/asx:Microsoft ASX playlist:asx:$ 12:audio/x-ms-wma:Windows Media audio:wma:$ libtotem-narrowspace-plugin.so:$ /usr/lib/mozilla/plugins/libtotem-narrowspace-plugin.so:$ :$ 1318915705000:1:5:$ The <a href="http://www.gnome.org/projects/totem/">Totem</a> 3.0.1 plugin handles video and audio streams.:$ QuickTime Plug-in 7.6.6:$ 5 0:video/quicktime:QuickTime video:mov:$ 1:video/mp4:MPEG-4 video:mp4:$ 2:image/x-macpaint:MacPaint Bitmap image:pntg:$ 3:image/x-quicktime:Macintosh Quickdraw/PICT drawing:pict, pict1, pict2:$ 4:video/x-m4v:MPEG-4 video:m4v:$ libflashplayer.so:$ /usr/lib/mozilla/plugins/libflashplayer.so:$ :$ 1329954691000:1:12:$ Shockwave Flash 11.2 r202:$ Shockwave Flash:$ 2 0:application/x-shockwave-flash:Shockwave Flash:swf:$ 1:application/futuresplash:FutureSplash Player:spl:$  [INVALID] /home/marko/.mozilla/plugins/nppdf.so:$ 1328016560000:$ 
```

---

### Post by fonsi2099 on 2012-03-27
I have the same problem with Ubuntu 11.10 64B Firefox 11.0. Ultrabook ACER.
Thank you for help.
:guitar:

---

### Post by bwallum on 2012-04-06
For 32 bit flashplayer solution try
#41 [http://ubuntuforums.org/showthread.php?p=11822411](http://ubuntuforums.org/showthread.php?p=11822411)

---

### Post by lovinglinux on 2012-04-06
> **hacker_nk said:**
> I have the same problem here. I posted a thread already but nobody seemed to care so I will join here. This is my report from FlashAid, I tried everything you mentioned in the above posts.
```

Ubuntu Architecture  Linux marko-Inspiron-N5110 3.0.0-16-generic #29-Ubuntu SMP Tue Feb 14 12:48:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux  Ubuntu Version  DISTRIB_ID=Ubuntu DISTRIB_RELEASE=11.10 DISTRIB_CODENAME=oneiric DISTRIB_DESCRIPTION="Ubuntu 11.10"  Firefox Packages  firefox						install firefox-globalmenu				install firefox-locale-en				install  Firefox binaries  /usr/bin/firefox /usr/bin/firefox: symbolic link to `../lib/firefox-11.0/firefox.sh' /usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory) /opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)  Firefox divertion  /usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)  Sources  oneiric-partner.list opera.list  Flash packages  adobe-flash-properties-gtk			install adobe-flashplugin				install Plugin locations  /home/marko/.mozilla/firefox/xpfj8oo1.default/extensions/flashlight@stephennolan.com.au/archive/11/libflashplayer.so /home/marko/.mozilla/firefox/xpfj8oo1.default/extensions/flashlight@stephennolan.com.au/plugins/libflashplayer.so /usr/lib/adobe-flashplugin/libflashplayer.so /usr/lib/chromium-browser/plugins/libflashplayer.so /usr/lib/firefox-addons/plugins/libflashplayer.so /usr/lib/mozilla/plugins/libflashplayer.so  /usr/lib/firefox/plugins/flashplugin-alternative.so /usr/lib/iceape/plugins/flashplugin-alternative.so /usr/lib/iceweasel/plugins/flashplugin-alternative.so /usr/lib/midbrowser/plugins/flashplugin-alternative.so /usr/lib/mozilla/plugins/flashplugin-alternative.so /usr/lib/xulrunner/plugins/flashplugin-alternative.so /usr/lib/xulrunner-addons/plugins/flashplugin-alternative.so  Flash symlinks   /usr/lib/mozilla/plugins/libflashplayer.so: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, stripped /usr/lib/mozilla/plugins/flashplugin-alternative.so: symbolic link to `/etc/alternatives/mozilla-flashplugin' /etc/alternatives/mozilla-flashplugin: symbolic link to `/usr/lib/adobe-flashplugin/libflashplayer.so' /usr/lib/flashplugin-installer/libflashplayer.so: ERROR: cannot open `/usr/lib/flashplugin-installer/libflashplayer.so' (No such file or directory) /usr/lib/flashplugin-nonfree/libflashplayer.so: ERROR: cannot open `/usr/lib/flashplugin-nonfree/libflashplayer.so' (No such file or directory) /usr/lib/adobe-flashplugin/libflashplayer.so: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, stripped /usr/lib/lightspark/lightspark.so: ERROR: cannot open `/usr/lib/lightspark/lightspark.so' (No such file or directory) /usr/lib/swfdec-mozilla/libswfdecmozilla.so: ERROR: cannot open `/usr/lib/swfdec-mozilla/libswfdecmozilla.so' (No such file or directory) /usr/lib/gnash/libgnashplugin.so: ERROR: cannot open `/usr/lib/gnash/libgnashplugin.so' (No such file or directory) /var/lib/flashplugin-installer/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-installer/npwrapper.libflashplayer.so' (No such file or directory) /var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so' (No such file or directory)  pluginreg.dat  Generated File. Do not edit.  [HEADER] Version:0.15:$ Arch:x86_64-gcc3:$  [PLUGINS] libflashplayer.so:$ /home/marko/.mozilla/firefox/xpfj8oo1.default/extensions/flashlight@stephennolan.com.au/plugins/libflashplayer.so:$ :$ 1332795981000:1:5:$ Shockwave Flash 11.2 r202:$ Shockwave Flash:$ 2 0:application/x-shockwave-flash:Shockwave Flash:swf:$ 1:application/futuresplash:FutureSplash Player:spl:$ libflashplayer.so:$ /usr/lib/adobe-flashplugin/libflashplayer.so:$ :$ 1330400964000:1:1:$ Shockwave Flash 11.1 r102:$ Shockwave Flash:$ 2 0:application/x-shockwave-flash:Shockwave Flash:swf:$ 1:application/futuresplash:FutureSplash Player:spl:$ IcedTeaPlugin.so:$ /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/IcedTeaPlugin.so:$ :$ 1320721707000:1:5:$ The <a href="http://icedtea.classpath.org/wiki/IcedTea-Web">IcedTea-Web Plugin</a> executes Java applets.:$ IcedTea-Web Plugin (using IcedTea-Web 1.1.3 (1.1.3-1ubuntu1.1)):$ 34 0:application/x-java-vm:IcedTea:class,jar:$ 1:application/x-java-applet:IcedTea:class,jar:$ 2:application/x-java-applet;version=1.1:IcedTea:class,jar:$ 3:application/x-java-applet;version=1.1.1:IcedTea:class,jar:$ 4:application/x-java-applet;version=1.1.2:IcedTea:class,jar:$ 5:application/x-java-applet;version=1.1.3:IcedTea:class,jar:$ 6:application/x-java-applet;version=1.2:IcedTea:class,jar:$ 7:application/x-java-applet;version=1.2.1:IcedTea:class,jar:$ 8:application/x-java-applet;version=1.2.2:IcedTea:class,jar:$ 9:application/x-java-applet;version=1.3:IcedTea:class,jar:$ 10:application/x-java-applet;version=1.3.1:IcedTea:class,jar:$ 11:application/x-java-applet;version=1.4:IcedTea:class,jar:$ 12:application/x-java-applet;version=1.4.1:IcedTea:class,jar:$ 13:application/x-java-applet;version=1.4.2:IcedTea:class,jar:$ 14:application/x-java-applet;version=1.5:IcedTea:class,jar:$ 15:application/x-java-applet;version=1.6:IcedTea:class,jar:$ 16:application/x-java-applet;jpi-version=1.6.0_50:IcedTea:class,jar:$ 17:application/x-java-bean:IcedTea:class,jar:$ 18:application/x-java-bean;version=1.1:IcedTea:class,jar:$ 19:application/x-java-bean;version=1.1.1:IcedTea:class,jar:$ 20:application/x-java-bean;version=1.1.2:IcedTea:class,jar:$ 21:application/x-java-bean;version=1.1.3:IcedTea:class,jar:$ 22:application/x-java-bean;version=1.2:IcedTea:class,jar:$ 23:application/x-java-bean;version=1.2.1:IcedTea:class,jar:$ 24:application/x-java-bean;version=1.2.2:IcedTea:class,jar:$ 25:application/x-java-bean;version=1.3:IcedTea:class,jar:$ 26:application/x-java-bean;version=1.3.1:IcedTea:class,jar:$ 27:application/x-java-bean;version=1.4:IcedTea:class,jar:$ 28:application/x-java-bean;version=1.4.1:IcedTea:class,jar:$ 29:application/x-java-bean;version=1.4.2:IcedTea:class,jar:$ 30:application/x-java-bean;version=1.5:IcedTea:class,jar:$ 31:application/x-java-bean;version=1.6:IcedTea:class,jar:$ 32:application/x-java-bean;jpi-version=1.6.0_50:IcedTea:class,jar:$ 33:application/x-java-vm-npruntime:::$ libtotem-cone-plugin.so:$ /usr/lib/mozilla/plugins/libtotem-cone-plugin.so:$ :$ 1318915705000:1:5:$ The <a href="http://www.gnome.org/projects/totem/">Totem</a> 3.0.1 plugin handles video and audio streams.:$ VLC Multimedia Plugin (compatible Totem 3.0.1):$ 21 0:application/x-vlc-plugin:VLC Multimedia Plugin::$ 1:application/vlc:VLC Multimedia Plugin::$ 2:video/x-google-vlc-plugin:VLC Multimedia Plugin::$ 3:application/x-ogg:Ogg multimedia file:ogg:$ 4:application/ogg:Ogg multimedia file:ogg:$ 5:audio/ogg:Ogg Audio:oga:$ 6:audio/x-ogg:Ogg Audio:ogg:$ 7:video/ogg:Ogg Video:ogv:$ 8:video/x-ogg:Ogg Video:ogg:$ 9:application/annodex:Annodex exchange format:anx:$ 10:audio/annodex:Annodex Audio:axa:$ 11:video/annodex:Annodex Video:axv:$ 12:video/mpeg:MPEG video:mpg, mpeg, mpe:$ 13:audio/wav:WAV audio:wav:$ 14:audio/x-wav:WAV audio:wav:$ 15:audio/mpeg:MP3 audio:mp3:$ 16:application/x-nsv-vp3-mp3:NullSoft video:nsv:$ 17:video/flv:Flash video:flv:$ 18:video/webm:WebM video:webm:$ 19:application/x-totem-plugin:Totem Multimedia plugin::$ 20:audio/midi:MIDI audio:mid, midi:$ libtotem-mully-plugin.so:$ /usr/lib/mozilla/plugins/libtotem-mully-plugin.so:$ :$ 1318915705000:1:5:$ DivX Web Player version 1.4.0.233:$ DivXÂ® Web Player:$ 1 0:video/divx:AVI video:divx:$ libtotem-gmp-plugin.so:$ /usr/lib/mozilla/plugins/libtotem-gmp-plugin.so:$ :$ 1318915705000:1:5:$ The <a href="http://www.gnome.org/projects/totem/">Totem</a> 3.0.1 plugin handles video and audio streams.:$ Windows Media Player Plug-in 10 (compatible; Totem):$ 13 0:application/x-mplayer2:AVI video:avi, wma, wmv:$ 1:video/x-ms-asf-plugin:ASF video:asf, wmv:$ 2:video/x-msvideo:AVI video:asf, wmv:$ 3:video/x-ms-asf:ASF video:asf:$ 4:video/x-ms-wmv:Windows Media video:wmv:$ 5:video/x-wmv:Windows Media video:wmv:$ 6:video/x-ms-wvx:Windows Media video:wmv:$ 7:video/x-ms-wm:Windows Media video:wmv:$ 8:video/x-ms-wmp:Windows Media video:wmv:$ 9:application/x-ms-wms:Windows Media video:wms:$ 10:application/x-ms-wmp:Windows Media video:wmp:$ 11:application/asx:Microsoft ASX playlist:asx:$ 12:audio/x-ms-wma:Windows Media audio:wma:$ libtotem-narrowspace-plugin.so:$ /usr/lib/mozilla/plugins/libtotem-narrowspace-plugin.so:$ :$ 1318915705000:1:5:$ The <a href="http://www.gnome.org/projects/totem/">Totem</a> 3.0.1 plugin handles video and audio streams.:$ QuickTime Plug-in 7.6.6:$ 5 0:video/quicktime:QuickTime video:mov:$ 1:video/mp4:MPEG-4 video:mp4:$ 2:image/x-macpaint:MacPaint Bitmap image:pntg:$ 3:image/x-quicktime:Macintosh Quickdraw/PICT drawing:pict, pict1, pict2:$ 4:video/x-m4v:MPEG-4 video:m4v:$ libflashplayer.so:$ /usr/lib/mozilla/plugins/libflashplayer.so:$ :$ 1329954691000:1:12:$ Shockwave Flash 11.2 r202:$ Shockwave Flash:$ 2 0:application/x-shockwave-flash:Shockwave Flash:swf:$ 1:application/futuresplash:FutureSplash Player:spl:$  [INVALID] /home/marko/.mozilla/plugins/nppdf.so:$ 1328016560000:$ 
```

I am tracking dozens of threads an many users at the same time, trying to solve their issues. Jumping on other peoples thread will just increase the confusion. Please post the link to the original thread so I can reply there.

---

### Post by fonsi2099 on 2012-04-09
Resolved in this way:

> **shantiq said:**
> maybe try this


[ATTACH]214173[/ATTACH]


[SIZE="3"]
**or**[/SIZE]



First, remove old, unnecessary packages.

```
sudo apt-get remove --purge adobe-flashplugin flashplugin* nspluginwrapper
```

Install 32 or 64-bit Flash. Answer "Y" to confirm this operation.

```
sudo apt-get install --reinstall adobe-flashplugin
```

Many thanks
:guitar:

---

