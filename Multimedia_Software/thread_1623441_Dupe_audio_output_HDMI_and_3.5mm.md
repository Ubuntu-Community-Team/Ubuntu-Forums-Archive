---
title: "Dupe audio output HDMI and 3.5mm"
date: 2010-11-16
forum: Multimedia Software
---

### Post by omax on 2010-11-16
I have a surround system connected to my htpc running xubuntu. Audio goes out over HDMI and it works well.

However, I would like to connect a second amplifier with a stereo-setup.

I figured the easiest way to to this is by duping the audio that goes out to HDMI to the normal stereo 3.5 output on my motherboard as well.

However, I have no idea how to do this. I've never worked with either alsa or pulseaudio, and the syntax it uses in asound.conf is ridicoulus.

However, here is my current asound.conf:
```
pcm.dmixer {
        type dmix
        ipc_key 1024
        ipc_key_add_uid false
        ipc_perm 0660
        slave {
                pcm "hw:0,3"
                rate 48000
                channels 2
                period_time 0
                period_size 1024
                buffer_time 0
                buffer_size 4096
        }
}

pcm.!default
{
        type plug
        slave.pcm "dmixer"
}

```

How do I dupe this so that the stereo-channels also get sent to the normal 3.5 mm output?

Very greatful for responses!

omax

---

