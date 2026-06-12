---
title: "[SOLVED] How to use laptop as a media hub?"
date: 2007-07-13
forum: Multimedia &amp; Video
---

### Post by ubuhick on 2007-07-13
I know what I want to do, but I don't know the correct terminology to get a concise search.  

I have a desktop with 2 harddrives.  One hardrive contains programs; the other is used as file storage.  The storage hardrive has all my audio files.  I want to be able to access these audio files from my laptop so I can play the music in another room.  

I've got the wireless router.

What I'm asking for is some help narrowing down what to search and ask for.  I've tried home networking but it is such a broad topic. 

Thanks,

Ubuhick



.

---

### Post by ubuhick on 2007-07-13
I know what I want to do, but I don't know the correct terminology to get a concise search.

I have a desktop with 2 harddrives. One hardrive contains programs; the other is used as file storage. The storage hardrive has all my audio files. I want to be able to access these audio files from my laptop so I can play the music in another room.

I've got the wireless router.

What I'm asking for is some help narrowing down what to search and ask for. I've tried home networking but it is such a broad topic.

Thanks,

Ubuhick

---

### Post by spd106 on 2007-07-13
The simplest way would be to use DAAP in Rhythmbox.

Basically all you do to set up the server is import your music into Rhythmbox or set it to watch your music directory, then enable sharing the DAAP Music Sharing Plugin.

Now when you open Rhythmbox or any other application that supports DAAP on a client, it will find the share automatically. Just click to play. It also imports playlists and favourites meta-data, though no album art yet.

This used to work very well with iTunes on a Mac or even on Windows (with Bonjour for Windows as well). But Apple crippled it with v7, so now it will only act as a client unless you have iTunes on both ends. DRM Boo! :evil: etc.

There are several alternatives to Rhythmbox, such as Amarok, Tangerine, Firefly, daapd, etc

There's no video support, this is only for music. To do video you'll probably have to stream it through a dedicated server application like VLC.

---

### Post by ubuhick on 2007-07-13
Thanks spd106!  

I already use rhythmbox so everything you suggested worked like a charm.

I was ready to dive into networking technobabble, but this was effortless.

Thanks again.

---

### Post by ubuhick on 2007-07-13
I figured out how to do it.  Real simple.

If anyone reading this wants to do the same thing, check this thread out:

[http://ubuntuforums.org/showthread.php?t=500128]("http://ubuntuforums.org/showthread.php?t=500128")

---

