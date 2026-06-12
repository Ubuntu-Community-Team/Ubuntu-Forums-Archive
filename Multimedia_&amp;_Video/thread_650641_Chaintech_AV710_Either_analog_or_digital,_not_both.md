---
title: "Chaintech AV710: Either analog or digital, not both at once"
date: 2007-12-26
forum: Multimedia &amp; Video
---

### Post by applezip on 2007-12-26
I have read all the other posts on the AV710, here, and all over the net. Most of them are for getting optical (SPDIF out) working. Those posts did help me get SPDIF working, but they disable analog out. 

So my basic problem is, SPDIF and analog do not work at the same time. SPDIF only works with this .asoundrc (which I believe I got from headfi). Analog only works if I rename this file (effectively disabling). I am not a coder, so I do not really know what to change.

```
#

pcm.!default {
type plug
slave.pcm "dmixer"
}

pcm.dmixer {
type dmix
ipc_key 1024
slave {
pcm "hw:0,1"
format S32_LE
period_time 0
period_size 1024
buffer_size 8096

rate 44100
}
bindings {
0 0
1 1
}
}

ctl.dmixer {
type hw
card 0
device 1
}

#
```

I have ALSA 1.0.15 using snd_ice1724

Both analog and optical work at the same time in XP, so there is probably a way to get it working in Linux.

---

