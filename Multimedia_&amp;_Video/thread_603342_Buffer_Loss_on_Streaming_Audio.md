---
title: "Buffer Loss on Streaming Audio"
date: 2007-11-05
forum: Multimedia &amp; Video
---

### Post by juniah on 2007-11-05
I'm trying to stream music through Totem, however I continually lose my buffer on the stream.  It buffers for a few seconds, then resets itself.   Is there anyway to stop this?

---

### Post by GlennW on 2008-02-06
Although I'm not streaming music, I have what appears to be a similar issue while streaming video. Totem-xine continually buffers every few seconds, leaving me frustrated and wondering when I'll ever find a solution for this. I've tried every permutation of mplayer I can come up with including reassuinglyoffensive's streaming how-to (which left me with a 1" x 1.5" totally pixelated image that buffered a couple of times and then shut down)  to no avail. I've now got it to the point where I've got sharp full screen video but it buffers constantly, forever interrupting the stream.

Does anyone have an answer to this?

---

### Post by andrew.46 on 2008-02-13
Hi,

 I only have experience with mplayer and that with the command line version but the answer may be there for you. This in the man pages:

>  -cache <kBytes>
    This  option  specifies  how much memory (in kBytes) to use when
    precaching a file or URL.  Especially useful on slow media.

So the following is possible:

```
$ mplayer -cache 25000 <address.file>
```

  Andrew

---

