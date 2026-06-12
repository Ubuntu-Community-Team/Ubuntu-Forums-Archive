---
title: "Playing AAC iTunes files in banshee?"
date: 2010-02-10
forum: Multimedia Software
---

### Post by Tsquad on 2010-02-10
im wondering if this is possible. I have downloaded every gstreamer plugin possible and they still dont play. any ideas? im running ubuntu 9.10

---

### Post by VertexPusher on 2010-02-10
Encrypted AAC files from iTunes can only be played back on Apple hardware. You are just experiencing the effects of vendor lock-in.

If you don't like vendor lock-in, don't buy from iTunes. Purchase unencrypted MP3 files from Amazon or other platforms instead.

---

### Post by Uncle Spellbinder on 2010-02-10
> **VertexPusher said:**
> Encrypted AAC files from iTunes can only be played back on Apple hardware.

Actually, that should be *software*. On my Windows boot, I download from iTunes regularly. No issues playing anything downloaded from iTunes on a Windows machine as long as it's being played in iTunes.

---

### Post by End Us3r on 2010-02-10
> **VertexPusher said:**
> If you don't like vendor lock-in, don't buy from iTunes. Purchase unencrypted MP3 files from Amazon or other platforms instead.

100% of the songs available from the iTunes music store are DRM free. Every single one of my AAC songs purchased from the iTunes music store plays via Rhythmbox (which uses GStreamer) under Karmic.

It sounds like the OP may be trying to play protected AAC content. The OP can upgrade their protected AAC content to remove the DRM:

[http://support.apple.com/kb/HT1711](http://support.apple.com/kb/HT1711)


DRM free music from iTunes was announced way back in 2007:

[http://www.apple.com/pr/library/2007/05/30itunesplus.html](http://www.apple.com/pr/library/2007/05/30itunesplus.html)

---

### Post by Tsquad on 2010-02-10
> **End Us3r said:**
> 100% of the songs available from the iTunes music store are DRM free. Every single one of my AAC songs purchased from the iTunes music store plays via Rhythmbox (which uses GStreamer) under Karmic.

It sounds like the OP may be trying to play protected AAC content. The OP can upgrade their protected AAC content to remove the DRM:

[http://support.apple.com/kb/HT1711](http://support.apple.com/kb/HT1711)


DRM free music from iTunes was announced way back in 2007:

[http://www.apple.com/pr/library/2007/05/30itunesplus.html](http://www.apple.com/pr/library/2007/05/30itunesplus.html)
so your saying i should be able to get it i to work with rythmbox and gstreamer? and what do you mean i can "upgraded my protected acc content" and what is "DRM"

---

### Post by End Us3r on 2010-02-10
> **Tsquad said:**
> so your saying i should be able to get it i to work with rythmbox and gstreamer? and what do you mean i can "upgraded my protected acc content" and what is "DRM"


**DRM**
[http://en.wikipedia.org/wiki/Digital_rights_management]("http://en.wikipedia.org/wiki/Digital_rights_management")

I can play music I purchased from iTunes in Rythmbox and Songbird. If your music has no DRM then you should be able to as well (see below).


The following only applies if you purchased music from the iTunes music store:

If you have a .m4a file extension on your AAC music files then they are not DRM'ed. If you have a .m4p file extension on your music files then they are DRM'ed and you need to uprade them via iTunes to remove the DRM: [http://support.apple.com/kb/HT1711]("http://support.apple.com/kb/HT1711")

---

