---
title: "Amarok stutters, xmms and mplayer do not using spdif."
date: 2007-05-06
forum: Multimedia &amp; Video
---

### Post by jluros on 2007-05-06
I'm using plug:spdif as the device. Is there a way to make that Alsa's default device?

So, whenever I use plug:spdif in mplayer or xmms, it works fine, but Amarok stutters every 2 or 3 seconds. However, when driving the speakers over an analog line to my receiver, it works fine without stuttering. I'd like plug:spdif to not stutter in amarok. Is that possible? 

As a second question, is there a way to make plug:spdif the default device, so all the custom configuration of linux multimedia apps isn't necessary? Something in /etc/asound.conf perhaps?

This is my /etc/asound.conf:

pcm.via82xx-hw {
type hw
card 0
}

pcm.!default {
type plug
slave.pcm "via82xx-hw"
}

slave {
    pcm "hw:0,0"
    period_time 0
    buffer_time 0
    period_size 2048
    buffer_size 65536
    rate 44100
}


ctl.via82xx-hw {
type hw
card 0
}

---

