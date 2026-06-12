---
title: "Can't play Flash Videos after upgrade to 14.04"
date: 2014-10-28
forum: Multimedia Software
---

### Post by bobnn on 2014-10-28
[B][SIZE=2]ETA 20141103 So the problem is NOT as originally stated - it only is an issue when using su, gksu, sux, etc - the Flash Player work fine for the user that logged in thru the graphic interface.
[/SIZE][/B]

I just upgraded to 14.04.1 LTS and can no longer play Flash Videos.

IEvery vido I've clicked on in Facebook freezesd, and this was not happening a few days ago, before I upgraded from 12.04.

Videos in YouTube work also freeze the browser if you end up with a swf/Flash video - HTML5 vids are fine.  

This is true on Firefox, Chromium and Chrome.  

Getting a Flash video on youtube seems to be a matter of adding '&embed' to the basic URL _before accessing any HTML5 videos_ ala:

```
https://www.youtube.com/watch?v=DhTNu6ETd3s&embed
``` 

(almost all vids on youtube seem to be HTML5 now w/o the embed param - someday this Flash crap will just wither on the vine). 

All vids in Facebook seem to be Flash is my guess.  


Plugin info:

Chrome:
```

Adobe Flash Player - Version: 15.0.0.189
Shockwave Flash 15.0 r0
Name:	Shockwave Flash
Description:	Shockwave Flash 15.0 r0
Version:	15.0.0.189
Location:	/opt/google/chrome/PepperFlash/libpepflashplayer.so
Type:	PPAPI (out-of-process)
 	Disable
MIME types:	
MIME type	Description	File extensions
application/x-shockwave-flash	Shockwave Flash	.swf
application/futuresplash	FutureSplash Player.spl

```

Chromium:
```
Adobe Flash Player - Version: 15.0.0.189
Shockwave Flash 15.0 r0
Name:	Shockwave Flash
Description:	Shockwave Flash 15.0 r0
Version:	15.0.0.189
Location:	/usr/lib/pepperflashplugin-nonfree/libpepflashplayer.so
Type:	PPAPI (out-of-process)
 	Disable
MIME types:	
MIME type	Description	File extensions
application/x-shockwave-flash	Shockwave Flash	.swf
application/futuresplash	FutureSplash Player	.spl

```
Those pepperflash plugins are copies:
```
$ md5sum /usr/lib/pepperflashplugin-nonfree/libpepflashplayer.so /opt/google/chrome/PepperFlash/libpepflashplayer.so
ec655d69a2c4a15a39d4fb1ac13591d6  /usr/lib/pepperflashplugin-nonfree/libpepflashplayer.so
ec655d69a2c4a15a39d4fb1ac13591d6  /opt/google/chrome/PepperFlash/libpepflashplayer.so


$ ll /usr/lib/pepperflashplugin-nonfree/libpepflashplayer.so /opt/google/chrome/PepperFlash/libpepflashplayer.so
-rw-r--r-- 1 root root 17350240 Oct 21 20:59 /opt/google/chrome/PepperFlash/libpepflashplayer.so
-rw-r--r-- 1 root root 17350240 Oct 21 20:59 /usr/lib/pepperflashplugin-nonfree/libpepflashplayer.so


```


Firefox:
[ATTACH=CONFIG]257558[/ATTACH]

---

### Post by bobnn on 2014-11-01
Here is a URL that locks right up:

[https://www.youtube.com/watch?v=5jP_WQIpVr4](https://www.youtube.com/watch?v=5jP_WQIpVr4)

There is also a firefox add-on that makes Flash the default.

Should I be opening a bug on this?

---

### Post by bobnn on 2014-11-03
ARGHHH!!!!!  So the problem is NOT as stated - it only is an issue when using su, gksu, sux, etc - the Flash Player work fine for the user that logged in thru the graphic interface.

It seems like a lot of different X things are breaking when I try to run as other than the graphically logged user - stuff that used to work just fine in 12.04 via sux or gksu.

---

### Post by bobnn on 2014-11-06
And now it all works fine.  And I have no idea why.

---

