---
title: "DBUS MPRIS emitted by amarok?"
date: 2008-09-21
forum: Multimedia Software
---

### Post by bmhm on 2008-09-21
Hi there,

I wondered when I saw that amarok emits mpris-signals over dbus. My amarok installation does not. Audacious on the other hand does.

So I'd like to ask readers of this thread to help me testing my new plugin:
Open a new terminal and type:
```
dbus-monitor "interface='org.freedesktop.MediaPlayer'"
```

Now, when you start/stop playing a song in your favourite audio player, do you get any messages? I don't, expect for audacious. VLC, Totem, Amarok... they just won't emit anything.

-----

Well, why am I asking? I am about to code a new plugin for Pidgin, I call it "cooroo" (like the sound of a pidgeon). 

What it does: 
Setting your Status to your current track, artist, album.
If someone writes you a magic word (like !cooroo), a file transfer of the current track will automatically start.

I found that none of the existing plugins are working for me. I tried musictracker, currenttrack, audacious-pidgin and a few others. Mine does work (for me, and hopefully for others, too).

So if you like to help me with this plugin, just tell me whether there are signals emitted by amarok and such.

Thanks!

---

### Post by jack24 on 2009-10-11
I get a signal.  This is what I get when I start a song, then switch to a couple of different ones:


l@l-laptop:~$ dbus-monitor "interface='org.freedesktop.MediaPlayer'"
signal sender=org.freedesktop.DBus -> dest=:1.139 serial=2 path=/org/freedesktop/DBus; interface=org.freedesktop.DBus; member=NameAcquired
   string ":1.139"
method call sender=:1.67 -> dest=:1.139 serial=437 path=/org/freedesktop/indicate; interface=org.freedesktop.DBus.Properties; member=Get
   string "org.freedesktop.indicator"
   string "type"
signal sender=:1.100 -> dest=(null destination) serial=302 path=/Player; interface=org.freedesktop.MediaPlayer; member=TrackChange
   array [
      dict entry(
         string "album"
         variant             string "At Fillmore East"
      )
      dict entry(
         string "artist"
         variant             string "Allman Brothers Band"
      )
      dict entry(
         string "arturl"
         variant             string ""
      )
      dict entry(
         string "audio-bitrate"
         variant             int32 128
      )
      dict entry(
         string "audio-samplerate"
         variant             int32 44100
      )
      dict entry(
         string "comment"
         variant             string ""
      )
      dict entry(
         string "genre"
         variant             string "Rock"
      )
      dict entry(
         string "location"
         variant             string "file:///storage/Music/Allman%20Brothers%20Band/At%20Fillmore%20East/01%20-%20Allman%20Brothers%20Band%20-%20At%20Fillmore%20East%20-%20Statesboro%20Blues.mp3"
      )
      dict entry(
         string "mtime"
         variant             int64 257000
      )
      dict entry(
         string "rating"
         variant             int32 0
      )
      dict entry(
         string "time"
         variant             int64 257
      )
      dict entry(
         string "title"
         variant             string "Statesboro Blues"
      )
      dict entry(
         string "tracknumber"
         variant             int32 1
      )
      dict entry(
         string "year"
         variant             string "1971"
      )
   ]
signal sender=:1.100 -> dest=(null destination) serial=303 path=/Player; interface=org.freedesktop.MediaPlayer; member=StatusChange
   struct {
      int32 0
      int32 0
      int32 0
      int32 0
   }
signal sender=:1.100 -> dest=(null destination) serial=304 path=/Player; interface=org.freedesktop.MediaPlayer; member=CapsChange
   int32 116
signal sender=:1.100 -> dest=(null destination) serial=305 path=/Player; interface=org.freedesktop.MediaPlayer; member=StatusChange
   struct {
      int32 2
      int32 0
      int32 0
      int32 0
   }
signal sender=:1.100 -> dest=(null destination) serial=306 path=/Player; interface=org.freedesktop.MediaPlayer; member=CapsChange
   int32 107
signal sender=:1.100 -> dest=(null destination) serial=307 path=/Player; interface=org.freedesktop.MediaPlayer; member=StatusChange
   struct {
      int32 2
      int32 0
      int32 0
      int32 0
   }
signal sender=:1.100 -> dest=(null destination) serial=308 path=/Player; interface=org.freedesktop.MediaPlayer; member=CapsChange
   int32 107
