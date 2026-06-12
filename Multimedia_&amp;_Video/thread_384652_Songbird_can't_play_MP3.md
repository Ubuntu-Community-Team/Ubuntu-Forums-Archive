---
title: "Songbird can't play MP3"
date: 2007-03-14
forum: Multimedia &amp; Video
---

### Post by idtt2s on 2007-03-14
I can't play MP3 on Songbird on my newly installed Ubuntu Edgy. I can play them fine on Totem, why not Songbird?

---

### Post by GreenDevil on 2007-03-14
Are you adding the files to the library, or just playing them outright?

---

### Post by idtt2s on 2007-03-14
I can add them, but I can't play them. Not even ones from online websites can be played.

---

### Post by GreenDevil on 2007-03-14
You may need to install the gstreamer plugins.

Open up synaptic package manager and search for gstreamer and install the following;
gstreamer0.10-alsa
gstreamer0.10-esd
gstreamer0.10-ffmpeg
gstreamer0.10-fluendo-mp3
gstreamer0.10-plugins-base
gstreamer0.10-plugins-base-apps
gstreamer0.10-plugins-good
gstreamer0.10-x
libgstreamer0.10-0
libgstreamer-plugins-base0.10-0

That should get you going for most if not all codecs for Songbird.

- GreenDevil

---

### Post by idtt2s on 2007-03-14
Thank you, that worked!

---

