---
title: "High pitched ringing on microphone"
date: 2009-07-12
forum: Multimedia Software
---

### Post by kevuk on 2009-07-12
Hi all,

New HP TX2500 series (TX2530ea) laptop running 9.04 ubuntu, has a constant high pitched sound when I try to use the microphone.  The microphone works, I can hear myself just behind the tone.  I've tried both the inbuilt microphone and a new external one plugged into the microphone socket.

This occurs with or without the speakers operating, and also using "arecord -f cd out.wav" and replaying.

cat /proc/asound/card0/pcm0c/info gives this information
card: 0
device: 0
subdevice: 0
stream: CAPTURE
id: ALC268 Analog
name: ALC268 Analog
subname: subdevice #0
class: 0
subclass: 0
subdevices_count: 1
subdevices_avail: 1

and "cat /proc/asound/card0/codec#* | grep Codec" gives
Codec: Realtek ALC268
Codec: Motorola Si3054

Any help appreciated

---

### Post by igorzwx on 2009-07-12
I had 50Hz with odd overtones in my recordings on IMB notebook.

Now, the problem is fixed.

I just failed to understend your description of the problem.

Try to record on battery (without AC), and offline.
And tell the result.

---

### Post by kevuk on 2009-07-12
The problem (high pitched whine on audio recording made through microphone), continues despite being on battery and broadband modem disconnected.

---

### Post by igorzwx on 2009-07-12
The same is with Dell notebook.
The artefacts are still strong,
even with battery, offline, and USB sound card.

On my old IMB, I could get rid of them when
on battery and iMic USB.

Eventually, I removed the evil and the problem is fixed.
But now I cannot use USB audio devices.
It is not a big problem for me, however.

---

### Post by igorzwx on 2009-07-12
I mean PulseAudio server.
Now I have OSS4

---

