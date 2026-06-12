---
title: "VLC DVD.  Can't select Menu"
date: 2009-09-17
forum: Multimedia Software
---

### Post by buster2209 on 2009-09-17
I can run DVDs fine with VLC via a DVD in the drive, VIDEO_TS folder on my hard drive or iso image.

When the DVD loads up, I get the menu screen but CANNOT select any of the options.

I have tried using the mouse and the up/down/left/right and enter keys on the keyboard to no avail!

I have tried it with the screen maximised and still no result!

Any help?  :confused:

---

### Post by HappyFeet on 2009-09-17
Check your preferences in vlc. Perhaps restore default settings, or check your OSD settings.

---

### Post by buster2209 on 2009-09-17
> **HappyFeet said:**
> Check your preferences in vlc. Perhaps restore default settings, or check your OSD settings.

Settings have been reset to default and still no joy.

The keyboard shortcuts do work for volume, next, previous, etc.  I just can't select the menu options!

---

### Post by sedawk on 2009-09-17
Does this happen with every DVD?

If it only happens with one/some special DVDs search
the web if there are known problems with that specific
DVD and some DVD players.

I'm using VLC sometimes for some DVDs that are part
of some local computer magazine and the (animated)
menues often stop working after a few idle minutes.

---

### Post by buster2209 on 2009-09-17
> **sedawk said:**
> Does this happen with every DVD?


Not with ACTUAL DVDs in the drive but with EVERY one on my hard drive

---

### Post by mc4man on 2009-09-17
Try a VIDEO_TS this way.

Open vlc -> media -> open disc, Click on browse and go to your VIDEO_TS or the folder holding it, click choose and then play

(maybe also post release of ubuntu and what vlc version you're using

---

### Post by HappyFeet on 2009-09-17
> **buster2209 said:**
> Not with ACTUAL DVDs in the drive but with EVERY one on my hard drive

It is obviously a problem with your extracted dvd images, and not vlc.

---

### Post by buster2209 on 2009-09-17
I'm using Ubuntu Hardy (8.04.3) and VLC version 0.8.6

There isn't a problem with the file I am using.  I transferred the file to an _external_ hard drive and ran it from there.

I can now select menus!  :guitar:

It seems to be a problem when the file or iso is on my _internal_ hard drive

---

### Post by buster2209 on 2009-09-17
File > Open File seems to fix the problem with the internal hard drive problem.

Must be a bug with the version of VLC I am using

---

### Post by mc4man on 2009-09-17
while I use hardy don't have 0.8.6 anymore. The 0.9.9a thru 1.1 git need a video_ts to be opened as a disk rather than a directory for proper navigation, an .iso is no issue (as a file

What you could check in 0.8.6

In terminal
```
alacarte
```

Then go down and highlight Sound & Video, then in r. side box right click on vlc -> properties -> command

If it's vlc %U then change to 
```
vlc %f
```

In 0.8.6 VIDEO_TS can be opened as a directory, .iso as a file

---

### Post by buster2209 on 2009-09-18
> **mc4man said:**
> 

If it's vlc %U then change to 
```
vlc %f
```



Thanks, that did the trick.  I also upgraded to  0.9.9a

What is the difference between vlc %U and vlf %f?

---

### Post by mc4man on 2009-09-18
> What is the difference between vlc %U and vlf %f? 

Descriptions here under the Exec key section
[http://library.gnome.org/devel/desktop-entry-spec/](http://library.gnome.org/devel/desktop-entry-spec/)

Now that you have 0.9.9a .iso's are the same, use - Open file

For a video_ts if you have any trouble then use the method previously described, - Open Disc -> browse  (this way vlc knows it's a dvd format, not just a directory of files

---

