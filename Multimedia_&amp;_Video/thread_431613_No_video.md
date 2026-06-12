---
title: "No video"
date: 2007-05-03
forum: Multimedia &amp; Video
---

### Post by onedeep713 on 2007-05-03
When I try to watch a movie in VLC Player the video flashes for just a second and then goes black. The sound keeps going. When i try to watch it in Totem the screen is black the whole time. How do I fix this?

---

### Post by lukew on 2007-05-03
> **onedeep713 said:**
> When I try to watch a movie in VLC Player the video flashes for just a second and then goes black. The sound keeps going. When i try to watch it in Totem the screen is black the whole time. How do I fix this?

what type of movie is it? Do you have the right codecs installed?

---

### Post by onedeep713 on 2007-05-03
its an .avi Do I need a codec for it?

---

### Post by josephus on 2007-05-03
are you running compiz or beryl?

try System->Preferences->Multimedia System Selector and select the No Xv plugin

---

### Post by onedeep713 on 2007-05-03
I'm using Ubuntu gamers edition. I'm using Beryl. I do not have Multimedia System Selector in Preferences.

---

### Post by onedeep713 on 2007-05-03
Kaffeine is the only one that plays it. MPlayer won't open at all for some reason.

---

### Post by josephus on 2007-05-03
try gstreamer-properties from terminal

---

### Post by Starwind on 2007-05-03
> **onedeep713 said:**
> its an .avi Do I need a codec for it?

Yes, you need a decoder for both the audio and video streams.  BTW avi is just a container for video and audio streams, it's not a video/audio format.

---

### Post by onedeep713 on 2007-05-03
I tried no Xv but nothing changed. I have to drag the VLC window around the screen for the wideo to start. It disappears every time i mess with it or fullscreen it. Its getting pretty frustrating...

---

### Post by josephus on 2007-05-03
does it work if you switch to metacity instead of beryl?

---

### Post by onedeep713 on 2007-05-03
This solved the problem:

[http://ubuntuforums.org/showpost.php?p=2434848&postcount=6](http://ubuntuforums.org/showpost.php?p=2434848&postcount=6)

Thanks!

---

### Post by josephus on 2007-05-03
the same solution applies to mplayer, you have to set the video output to x11 in the config file in ~/.mplayer

---

### Post by onedeep713 on 2007-05-03
I can't even open MPlayer for some reason.  I get this:

MPlayer 1.0rc1-4.1.2 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Pentium(R) M processor 1.60GHz (Family: 6, Model: 13, Stepping: 6)
CPUflags: MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
98 audio & 216 video codecs
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.
[skin] file ( /usr/share/mplayer/skins/default/skin ) not found.
Skin not found (default).

---

