---
title: "firefox flash have sound, but no video"
date: 2011-01-02
forum: Multimedia Software
---

### Post by Eremis on 2011-01-02
Hi everyone,

I have an issue that I just noticed a few days ago...
When I play a flash vid (ex. from youtube) I have sound but the entire screen is simply white...

When I put my mouse where where the "play/pause" button should be I can click there and they work, but its all white...

Do you guys know what might have caused this?
What info do you need?

p.s.

flash in chrome works just fine, I use regular ubuntu repos. (ubuntu 10.04 32 bit)

---

### Post by wojox on 2011-01-02
Install [Flash-Aid]("https://addons.mozilla.org/en-US/firefox/addon/161939/"). It sounds like a conflict problem.

---

### Post by Eremis on 2011-01-02
did not help, the screen is still white

---

### Post by lovinglinux on 2011-01-02
> **Eremis said:**
> did not help, the screen is still white

Get [version 2.0 of Flash-Aid]("http://www.webgapps.org/addons/flash-aid") and run it. It installs the beta version of flash and applies some tweaks that most likely will fix your problem.

If not, then go to the Help tab in Flash-Aid, click "Generate Report" and post the results so I can take a look it.

Also try to delete the browser cache, cookies and the ~/.macromedia folder (game scores will be deleted too).

If nothing works, then disable Compiz and check if the problem persists.

---

### Post by TechWiz2100 on 2011-01-03
I can't get flash x64 to work in either Chrome nor Firefox... grey box where flash should be and controls work just fine + audio

32bit works, but its extremely buggy and tends to crap out more often than I would like it to and I've tried just about everything including turning off Murrine engine.

Heres some info about my set up:

Shockwave Flash

File: /usr/lib/mozilla/plugins/libflashplayer.so
Version: Shockwave Flash 10.3 d162

Useragents

Mozilla/5.0 (X11; U; Linux x86_64; en-US; rv:1.9.2.13) Gecko/20101206 Ubuntu/10.10 (maverick) Firefox/3.6.13
Mozilla/5.0 (X11; U; Linux x86_64; en-US) AppleWebKit/534.10 (KHTML, like Gecko) Chrome/8.0.552.224 Safari/534.10

Ubuntu Architecture

Linux techwiz-ThinkPad-T510 2.6.35-24-generic #42-Ubuntu SMP Thu Dec 2 02:41:37 UTC 2010 x86_64 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick
DISTRIB_DESCRIPTION="Ubuntu 10.10"

Firefox Packages

firefox						install
firefox-branding				install
firefox-gnome-support				install

Firefox binaries

