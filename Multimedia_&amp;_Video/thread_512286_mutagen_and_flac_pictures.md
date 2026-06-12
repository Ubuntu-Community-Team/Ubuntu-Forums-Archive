---
title: "mutagen and flac pictures"
date: 2007-07-29
forum: Multimedia &amp; Video
---

### Post by code-breaker on 2007-07-29
I am using mutagen in python to work with flac tags. Everything works great, except when I try to display some album art. The image data seems to be encoded, but I don't know how to decode. Here is a snippet of what the picture data look like.  

```
from mutagen.flac import FLAC as md
metadata = md('soundfile.flac')
metadata.pictures[0].data[0:25]
'\xff\xd8\xff\xdb\x00C\x00\x08\x06\x06\x07\x06\x05\x08\x07\x07\x07\t\t\x08\n\x0c\x14\r\x0c'
```

It doesn't seem to be unicode, and I tried base64 as well. How can I get this data into a PIL Image?

---

### Post by PaulFr on 2007-07-29
The first two bytes are FF and D8 - looking in **/usr/share/file/magic**, these first two bytes are the signature of a JPEG file (search for ffd8 ). Does this help ?

---

### Post by code-breaker on 2007-07-31
Thanks PaulFr, your reply was helpful. I have it working now with:

```
imagedata = Image.open(StringIO.StringIO(metadata.pictures[0].data))

```

---

