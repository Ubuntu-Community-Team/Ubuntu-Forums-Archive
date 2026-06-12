---
title: "gtk-recordmydesktop and playback"
date: 2009-12-25
forum: Multimedia Software
---

### Post by The Funkbomb on 2009-12-25
Here is what I'm attempting to do.  Suppose I was playing a youtube video and I wanted to record it with sound and video.  I can get the video going okay and I can record from my microphone if I wanted to do a podcast with this hardware address:

```
hw:0,0
```

I cannot for the life of me figure out how to get gtk-recordmydesktop to record the playback sounds of my machine.

I have tried looking up my soundcard's hardware devices with:

```
cat /proc/asound/Intel/foo/info
```

but I can't decipher the results.

I have five listed:

pcm0p, pcm0c, pcm1p, pcm1c, pcm2c

I assume pcm0* are the rear ports for playback and capture, pcm1* are the front ports for playback and capture.  I know pcm2c is a capture device but I am absolutely boggled as to where that port is.  Maybe I have another line in on the rear.  I dunno.

Also, another odd thing is that when I cat the info for pcm0p and pcm0c, it shows both as a hardware address of 0,0.  This does not make sense to me.

pcm0p:

```
card: 0
device: 0
subdevice: 0
stream: PLAYBACK
id: ALC888 Analog
name: ALC888 Analog
subname: subdevice #0
class: 0
subclass: 0
subdevices_count: 1
subdevices_avail: 0

```

pcm0c:

```
card: 0
device: 0
subdevice: 0
stream: CAPTURE
id: ALC888 Analog
name: ALC888 Analog
subname: subdevice #0
class: 0
subclass: 0
subdevices_count: 1
subdevices_avail: 1

```

---