/usr/bin/firefox
/usr/bin/firefox: symbolic link to `../lib/firefox-3.6.13/firefox.sh'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)

Firefox divertion

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

Sources

erik-b-andersen-rgba-gtk-maverick.list
erik-b-andersen-rgba-gtk-maverick.list.save
google-chrome.list
google-chrome.list.save
nvidia-vdpau-ppa-maverick.list
nvidia-vdpau-ppa-maverick.list.save
sevenmachines-flash-maverick.list
sevenmachines-flash-maverick.list.save
ubuntu-x-swat-x-updates-maverick.list
ubuntu-x-swat-x-updates-maverick.list.save

Flash packages


Plugin locations

/home/techwiz/libflashplayer.so

/usr/lib/firefox/plugins/flashplugin-alternative.so
/usr/lib/mozilla/plugins/flashplugin-alternative.so
/usr/lib/xulrunner-addons/plugins/flashplugin-alternative.so

Flash symlinks

/usr/lib/firefox-addons/plugins/libflashplayer.so: symbolic link to `/usr/lib/mozilla/plugins/libflashplayer.so'
/usr/lib/mozilla/plugins/flashplugin-alternative.so: ERROR: cannot open `/usr/lib/mozilla/plugins/flashplugin-alternative.so' (No such file or directory)
/etc/alternatives/mozilla-flashplugin: ERROR: cannot open `/etc/alternatives/mozilla-flashplugin' (No such file or directory)
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so: ERROR: cannot open `/var/lib/flashplugin-installer/npwrapper.libflashplayer.so' (No such file or directory)

If anyone can help me get the 64 bit plugin working that would be a great help! NSPluginWrapper is too buggy for my tastes

---

### Post by lovinglinux on 2011-01-03
> **TechWiz2100 said:**
> I can't get flash x64 to work in either Chrome nor Firefox... grey box where flash should be and controls work just fine + audio

32bit works, but its extremely buggy and tends to crap out more often than I would like it to and I've tried just about everything including turning off Murrine engine.

Heres some info about my set up:

Shockwave Flash

File: /usr/lib/mozilla/plugins/libflashplayer.so
Version: Shockwave Flash 10.3 d162

There is nothing wrong in your report.

Have you tried to create a new Ubuntu user, just for testing? Login with that clean account and test if you get the same problem with flash.

This way we will know if the problem is in your user configurations.

---

### Post by TechWiz2100 on 2011-01-03
> **lovinglinux said:**
> There is nothing wrong in your report.

Have you tried to create a new Ubuntu user, just for testing? Login with that clean account and test if you get the same problem with flash.

This way we will know if the problem is in your user configurations.

Well that helped a whole hell of alot...

Flash works fine it seems on the new user in Chrome but still gets blank box in firefox

---

### Post by lovinglinux on 2011-01-03
> **TechWiz2100 said:**
> Well that helped a whole hell of alot...

Flash works fine it seems on the new user in Chrome but still gets blank box in firefox

Try to create a new Firefox profile and check if the problem persists.

---

### Post by TechWiz2100 on 2011-01-04
Well, new profile did squat however I figured out that the issue is Compiz related...

Like with Eclipse IDE and others, Chrome and Firefox do not have a single executable binary that can be targeted by the exclude method in .profile

Instead you have to add
```
env XLIB_SKIP_ARGB_VISUALS=1
```
before the command in your firefox/chrome shortcut properties and everything is A-OK every time you launch from that shortcut.

If anyone knows how to make this permanent for whenever firefox/chrome is launched, including when links are clicked, that would be grand because this will only work if you click the shortcut and is NOT global.

---

### Post by lovinglinux on 2011-01-04
> **TechWiz2100 said:**
> Well, new profile did squat however I figured out that the issue is Compiz related...

Like with Eclipse IDE and others, Chrome and Firefox do not have a single executable binary that can be targeted by the exclude method in .profile

Instead you have to add
```
env XLIB_SKIP_ARGB_VISUALS=1
```
before the command in your firefox/chrome shortcut properties and everything is A-OK every time you launch from that shortcut.

If anyone knows how to make this permanent for whenever firefox/chrome is launched, including when links are clicked, that would be grand because this will only work if you click the shortcut and is NOT global.

Interesting. I have included a link to your post in my Flash issues and solutions tutorial. 

Perhaps you could add that to /usr/bin/firefox. However I cannot test if it is effective, since I can't reproduce this issue. Additionally, that would probably be overwritten with updates. The correct way would be copying /usr/bin/firefox to /usr/local/bin/firefox and modifying that file. However, I'm afraid that would work only if you launch Firefox via terminal.

---

### Post by TechWiz2100 on 2011-01-04
> **lovinglinux said:**
> Interesting. I have included a link to your post in my Flash issues and solutions tutorial. 

Perhaps you could add that to /usr/bin/firefox. However I cannot test if it is effective, since I can't reproduce this issue. Additionally, that would probably be overwritten with updates. The correct way would be copying /usr/bin/firefox to /usr/local/bin/firefox and modifying that file. However, I'm afraid that would work only if you launch Firefox via terminal.

env sets an temporary environment variable prior to launch so just putting in the variable and value should make it work at all times but yes it would probably die as soon as firefox is updated to a new version because the folder is different for each (major?) version

You could set the variable in .profile but that would kill Compiz for all I assume which would then defeat the purpose of installing Compiz in the first place.

What would be nice is if the firefox and chrome dev teams could add ARGB as a setting or something since its known to have issues with ARGB settings. Actually that would be a nice feature for all programs to have... maybe it can be implemented with Gnome?

---

### Post by Eremis on 2011-01-21
Sorry for a long pause, but here is my report (2.0 did not help)

```

Ubuntu Architecture

Linux linux-machine 2.6.32-26-generic #48-Ubuntu SMP Wed Nov 24 09:00:03 UTC 2010 i686 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"

Firefox Packages

firefox						install
firefox-branding				install
firefox-gnome-support				install

Firefox binaries

/usr/bin/firefox
/usr/bin/firefox: symbolic link to `../lib/firefox-3.6.13/firefox.sh'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: ERROR: cannot open `/opt/firefox/firefox' (No such file or directory)

Firefox divertion

