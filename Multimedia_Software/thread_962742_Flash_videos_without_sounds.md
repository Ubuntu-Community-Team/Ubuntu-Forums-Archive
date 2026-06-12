---
title: "Flash videos without sounds"
date: 2008-10-29
forum: Multimedia Software
---

### Post by amr_essam on 2008-10-29
Dear there

i downloaded the flash player plugin on Ubuntu , and web videos (like youtube) dont play the sound , just the movie with out any sound

please help

Regards

---

### Post by gandaran on 2008-10-29
> **amr_essam said:**
> Dear there

i downloaded the flash player plugin on Ubuntu , and web videos (like youtube) dont play the sound , just the movie with out any sound

please help

Regards
you download from where, adobe site or you used the flashplugin-nonfree from synaptic, find out what you have installed if flash 9 or flash 10
if you have an updated firefox to 3.0.3 and flash 10 installed you wont have any sound problem.

---

### Post by Maheriano on 2008-10-29
I got the same problem. How do I find out which one I have? I Followed a bunch of lines of code from these forums and now don't know what I got.

---

### Post by gandaran on 2008-10-30
> **Maheriano said:**
> I got the same problem. How do I find out which one I have? I Followed a bunch of lines of code from these forums and now don't know what I got.
to find out the version go to firefox»tools»addons»plugins»shockwave flash
open a terminal and type **locate libflash** post the output here

---

### Post by amr_essam on 2008-10-31
> **gandaran said:**
> to find out the version go to firefox»tools»addons»plugins»shockwave flash
open a terminal and type **locate libflash** post the output here

here is my output
/usr/lib/adobe-flashplugin/libflashplayer.so
/usr/lib/openoffice/program/libflash680li.so

---

### Post by gandaran on 2008-10-31
then you have flash 10 and still no sound?
try installing libflashsupport, if no work remove it and go to system » preferences » sound, set the sound capture to alsa  leave the rest music, sound and audio in auto-detect

---

### Post by amr_essam on 2008-10-31
> **gandaran said:**
> then you have flash 10 and still no sound?
try installing libflashsupport, if no work remove it and go to system » preferences » sound, set the sound capture to alsa  leave the rest music, sound and audio in auto-detect

Dear there

i installed the libflashsupport through this command

sudo apt-get install libflashsupport

and now , the video doesnt load  , the box itself doesnt appear

i fed up actually , tell me how i can install and reinstall both mozilla and flash

Regards

---

### Post by gandaran on 2008-10-31
> **amr_essam said:**
> Dear there

i installed the libflashsupport through this command

sudo apt-get install libflashsupport

and now , the video doesnt load  , the box itself doesnt appear

i fed up actually , tell me how i can install and reinstall both mozilla and flash

Regards
use synaptic to install and remove programs, look for them there mark for install or complete removal to remove and click the apply button, it's better than to use the command line.

your flash sound problem is due to a pulseaudio bug, search the forum, there are plenty of fixes here

---

### Post by Maheriano on 2008-10-31
> **gandaran said:**
> to find out the version go to firefox»tools»addons»plugins»shockwave flash
open a terminal and type **locate libflash** post the output here

Is this good or bad?
```
deemar@chugger:~$ locate libflash
/usr/lib/libflashsupport.so
/usr/lib/adobe-flashplugin/libflashplayer.so
/usr/lib/openoffice/program/libflash680li.so
/usr/share/doc/libflashsupport
/usr/share/doc/libflashsupport/changelog.Debian.gz
/usr/share/doc/libflashsupport/copyright
/usr/share/lintian/overrides/libflashsupport
/var/cache/apt/archives/libflashsupport_1.9-0ubuntu1_i386.deb
/var/lib/dpkg/info/libflashsupport.list
/var/lib/dpkg/info/libflashsupport.md5sums
/var/lib/dpkg/info/libflashsupport.postinst

```

---

### Post by gandaran on 2008-11-01
> **Maheriano said:**
> Is this good or bad?
```
deemar@chugger:~$ locate libflash
/usr/lib/libflashsupport.so
/usr/lib/adobe-flashplugin/libflashplayer.so
/usr/lib/openoffice/program/libflash680li.so
/usr/share/doc/libflashsupport
/usr/share/doc/libflashsupport/changelog.Debian.gz
/usr/share/doc/libflashsupport/copyright
/usr/share/lintian/overrides/libflashsupport
/var/cache/apt/archives/libflashsupport_1.9-0ubuntu1_i386.deb
/var/lib/dpkg/info/libflashsupport.list
/var/lib/dpkg/info/libflashsupport.md5sums
/var/lib/dpkg/info/libflashsupport.postinst

```
remove the libflashsupport, libflashsupport is for use with flash 9, it corrects a flash 9 sound bug
are you still using ubuntu 8.04 or upgraded to 8.10?

---

