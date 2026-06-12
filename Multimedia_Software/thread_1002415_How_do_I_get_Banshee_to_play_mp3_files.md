---
title: "How do I get Banshee to play mp3 files?"
date: 2008-12-05
forum: Multimedia Software
---

### Post by jazzyditty on 2008-12-05
I really enjoy using banshee, however it doesn't seem to like mp3 files, and i've been going without listening to my music for a while. I've been running last.fm radio.

But, now since I can't seem to figure it out on my own, could someone tell me how to make it so banshee plays mp3 files? I know it can be done, as many people do it, but how?

Thanks!

---

### Post by utnubuuser on 2008-12-05
I don't usually play mp3s, but I think you have to have Universe or Multiverse enabled in repositories, (Synaptic >> Settings >> Repositories >> software restricted by license agreements/copyright)  then get **ubuntu-restricted-extras** through Synaptic

Be aware though that *as far as I know*, those are non-free codecs, so you might have to accept license terms

---

### Post by kpkeerthi on 2008-12-05
If you just need the restricted codecs and not the complete ubuntu-restrictes-extras, install the following packages using synaptic.
```

gstreamer0.10-ffmpeg
gstreamer0.10-pitfdll
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-bad-multiverse
gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-ugly-multiverse
libavcodec-unstripped-51
libdvdread3
libmp3lame0 

```
Enable multiverse and universe repos from System -> Admin -> Software Sources before installing the packages.

See [http://packages.ubuntu.com/intrepid/ubuntu-restricted-extras](http://packages.ubuntu.com/intrepid/ubuntu-restricted-extras) for more info

---

### Post by MutantJohn on 2011-07-19
Thanks KP, totally worked lol. Now it's time for me to meld with Senses Fail.

---

### Post by killfrogg on 2011-07-24
After *kpkeerthi*'s suggestion I additionally had to install the package ```
gstreamer0.10-fluendo-mp3
``` until it worked. On the banshee-website they say > Whatever codecs you have installed for GStreamer, Banshee will be able to use by the way.

Wrong information, sorry ... it works without the fluendo-mp3 aswell. I must have had some problems with accessing a different drive before ...

---

