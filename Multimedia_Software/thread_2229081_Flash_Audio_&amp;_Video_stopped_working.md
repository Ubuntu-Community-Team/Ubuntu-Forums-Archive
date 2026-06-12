---
title: "Flash Audio &amp; Video stopped working"
date: 2014-06-11
forum: Multimedia Software
---

### Post by bluedalek on 2014-06-11
Hello Everyone

I did an update a couple weeks ago, and ever since flash based sites such as Youtube (and others) stopped working correctly.  The playback streams would start, then stop at 2 sec and do nothing else. I did some searching around and was able to get Youtube to work with video, but no sound, by forcing HTML5, but it does not solve all the other sites.  I've also done a complete uninstall and reinstall of Flash with no change.

I have multiple desktops, all running the same OS and browsers, and the others work fine, so it has to be a setting on this system, but I could not figure out what it is.  All other Audio/Video works fine including Amarok, VLC and XBMC.  Youtube works fine when streaming through XBMC, just not Firefox, Chrome or Konqueror.

I am running KDE 4.13.0 on the following:
```
3.2.0-64-generic #97-Ubuntu SMP Wed Jun 4 22:04:21 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
```

Hardware:
ASUS H81I-PLUS Motherboard
8GB Fujitsu 1600MHz
Intel Pentium CPU G3220 @ 3.00GHz

Audio Devices listed:
8 Series/C220 Series Chipset High Definition Audio Controller
Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller

Any pointers or suggestions appreciated!

---

### Post by Yellow Pasque on 2014-06-11
Sometimes, the Flash cache gets corrupted (and it doesn't get removed just by removing/reinstalling the package). Try to reset the cache:
```
rm -rf ~/.adobe/Flash_Player
```

---

### Post by bluedalek on 2014-06-11
Still not working... Any other thoughts?

---

### Post by bluedalek on 2014-06-14
So I've gone through various trouble shooting steps that I've found online, and am still no further ahead than I was when I started.
I've opened Firefox and entered about:plugins and had the following returned:

[HTML]
Shockwave Flash

    File: libflashplayer.so,libflashplayer.so
    Path: /usr/lib/flashplugin-installer/libflashplayer.so,/usr/lib/firefox-addons/plugins/libflashplayer.so
    Version: 11.2.202.378
    State: Enabled
    Shockwave Flash 11.2 r202

MIME Type	Description	Suffixes
application/x-shockwave-flash	Shockwave Flash	swf
application/futuresplash	FutureSplash Player	spl
application/x-shockwave-flash	Shockwave Flash	swf
application/futuresplash	FutureSplash Player	spl
[/HTML]

I've then clicked the mozilla.org/checkplugin link on the page, and was redirected to a Mozilla site indicating that my Flash was up to date:

[HTML]
These plugins are up to date Plugin 	Status 	Action
Shockwave FlashShockwave Flash 11.2 r202	Up to Date
11.2.202.378
	Up to Date
[/HTML]

So I've restarted everything and still, I get the 'Install Adobe Flash' icon/button on most websites (tsn.ca as an example), or I get the player, and it jumps to 0:02 and stops ([http://www.air1.com/broadcast/playnow.aspx?media=listen&bt=3&](http://www.air1.com/broadcast/playnow.aspx?media=listen&bt=3&)).

I've tried Firefox, Chromium and Konqueror with no success.

Can someone explain how a plugin and be installed correctly, yet not recognised?

---

### Post by Yellow Pasque on 2014-06-14
You don't have any interfering plugins (such as gnash or lightspark) installed, correct?

---

