---
title: "How do I install Flash Player in Ubuntu 10.10"
date: 2013-02-23
forum: Multimedia Software
---

### Post by jacatone on 2013-02-23
I installed Ubuntu 10.10 on an old Centrino laptop of mine. I know this is an outdated distro and no longer supported, but how do I install the tar ball for Flash player 10 I downloaded. After unzipping it, I get a "libflashplayer.so" file and a "usr" folder. Thanks.

---

### Post by howefield on 2013-02-23
Move the libflashplayer.so file either to ~/mozilla/plugins/ or  /usr/lib/mozilla/plugins/

---

### Post by jacatone on 2013-02-23
Great, that worked. Do you know where I can get the follow codecs?

"gstreamer0.10-ffmpeg libavcodec52 libavformat52 libavutil50 libpostproc51 libschroedinger-1.0-0 libswscale0 libva1 libvpx0"

---

### Post by howefield on 2013-02-23
I replied to the thread you made on the subject.

Either change your sources.list to reflect the old-releases repositories which will give you the package versions from Maverick or download straight from packages.ubuntu.com - you may need to download a load of dependencies along with them.

I'd go for the first option.

---

