---
title: "Can't play FFWMAV2 songs?"
date: 2010-12-02
forum: Multimedia Software
---

### Post by chippy_250 on 2010-12-02
Can't play on MPlayer, Rythembox nor movie player.
Please help!

---

### Post by mc4man on 2010-12-02
Make sure you have the ffmpeg gstreamer plugin installed, wma2 should then be available
```
sudo apt-get install gstreamer0.10-ffmpeg
```
or for most all decoding support
```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad \
gstreamer0.10-plugins-ugly
```

As seen by default in in maverick (w/plugin installed
> $ gst-inspect plugins ffmpeg |grep wma
  ffenc_wmav1: FFmpeg Windows Media Audio 1 encoder
  ffenc_wmav2: FFmpeg Windows Media Audio 2 encoder
  ffdec_wmapro: FFmpeg Windows Media Audio 9 Professional decoder
  ffdec_wmav1: FFmpeg Windows Media Audio 1 decoder
  [COLOR="Blue"]ffdec_wmav2: FFmpeg Windows Media Audio 2 decoder[/COLOR]
  ffdec_wmavoice: FFmpeg Windows Media Audio Voice decoder

---

### Post by chippy_250 on 2010-12-04
> **mc4man said:**
> Make sure you have the ffmpeg gstreamer plugin installed, wma2 should then be available
```
sudo apt-get install gstreamer0.10-ffmpeg
```or for most all decoding support
```
sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad \
gstreamer0.10-plugins-ugly
```As seen by default in in maverick (w/plugin installed

I've done them things ^ you asked. It says they're both already installed.

---

