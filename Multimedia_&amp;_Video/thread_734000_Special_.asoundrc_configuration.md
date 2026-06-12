---
title: "Special .asoundrc configuration"
date: 2008-03-24
forum: Multimedia &amp; Video
---

### Post by Dedors on 2008-03-24
hi there

i want a special configuration of my sound card. i even dont know if it is possible to configure that.

Soundcard: onboard nforce 3 250 12 channel (6 outputs)

_**i want the following constellation:**_
3x2channel music output (**currently working**), see my .asoundrc for that
**additional i want:**
1x2channel for misc sound (system sound), can be a virtual sound card is this is easier to do
volume control: should only affect the 1x2 channel system sound AND ONLY ONE of the 3 channels for music output (both together or just induvidual, the one from the "music channel" should be the system master)
 

my current .asoundrc for 3x2 channel duplicate output
```
pcm.dmixs51 {
    type dmix
    ipc_key 1024
    slave {
        pcm "hw:0,1"
        rate 48000
        channels 6
        period_time 0
        period_size 1024
        buffer_time 0
        buffer_size 4096
   }
}
pcm.duplicate {
    type plug
    slave.pcm "dmixs51"
    slave.channels 6
    route_policy duplicate
}
```

any ideas how to do that configuration? thanks for any advice

edit: i only got one subdevice
```

**** List of PLAYBACK Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

