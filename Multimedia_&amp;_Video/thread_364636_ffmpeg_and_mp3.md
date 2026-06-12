---
title: "ffmpeg and mp3"
date: 2007-02-18
forum: Multimedia &amp; Video
---

### Post by pgilmon on 2007-02-18
Hi all,

I'm trying to extract audio from a .mpg file into mp3, but when I try with
```
ffmpeg -i input_file.mpg -f mp3 output_file.mp3
```

I get the error

```
Unsupported codec for output stream #0.0
```

I have tried setting the output to ogg format and it works. Is there any way to add mp3 encoding capabilities to ffmpeg?

---

### Post by chggr on 2007-02-19
In order to have full mp3 capabilities on your machine (plus many more codecs), you should check (using Synaptic Package Manager) that all of these packets are installed:

gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-ugly-multiverse
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-bad-multiverse

---

