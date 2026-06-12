---
title: "Need a music manager/player"
date: 2010-02-24
forum: Multimedia Software
---

### Post by undecim on 2010-02-24
I'm very picky about my music, and I'm looking for a good music player.

Previously, I've been using Amarok, but having switched from KDE to fluxbox, I don't want to load all those KDE libs for one program.

if anyone can recommend a music player that matches these features, I would appreciate it.

Features that are required:

1: mp3, ogg, flac support
2: Customizable library hierarchy (A folder-like view of my tracks, and I can choose how those folders are organized)
3: Tag editing of both branches and individual songs
4: Crossfading (If a note is being played across two adjacent tracks on an album, I shouldn't be able to tell where one track ends and the other begins.)
5: A way to set up hotkeys (either customizable hotkeying, command line options to control it, or a dbus interface)

Features not required, but appreciated.

1: Minimize to tray
2: Automatic lyric downloading
3: Automatic album art downloading
4: Jamendo Plugin

Again, if anyone knows of a music player that does all this, I would love to know about it.

Thanks in advance.

---

### Post by Enigmapond on 2010-02-24
[SIZE=3]*Try Banshee or* [I]Guayadeque..both work great for me.
[/I][/SIZE]

---

### Post by entikryst on 2010-02-24
I'm using fluxbox also and recently switched to banshee.  I have no complaints.

---

### Post by undecim on 2010-02-26
I tried banshee, but it was awful buggy on my machine.

After toying around with various players, I think I'm going with xmms2... I just need to find a good client for it now...

Also, it looks like mp3s don't work well with grossfading/gapless playback... stupid proprietary formats... Time to get converting, I guess.

---

### Post by bruno9779 on 2010-02-26
Guayadeque, as said above, is a pretty good lightweight player oriented to very large music collections.

It meets almost all you requirements, I just don't know about jamendo

It is a small project in very active development, I have submitted some minor bugs and have seen them fixed daily!!

---

### Post by undecim on 2010-03-01
After trying guayadeque, I rather like it.

Though I just found out that MP3s don't support gapless playback... Time to start converting my collection to OGG, I guess.

---

### Post by hxcobd on 2010-03-01
Another one I rarely see people mention that I really like is Decibel Audio Player.

Really clean, simple interface, and its built-in directory browser is awesome for those of us that don't use ID3 tags.

It also has a bunch of plugins built-in for stuff like desktop notification, etc.

---

### Post by rabiabidabi on 2010-03-01
I have tried several. Rhythmbox sends import errors to the trash ( I almost lost 1400 songs). Banshee has horrible metadata fetching. Amarok won't even start. Listen,also, had many import errors. I tried Guayadeque over the past weekend and nothing really worked right at all. Listen was bad at importing, too.

So, I'm using Exaille. No equalizer (supposed to, but I can't find it.) It imported my entire collection from an external drive, though the metadata (present in properties/details) has to be manually added in the library for about 1500 songs out of 4050.

I am not, so far, happy with any of them, but I'm having fun trying them all.

---

### Post by DubyBreaks on 2010-03-03
I've tried a bunch of media players as well (RB, Banshee, Amarok, Audacious2, Exaile, Minirok, Songbird, Beep, Listen) and the one that I like the best (and just recently ran across) is Guayadeque (G-que for short).  It is pretty new and is being updated often, great for large music collection, worked great for me ootb, and the interface can be customized to your liking.  Lots of potential in this one!

---

### Post by mcduck on 2010-03-03
> **undecim said:**
> After trying guayadeque, I rather like it.

Though I just found out that MP3s don't support gapless playback... Time to start converting my collection to OGG, I guess.

MP3's work  just fine with gapless playback & crossfades. If you have troubles doing that then either your files use some strange, non-standard structure for tags or weird enconding, or your player application just fails to do this correctly. Actually you are much mor elielly finding yourself in troubles trying to do this with Ogg files.

I've never had any troubles with gapless playback of my MP3 files (I use MPD with Sonata and ncmpcpp as clients, by the way).

---

### Post by undecim on 2010-03-04
> **mcduck said:**
> MP3's work  just fine with gapless playback & crossfades. If you have troubles doing that then either your files use some strange, non-standard structure for tags or weird enconding, or your player application just fails to do this correctly. Actually you are much mor elielly finding yourself in troubles trying to do this with Ogg files.

I've never had any troubles with gapless playback of my MP3 files (I use MPD with Sonata and ncmpcpp as clients, by the way).

[http://en.wikipedia.org/wiki/Gapless_playback#Format_support](http://en.wikipedia.org/wiki/Gapless_playback#Format_support)

I have tracks that segue into the next. Many of them have a clicking sound between the tracks, which I really hate. The only pattern I can find between tracks that do and don't click is that the ones that do are always MP3, and the ones that don't are always OGG or FLAC.

---

### Post by mcduck on 2010-03-05
> **undecim said:**
> [http://en.wikipedia.org/wiki/Gapless_playback#Format_support](http://en.wikipedia.org/wiki/Gapless_playback#Format_support)

I have tracks that segue into the next. Many of them have a clicking sound between the tracks, which I really hate. The only pattern I can find between tracks that do and don't click is that the ones that do are always MP3, and the ones that don't are always OGG or FLAC.

Well, I can  only repeat what I already said, I have no problems with gapless playback of MP3 files so it must be either because of the player I use, or the files themselves.

No wikipedia article can change that. :D

edit: notice this line in the article you posted: "LAME-encoded MP3 can be gapless with players that support the LAME Mp3 info tag.". This could be the reason, since I've always used LAME as my encoder.

---

### Post by stylofone on 2010-05-27
I've had a similar experience to rabiabidabi. Gmusicbrowser is the latst one to disappoint, its index got amnesia. I actually find the venerable Methlab to be a good, simple, reliable music indexer. Unfortunately upgrading to Lucid/xfce meant Audacious wouldn't partner with it, but I've just got xmms2/Esperanza to work as its player. It's no-frills, but it finds songs and plays them from the 50,000 files on my NAS.

> **rabiabidabi said:**
> 

I am not, so far, happy with any of them, but I'm having fun trying them all.

---

