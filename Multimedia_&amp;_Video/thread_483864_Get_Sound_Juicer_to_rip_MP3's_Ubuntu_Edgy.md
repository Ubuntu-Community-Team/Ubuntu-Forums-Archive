---
title: "Get Sound Juicer to rip MP3's Ubuntu Edgy"
date: 2007-06-25
forum: Multimedia &amp; Video
---

### Post by costa_g on 2007-06-25
Hi there,

I have decided to create this posting using information from past posts getting things working on Edgy to help save people time. 
I have tested this myself and all works well.

Here we go.

To rip MP3's with Sound Juicer, you you will need to install the following:
1. liblame0
2. gstreamer0.8-lame
3. gstreamer0.10-plugins-ugly
4. gstreamer0.10-plugins-ugly-multiverse

Both are available using "Ubuntu Package Search" in Firefox.

Create new Profile e.g. "MP3"
the pipeline settings are
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc ! id3mux

Restart SoundJuicer :popcorn:

---

### Post by corney91 on 2007-06-25
Wow, thanks. I'd nearly given up on Sound Juicer but I was missing the multiverse plugin.

---

