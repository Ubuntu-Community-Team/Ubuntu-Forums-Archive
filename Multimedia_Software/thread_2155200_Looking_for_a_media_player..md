---
title: "Looking for a media player."
date: 2013-06-17
forum: Multimedia Software
---

### Post by Cheesemill on 2013-06-17
Hi there guys and gals.

I'm looking for a new media player but I have a specific requirement.

For one of my conky scripts I need to be able to query the music player for the full path of the currently playing song from the command line. I was happy enough using Rhythmbox until now but unfortunately it doesn't have this feature.

I've tried Audacious and it does what I need but I'm not happy with the way it handles large music libraries.

I'd rather not have to pull in the K libraries as I don't have them installed on my system for anything else.

Any suggestions?

---

### Post by Toz on 2013-06-17
Here are a couple of suggestions:

1. gmusicbrowser - have a look at its [dbus api]("http://wiki.gmusicbrowser.org/dbus_api") for info on how to get song information:
```
$ dbus-send --print-reply --dest=org.gmusicbrowser /org/gmusicbrowser org.gmusicbrowser.CurrentSong
method return sender=:1.417 -> dest=:1.434 reply_serial=2
   array [
      dict entry(
         string "album_picture"
         string "/home/toz/Music/A Tattered Line Of String [The Postal Service].mp3"
      )
      dict entry(
         string "track"
         string "2"
      )
      dict entry(
         string "file"
         string "A Tattered Line Of String [The Postal Service].mp3"
      )
      dict entry(
         string "path"
         string "/home/toz/Music/"
      )
      dict entry(
         string "uri"
         string "file:///home/toz/Music/A%20Tattered%20Line%20Of%20String%20%5BThe%20Postal%20Service%5D.mp3"
      )
      dict entry(
         string "album"
         string "Give Up (10th Anniversary Deluxe Edition)"
      )
      dict entry(
         string "artist"
         string "The Postal Service"
      )
      dict entry(
         string "length"
         string "188"
      )
      dict entry(
         string "title"
         string "A Tattered Line Of String"
      )
      dict entry(
         string "disc"
         string "0"
      )
      dict entry(
         string "album_artist"
         string "The Postal Service"
      )
   ]
```

2. cmus (console-based and my favourite) - just enable the built-in status_display_program and use "cmus-remote -Q" to get a full report of the playing song:
```
$ cmus-remote -Q
status paused
file /home/toz/Music/Radiohead - Exit Music (For a Film).flac
duration 264
position 183
tag title Exit Music (for a Film)
tag artist Radiohead
tag albumartist Radiohead
tag album OK Computer
tag date 1997
tag tracknumber 04
tag genre Alternative
set aaa_mode all
set continue true
set play_library false
set play_sorted false
set replaygain disabled
set replaygain_limit true
set replaygain_preamp 6.000000
set repeat true
set repeat_current false
set shuffle true
set softvol false
set vol_left 101
set vol_right 101

```

---

