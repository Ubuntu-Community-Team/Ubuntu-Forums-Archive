---
title: "ice1712, gstreamer-properties default input:Could not open resource for writing"
date: 2007-02-06
forum: Multimedia &amp; Video
---

### Post by hanzomon4 on 2007-02-06
I'm trying to get the input on my delta 66(ice1712)) working with gstreamer. I have an asound.conf setup to use "softvol" and "dmix" and I can record using jack, problem is jokosher uses gstreamer. 

I started gstreamer-properties and set the default input plugin to alsa, I clicked test and it failed. I tried a few custom options but none worked. I'll post the different combinations I tried using for the "Pipeline" and my asound.conf.

[list][*]pipelines that failed with "Could not open resource for writing"[list][*]alsasrc[*]alsasrc device=dmix[*]alsasrc device=dmixer[*]alsasrc device=default[/list][/list]
[list][*]pipelines that failed with "Could not negotiate format"[list][*]alsasrc device="hw:0,0"[/list][/list]

**/etc/asound.conf**
```
pcm.ice1712 {
  type hw
  card 0
  }
ctl.ice1712 {
  type hw
  card 0
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

Any help is appreciated.....

---

### Post by hanzomon4 on 2007-02-17
I found that if I remove my asound.conf I can get it to work but I need my asound.conf for the softvol plugin. So does any one know why gstreamer input won't work with my asound.conf?

---

