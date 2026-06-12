---
title: "Hulu"
date: 2009-07-24
forum: Multimedia Software
---

### Post by johnswb on 2009-07-24
I'm I the only one that hulu.com is not working for under Ubuntu 9.04?  I've trying everything I know and still no go.  I was able to view shows on hulu.com in 8.10 and now I can not.  please help if you can...

---

### Post by philcamlin on 2009-07-24
nope everything is working here

---

### Post by wojox on 2009-07-24
Type:

about : plugins 

In web browser and make sure everything is installed.

Specificly Adobe flash 10.*

---

### Post by johnswb on 2009-07-24
This is what I have.  

  File name: libswfdecmozilla.so
    Shockwave Flash 9.0 r999

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Adobe Flash movie 	swf 	Yes
application/futuresplash 	FutureSplash movie 	spl 	Yes

---

### Post by wojox on 2009-07-24
Remove old:

```
sudo apt-get remove flashplugin-* --purge
```

Upgrade new

```
sudo apt-get install flashplugin-nonfree
```

Restart Browser.

---

### Post by johnswb on 2009-07-24
Did that and still no hulu... I really don't want to re-install just to view hulu.com.

---

### Post by earrame on 2009-07-24
Hulu works fine here in 9.04. Rather, it used to. A series of system updates yesterday (mostly related to Firefox) destroyed video playback from all my normal venues. Hulu, YouTube, etc.

I guess I get to start researching and installing codecs and whatnot for stuff that shouldn't have been broken in the first place.

---

### Post by wojox on 2009-07-24
Search Synaptic for

```
ubuntu-restricted-extras
```

---

### Post by martinbaselier on 2009-07-24
I've found this guide quite helpful in the past.
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

