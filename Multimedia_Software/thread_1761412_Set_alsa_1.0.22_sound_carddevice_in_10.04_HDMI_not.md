---
title: "Set alsa 1.0.22 sound card/device in 10.04? HDMI not working."
date: 2011-05-18
forum: Multimedia Software
---

### Post by its__ on 2011-05-18
Hi guys

I've just gotten my ASRock 3D 152 HTPC and are setting everything up.

So far, I've gotten WiFi and the remote working.

But the audio still troubles me. I get NO audio at all. I **have** went to alsamixer and unmuted the output.

Here's what terminal shows:

```

boxee@boxee-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

------------------------------------------------------------------------

boxee@boxee-desktop:~$ lspci
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 04)
...........
02:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)

```So, it looks like I have 1 card (NVidia [HDA Nvidia]) with 4 devices (3,7,8,9).

Therefore I tried using aplay on all those devices. The one that worked was **aplay -D plughw:1,7 im.wav**

So it's card 1, device 7 that works. But how do I get Ubuntu (and Boxee, that I'm using) to use that card and device?

I've tried creating a /etc/asound.conf and ~/.asoundrc with the following content:
```

pcm.!default {
    type plug
    slave.pcm {
        type hw
        card 1
    device 7
    }
}

pcm.digital-hw {
    type hw
    card 1
    device 7
}

```Rebooted, but that didn't work for me.

So, anyone here that knows what I can do to fix this?

---

### Post by SirKingChase on 2012-02-10
To anyone that comes across this, thank the guys at ARCH linux for the solution.

[https://bbs.archlinux.org/viewtopic.php?pid=1045323](https://bbs.archlinux.org/viewtopic.php?pid=1045323)

---

