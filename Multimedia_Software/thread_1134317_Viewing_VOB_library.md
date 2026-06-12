---
title: "Viewing VOB library"
date: 2009-04-23
forum: Multimedia Software
---

### Post by sasampson on 2009-04-23
Hello:  

I have an extensive DVD library that I've ripped to disk (VOB files) on an 8.04 LTS Ubuntu server.  I would like to be able to serve up that content to a large monitor through an HTPC.  

The problem I'm running into is that it seems that nothing wants to use/play/display VOB files. I don't want to have to re-rip/convert the content, especially if I'm going to lose resolution by doing so.  Is there some way to do this, or will I have do break down and use something like Handbrake to convert all my content to something like H.264?  

Thanks in advance for you thoughts and advice.

Sven

---

### Post by andrew.46 on 2009-04-23
Hi Sven,

MPlayer will do this by using the -dvd-device option:

> 
-dvd-device <path to device> (DVD only)
Specify the DVD device or .iso  filename (default: /dev/dvd).
You can also specify a directory that contains files previously
copied directly from a DVD (with e.g. vobcopy).


Hopefully this is what you are after?

Andrew

---

### Post by mc4man on 2009-04-23
If your still having difficulty maybe clarify this

> it seems that **nothing** wants to use/play/display **VOB files**

If you've ripped to file maintaining dvd video format than the .VOBS should be in a VIDEO_TS with .ifo's and .bup's.
The VIDEO_TS should be a folder with the movie name (or whatever, not important

If that's the case you want to have your player (?) open a directory, (the folder containing the VIDEO_TS), not a file.

As far as a few players

smplayer should have no difficulty as long as you have it open the folder containing the VIDEO_TS (some combo's of smplayer and mplayer will fail if told to open the VIDEO_TS directly

vlc 0.9x - 1,0 pre **can** have problems opening a directory containing a VIDEO_TS, most likely will crash (works ocassionally with some builds.
(( If vlc is used from the opposite direction then it will work fine, ie. right click on the VIDEO_TS or folder containing one -> 'open with vlc' (don't know if that's possible in your set up

mplayer from the cli just as andrew described

ex 
mplayer -dvd-device /home/doug/Videos/THE_WRESTLER/VIDEO_TS dvd://[COLOR="Red"]1[/COLOR] <additional options>
(where red is the title # of main movie

or with  a dvdnav mplayer
mplayer -dvd-device /home/doug/Videos/THE_WRESTLER/VIDEO_TS dvdnav:// <additional options>

Totem-xine should work fine

Totem-gstreamer should be avoided (for all dvd video, file or .iso

If you where to 'convert' I'd just turn your VIDEO_TS's into .iso's, then all the above players should work fine, in that case your just opening a file, not a directory.


Note: in some cases if you ripped a title with structure protection and some sectors were skipped then playback will be affected if the rip isn't repaired first. (would only be a small % of your 'collection', if at all.

---

