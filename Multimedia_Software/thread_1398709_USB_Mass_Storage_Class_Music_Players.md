---
title: "USB Mass Storage Class Music Players"
date: 2010-02-04
forum: Multimedia Software
---

### Post by dartmusic on 2010-02-04
I am so completely frustrated with this and can't seem to find any solid answers.

I have a Google Nexus One phone.  I want to also use it as a portable music player.  I can find no player for Linux that can do ALL of the following:

- copy music
- transcode when necessary
- transfer cover art in appropriate format
- transfer playlists (music files AND .m3u playlist files)

Banshee is the closest, but it is so painfully slow, has many problems with tags and also doesn't transfer playlist files.  Banshee advertises support "out of the box" for this device.  I've tried overriding with an .is_audio_player file, but it is ignored.

Rhythmbox will transfer song files and transcode as necessary, but no artwork, no playlists.

Exaile doesn't recognize this device for some reason.

Amarok, forget it.

Beyond that, I don't know what to try.

Any suggestions?

Thanks in advance.

---

### Post by dartmusic on 2010-02-06
Really?  Nothing??

---

### Post by dartmusic on 2010-02-16
bump?

---

### Post by dalesd on 2010-02-23
Did you look at Songbird?  There's an extension that lets you selectively transfer playlists to a filesystem based MP3 player.  It's called FolderSync.  I tried it (once so far) and it works fine with my N1.  The initial setup is a little daunting, but after that it's fine.  [http://addons.songbirdnest.com/addon/1535](http://addons.songbirdnest.com/addon/1535)

It does album art and playlists.  I don't know about transcoding.

---

### Post by rossmoore on 2010-02-23
Hiya,

I have an N1. I've tried Songbird, but I was never quite convinced by it. I use Banshee - it's latest "Daily" build from their daily ppa syncs playlists with a device, and I've found it pretty good. I don't transcode much of my audio though, just transfer.

I put the .is_audio_player in the right place and it was immediately recognised as an N1 (although admittedly the picture was of a G1, I think!). You've got the right stuff in the .is_audio_player file?

---

