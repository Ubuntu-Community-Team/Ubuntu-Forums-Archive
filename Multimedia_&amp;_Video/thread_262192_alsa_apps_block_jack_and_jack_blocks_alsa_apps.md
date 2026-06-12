---
title: "alsa apps block jack and jack blocks alsa apps"
date: 2006-09-21
forum: Multimedia &amp; Video
---

### Post by hanzomon4 on 2006-09-21
This is the issue.. I have dmix setup in my asound.conf and all alsa apps share the sound card. Jack use to share but now it doesn't. 

I have to stop all apps that may be using alsa to get qjackctl to connect, otherwise I get this error ```
the playback device "hw:0" is already in use. Please stop the application using it and run JACK again
cannot load driver module alsa
starting server engine shutdown
```

Here is my asound.conf ```
pcm.dsp0 {
    type plug
    slave.pcm "dmixer"
}

pcm.!default {
    type plug
    slave.pcm "dmixer"
} 
pcm.!default {
  type plug
  slave.pcm "softvol"
  }
 softvol - Volume Control
pcm.softvol {
    type softvol
    slave.pcm "dmixer"
    control {
        name "PCM Volume"
    card 0
    }
}
# dmixer:
pcm.dmixer {
  type dmix
  ipc_key 1024
  ipc_key_add_uid false
  ipc_perm 0666 
  slave {
  pcm "hw:0,0"
  period_time 0
  period_size 1024
  buffer_size 4096
  rate 44100
  format S32_LE
  }
  bindings {
  0 0
  1 1
  }
  }



``` 
My soundcard is a delta 66 Kernel is 2.6.18-rt3

I've killed esd, messed around with the qjackctl settings, but nothing.. any help would be appreciated

---

### Post by pljones on 2007-09-28
You can't have two applications with the same hardware device open at the same time.  Software like esd acts as a mixer - it holds the hardware device open and allows multiple access, mixing the streams.

Apararently there's an ALSA plugin, libasound_module_pcm_jack, that lets you use jack as an ALSA pcm output.  I've not been able to find it.

---

