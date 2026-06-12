---
title: "Can't get USB audio card to work on ARM build of lubuntu"
date: 2012-07-12
forum: Multimedia Software
---

### Post by burnmp3s on 2012-07-12
I'm running an ARM build of lubuntu 12.04 designed for the MK802, which is a new AllWinner A10 mini PC that comes preloaded with Android but supports other OSes being loaded from the microSD slot.  The build I installed comes preconfigued to work with the onboard HDMI video and audio out, but I can't get it to recognize and use an [external USB audio out interface]("http://www.amazon.com/Syba-SD-CM-UAUD-Adapter-C-Media-Chipset/dp/B001MSS6CS/").  Since it's a non-standard build I don't think it comes with the relevant audio drivers and I'm not skilled enough at this kind of stuff to figure it out.

After plugging in my USB audio adapter, running When I run alsamixer does not show me an option for my USB device.  Doing "aplay -l" gives me this output:
```
    **** List of PLAYBACK Hardware Devices ****
    card 0: sun4icodec [sun4i-CODEC], device 0: M1 PCM [sun4i PCM]
      Subdevices: 1/1
      Subdevice #0: subdevice #0
    card 1: sun4isndhdmi [sun4i-sndhdmi], device 0: SUN4I-HDMIAUDIO sndhdmi-0 []
      Subdevices: 1/1
      Subdevice #0: subdevice #0
```

So looks like just the HDMI devices listed in alsamixer are found and not my USB Audio device.  However doing "lsusb" gives me:
```
    Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
    Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
    Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
    Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
    Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
    Bus 003 Device 002: ID 0d8c:000e C-Media Electronics, Inc. Audio Adapter (Planet UP-100, Genius G-Talk)
    Bus 004 Device 002: ID 0bda:8176 Realtek Semiconductor Corp. RTL8188CUS 802.11n WLAN
```

Which means the actual USB device is being detected fine.  The general Sound Debugging guide for Ubuntu suggested running "find /lib/modules/uname -r | grep snd", which for me outputs:
```
   /lib/modules/3.0.36-t1+/kernel/sound/core/snd-rawmidi.ko
   /lib/modules/3.0.36-t1+/kernel/sound/soc/sun4i/i2s/sun4i-sndi2s.ko
   /lib/modules/3.0.36-t1+/kernel/sound/soc/sun4i/i2s/sndi2s.ko
   /lib/modules/3.0.36-t1+/kernel/sound/soc/sun4i/spdif/sndspdif.ko
   /lib/modules/3.0.36-t1+/kernel/sound/soc/sun4i/spdif/sun4i_sndspdif.ko
```

I think that is probably the problem.  The module I need after searching online seems to be the one for Generic USB Audio Device, which is snd-usb-audio.  Doing "modprobe snd-usb-audio" gives me a "FATAL: Module snd_usb_audio not found." error.  So I think I need that module but I have no idea how I am supposed to install or build it, all of the references I can find to it online seem to suggest just re-installing the distro.  Does anyone know how to get around this problem?

---

### Post by capa_da_gaita on 2012-07-14
i'am with the same problem.

I'll follow the topic.

---

### Post by tomvandermeer on 2012-08-24
Same here also trying the MK802 with a Belkin tunestudio.
I'd love to see Ardour working on the MK802

---

