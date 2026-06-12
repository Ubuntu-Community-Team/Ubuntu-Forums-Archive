---
title: "Recording shoutcast radio streams."
date: 2007-07-22
forum: Multimedia &amp; Video
---

### Post by gardara on 2007-07-22
I found this handy manual about recording shoutcast (and last.fm) streams.
[http://news.softpedia.com/news/Record-Shoutcast-and-Last-FM-Streams-49851.shtml](http://news.softpedia.com/news/Record-Shoutcast-and-Last-FM-Streams-49851.shtml)

It is pretty good but there is one thing that I don't like about it, it does automatically cut the streams I record. 
This could be a handy feature but as the radiostation I am recording and listening to does send some advertisements through their ID3 metadata. I was recording one song and while it was playing there came 1 advertisemen, so the song was cutted in three part, the part before the advertisement, the part while the advertisement lasted (only about 2seconds long mp3 file) and then the part after the advertisement.

Does anyone know how I can change this? I would like to be manually start and stop the recording whenever I want....

Thanks in advance.

---

### Post by gardara on 2007-09-14
Found a really easy way of doing this.. Only thing needed is mplayer and then this command. 

```
mplayer -dumpstream http://url.to/stream
```

---

