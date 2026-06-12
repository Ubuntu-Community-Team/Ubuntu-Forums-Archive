---
title: "rhythmbox playlist export script"
date: 2009-05-20
forum: Multimedia Software
---

### Post by brw02005 on 2009-05-20
Well I am running a dual boot of windows and linux, and have a nokia n810, midia center pc, and an xbox running xbmc.  I would like to be able to run a script that will export my playlists from rhythmbox and edit the paths then I will use unison to sync up all of this stuff.

---

### Post by kostkon on 2009-05-20
If your systems are in the same network then you could use the DAAP plugin that comes with Rhythmbox by default. For more info about [DAAP]("http://en.wikipedia.org/wiki/Digital_Audio_Access_Protocol") check here.

I assume you can use iTunes or other software that supports DAAP in your media PC and I believe XBMC supports DAAP too, although I may be wrong here.

Also, if your mobile works like an MTP device then just connect it to your system and Rhythmbox will be able to sync with it.

If it is recognised as a USB mass storage device, you can create an empty file with the filename
```
.is_audio_player
```
to make Rhythmbox to see it as a media player.

Hope that helps.

---

### Post by brw02005 on 2009-05-20
I like daap and it does work quite well problem is that I haven't found anything in linux that can edit my itunes library and I can also use it for rhythmbox but then I can't edit it in windows.  I would prefer to just export my new playlist I made in linux since that what I use it for most the time.  A nokia n810 runs a form of linux similar to ubuntu called maemo I typically use SSH to transfer files to it wirelessly.  I could plug it in and use it as a flash drive however, I am looking for an automated solution.  Thanks for your suggestion but I have way too many thing I like making and editing playlists from.

---

