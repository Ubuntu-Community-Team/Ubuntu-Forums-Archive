---
title: "Working disabling of Dmix? Is it possible"
date: 2012-04-19
forum: Multimedia Software
---

### Post by kutalion on 2012-04-19
Hello,

I am using Ubuntu 11.04 and a netbook by eMachines (em355 to be precise). I am a huge music fan and I LOVE listening to music while doing whatever else I want. Until yesterday I was thinking that ANY player works normally taking about 15% of my processor (an Intel Atom N455 - I know it isn't a monster but anyway). Yesterday I by chance played a music file with mplayer and discovered the painful truth that ALSA is resampling my music in REAL TIME with explains the heavy load of music players I have.
I did some research and eventually found how to disable dmix and my music received an exclusive lock of my sound card blocking ANY other sound. Well I do like to listen music but I also need Opera to inform me with sound signals from time to time which became impossible. Anyway I did find some relief for the processor doing so (3-4 times lighter loads of QuodLibet down to 5% from 15~% of processor load).
My humble question is: How can I keep dmix disabled but still be able to listen to sound from more than one source.

Any help is more than welcome. It is needed.

P.S. By the way I AM NOT using that b*stard Pulse since it does not even know that I have built-in microphone (and I occasionally make skype calls). I use bare ALSA. But even when I had it it still used dmix to make my life miserable.

---

### Post by kutalion on 2012-04-24
I have found the solution! After a week+ of searching the forums and wiki how-tos I have found. Look now I don't know which part of is practically the solution but I'll write it.
First I have my /etc/asound.conf looking like this

```
pcm.dmixer {
  type dmix
  ipc_key 1024
  ipc_key_add_uid false
  ipc_perm 0666                       # mixing for all users
  slave {
    pcm "hw:0,0"
    period_time 0
    period_size 1024
    buffer_size 8192
    rate 44100
  }
  bindings {
    0 0
    1 1
  }
}

pcm.dsp0 {
  type plug
  slave.pcm "dmixer"
}

pcm.!default {
  type plug
  slave.pcm "dmixer"
}
pcm.default {
  type plug
  slave.pcm "dmixer"
}
ctl.mixer0 {
  type hw
  card 0
}
```

Then in /usr/share/alsa/alsa.conf
I found a line that states the following [COLOR="Red"]defaults.pcm.dmix.rate 48000[/COLOR] and changed the value to [COLOR="red"]44100[/COLOR].
Afterwards you only have to log out and back in and it works! The load of my players is now much lighter.
(Now I think that every source that has sample rate other than 44100 will get resampled but it is more rare to encounter such than this situation).

---

### Post by kiwinewt on 2012-07-04
Thanks! Hopefully this will fix mine. I don't see ALSA having high CPU use in general, but the background load has been high since I installed it to try get surround working

---

