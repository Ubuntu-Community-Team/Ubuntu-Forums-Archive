---
title: "Flash Player problem in firefox"
date: 2008-11-04
forum: Multimedia Software
---

### Post by Bcampoli5 on 2008-11-04
Whenever I go to youtube, it says I don't have the newest version of the flash player.  So i download the flash player, double click on the folder, but when I hit run in terminal, nothing happens.  Can anyone help me?

---

### Post by gandaran on 2008-11-04
did you download the .deb package, only this one works double clicking, remove the flash installed first or it mite not work

---

### Post by Bcampoli5 on 2008-11-04
Ok, I'll try that.  I remember downloading the .deb player and it wouldn't work.  I think it said something was wrong with the file, but I'll try again.

---

### Post by gandaran on 2008-11-04
the .deb file you just double click to install, [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)  no need to run in terminal
you can also install the flash from the repos, look in synaptic for flashplugin-nonfree mark for install and click the apply button or install this package using the command line **sudo apt-get install flashplugin-nonfree**
remove the older version first.

---

### Post by bob brazie on 2008-11-04
I can't seem to get the newest flash player to work and I have tried all suggestions mentioned here.

Synaptic says it is installed and is active.

It does not so up in the applications menu but I am not sure it would.

Here is a site that I am trying to open. [http://video.nationalgeographic.com/video/wildcambelize/](http://video.nationalgeographic.com/video/wildcambelize/)

 I have a windows machine with flash installed and it plays fine but I would like to view it in the new Ubuntu 8.10

I would be grateful for any help resolving this issue.

Thanks in advance. Bob.

---

### Post by Safder on 2008-11-04
I had the same problem and [this]("http://www.ubuntugeek.com/how-to-install-adobe-flash-player-10-in-ubuntu-804-hardy-heron.html") is what I did. Hope this helps you

---

### Post by gandaran on 2008-11-05
> **bob brazie said:**
> I can't seem to get the newest flash player to work and I have tried all suggestions mentioned here.

Synaptic says it is installed and is active.

It does not so up in the applications menu but I am not sure it would.

Here is a site that I am trying to open. [http://video.nationalgeographic.com/video/wildcambelize/](http://video.nationalgeographic.com/video/wildcambelize/)

 I have a windows machine with flash installed and it plays fine but I would like to view it in the new Ubuntu 8.10

I would be grateful for any help resolving this issue.

Thanks in advance. Bob.

can you post here the output of **locate libflash**? type this in terminal/console.

---

### Post by bob brazie on 2008-11-05
bob@ubuntu:~$ locate libflash
/usr/lib/openoffice/program/libflash680li.so
bob@ubuntu:~$

---

### Post by jadhav333 on 2008-11-05
> **Safder said:**
> I had the same problem and [this]("http://www.ubuntugeek.com/how-to-install-adobe-flash-player-10-in-ubuntu-804-hardy-heron.html") is what I did. Hope this helps you

The information provided in the url is to run a script. The script along with other things also downloads some lib packages from the following site.. 
"wget http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb"

boundlesssupremacy?????

I dont know whether the source seems reliable or secure. I would not trust my machine with a script that downloads and installs data from a unreliable source.

There is no way one can predict its possible impact on the proper functioning of the OS.

So if anyone does try it out.. pls share your experiences as well.. good or bad :)

---

### Post by gandaran on 2008-11-05
> **bob brazie said:**
> bob@ubuntu:~$ locate libflash
/usr/lib/openoffice/program/libflash680li.so
bob@ubuntu:~$

you have no flash at all installed, can you provide details of what package synaptic says  is installed?

---

### Post by Bcampoli5 on 2008-11-05
> **gandaran said:**
> the .deb file you just double click to install, [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)  no need to run in terminal
you can also install the flash from the repos, look in synaptic for flashplugin-nonfree mark for install and click the apply button or install this package using the command line **sudo apt-get install flashplugin-nonfree**
remove the older version first.

I'm kind of confused on using a "command line".  Where do I type this command in?

---

### Post by gandaran on 2008-11-05
applications » accessories » terminal or console

---

### Post by bob brazie on 2008-11-05
On closer examination it is saying it is the plug-in installer and not that it was installed.

I guess I am at a loss as to how to install it. I had thought that when I downloaded it, it was installing automatically.

---

### Post by gandaran on 2008-11-05
> **bob brazie said:**
> On closer examination it is saying it is the plug-in installer and not that it was installed.

I guess I am at a loss as to how to install it. I had thought that when I downloaded it, it was installing automatically.
have you succeed installing it now?
if you install the **flashplugin-nonfree** package you can find in synaptic package manager, this flash is exactly the same adobe flash you download from the adobe site, theres no deference!

---

### Post by bob brazie on 2008-11-05
No, I guess being new to 8.10 I am at a loss as to how to install it.

---

### Post by aysiu on 2008-11-05
Can you paste these commands into [the terminal](http://www.psychocats.net/ubuntu/terminal) and then paste the output back here? ```
sudo updatedb
locate libflash
uname -m
cat /etc/lsb-release
dpkg -s flashplugin-nonfree
dpkg -s mozilla-plugin-gnash
dpkg -s swfdec-mozilla
``` Warning: the first command may take a few minutes to execute.

---

### Post by bob brazie on 2008-11-05
bob@ubuntu:~$ sudo updatedb
[sudo] password for bob: 
sudo updatedb
locate libflash
uname -m
cat /etc/lsb-release
dpkg -s flashplugin-nonfree
dpkg -s mozilla-plugin-gnash
dpkg -s swfdec-mozilla
bob@ubuntu:~$ sudo updatedb


bob@ubuntu:~$ locate libflash
/usr/lib/flashplugin-nonfree/libflashplayer.so
/usr/lib/openoffice/program/libflash680li.so
bob@ubuntu:~$ uname -m
i686
bob@ubuntu:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=8.10
DISTRIB_CODENAME=intrepid
DISTRIB_DESCRIPTION="Ubuntu 8.10"
bob@ubuntu:~$ dpkg -s flashplugin-nonfree
Package: flashplugin-nonfree
Status: install ok installed
Priority: optional
Section: contrib/web
Installed-Size: 164
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Architecture: i386
Version: 10.0.12.36ubuntu1
Replaces: flashplugin (<< 6)
Depends: debconf | debconf-2.0, wget, libgtk2.0-0, fontconfig, libxt6, libxext6, libatk1.0-0, libc6, libcairo2, libexpat1, libfontconfig1, libfreetype6, libglib2.0-0, libice6, libpango1.0-0, libpng12-0, libsm6, libx11-6, libxau6, libxcursor1, libxdmcp6, libxfixes3, libxi6, libxinerama1, libxrandr2, libxrender1, zlib1g
Recommends: libasound2-plugins (>= 1.0.16)
Suggests: firefox, xulrunner-1.9, firefox-3.0, konqueror-nsplugins, x-ttcidfont-conf, msttcorefonts, ttf-bitstream-vera | ttf-dejavu, ttf-xfree86-nonfree, xfs (>= 1:1.0.1-5)
Conflicts: flashplayer-mozilla, flashplugin (<< 6), libflashsupport, xfs (<< 1:1.0.1-5)
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
Homepage: [http://wiki.ubuntu.com/FlashPlayer9](http://wiki.ubuntu.com/FlashPlayer9)
Npp-Applications: ec8030f7-c20a-464f-9b0e-13a3a9e97384, 92650c4d-4b8e-4d2a-b7eb-24ecf4f6b63a, aa5ca914-c309-495d-91cf-3141bbb04115
Npp-Description: Adobe Flash SWF Player ([http://www.adobe.com](http://www.adobe.com))
Npp-File: libflashplayer.so
Npp-Mimetype: application/x-shockwave-flash
Npp-Name: Adobe Flash Player (installer)
Original-Maintainer: Bart Martens <bartm@knars.be>
bob@ubuntu:~$ dpkg -s mozilla-plugin-gnash
Package `mozilla-plugin-gnash' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
bob@ubuntu:~$ dpkg -s swfdec-mozilla
Package `swfdec-mozilla' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
bob@ubuntu:~$ 
bob@ubuntu:~$ 
bob@ubuntu:~$

---

### Post by aysiu on 2008-11-05
Kind of weird that *flashplugin-nonfree* is installed but only in /usr/lib/flashplugin-nonfree/

Can you try this?

**Step 1**
Copy and paste this command into the terminal but don't hit *Enter* yet: ```
sudo ln -s /usr/lib/flashplugin-nonfree/libflashplayer.so /usr/lib/xulrunner-addons/plugins/libflashplayer.so
```

**Step 2**
Close Firefox completely

**Step 3**
Go back to the terminal and hit *Enter* to execute the aforementioned command

**Step 4**
Start Firefox again and visit a Flash website

---

### Post by aysiu on 2008-11-05
Kind of weird that *flashplugin-nonfree* is installed but only in /usr/lib/flashplugin-nonfree/

Can you try this?

**Step 1**
Copy and paste this command into the terminal but don't hit *Enter* yet: ```
sudo ln -s /usr/lib/flashplugin-nonfree/libflashplayer.so /usr/lib/xulrunner-addons/plugins/libflashplayer.so
```

**Step 2**
Close Firefox completely

**Step 3**
Go back to the terminal and hit *Enter* to execute the aforementioned command

**Step 4**
Start Firefox again and visit a Flash website

---

### Post by aysiu on 2008-11-05
Actually, that isn't weird. I just tried on the live CD. If you install *flashplugin-nonfree* and then update the database index, it's located only in /usr/lib/flashplugin-nonfree/libflashplayer.so, but it works (or should work) if it's there alone.

Still, try the instructions I gave above. They may work.

Can you also tell us what the output of this command is? ```
ls -l /usr/lib/xulrunner-addons/plugins
```

---

### Post by bob brazie on 2008-11-05
Still can't view a flash site.

This was information after I Hit enter.

bob@ubuntu:~$ sudo ln -s /usr/lib/flashplugin-nonfree/libflashplayer.so /usr/lib/xulrunner-addons/plugins/libflashplayer.so
ln: creating symbolic link `/usr/lib/xulrunner-addons/plugins/libflashplayer.so': File exists
bob@ubuntu:~$

---

### Post by bob brazie on 2008-11-05
bob@ubuntu:~$ ls -l /usr/lib/xulrunner-addons/plugins
total 40
lrwxrwxrwx 1 root root    46 2008-11-05 14:46 flashplugin-alternative.so -> /etc/alternatives/xulrunner-addons-flashplugin
lrwxrwxrwx 1 root root    46 2008-11-05 15:20 libflashplayer.so -> /usr/lib/flashplugin-nonfree/libflashplayer.so
-rw-r--r-- 1 root root 17976 2008-10-13 09:10 libnullplugin.so
-rw-r--r-- 1 root root  5400 2008-10-24 16:00 librhythmbox-itms-detection-plugin.so
lrwxrwxrwx 1 root root    44 2008-11-02 10:36 libtotem-basic-plugin.so -> ../../totem/default/libtotem-basic-plugin.so
lrwxrwxrwx 1 root root    42 2008-11-02 10:36 libtotem-gmp-plugin.so -> ../../totem/default/libtotem-gmp-plugin.so
lrwxrwxrwx 1 root root    44 2008-11-02 10:36 libtotem-mully-plugin.so -> ../../totem/default/libtotem-mully-plugin.so
lrwxrwxrwx 1 root root    50 2008-11-02 10:36 libtotem-narrowspace-plugin.so -> ../../totem/default/libtotem-narrowspace-plugin.so
-rw-r--r-- 1 root root  9480 2008-10-13 09:10 libunixprintplugin.so
lrwxrwxrwx 1 root root    43 2008-11-04 12:53 mplayerplug-in-dvx.so -> ../../mozilla/plugins/mplayerplug-in-dvx.so
lrwxrwxrwx 1 root root    44 2008-11-04 12:53 mplayerplug-in-dvx.xpt -> ../../mozilla/plugins/mplayerplug-in-dvx.xpt
lrwxrwxrwx 1 root root    42 2008-11-04 12:53 mplayerplug-in-qt.so -> ../../mozilla/plugins/mplayerplug-in-qt.so
lrwxrwxrwx 1 root root    43 2008-11-04 12:53 mplayerplug-in-qt.xpt -> ../../mozilla/plugins/mplayerplug-in-qt.xpt
lrwxrwxrwx 1 root root    42 2008-11-04 12:53 mplayerplug-in-rm.so -> ../../mozilla/plugins/mplayerplug-in-rm.so
lrwxrwxrwx 1 root root    43 2008-11-04 12:53 mplayerplug-in-rm.xpt -> ../../mozilla/plugins/mplayerplug-in-rm.xpt
lrwxrwxrwx 1 root root    39 2008-11-04 12:53 mplayerplug-in.so -> ../../mozilla/plugins/mplayerplug-in.so
lrwxrwxrwx 1 root root    43 2008-11-04 12:53 mplayerplug-in-wmp.so -> ../../mozilla/plugins/mplayerplug-in-wmp.so
lrwxrwxrwx 1 root root    44 2008-11-04 12:53 mplayerplug-in-wmp.xpt -> ../../mozilla/plugins/mplayerplug-in-wmp.xpt
lrwxrwxrwx 1 root root    40 2008-11-04 12:53 mplayerplug-in.xpt -> ../../mozilla/plugins/mplayerplug-in.xpt
bob@ubuntu:~$

---

### Post by gandaran on 2008-11-06
bob brazie
flash is installed in /usr/lib/flashplugin-nonfree/libflashplayer.so and should work, if it does'nt then the problem lies somewhere else, maybe firefox (you can try another web browser like opera, it uses the same flash)
check in firefox » tools » addons » plugins » shockwave flash 10.0 r12 if enabled or disabled, also do you have any firefox addon like flashblock or addblock installed?

firefox needs a restart to get flash working after installing!

---

### Post by bob brazie on 2008-11-06
I don't have anything else installed. This was a fresh clean install of 8.10.

I have since removed and re-installed.

The site says the download is for ubuntu 8.4. Could this be the problem as I am running 8.10?

If not and I download the application again how would you recommend I install it?

Thanks in advance for all of your help.

BTW when I check my throw away mail site at MSN HotMail they suggest I up-grade my browser. I am running the one that came with 8.10. Mozilla Firefox Mozilla/5.0 (X11; U; Linux i686;

---

### Post by gandaran on 2008-11-06
> The site says the download is for ubuntu 8.4. Could this be the problem as I am running 8.10?
it works the same in 8.10 as it does in 8.04

well if you install this adobe package, remove first the one installed in synaptic

can you type in firefox url bar **about: plugins** (without spaces) and post the results here?

---

### Post by bob brazie on 2008-11-06
Sure but I am not sure what it means. How to un-install? Should I save it to the desktop and run it from there?

Installed plugins
Find more information about browser plugins at mozilla.org.
Help for installing plugins is available from plugindoc.mozdev.org.
Totem Web Browser Plugin 2.24.2

    File name: libtotem-basic-plugin.so
    The Totem 2.24.2 plugin handles video and audio streams.

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
    The Totem 2.24.2 plugin handles video and audio streams.

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
    The Totem 2.24.2 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
video/quicktime 	QuickTime video 	mov 	Yes
video/mp4 	MPEG-4 video 	mp4 	Yes
image/x-macpaint 	MacPaint Bitmap image 	pntg 	Yes
image/x-quicktime 	Macintosh Quickdraw/PICT drawing 	pict, pict1, pict2 	Yes
video/x-m4v 	MPEG-4 video 	m4v 	Yes
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

---

### Post by bob brazie on 2008-11-06
Sure but I am not sure what it means. How to un-install? Should I save it to the desktop and run it from there?

Installed plugins
Find more information about browser plugins at mozilla.org.
Help for installing plugins is available from plugindoc.mozdev.org.
Totem Web Browser Plugin 2.24.2

    File name: libtotem-basic-plugin.so
    The Totem 2.24.2 plugin handles video and audio streams.

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
    The Totem 2.24.2 plugin handles video and audio streams.

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
    The Totem 2.24.2 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
video/quicktime 	QuickTime video 	mov 	Yes
video/mp4 	MPEG-4 video 	mp4 	Yes
image/x-macpaint 	MacPaint Bitmap image 	pntg 	Yes
image/x-quicktime 	Macintosh Quickdraw/PICT drawing 	pict, pict1, pict2 	Yes
video/x-m4v 	MPEG-4 video 	m4v 	Yes
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

---

### Post by gandaran on 2008-11-06
was this the full output? I don't see the flashplugin  listed here,
did you remove the flashplugin-nonfre you had installed?

---

### Post by gandaran on 2008-11-06
look, download the .deb package here [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/) to desktop, to install it just double click the package and hit install package

---

### Post by bob brazie on 2008-11-06
I am doing that now and will let you know how it works out.

A couple of posts ago I mentioned that I removed 8.10 and the re-installed it again.

---

### Post by bob brazie on 2008-11-07
I haven't installed the downloaded deb file yet.

I just went to a flash site and I noticed at the top of the Mozilla Firefox browser was a bar to click on that askes to install a missing plug in. Whould this be better than installing the downloaded file?

---

### Post by NilsE on 2008-11-07
> **bob brazie said:**
> I haven't installed the downloaded deb file yet.

I just went to a flash site and I noticed at the top of the Mozilla Firefox browser was a bar to click on that askes to install a missing plug in. Whould this be better than installing the downloaded file?

That did not work in the past real well but now that Adobe provides the deb file it may work.  Won't hurt to try but it is just as easy to download the deb and install it.

Or, turn on the partner repos in Software Sources (assuming 8.10)and install it from Synaptic.

---

### Post by gandaran on 2008-11-07
> **bob brazie said:**
> I haven't installed the downloaded deb file yet.

I just went to a flash site and I noticed at the top of the Mozilla Firefox browser was a bar to click on that askes to install a missing plug in. Whould this be better than installing the downloaded file?

there are about a dozen deferent ways you can install flash in ubuntu, all of them are easy, adobe flash comes in a lot of deferent packages with deferent names, but they all install exactly the same flash/version that is released by adobe website, theres no deference in the flash, it's the same one and works the same! you just choose the way you like to install!
clicking on the missing plugin link (ubuntu 8.04) to install just make sure you choose the adobe flash and not gnash or swfdec flash, (ubuntu 8.10 directs you to adobe website)

---

