---
title: "MP4 in Amarok or Kaffeine?"
date: 2007-09-18
forum: Multimedia &amp; Video
---

### Post by mivo on 2007-09-18
Which package(s) do I need to install to play MP4 encoded videos in Amarok or Xine? I already added libxine-extracodecs, which took care of MP3 audio files, but I still can't watch MP4 videos (just listen to them :)).

---

### Post by nzlee34 on 2007-09-18
Try installing the gstreamer packages.

```
sudo apt-get install gstreamer0.10-ffmpeg
```

---

### Post by RomeReactor on 2007-09-18
Hi. Medibuntu's Amarok package has MP3 and MP4 enabled by default; you might want to use that one instead. To add the Medibuntu repositories, enter the following in a terminal:
```
sudo wget http://www.medibuntu.org/sources.list.d/dapper.list -O /etc/apt/sources.list.d/medibuntu.list
```
then:
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

After that, open Synaptic and search for amarok; once you find it, read its description to make sure it's the version with MP3 and MP4 enabled.

---