### Post by ve4cib on 2008-11-01
I've got similar issues with video and no sound on YouTube, despite having FF3 and Flash10 installed correctly.  I suspect that it may actually be a kernel bug, or an issue with the soundcard driver.  I've posted another thread [here](http://ubuntuforums.org/showthread.php?p=6078737#post6078737) with details of my situation.  Does anything there look similar to what you're experiencing?

---

### Post by veaviskos on 2008-11-01
I've only had Linux installed for 2 days and have had the same problem with audio of Flash videos in Firefox 3.  I've searched the Forum and via Google and found plenty of threads/posts discussing the problem,  Many of them provide fairly complex (to me, as a newbie) procedures for troubleshooting the problem, but nothing worked for me.  After reading this thread again a few minutes ago, I just decided to go to a YouTube video and try to play it again.  But, of course, I hadn't changed anything and so, still no sound --  except I idly decided to right click on the playing video. And when I did I saw a brief popup window on the video for Flash "Settings"; but before I could pursue the possibility that this might provide a path to solution, the audio for the Flash video came on!  I believe simply right clicking on the playing video may have activated the sound function (the only setting that appeared in the popup window was to check for allowing hardware acceleration and it was checked as soon as I saw the setting window -- I suppose it's possible that right clicking brought up the setting window AND selected "hardware acceleration" at the same time).  For those who haven't had any luck solving the "no sound in Flash videos" problem and have been as frustrated as I, it might be worth a try to simply right click on a playing video and see what happens -- perhaps the Flash Player plugin requires an initial audio configuration which commonly happens only when one accesses the "settings" function?

---

### Post by Maheriano on 2008-11-01
> **gandaran said:**
> remove the libflashsupport, libflashsupport is for use with flash 9, it corrects a flash 9 sound bug
are you still using ubuntu 8.04 or upgraded to 8.10?

First I want to say it's awesome that you're helping me, thanks.
So do I just type sudo apt-get uninstall libflashsupport? Or maybe sudo apt-get --install libflashsupport? I can't remember but I'll look it up.
And I'm running 8.04 but if Ubuntu doesn't upgrade automatically, I'll be doing it manually over the next week. I also noticed that my asound.conf file had been erased for some reason so I replaced it with a backup. Still not working though.

---

### Post by lexen on 2008-11-01
I have the opposite problem.  The audio loads some of the time, but it crashes a lot, and the video never works.  I have tried using gnash with no luck and I can't get the non-free to work well either.



Thanks,
Lexen

---

### Post by gandaran on 2008-11-02
> **Maheriano said:**
> First I want to say it's awesome that you're helping me, thanks.
So do I just type sudo apt-get uninstall libflashsupport? Or maybe sudo apt-get --install libflashsupport? I can't remember but I'll look it up.
And I'm running 8.04 but if Ubuntu doesn't upgrade automatically, I'll be doing it manually over the next week. I also noticed that my asound.conf file had been erased for some reason so I replaced it with a backup. Still not working though.
it's best to use synaptic to install and remove applications, just look for libflashsupport, mark for complete removal and click the apply button

---

### Post by beauman on 2008-11-02
Hi! I have this problem with no sound in flash, when I use an usb-audio-device.

So, sound works on my laptop over the build-in speakers. If I plug in
the usb-audio device, its detected and I can play the test sounds
from the audio settings dialog.

But Flash does not output sound to it. I couldn't find any audio setups
in flash either. With the usb-device plugged in,
it didn't play any sound at all.

Any idea what I am doing wrong?

regards,

Edit:
Flash: adobe-flashplugin 10.0.12.36-1intrepid2
OS: Ubuntu 8.10 Intrepid Ibex
beauman

---

### Post by xdotx on 2008-11-02
[http://ubuntuforums.org/showthread.php?p=6086248](http://ubuntuforums.org/showthread.php?p=6086248) is a workaround that solved a few of my sound related problems (included no sound in flash)

---

### Post by Maheriano on 2008-11-07
> **gandaran said:**
> remove the libflashsupport, libflashsupport is for use with flash 9, it corrects a flash 9 sound bug
are you still using ubuntu 8.04 or upgraded to 8.10?

I just reinstalled 8.04 fresh and upgraded to 8.1. Now here I am, I installed Alsa, configured everything to work with the SPIDF port on my Chaintech AV710 using ALSA. I go to System - Preferences - Sound and change all the options from Auto Detect to Chaintech AV-710 IEC1724 IEC958 (ALSA), hit Test and I hear the beeeeeeep for all of them. So I know it works and everything is set up correctly. Now how do I get sound from the Flash videos in Firefox as well? Here's the output of my locate libflash....

```
deemar@Chugger:~$ locate libflash
/usr/lib/openoffice/program/libflash680li.so

```

I also installed the .deb Flash file from the Adobe website.

---

### Post by gandaran on 2008-11-07
Maheriano
> I also installed the .deb Flash file from the Adobe website.
does the flash video work?
> Code:

deemar@Chugger:~$ locate libflash
/usr/lib/openoffice/program/libflash680li.so 
well, according to locate libflash output you don't have the adobe flash player installed, just to make sure type **about: plugins** (without spaces) in firefox url bar, post the output back here

---

### Post by Maheriano on 2008-11-07
> **gandaran said:**
> Maheriano

does the flash video work?
 
well, according to locate libflash output you don't have the adobe flash player installed, just to make sure type **about: plugins** (without spaces) in firefox url bar, post the output back here

Yes, the Flash videos work. I went to Youtube and there was no video, so I clicked the link to get the latest Flash video and it brought me to the Adobe page to download it. I chose the .deb package for Ubuntu 8.04+ and installed it. Closed Firefox, opened Firefox, Youtube videos worked.

Here's the output:
```
Installed plugins
Find more information about browser plugins at mozilla.org.
Help for installing plugins is available from plugindoc.mozdev.org.
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
Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 10.0 r12

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
```

---

