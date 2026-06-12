---
title: "Add MP3 tag ID3v1 and ID3v2"
date: 2007-05-18
forum: Multimedia &amp; Video
---

### Post by yaidiot! on 2007-05-18
I'm using Sound Juicer to rip discs with the following encoding line:

audio/x-raw-int,rate=44100,channels=2 ! lame name=enc vbr=0 bitrate=160 ! id3v2mux

No trouble encoding and the id3v2.4 tag are written properly.

However, I'd like to have is both id3v1 and v2.4 tags written. Is there a way to include both types of tags?

---

### Post by yaidiot! on 2007-05-22
I found a workaround. Grip writes both id3v1 and id3v2 tags.

For those who may want to try it:
```
sudo aptitude install grip lame
```
Go to Config/ID3 to set tagging. Test the tags at the command line with 
```
m3info
``` for the id3v1, and for the id3v2.x tags ```
mid3v2
```
One side note, it appears Grip writes the more common id3v2.3 tag rather than v2.4 added in the above pipline. -- If anyone is able to get id3v1 *and* id3v2 from sound-juicer, I'd still appreciate hearing it.

---

