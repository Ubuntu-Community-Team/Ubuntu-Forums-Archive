---
title: "nforce2 onboard S/PDIF + OSS emulation (A7N8X-DX)"
date: 2006-03-30
forum: Multimedia &amp; Video
---

### Post by Casey J. Morris on 2006-03-30
I'm using the onboard S/PDIF output on my A7N8X Deluxe mainboard, and it works fine for ALSA-Native programs.  However, OSS programs give no sound and aoss makes them segfault or malfunction, which makes me thing something's configured improperly.  


[quote="~/.asoundrc"]pcm.!default {
type plug
slave.pcm "dmixer"
}

#Pretty sure this part does nothing
pcm.dsp {
        type plug
        slave.pcm "dmixer"
}

pcm.dmixer {
type dmix
ipc_key 1024
slave {
pcm "hw:0,2"
period_time 0
period_size 1024
buffer_size 4096
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
}
[/quote]

---

### Post by Casey J. Morris on 2006-03-30
Well wouldn't you know, this one fixed it.

[quote="~/.asoundrc"]pcm.nforce-hw {
type hw
card 0
}

pcm.!default {
type plug
slave.pcm "nforce"
}


pcm.nforce {
type dmix
ipc_key 1234
slave {
pcm "hw:0,2"
period_time 0
period_size 1024
buffer_size 32768
rate 44100
}
}

ctl.nforce-hw {
type hw
card 0
}
[/quote]

For some reason aoss still hangs fceu though.  But that's much more specific and I suppose no one's gonna know about that.

---

### Post by FarEast on 2006-03-31
Hi,
Thanks for telling me how to describe .asoundrc for dmix plugin!
Very helpful and timely:)

---

