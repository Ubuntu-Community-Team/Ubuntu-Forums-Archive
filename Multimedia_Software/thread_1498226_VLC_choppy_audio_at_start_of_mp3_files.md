---
title: "VLC choppy audio at start of mp3 files"
date: 2010-05-31
forum: Multimedia Software
---

### Post by choikwa on 2010-05-31
VLC freshly installed using pulse-audio as output still gets choppy start when opening audio files. I could see a lot of broken frames with ctrl+i option. It seems the read, write speed shoots up to >220kb/s and then settle down to <200kb/s to get smooth audio. I've tried killall pulseaudio, sudo pulseaudio to no avail, 

If anyone has a solution to this, I'd greatly appreciate it.

---

### Post by choikwa on 2010-06-04
bump

---

### Post by accumulator on 2010-06-23
I've reduced the pulseaudio buffers to a smaller size, so vlc doesn't get confused when pulseaudio fills its buffers faster than playing speed. This fixes it for me.

```
default-fragments = 4
default-fragment-size-msec = 8
```

Please note that reducing the buffers might also introduce skips because it increases the chances of buffer underruns!

---

### Post by accumulator on 2010-06-23
forgot to say, this should go in /etc/pulse/daemon.conf

---

### Post by Neobuntu on 2010-07-02
Umm, Thanks; but didn't work. VLC doesn't work. I even upgraded to the newest VLC and it didn't work (MP4 in AVI), Audio is "choppy". Ubuntu 10.04 upgraded.

VLC has just become a Windows only program.

---

