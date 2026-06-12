---
title: "Lost Sound, Followed troubleshooter, not resolved"
date: 2008-05-22
forum: Multimedia Software
---

### Post by dominicw on 2008-05-22
I lost sound all of a sudden, so I went through the list here at:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

The error I get when clicking on the tray icon for sound is:

No volume control Gstreamer plugins and/or devices found

Still no luck, here is the output of what I found so far:

Using:  lspci -v

```

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
        Subsystem: Dell Unknown device 01d7
        Flags: bus master, fast devsel, latency 0, IRQ 20
        Memory at efebc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>


```

If I try to use modprobe, any driver, this is what I get:

```

dominic@Kane:~$ sudo modprobe snd-als100
FATAL: Error inserting snd (/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_seq_device (/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/acore/seq/snd-seq-device.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd (/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_seq_device (/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/acore/seq/snd-seq-device.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_rawmidi (/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/acore/snd-rawmidi.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd_rawmidi
WARNING: Error inserting snd_mpu401_uart (/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/drivers/mpu401/snd-mpu401-uart.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_timer (/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/acore/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd (/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/acore/snd.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd
WARNING: Error inserting snd_timer (/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/acore/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_pcm (/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/acore/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd_pcm
WARNING: Error inserting snd_sb_common (/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/isa/sb/snd-sb-common.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_sb16_dsp (/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/isa/sb/snd-sb16-dsp.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_hwdep (/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/acore/snd-hwdep.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_opl3_lib (/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/drivers/opl3/snd-opl3-lib.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_als100 (/lib/modules/2.6.24-16-generic/ubuntu/sound/alsa-driver/isa/snd-als100.ko): Unknown symbol in module, or unknown parameter (see dmesg)


```

I checked the following:

The user is attached to the audio group

I upgraded to Hardy last night with hopes that any bad configuration would fix itself during upgrade

I reinstalled Gstreamer

I purged/removed linux sound base alsa base then installed it again

Sound did work until recently, however I am not sure I can pinpoint an event or install that would have changed anything.

This is on a Dell M1210 XPS laptop

When using the aply -l I get:

```
aplay: device_list:205: no soundcards found...
```

Any thoughts?

Dominic

My

---

### Post by dominicw on 2008-05-22
Just confirmed that the sound does work in Windows (dual boot)

Dominic

---

### Post by dominicw on 2008-05-24
I now have sound, but no control over the volume level or mute.  My laptop buttons do not affect the sound level, nor is there any access to the on screen audio levels.  (Same Gstreamer error).

Dominic

---

