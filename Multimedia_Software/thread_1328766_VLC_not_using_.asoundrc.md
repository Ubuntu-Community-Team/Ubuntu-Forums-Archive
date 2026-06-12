---
title: "VLC not using .asoundrc"
date: 2009-11-16
forum: Multimedia Software
---

### Post by Phoenixfatali on 2009-11-16
For background information I'm using Karmic, have an X-FI hooked up to a home theater via spdif cable, and the receiver only accepts a sample rate of 48k (anything else causes static, which I ended up finding out in windows a long time ago).  I'm using ALSA and have removed pulse (since pulse doesn't like the idea of 5.1 over spdif).  I've set up an asoundrc file for the hardware, and I was able to verify it's working via Wine (dmix-digital is a selectable output option and sound works fine in applications in wine).

I use VLC player for my media, and I've run into a snag because I can't get it to allow me to select dmix-digital as an output option.  It works okay most of the time, but if the audio is anything above or below 48k sample rate I get static.  I'm not a linux pro, so I'm not sure if I butchered something with my asoundrc that makes VLC not take it, or if I have to do something else to VLC to get it to read the config.  Any help would be appreciated.

Below is my .asoundrc

```
pcm.!default {
type plug
slave.pcm "dmix-digital"
}

pcm.analog {
type plug
slave.pcm "analog-hw"
}

ctl.analog {
type hw
card 0
}

pcm.mixed-analog {
type plug
slave.pcm "dmix-analog"
}

ctl.mixed-analog {
type hw
card 0
}

pcm.digital {
type plug
slave.pcm "digital-hw"
}
ctl.digital {
type hw
card 0
}

pcm.mixed-digital {
type plug
slave.pcm "dmix-digital"
}

ctl.mixed-digital {
type hw
card 0
}

pcm.analog-hw {
type hw
card 0
# The default value for device is 0, so no need to specify
}

ctl.analog-hw {
type hw
card 0
}

pcm.digital-hw {
type hw
card 0
device 4
}ctl.digital-hw {
type hw
card 0
}

pcm.dmix-analog {
type dmix
ipc_key 1234
slave {
pcm "analog-hw"
period_time 0
period_size 1024
buffer_size 32768
rate 48000
}
}

ctl.dmix-analog {
type hw
card 0
}

pcm.dmix-digital {
type dmix
ipc_key 1235
slave {
pcm "digital-hw"
period_time 0
period_size 1024
buffer_size 32768
rate 48000
channels 6
}
}

ctl.dmix-digital {
type hw
card 0
}
```

---