signal sender=:1.100 -> dest=(null destination) serial=309 path=/Player; interface=org.freedesktop.MediaPlayer; member=StatusChange
   struct {
      int32 2
      int32 0
      int32 0
      int32 0
   }
signal sender=:1.100 -> dest=(null destination) serial=310 path=/Player; interface=org.freedesktop.MediaPlayer; member=CapsChange
   int32 107
signal sender=:1.100 -> dest=(null destination) serial=311 path=/Player; interface=org.freedesktop.MediaPlayer; member=StatusChange
   struct {
      int32 0
      int32 0
      int32 0
      int32 0
   }
signal sender=:1.100 -> dest=(null destination) serial=312 path=/Player; interface=org.freedesktop.MediaPlayer; member=CapsChange
   int32 119
signal sender=:1.100 -> dest=(null destination) serial=317 path=/Player; interface=org.freedesktop.MediaPlayer; member=StatusChange
   struct {
      int32 0
      int32 0
      int32 0
      int32 0
   }
signal sender=:1.100 -> dest=(null destination) serial=318 path=/Player; interface=org.freedesktop.MediaPlayer; member=CapsChange
   int32 119
signal sender=:1.100 -> dest=(null destination) serial=320 path=/Player; interface=org.freedesktop.MediaPlayer; member=TrackChange
   array [
      dict entry(
         string "album"
         variant             string "At Fillmore East"
      )
      dict entry(
         string "artist"
         variant             string "Allman Brothers Band"
      )
      dict entry(
         string "arturl"
         variant             string ""
      )
      dict entry(
         string "audio-bitrate"
         variant             int32 128
      )
      dict entry(
         string "audio-samplerate"
         variant             int32 44100
      )
      dict entry(
         string "comment"
         variant             string ""
      )
      dict entry(
         string "genre"
         variant             string "Rock"
      )
      dict entry(
         string "location"
         variant             string "file:///storage/Music/Produced%20CDs%202/CD-18/The%20Allman%20Brothers%20Band%20-%20Statesboro%20Blues.mp3"
      )
      dict entry(
         string "mtime"
         variant             int64 246000
      )
      dict entry(
         string "rating"
         variant             int32 0
      )
      dict entry(
         string "time"
         variant             int64 246
      )
      dict entry(
         string "title"
         variant             string "Statesboro Blues 3"
      )
      dict entry(
         string "tracknumber"
         variant             int32 1
      )
      dict entry(
         string "year"
         variant             string "1971"
      )
   ]
signal sender=:1.100 -> dest=(null destination) serial=321 path=/Player; interface=org.freedesktop.MediaPlayer; member=StatusChange
   struct {
      int32 0
      int32 0
      int32 0
      int32 0
   }
signal sender=:1.100 -> dest=(null destination) serial=322 path=/Player; interface=org.freedesktop.MediaPlayer; member=CapsChange
   int32 119
signal sender=:1.100 -> dest=(null destination) serial=323 path=/Player; interface=org.freedesktop.MediaPlayer; member=StatusChange
   struct {
      int32 2
      int32 0
      int32 0
      int32 0
   }
signal sender=:1.100 -> dest=(null destination) serial=324 path=/Player; interface=org.freedesktop.MediaPlayer; member=CapsChange
   int32 107
signal sender=:1.100 -> dest=(null destination) serial=325 path=/Player; interface=org.freedesktop.MediaPlayer; member=StatusChange
   struct {
      int32 2
      int32 0
      int32 0
      int32 0
   }
signal sender=:1.100 -> dest=(null destination) serial=326 path=/Player; interface=org.freedesktop.MediaPlayer; member=CapsChange
   int32 107
signal sender=:1.100 -> dest=(null destination) serial=327 path=/Player; interface=org.freedesktop.MediaPlayer; member=StatusChange
   struct {
      int32 2
      int32 0
      int32 0
      int32 0
   }
signal sender=:1.100 -> dest=(null destination) serial=328 path=/Player; interface=org.freedesktop.MediaPlayer; member=CapsChange
   int32 107
signal sender=:1.100 -> dest=(null destination) serial=329 path=/Player; interface=org.freedesktop.MediaPlayer; member=StatusChange
   struct {
      int32 0
      int32 0
      int32 0
      int32 0
   }
signal sender=:1.100 -> dest=(null destination) serial=330 path=/Player; interface=org.freedesktop.MediaPlayer; member=CapsChange
   int32 119
