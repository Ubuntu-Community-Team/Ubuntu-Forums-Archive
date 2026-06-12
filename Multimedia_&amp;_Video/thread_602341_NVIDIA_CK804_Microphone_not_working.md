---
title: "NVIDIA CK804 Microphone not working"
date: 2007-11-04
forum: Multimedia &amp; Video
---

### Post by survient on 2007-11-04
I have a MSI K8N Neo4 Platinum 939 NVIDIA nForce4 Ultra ATX AMD Motherboard, showing up in alsamixer as NVidia CK804, OSS as Realtek ALC850 rev 0. I've set up my /etc/asound.conf file to work with dmixer, but I'm having trouble getting the sound capture to work. Audacity either says the device cannot be opened or when it does work it makes this horrible beeping noise. The microphone jack onboard my motherboard works fine in windows, I just don't know how to set it up to work with alsa. Here's my asound.conf:
> 
pcm.card0 {
  type hw
  card 0
}

pcm.dmixer {
  type dmix
  ipc_key 1025
  slave {
    pcm "hw:0,0"
    period_time 0
    period_size 2048
    buffer_size 32768
    rate 48000
  }
  bindings {
    0 0
    1 1
  }
}

pcm.skype {
  type asym

  playback.pcm "dmixer"
  capture.pcm "card0"
}

pcm.!default {
  type plug
  slave.pcm "skype"
}

I've also been trying to get the dmixer to let me use different sample rates on the fly, but I haven't been able to implement it yet. Any help would be appreciated.

---

### Post by soxs on 2007-11-26
Something more general... how did you manage to get ANY OUTPUT??? I have the same soundchip and .. well.. it simply doesn't work ...

---

### Post by survient on 2007-11-26
I switched to alsa.

---

### Post by soxs on 2007-11-27
May you be a little more specific? I compile alsa twice and it still doesn't work *g*..
EDIT: Fresh install of ubuntu now... but still no sound...

---

### Post by survient on 2007-11-27
in the most recent version of ubuntu the dmixer is enabled by default, so by deleting the asound.conf file in both my home folder and in the system specific config, I was able to have it working.

---

