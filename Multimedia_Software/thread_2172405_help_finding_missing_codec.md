---
title: "help finding missing codec"
date: 2013-09-04
forum: Multimedia Software
---

### Post by josh17 on 2013-09-04
I'm trying to export a video in  kdenlive as h.264 and i get an error saying Unsupported video codec: libx264
How do i get this codec so I can export in this video format?

---

### Post by Yellow Pasque on 2013-09-04
You probably have to install the libavcodec-extra-53 package (and it will  grab the other -extra packages).

---

### Post by josh17 on 2013-09-04
> **Temüjin said:**
> You probably have to install the libavcodec-extra-53 package (and it will  grab the other -extra packages).
Alright, would that be ```
sudo apt-get install libavcodec-extra-53
```? or something different?

---

### Post by varunendra on 2013-09-04
> **josh17 said:**
> Alright, would that be ```
sudo apt-get install libavcodec-extra-53
```

Yes, it would be the above command which will replace the libavcodec-53 package if it is already installed.

After installation, you will have to re-run the configuration wizard in Kdenlive to be able to use the newly installed codec (Settings > Run Config Wizard).

By the way, if it is some simple editing or just capturing/importing > exporting, then I find OpenShot much simpler (yet much configurable at the same time) and thus better for that purpose.

---

### Post by josh17 on 2013-09-05
> **varunendra said:**
> Yes, it would be the above command which will replace the libavcodec-53 package if it is already installed.

After installation, you will have to re-run the configuration wizard in Kdenlive to be able to use the newly installed codec (Settings > Run Config Wizard).

By the way, if it is some simple editing or just capturing/importing > exporting, then I find OpenShot much simpler (yet much configurable at the same time) and thus better for that purpose.
I've tried openshot, it crashes before I can finish editing or exporting, if it didn't do that it would be one of my fav programs though.

---

### Post by tgalati4 on 2013-09-05
Run *openshot* in a terminal and see what the errors are and post them.  It's in rapid development so there may be a fix.  Also *ffmpeg* can handle h.264 if you have it installed with all of the codecs.

---

### Post by Yellow Pasque on 2013-09-05
> **tgalati4 said:**
> *ffmpeg* can handle h.264 if you have it installed with all of the codecs.

kdenlive uses ffmpeg. Again, user needs the libavcodec-extra-53 package...

---

### Post by marinecomm on 2013-11-16
I have the same issue. I tried installing the libavcodec-extra-53 package and it's dependencies, restarted and reran the config wizard and I'm still getting the same error message. Also, if I try to do the same job through OpenShot, it will accept the libmp3lame codec and doesn't give me any error message about it.

---

