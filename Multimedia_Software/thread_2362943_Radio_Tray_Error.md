---
title: "Radio Tray Error"
date: 2017-06-04
forum: Multimedia Software
---

### Post by nicchifudo on 2017-06-04
Hello, everyone!

I'm new to Ubuntu, I'm currently using Ubuntu 16.04 and just using it  for about 3 months. Today I just installed online radio streaming app,  Radio Tray. I managed to configure the radios by adding the following 2  radio stations. Here's the following radio stations I want to add  including it's streaming URL:
- 98.7 Gen FM ([http://www.987genfm.com]("http://www.987genfm.com/streaming"))
- Prambors FM ([http://www.pramborsfm.com]("http://www.pramborsfm.com/streaming/"))

I've added the radio stations and I manage to play it. But when I do, an error message occurs. It said:
Radio Error
...
no suitable plugins found:
gstdecodebin2.c(4565):
gst_decode_bin_expose():/
GstPlayBinplayer/
GstURIDecodeBin:uridecodebin5:
no suitable plugins found:
Missing decoder:t text/html (text/html)

What could possibly wrong? I've installed ubuntu-restricted-extras which  used to play audio/video formats. Is there any solutions for this  error?

---

### Post by ron998 on 2017-06-04
> **nicchifudo said:**
> 
- 98.7 Gen FM ([http://www.987genfm.com]("http://www.987genfm.com/streaming"))
- Prambors FM ([http://www.pramborsfm.com]("http://www.pramborsfm.com/streaming/"))

What could possibly wrong? Hi
Those _website_ URLs won't play in RadioTray.
You need to try and find the URLs that contain the audio feeds for those radio stations.

---

### Post by mc4man on 2017-06-04
One would be fairly obvious, the other don't see
```
http://streaming.sim-indonesia.com:8000/genfm
```

---

### Post by howefield on 2017-06-04
The other one could be : 

```
http://masima.rastream.com/masima-pramborsjakarta
```

---

### Post by hondyck on 2017-06-06
AT 2017-06-07 04:32 GMT : When entered in Firefox browser, the url 
[http://streaming.sim-indonesia.com:8000/genfm](http://streaming.sim-indonesia.com:8000/genfm) returns the following output:
Icecast connection limit reached

which means that no new connections are currently being accepted.

AT 2017-06-07 04:38 GMT The URL:
[http://masima.rastream.com/masima-pramborsjakarta](http://masima.rastream.com/masima-pramborsjakarta)
plays fine in my Audacious and also plays fine in Firefox.
You may be missing a 'handler' for this URL e.g. mp3 or AAC stream.

---

### Post by howefield on 2017-06-07
> **hondyck said:**
> AT 2017-06-07 04:32 GMT : When entered in Firefox browser, the url 
[http://streaming.sim-indonesia.com:8000/genfm](http://streaming.sim-indonesia.com:8000/genfm) returns the following output:

Doesn't matter if it plays in the browser or not, the issue is getting radio tray to play them and both links play fine in radiotray.

---

