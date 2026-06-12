---
title: "DVD Playback Weirdness"
date: 2006-06-11
forum: Multimedia &amp; Video
---

### Post by jalefkowit on 2006-06-11
Hey everyone -- 

I recently updated to Kubuntu Dapper and it generally went pretty well, but there's one thing that's not working properly out of the box (even after installing the required non-Free bits): DVD playback.

When I try to play a DVD in Kaffeine, I get the video track, but no audio.  I know the DVD is good because it plays fine in Windows, and on my DVD player.  To see if it was just a Kaffeine thing, I grabbed VLC and tried playing it in there.  In VLC it works great, I get both audio and video.  It's just Kaffeine that's deaf, I guess.

Anyone experienced this?  Is there some setting in Kaffeine I need to tweak to enable audio off a DVD?

---

### Post by blastus on 2006-06-11
I've never had much success with Kaffeine, Totem or any of the other video players. I find xine extremely simple to setup and use. To install DVD playback and xine you would enter the following:
```
sudo apt-get install libdvdread3
sudo /usr/share/doc/libdvdread3/examples/install-css.sh
sudo apt-get install libxine-extracodecs xine-ui
```
When you run xine, click on the DVD button to play a DVD movie. The keyboard shortcuts in xine are fully programmable. Some of the most useful defaults are:
```
ALT-2 (zoom 1:1)
PAGE-UP (previous chapter)
PAGE-DOWN (next chapter)
CTRL-LEFT (rewind 15 seconds)
CTRL-RIGHT (fast forward 15 seconds)
LEFT (rewind 60 seconds)
RIGHT (fast forward 60 seconds)
F (full screen mode)
G (toggle show controls)
E (eject DVD)
```

---

### Post by jalefkowit on 2006-06-11
Well, since I already have playback in VLC I'm not out by much if the answer is just "Kaffeine is broken, find a player that works".  But I went ahead and followed your instructions to install xine anyway, because you can never have too many media players, right?  :-D

The install instructions you gave worked great until the last step, when I got this error:

> Package libxine-extracodecs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libxine-extracodecs has no installation candidate

Wonder what that means?  Maybe the package has been renamed?

---

### Post by blastus on 2006-06-11
libxine-extracodecs is in the multiverse.
```
sudo kwrite /etc/apt/sources.list
```
and look for a line like this (yours may be different if you are in the U.S.):
```
deb http://ca.archive.ubuntu.com/ubuntu/ dapper universe
```
and change it to 
```
deb http://ca.archive.ubuntu.com/ubuntu/ dapper universe multiverse
```
then save the file and
```
sudo apt-get update
sudo apt-get install libxine-extracodecs
```

---

