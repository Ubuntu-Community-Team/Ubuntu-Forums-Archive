---
title: "TS file"
date: 2007-09-11
forum: Multimedia &amp; Video
---

### Post by Sockerdrickan on 2007-09-11
Hi how do I play a TS file (HD-DVD) I tried VLC 0.8.6 :confused:

---

### Post by RomeReactor on 2007-09-11
Hi. Open Totem and try dragging the TS folder on it.

---

### Post by Sockerdrickan on 2007-09-11
Crashes when after getting the plugins when I try to play it :/

---

### Post by RomeReactor on 2007-09-11
You may need additional packages installed to correctly play it. If you're using **totem-gstreamer**:
```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-fluendo-mp3 gstreamer0.10-fluendo-mpegdemux gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse libdvdnav4 libdvdplay0 libdvdread3
```
If you're using **totem-xine**:
```
sudo apt-get install libxine1 libxine1-ffmpeg libxine-extracodecs libdvdnav4 libdvdplay0 libdvdread3
```
I'm not sure you need [libdvdcss2]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs#head-e3dafb305e64ec576176ee706e287bb4d839cb12"), though, unless the TS folder contains encrypted information.

Please post the error you're getting; also, open Totem from the command line and then drop the TS folder on it. If/when it crashes, post the output left on the terminal.

---

### Post by Sockerdrickan on 2007-09-11
just segfault :(

---