signal sender=:1.100 -> dest=(null destination) serial=331 path=/Player; interface=org.freedesktop.MediaPlayer; member=StatusChange
   struct {
      int32 0
      int32 0
      int32 0
      int32 0
   }
signal sender=:1.100 -> dest=(null destination) serial=332 path=/Player; interface=org.freedesktop.MediaPlayer; member=CapsChange
   int32 119
signal sender=:1.100 -> dest=(null destination) serial=334 path=/Player; interface=org.freedesktop.MediaPlayer; member=TrackChange
   array [
      dict entry(
         string "album"
         variant             string "Dreams"
      )
      dict entry(
         string "artist"
         variant             string "Allman Brothers Band"
      )
      dict entry(
         string "arturl"
         variant             string ""
      )
      dict entry(
         string "audio-bitrate"
         variant             int32 160
      )
      dict entry(
         string "audio-samplerate"
         variant             int32 44100
      )
      dict entry(
         string "comment"
         variant             string ""
      )
      dict entry(
         string "genre"
         variant             string "Rock"
      )
      dict entry(
         string "location"
         variant             string "file:///storage/Music/Allman%20Brothers%20Band/Dreams/Allman%20Brothers%20Band%20-%20Dreams%20-%20Morning%20Dew.mp3"
      )
      dict entry(
         string "mtime"
         variant             int64 223000
      )
      dict entry(
         string "rating"
         variant             int32 0
      )
      dict entry(
         string "time"
         variant             int64 223
      )
      dict entry(
         string "title"
         variant             string "Morning Dew"
      )
      dict entry(
         string "tracknumber"
         variant             int32 0
      )
      dict entry(
         string "year"
         variant             string "1989"
      )
   ]
signal sender=:1.100 -> dest=(null destination) serial=335 path=/Player; interface=org.freedesktop.MediaPlayer; member=StatusChange
   struct {
      int32 0
      int32 0
      int32 0
      int32 0
   }
signal sender=:1.100 -> dest=(null destination) serial=336 path=/Player; interface=org.freedesktop.MediaPlayer; member=CapsChange
   int32 119
signal sender=:1.100 -> dest=(null destination) serial=337 path=/Player; interface=org.freedesktop.MediaPlayer; member=StatusChange
   struct {
      int32 2
      int32 0
      int32 0
      int32 0
   }
signal sender=:1.100 -> dest=(null destination) serial=338 path=/Player; interface=org.freedesktop.MediaPlayer; member=CapsChange
   int32 107
signal sender=:1.100 -> dest=(null destination) serial=339 path=/Player; interface=org.freedesktop.MediaPlayer; member=StatusChange
   struct {
      int32 2
      int32 0
      int32 0
      int32 0
   }
signal sender=:1.100 -> dest=(null destination) serial=340 path=/Player; interface=org.freedesktop.MediaPlayer; member=CapsChange
   int32 107
signal sender=:1.100 -> dest=(null destination) serial=341 path=/Player; interface=org.freedesktop.MediaPlayer; member=StatusChange
   struct {
      int32 2
      int32 0
      int32 0
      int32 0
   }
signal sender=:1.100 -> dest=(null destination) serial=342 path=/Player; interface=org.freedesktop.MediaPlayer; member=CapsChange
   int32 107
signal sender=:1.100 -> dest=(null destination) serial=343 path=/Player; interface=org.freedesktop.MediaPlayer; member=StatusChange
   struct {
      int32 0
      int32 0
      int32 0
      int32 0
   }
signal sender=:1.100 -> dest=(null destination) serial=344 path=/Player; interface=org.freedesktop.MediaPlayer; member=CapsChange
   int32 119
signal sender=:1.100 -> dest=(null destination) serial=345 path=/Player; interface=org.freedesktop.MediaPlayer; member=StatusChange
   struct {
      int32 0
      int32 0
      int32 0
      int32 0
   }
signal sender=:1.100 -> dest=(null destination) serial=346 path=/Player; interface=org.freedesktop.MediaPlayer; member=CapsChange
   int32 119

---

### Post by bmhm on 2009-10-13
Thanks, must be amarok2. When I was developing, there was only Amarok fast forward.

It's just been a kind of case study: My plugin did work flawlessly, but there was no configuration. I just wanted to see whether I could do such a plugin.

Thanks anyway, I might need that information some day.
Regards

---

