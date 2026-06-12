---
title: "Flash player issues"
date: 2008-12-07
forum: Multimedia Software
---

### Post by izenteno on 2008-12-07
Hi!
I installed the Adobe Flash player non-free, following the instructions of the forum, in order to stream videos in sites just like youtube, break, megavideo, etc. Since Im from Mexico I have restricted access to sites like hulu, pandora, nbc, etc... I used Ultrasurf in XP and worked just fine. 

A couple of days ago I found in this forums a linux supported program named TOR and privoxy that help mantain your computer IP hiden. It was a real challenge installing it and setting everything out cause im a newbie with linux. Finally I got it to work, but know Im getting a problem, some web pages give me a message that I need to have a version of adobe flash 9 or +, I know that I just installed a higher version than 9. I just dont know why this isnt working. Im allowing scripts at firefox.

---

### Post by gandaran on 2008-12-07
> some web pages give me a message that I need to have a version of adobe flash 9 or +, I know that I just installed a higher version than 9. I just dont know why this isnt working. Im allowing scripts at firefox.
you may have adobe flash 10 installed, but are you 100% sure you still don't have another older flash version or gnash flash and swfdec flash installed?

---

### Post by izenteno on 2008-12-09
Yes im 100% sure I dont have an older version, I just installed Ubuntu 2 weeks ago. 

What should I do?

---

### Post by gandaran on 2008-12-10
> **izenteno said:**
> Yes im 100% sure I dont have an older version, I just installed Ubuntu 2 weeks ago. 

What should I do?
type this code in firefox url bar and post full output here
```
about:plugins
```
also the output of **locate libflash** (type in terminal)

---

### Post by izenteno on 2008-12-10
> **gandaran said:**
> type this code in firefox url bar and post full output here
```
about:plugins
```
also the output of **locate libflash** (type in terminal)

Shockwave Flash

    File name: npwrapper.libflashplayer.so
    Shockwave Flash 10.0 r12

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

--------------------------------------------
**Locate Libflash**
/usr/lib/firefox/plugins/npwrapper.libflashplayer.so
/usr/lib/flashplugin-nonfree/libflashplayer.so
/usr/lib/iceweasel/plugins/npwrapper.libflashplayer.so
/usr/lib/mozilla/plugins/npwrapper.libflashplayer.so
/usr/lib/openoffice/program/libflash680lx.so
/var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so

---

### Post by gandaran on 2008-12-11
just one more question, what version of ubuntu, 8.04 or 8.10 and 32-bits or 64-bits?

---

### Post by izenteno on 2008-12-11
> **gandaran said:**
> just one more question, what version of ubuntu, 8.04 or 8.10 and 32-bits or 64-bits?

Im using 8.10 intrepid it came with WUBI (I had the XP Profesional 32 bit) I have AMD turion 64 (im not sure if I installed 32 or 64) I think I went for the 32 but im not sure...

---

### Post by gandaran on 2008-12-12
I suspect you do have the 64-bits version, the 32-bits flash from the repos sometimes doesn't work on 64-bits, what you can try is remove the flashplugin-nonfree and npwrapper then install the adobe 64-bits beta flash
get it here (.tar.gz package) [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)
if you have any problem installing this package I'll give you instructions later.

---

### Post by shires on 2009-07-05
I have a similar problem, my problem is that i can not watch videos at megavideo, but sites like YouTube or other streaming sites i have tried workes fine. I have allready installed and uninstalled flash player several times. Can someone help me?

---

### Post by ckonestroh on 2009-07-05
Hello,

Experienced problems where Adobe Flash player gave a blank box no sound 

Go to 


System > Adminstrator > Synaptic Package Manager do search for swfdec do a complete unistall not just a remove.... 

Then open Firefox select Tools > Add-ons > and Abode flash should be removed...

Go to 

[http://get.adobe.com/flashplayer/]("http://get.adobe.com/flashplayer/")

Select Debian install gives you Ubuntu 8.04 ignore this will install on Ubuntu Jaunty ...


Good luck 

just so many ways to install and uninstall Flash becomes to confusing...


bye....

---

### Post by shires on 2009-07-05
On my ubuntu i get two different types of swfdec (tools to play swf files on gnome) and the flash mozzilla plugin. Witch one do I uninstall?

EDIT: Tried the tip I got on how to propperly uninstall and reinstall flash, thanks man;) BUT it did not work, and did not make anydifference when i tried to watch a video at megavideo. I cant see video or hear anything. the only thing I see is a black box. And the links at the top of the site does not even have a "image." Can someone pleas help? 

As a reminder i can watch youtube videos without any problems at all. So I am partley convinced that its not flash.

---

### Post by ckonestroh on 2009-07-06
Its a flash video...  Its just that firefox is a pain in the butt to remove the flash driver... I did like three or four different posts on ubuntu get it to unistall


Like I said Firefox has different methods for unistalling drivers gets to be a bit confusing.... One this doesn't happen that often or there would be a manual by now this has only happened about 1 time in the past 3 years....


Try different searches on installing and removing flash from firefox... 


... 
Good luck its a mini project in its self next time this happens to me I will right down all the steps in order that it took to remove Flash player...

---