/usr/bin/firefox.ubuntu: ERROR: cannot open `/usr/bin/firefox.ubuntu' (No such file or directory)

Sources

am-monkeyd-nautilus-elementary-ppa-lucid.list
am-monkeyd-nautilus-elementary-ppa-lucid.list.save
elegant-gnome-ppa-lucid.list
elegant-gnome-ppa-lucid.list.save
erik-b-andersen-rgba-gtk-lucid.list
google-chrome.list
google-chrome.list.save
kevin-mehall-pithos-daily-lucid.list
kevin-mehall-pithos-daily-lucid.list.save
murrine-daily-ppa-lucid.list
murrine-daily-ppa-lucid.list.save
tiheum-equinox-lucid.list
tiheum-equinox-lucid.list.save

Flash packages

Plugin locations

/usr/lib/firefox-addons/plugins/libflashplayer.so
/usr/lib/mozilla/plugins/libflashplayer.so


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

pluginreg.dat

Generated File. Do not edit.

[HEADER]
Version:0.11:$

[PLUGINS]
libflashplayer.so:$
/usr/lib/mozilla/plugins/libflashplayer.so:$
:$
1294534332000:1:1:$
Shockwave Flash 10.2 r152:$
Shockwave Flash:$
2
0:application/x-shockwave-flash:Shockwave Flash:swf:$
1:application/futuresplash:FutureSplash Player:spl:$
IcedTeaPlugin.so:$
/usr/lib/jvm/java-6-openjdk/jre/lib/i386/IcedTeaPlugin.so:$
:$
1290752309000:1:5:$
The IcedTea NPR Web Browser Plugin (using IcedTea6 1.9.2 (6b20-1.9.2-0ubuntu1~10.04.1)) executes Java applets.:$
IcedTea NPR Web Browser Plugin (using IcedTea6 1.9.2 (6b20-1.9.2-0ubuntu1~10.04.1)):$
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
DivXÂ® Web Player:$
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


```

---

### Post by lovinglinux on 2011-01-22
> **Eremis said:**
> Sorry for a long pause, but here is my report (2.0 did not help)

You report is OK. Everything is find in the plugin side.

Have you tried one of the other suggested solutions?

Have you tried a clean FF profile?

---

### Post by Eremis on 2011-01-23
A clean Firefox profile? You mean just renaming the directory, so it will create a new profile? then yes I have tried that... Other solution, tried that, no luck...

---

### Post by lovinglinux on 2011-01-23
> **Eremis said:**
> A clean Firefox profile? You mean just renaming the directory, so it will create a new profile? then yes I have tried that... Other solution, tried that, no luck...

Try a new Ubuntu user then, just to test if the problem persists.

---

### Post by Rytron on 2011-01-23
Awesome. Works like a charm. Thank you.

---

### Post by thongstele on 2011-06-08
This is my problem with Youtube on Firefox 4.01:

My laptop with Ubuntu Natty (11.04). On the first time after installing Ubuntu Natty and the first update Ubuntu I can watch youtube video on Firefox normally.

After a few days and a fews updates ubuntu (automatically) I cannot watch youtube on Firefox any more (just hear sound, not video - white screen). I did many ways to solve but the problem is still the same.
I check 'about:plugins' on FF4, It shows: 
[B]Shockwave Flash
[/B]

File:  libgcflashplayer.soVersion:   Shockwave Flash 10.3 r181. However youtube on Chrome and Opera run correctly,  no any problem. I also checked video on the other website such as : [http://xhamster.com](http://xhamster.com), It plays normally (hixhix).

And now, what can I do to solve this problem. I love Firefox due to many nice themes and good addons, so I need a help as soon as possible.
Thx in advance!

---

### Post by lovinglinux on 2011-06-08
> **thongstele said:**
> This is my problem with Youtube on Firefox 4.01:

My laptop with Ubuntu Natty (11.04). On the first time after installing Ubuntu Natty and the first update Ubuntu I can watch youtube video on Firefox normally.

After a few days and a fews updates ubuntu (automatically) I cannot watch youtube on Firefox any more (just hear sound, not video - white screen). I did many ways to solve but the problem is still the same.
I check 'about:plugins' on FF4, It shows: 
[B]Shockwave Flash
[/B]

File:  libgcflashplayer.soVersion:   Shockwave Flash 10.3 r181. However youtube on Chrome and Opera run correctly,  no any problem. I also checked video on the other website such as : [http://xhamster.com](http://xhamster.com), It plays normally (hixhix).

And now, what can I do to solve this problem. I love Firefox due to many nice themes and good addons, so I need a help as soon as possible.
Thx in advance!

You are using the flash plugin bundled with Chrome. Install Flash-Aid, run the wizard and change the flash source to repositories or the beta from Adobe Labs.

---

### Post by garvinrick4 on 2011-06-08
@lovinglinux
> :arrow: [COLOR=Sienna]My [Ubuntu Membership has been accepted]("http://ubuntuforums.org/showthread.php?t=1777382"). I would like to thank everyone who supported my application.[/COLOR]
Was there ever a doubt lovinglinux, congrats.
[COLOR=Sienna][/COLOR]

---

### Post by lovinglinux on 2011-06-08
> **garvinrick4 said:**
> @lovinglinux

Was there ever a doubt lovinglinux, congrats.
[COLOR=Sienna][/COLOR]

Thanks :-)

---

