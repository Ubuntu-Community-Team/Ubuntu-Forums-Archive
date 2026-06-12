---
title: "Banshee streamrecorder no longer converts to MP3"
date: 2011-02-03
forum: Multimedia Software
---

### Post by joekm on 2011-02-03
Using Ubuntu 10.04 and installed latest Banshee via Banshee Team PPA repository.  Also installed the streamrecorder plugin and gstreamer-plugins-ugly.  When Banshee was at 1.8.0, I could convert streams to MP3.  Since it updated to 1.8.1, I can only save the unconverted stream.

Tried re-installing the gstreamer plugins but no effect.  

Any thoughts as to why I can no longer convert streams to mp3?

---

### Post by joekm on 2011-02-04
Update, besides not giving me the MP3 option (via LAME) or any other option other than raw stream.  Streamrecorder no longer works at all

I will probably make a new post to be more accurate.


> **joekm said:**
> Using Ubuntu 10.04 and installed latest Banshee via Banshee Team PPA repository.  Also installed the streamrecorder plugin and gstreamer-plugins-ugly.  When Banshee was at 1.8.0, I could convert streams to MP3.  Since it updated to 1.8.1, I can only save the unconverted stream.

Tried re-installing the gstreamer plugins but no effect.  

Any thoughts as to why I can no longer convert streams to mp3?

---

### Post by joekm on 2011-02-05
This is solved....

The problem seemed to surround "gstreamer element autoaudiosink"

So, first I tried the following...

rm -rf ~/.gconf/system/gstreamer
rm -rf ~/.gstreamer-0.10

Then rebooting...this didn't work


Then I tried simply deleting the  ~/.config/banshee-1 directory and letting Banshee rebuild it when I started it up again.  I had to re-set my preferences, and I lost my one saved radio station, but my liveradio settings were still intact and the streamrecorder plugin now works just fine.

I will post this as [SOLVED] but, if anyone has a more elegant solution, please add it to the thread.

---

