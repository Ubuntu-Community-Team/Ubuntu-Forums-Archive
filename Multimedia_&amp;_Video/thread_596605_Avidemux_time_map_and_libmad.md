---
title: "Avidemux time map and libmad?"
date: 2007-10-29
forum: Multimedia &amp; Video
---

### Post by the_mouse on 2007-10-29
Hi, guys!
I'm using Avidemux and want to encode an audio stream with quality based option and I read that:
> To compute the start offset/size, Avidemux has to know how the bitrate changes. For that use Audio->Build VBR Time Map. 

Avidemux will then decompress the whole stream one time and build a time map to know how to handle the stream. You will need libmad installed, else it will do nothing.
But I can't find the exact libmad package, there's only libmad0 and it's installed, but I still can't build the time map :(
When i run avidemux from the console and when I click on "Build VBR time map" there's a message:
 making audio timeline
and nothing else happens :(
I'm using the mp3 (LAME) and Vorbis codecs with avidemux 2.3.99 (same as in previous versions :()
Any ideas why?

---

### Post by tagawa on 2008-02-13
I know this is old and probably no longer relevant, but just in case...

Try installing libmad0-dev - it's needed for building VLC, etc. and might be what's needed for your audio timeline.

HTH

---

