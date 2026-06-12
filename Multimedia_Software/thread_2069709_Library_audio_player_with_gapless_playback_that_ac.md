---
title: "Library audio player with gapless playback that actually WORKS?"
date: 2012-10-11
forum: Multimedia Software
---

### Post by MrsUser on 2012-10-11
I'm on Ubuntu 12.04 (64-bit) and tried the following music players:

- Rhythmbox
- Banshee
- Guayadeque
- gmusicbrowser
- Quod Libet
- Clementine

Gapless playback is not working with any of them, contrary to what the developers claim. I know that mp3 is not a format that supports gapless playback natively. However, it's 2012 and still no gapless playback for mp3 files in Linux whereas this is not an issue at all in Windows for years now.

At the moment I have Audacious installed, which is the only player so far that is capable of doing gapless playback with my mp3 collection. But: It does not use a database, i.e. it has no music library manager.

I read about MPD with client frontend. But this isn't very handy to fiddle with the install, and the UI of those clients seems poor.

I'd like to ENJOY listening to music, with a nice, handy UI and a good library management. Basically I'm looking for something like Banshee, Guayadeque or Rhythmbox or gmusicbrowser, but with WORKING gapless playback.

Any recommendations?

EDIT:
I have tried Sonata + MPD today. And gapless playback works. However, the whole library management and UI feeling is awkward. I'm really looking for something like Banshee or Rhythmbox or Guayadeque, but with gapless playback for mp3 (my music is encoded with Lame).

---

### Post by MrsUser on 2012-10-16
After trying out many audio players, I finally came to the conclusion that **Quod Libet** is the best. As for a combination of library management, tagging capabilities, ease of use and UI design, there is nothing that can beat this player. It's layout is very smart, with different views centered on what you want to do (listen to albums, browse your collection, radio streams, etc). The whole interface is clean, straightforward, very functional, yet good-looking. Everything is in the right place, not as inconsistent and overloaded as some of the other players I've tried.

The functions and elements are well thought out and chosen. They all make sense and  don't clutter the player with tons of tabs and dozens of items in nested submenus. Yet Quod Libet can be customized very well and comes with many plugins. Also, it is one of the few audio players that support multiple genres and display embedded cover art properly (respecting covers per file, not setting the same cover for all files per folder). I think it should be the default player in Ubuntu. By the way, it integrates well in Ubuntu's sound control menu via plugin. And you can also have a tray icon via plugin (you need to whitelist 'quodlibet' with Dconf editor).

For mix albums or audio books I use Audacious for the time being. It's the only player I tried that does proper gapless playback. Of course, I hope for gapless playback in a future version of Quod Libet (that is to say that gstreamer gets fixed), so that it can be my only audio player on the system. However, Audacious is good as a second audio player, for those occasions when only quickly listening to a single audio file. I also found out that Audacious has a plugin called 'search tool' which can  index your music into one big playlist which you can then search. Not  very satisfying if you are someone who needs a player for large collections. But it's enough for using it with audio books.

[[IMG]http://i.imgur.com/yQV9Xl.png[/IMG]]("http://imgur.com/yQV9X")

---

### Post by hugmenot on 2012-10-18
MP3 is very much gapless whn encoded properly. Even in Quod Libet.

Since there's nothing in the MP3 standard to provide for this there are encoder specific standards. If encoded with LAME your MP3 play back gaplessly because of the LAME header. IF the same holds true for the iTunes header I'm not sure.

All other formats, as in Vorbis, MP4 AAC, FLAC, etc should be gapless natively.

tl;dr it's your files.

---

### Post by MrsUser on 2012-10-18
> **hugmenot said:**
> MP3 is very much gapless whn encoded properly. Even in Quod Libet.

Since there's nothing in the MP3 standard to provide for this there are encoder specific standards. If encoded with LAME your MP3 play back gaplessly because of the LAME header.

I encoded all the Mp3 files in question with latest LAME encoder and they do have the LAME tags. Still, Quod Libet does not playback them gaplessly, nor does any other of the other gstreamer-based players. It's not Quod Libet's fault, it's a gstreamer problem. I've done a bit more research and it seem gapless playback is broken in Ubuntu 12.04.

> **hugmenot said:**
> tl;dr it's your files.      What is **tl;dr** ?

---

### Post by mb_3000 on 2012-10-23
I've been looking for galpless playback in linux for years and always failed. 
the only two players that manage to do it properly are audacious and deadbeef. but sadly, both lack plenty of other features to make them usable (database, lyrics, etc) 

the other option you have is using foobar2000 through wine and pray that wine plays nice with pulseaudio. which is something it doesn't do for me.

---

### Post by alfh on 2012-12-25
Maybe it was something about 64-bit causing your gapless trouble? I'm on Ubuntu Studio 12.10 (32-bit) and experiencing gapless playback with both gmusicbrowser and clementine.

I like both players by the way. Clementine is more demanding on resources, but has by far the better-looking interface and detects more songs. gmusicbrowser is very light on resources, very fast and very customisable. Its tag editing dialog beats competition hands down.

Both of them miss a feature I'd like, namely to display artist info, lyrics, etc on songs not playing. As far as I can see both players show this info only for the songs currently playing.

---

