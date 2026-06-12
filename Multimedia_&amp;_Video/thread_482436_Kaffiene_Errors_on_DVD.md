---
title: "Kaffiene Errors on DVD"
date: 2007-06-23
forum: Multimedia &amp; Video
---

### Post by VoiceOvGod on 2007-06-23
Hi, getting errors when I am trying to watch a DVD

xine: cannot find input plugin for MRL [dvd:/]
xine: input plugin cannot open MRL [dvd:/]
xine: found input plugin : DVD Navigator
xine: cannot find input plugin for MRL [dvd:/]
xine: input plugin cannot open MRL [dvd:/]
xine: found input plugin : DVD Navigator
xine: found demuxer plugin: AVI/RIFF demux plugin
xine: found input plugin : file input plugin

Any ideas?

---

### Post by alan.clements on 2007-06-23
try:
```
sudo apt-get install libdvdread3 libdvdnav4 libdvdplay0 llibdvdcss2
```
in a terminal.

all should be good! :)

---

