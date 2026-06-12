---
title: "HELP!! Microphone not working!"
date: 2006-07-25
forum: Multimedia &amp; Video
---

### Post by odinfromvalhalla on 2006-07-25
i have installed dapper for some time now and everything is great except i can't use my microphone. i can play xmms/banshee/mplayer at the same time but when i record something then play it, it is just some noise. I have tryed to change the input source with no luck.

capture is unmuted in alsamixer.

here is my configuration:

```

illuvatar@ASGARD:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```

0000:00:1b.0 0403: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
        Subsystem: Intel Corporation: Unknown device 0606
        Flags: bus master, fast devsel, latency 0, IRQ 66
        Memory at 503c0000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <available only to root>

```

```

illuvatar@ASGARD:~$ cat /proc/asound/modules
0 snd_hda_intel

```

```

illuvatar@ASGARD:~$ lsmod |grep snd
snd_hda_intel          20468  2
snd_hda_codec         162160  1 snd_hda_intel
snd_pcm_oss            56448  0
snd_mixer_oss          20544  1 snd_pcm_oss
snd_pcm                96708  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              26884  1 snd_pcm
snd                    60004  10 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10784  1 snd
snd_page_alloc         11304  2 snd_hda_intel,snd_pcm

```


```

illuvatar@ASGARD:~$ cat /etc/esound/esd.conf
[esd]
auto_spawn=1
spawn_options=-terminate -nobeeps -as 1 -d duplex
spawn_wait_ms=50
# default options are used in non-spawned mode
default_options=-d duplex

```

```

illuvatar@ASGARD:~$ cat /etc/asound.conf
# Set default sound card
# Useful so that all settings can be changed to a different card here.
pcm.snd_card {
     type hw
     card 0
}

# Allow mixing of multiple output streams to this device
pcm.dmixer {
     type dmix
     ipc_key 1024
     slave.pcm "snd_card"
     slave {
          pcm "hw:0,0"
          # This stuff provides some fixes for latency issues.
          # buffer_size should be set for your audio chipset.
          period_time 0
          period_size 1024
          buffer_size 4096
          # rate 44100
     }

     bindings {
          0 0
          1 1
     }
}

# Allow reading from the default device.
# Also known as record or capture.
pcm.dsnooper {
     type dsnoop
     ipc_key 2048
     slave.pcm "snd_card"
     slave {
          pcm "hw:0,2"
     }


     bindings {
          0 0
          1 1
     }
}

# This is what we want as our default device
# a fully duplex (read/write) audio device.
pcm.duplex {
     type asym
     playback.pcm "dmixer"
     capture.pcm "dsnooper"
}

###################
# CONVERSION PLUG #
###################
# Setting the default pcm device allows the conversion
# rate to be selected on the fly.
# duplex mode allows any alsa enabled app to read/write
# to the dmix plug (Fixes a problem with wine).

#pcm.!default {
#     type asym
#     playback.pcm "dmixer"
#     capture.pcm "dsnooper"
#}

pcm.!default {
    type plug
    slave.pcm "duplex"
}

########
# AOSS #
########
# OSS dsp0 device (OSS needs only output support, duplex will break some stuff)
pcm.dsp0 {
     type plug
     slave.pcm "dmixer"
}

# OSS control for dsp0 (needed?...this might not be useful)
ctl.dsp0 {
     type plug
     slave.pcm "snd_card"
}

# OSS control for dsp0 (default old OSS is mixer0)
ctl.mixer0 {
     type plug
     slave.pcm "snd_card"
}

```

```

illuvatar@ASGARD:~$ cat /etc/libao.conf
default_driver=alsa

```

looking forward for your answer!

best regards,
Romeo

---

