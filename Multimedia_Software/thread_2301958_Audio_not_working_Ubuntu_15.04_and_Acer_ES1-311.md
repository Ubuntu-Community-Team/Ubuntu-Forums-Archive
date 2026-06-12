---
title: "Audio not working Ubuntu 15.04 and Acer ES1-311"
date: 2015-11-06
forum: Multimedia Software
---

### Post by Pablo_G_Prieto on 2015-11-06
Here is my audio device:

    00:1b.0 Audio device: Intel Corporation Atom Processor Z36xxx/Z37xxx Series High Definition Audio Controller (rev 0e)

In alsamixer everything is 100 and unmuted. There's also an option called 'Auto-Mute' which I disabled.

Running this command produces no sound:

    aplay /usr/share/sounds/alsa/Front_Center.wav

ALSA seems to detect the card:

    # aplay -l
    **** List of PLAYBACK Hardware Devices ****
    card 0: PCH [HDA Intel PCH], device 0: ALC283 Analog [ALC283 Analog]
      Subdevices: 1/1
      Subdevice #0: subdevice #0
    card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
      Subdevices: 1/1
      Subdevice #0: subdevice #0

More info:

    # lspci -v | grep -A7 -i "audio"
    00:1b.0 Audio device: Intel Corporation Atom Processor Z36xxx/Z37xxx Series High Definition Audio Controller (rev 0e)
        Subsystem: Acer Incorporated [ALI] Device 0938
        Flags: bus master, fast devsel, latency 0, IRQ 95
        Memory at 90800000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
        Kernel driver in use: snd_hda_intel

In pavucontrol it shows input from the microphone but not from the output speaker (you know the bars that fill up to show activity).

Now as well I've run:

    alsa force-reload
    apt-get remove --purge alsa-base pulseaudio
    apt-get install alsa-base pulseaudio

And now there is no audio applet and the sound window is transparent.

[Transparent sound window][1]

What else can I do? Can anyone please point me in the right direction, or somewhere I can find more info? If I reinstall Ubuntu, it doesn't fix the problem.

  [1]: [http://i.stack.imgur.com/8BVKE.png](http://i.stack.imgur.com/8BVKE.png)

---

