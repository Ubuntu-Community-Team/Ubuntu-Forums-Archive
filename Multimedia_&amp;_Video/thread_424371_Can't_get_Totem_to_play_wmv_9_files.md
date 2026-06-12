---
title: "Can't get Totem to play wmv 9 files"
date: 2007-04-26
forum: Multimedia &amp; Video
---

### Post by quirks on 2007-04-26
I am using Ubuntu Edgy and I have installed the following packages

```
gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gstreamer0.10-pitfdll gxine libxine-main1 libxine-extracodecs w32codecs
```
But Totem still doesn't want to play wmv files. There is sound, but no video. I know there are a couple of threads out there, but none of them helped me.

When I open a wmv 9 file (wmv 7, works by the way), Totem says

```
** Message: don't know how to handle video/x-wmv, wmvversion=(int)3, framerate=(fraction)25/1, width=(int)320, height=(int)240, codec_data=(buffer)4e291a01
```

Also, I have tried to run

```
gst-inspect-0.10
```

after installtion, but that didn't change anything.

When I run

```
gst-inspect-0.10 pitfdll
```

it gives the following output:

```
Plugin Details:
  Name:                 pitfdll
  Description:          DLL-loader elements
  Filename:             /usr/lib/gstreamer-0.10/libpitfdll.so
  Version:              0.9.1.1
  License:              GPL
  Source module:        pitfdll
  Binary package:       PitfDLL
  Origin URL:           http://ronald.bitfreak.net/pitfdll/


  0 features:
```

I guess this is not normal. What am I missing?

Thanks in advance.

P.S. I know there exist other players like MPlayer or VLC, which are likely to play the files, but I just can't stand their GUIs. So they are not really an option.

---

### Post by crispy_420 on 2007-04-26
Did you try totem-xine?

---

### Post by quirks on 2007-04-27
Totem-xine uses the xine engine, doesn't it? Shouldn't the video play in gxine then (I have tested that and they don't)?

Nevertheless, I will give that a try.

Thank you for your advice!

---

### Post by crispy_420 on 2007-04-27
Didn't think of this before but did you install w32-codecs from restricted?

---

### Post by quirks on 2007-04-27
Yes, I did. :(

---

### Post by quirks on 2007-04-27
Ok, I have decided to take VLC now. I have found a skin that is rather simple and fits acceptably with the rest of the desktop.

Thanks a lot for your help.

---

### Post by crispy_420 on 2007-04-27
Have you tried mplayer yet? I like VLC for playing my DVDs but mplayer for general desktop player.

---

