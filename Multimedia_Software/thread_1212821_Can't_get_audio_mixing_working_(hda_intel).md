---
title: "Can't get audio mixing working (hda intel)"
date: 2009-07-14
forum: Multimedia Software
---

### Post by Revelation60 on 2009-07-14
Hi,

I am having trouble getting mixing to work. I want to be able to listen to music (or have Amarok paused) while playing a flash movie. Now I have to close Amarok2. This is happening on two of my computers with intel cards.

This is my system information:

```

80:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)
        Subsystem: ASUSTeK Computer Inc. Device 81b3
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at bfffc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

```

aplay -l:
```

kaart 0: VT82xx [HDA VIA VT82xx], apparaat 0: AD198x Analog [AD198x Analog]
  Sub-apparaten: 0/1
  Sub-apparaat #0: subdevice #0
kaart 0: VT82xx [HDA VIA VT82xx], apparaat 1: AD198x Digital [AD198x Digital]
  Sub-apparaten: 1/1
  Sub-apparaat #0: subdevice #0

```


I have tried this .asoundrc configuration:

> 
pcm.ossmix {
   type dmix
   ipc_key 1024
   slave {
       pcm "hw:0,0"            # make sure this matches the actual device
       #period_time 0          # not necessary since ALSA 1.0pre
       period_size 1024        # Use a power of 2
       buffer_size 4096        # must be a multiple of period_size
       #rate 44100             # not necessary; let alsa-lib handle this
   }
   bindings {
       0 0
       1 1                     # bind only the first 2 channels
   }
}
pcm.duplex
{
   type asym
   playback.pcm "ossmix"
   capture.pcm "dsnoop"
}
# Everything shall be dmixed, so redefine "default":
# Note that this is _not_ a good idea, since dmix doesn't allow mmap access currently
#pcm.!default {
#   type plug
#   slave.pcm "duplex"
#}
# OSS via aoss should d(mix)stroyed:
pcm.dsp0 {
   type plug
   slave.pcm "duplex"
}
ctl.ossmix {
   type hw
   card 0
}


But it is not working.

---

### Post by Revelation60 on 2009-07-14
Bump.

---

