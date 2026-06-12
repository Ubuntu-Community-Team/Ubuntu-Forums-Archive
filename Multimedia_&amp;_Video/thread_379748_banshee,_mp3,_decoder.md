---
title: "banshee, mp3, decoder"
date: 2007-03-08
forum: Multimedia &amp; Video
---

### Post by palletjackracer on 2007-03-08
not to re-hash an overly sore topic, but i can't get mp3 playback.

i'm running edgy eft w/gnome.  i've tried installing the gstreamer libraries but that didn't work.  xmms seems to play mp3s fine but rhythmbox and banshee can't find the plugins (if indeed the gstreamer libraries are the correct ones).

any advice would be appreciated.  thanks.

---

### Post by Paul41 on 2007-03-09
It sounds like you have already done this, but have you installed everything mentioned for mp3 on this page?  [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by palletjackracer on 2007-03-09
well, apparently i hadn't installed *everything* from that page.  after running 

sudo apt-get install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs ogle ogle-gui

it now works just fine.

thanks for the help!

---

