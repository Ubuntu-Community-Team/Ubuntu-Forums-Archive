---
title: "Downmixed 2 Channel PCM to SPIF, Passthrough to HDMI"
date: 2010-07-31
forum: Multimedia Software
---

### Post by SeanOB on 2010-07-31
Hi ALSA (and PulseAudio) Experts!

I have a receiver that will only output stereo sources to Zone2 (Denon 2809ci).  So...  

I'd like to have both the SPDIF and HDMI outputing simultaneously.  With SPDIF always outputting stereo PCM and HDMI outputting stereo or DTS/AC3 passthrough (depending on the source).

My first priority is getting stereo source content (music) to output from both HDMI and SPDIF at the same time.

My second (lower) priority is to get downmixed stereo from SPDIF with passthrough DTS/AC3 from the HDMI.  This case isn't as important - since it's only really useful when I want to be able to hear a game broadcast in 5.1 while I'm in the kitchen (zone2).  Most of the time I just want to hear music in both zones and movies and tv in just zone 1 -- where the TV is.

About my system:
Ubuntu 9.04 jaunty
with sound outputs from:
[LIST]
[*]MythTV FrontEnd
[*]Boxee (XBMC derivative)
[*]Firefox Flash (uses whatever the system is using...)
[*]System Sounds
[/LIST]

While I'm totally open to using PulseAudio - I have no idea where to start ...  so I went down the ALSA road.

I've followed this thread:
[http://forum.xbmc.org/showthread.php?t=74882](http://forum.xbmc.org/showthread.php?t=74882)

And now have an asound.conf that looks like this:
```
# Control device (mixer, etc.) for the card
# Digital = HDMI
# Optical = SPDIF
# goal - send stereo out of the SPDIF and both stereo and multichannel out HDMI
# audio output device: ALSA:stereo
# passthrough output device: ALSA:digital


ctl.!default {
  type hw
  card 0
}

pcm.!default {
   type plug
   slave {
    pcm multi
    rate 48000
  }
  ttable.0.0 1.0
  ttable.1.1 1.0
  ttable.0.2 1.0
  ttable.1.3 1.0
}

pcm.stereo {
  type plug
  slave {
    pcm multi
    rate 48000
  }
  ttable.0.0 1.0
  ttable.1.1 1.0
  ttable.0.2 1.0
  ttable.1.3 1.0
  hint {
    show on
    description "Optical Stereo Output (SPDIF)"
  }


}

ctl.stereo {
  type hw
  card 0
}

pcm.multi {
  type multi
  slaves.a.pcm "optical-hw"
  slaves.a.channels 2
  slaves.b.pcm "digital-hw"
  slaves.b.channels 2
  bindings.0.slave a
  bindings.0.channel 0
  bindings.1.slave a
  bindings.1.channel 1
  bindings.2.slave b
  bindings.2.channel 0
  bindings.3.slave b
  bindings.3.channel 1
}

ctl.multi {
  type hw
  card 0
}

pcm.optical {
  type plug
  slave.pcm "optical-hw"
}

ctl.optical {
  type hw
  card 0
}

pcm.digital {
  type plug
  slave.pcm "digital-hw"
  hint {
    show on
    description "HDMI Digital Passthrough Output (HDMI)"
  }
}

ctl.digital {
  type hw
  card 0
}

pcm.optical-hw {
  type hw
  card 0
  device 1
}

ctl.optical-hw {
  type hw
  card 0
}

pcm.digital-hw {
  type hw
  card 0
  device 3
}

ctl.digital-hw {
  type hw
  card 0
}

```

With this setup I have MythTV working for my first priority - music only.  But it looks like when I run passthrough the stereo downmix is killed.
I have MythTV setup with ALSA:digital as the passthrough audio device and ALSA:stereo as the default audio device.

The systems sounds work too!

Boxee wouldn't accept ALSA:stereo or ALSA:digital.  So it's not working now.  And it's weird - but when it starts it plays it's little startup song.  But it won't let me play music.  Just reports that the audio device is in use: "Failed to initialize the audio device"

Any tips on how to do this better would be appreciated!

The aforementioned thread uses the a52 alsa plugin.  I'm not super keen on that - since it re-encodes the multichannel stream for HDMI output.  I'd prefer to passthrough the original stream to my receiver.

Thanks!

SeanOB

---

### Post by SeanOB on 2010-07-31
This asound.conf works a bit better for boxee.
No passthrough - but at least stereo is working with the Audio Output Device set to "stereo"

```
# Control device (mixer, etc.) for the card
# Digital = HDMI
# Optical = SPDIF
# goal - send stereo out of the SPDIF and both stereo and multichannel out HDMI
# audio output device: ALSA:stereo
# passthrough output device: ALSA:digital


ctl.!default {
  type hw
  card 0
}

pcm.!default {
  type plug
  slave {
    pcm multi
    rate 48000
  }
  ttable.0.0 1.0
  ttable.1.1 1.0
  ttable.0.2 1.0
  ttable.1.3 1.0
}

pcm.stereo {
  type plug
  slave {
    pcm multi
    rate 48000
  }
  ttable.0.0 1.0
  ttable.1.1 1.0
  ttable.0.2 1.0
  ttable.1.3 1.0
  hint {
    show on
    description "Optical Stereo Output (SPDIF)"
  }


}

ctl.stereo {
  type hw
  card 0
}

pcm.multi {
  type multi
  slaves.a.pcm "optical"
  slaves.a.channels 2
  slaves.b.pcm "digital"
  slaves.b.channels 2
  bindings.0.slave a
  bindings.0.channel 0
  bindings.1.slave a
  bindings.1.channel 1
  bindings.2.slave b
  bindings.2.channel 0
  bindings.3.slave b
  bindings.3.channel 1
}

ctl.multi {
  type hw
  card 0
}

pcm.optical {
  type plug
  slave.pcm "domixer"
}

ctl.optical {
  type hw
  card 0
}

pcm.digital {
  type plug
  slave.pcm "dmixer"
  hint {
    show on
    description "HDMI Digital Passthrough Output (HDMI)"
  }
}

ctl.digital {
  type hw
  card 0
}

pcm.domixer {
   type dmix
   ipc_key 1024
   ipc_key_add_uid false
   ipc_perm 0660
   slave {
      pcm "optical-hw"
      rate 48000
      channels 2
      format S32_LE
      period_time 0
      period_size 2048
      buffer_time 0
      buffer_size 32768
   }
}

pcm.dmixer {
   type dmix
   ipc_key 1024
   ipc_key_add_uid false
   ipc_perm 0660
   slave {
      pcm "digital-hw"
      rate 48000
      channels 2
      format S32_LE
      period_time 0
      period_size 2048
      buffer_time 0
      buffer_size 32768
   }
}

pcm.optical-hw {
  type hw
  card 0
  device 1
}

ctl.optical-hw {
  type hw
  card 0
}

pcm.digital-hw {
  type hw
  card 0
  device 3
}

ctl.digital-hw {
  type hw
  card 0
}

```

---

### Post by SeanOB on 2010-07-31
And here's the boxee guisettings.xml section for audio:
```
    <audiooutput>
        <ac3passthrough>true</ac3passthrough>
        <audiodevice>custom</audiodevice>
        <customdevice>stereo</customdevice>
        <custompassthrough>digital</custompassthrough>
        <downmixmultichannel>false</downmixmultichannel>
        <dtspassthrough>true</dtspassthrough>
        <library>0</library>
        <mode>1</mode>
        <passthroughdevice>custom</passthroughdevice>
        <sep1></sep1>
        <sep2></sep2>
        <sep3></sep3>
    </audiooutput>
```

It sort of works -- but its inconsistent.
Stereo audio works fine.
5.1 passthrough works for some movies.

BUT - when boxee can't get the audio device on a movie - it punts AND it resets the audio settings to default.  Boo!

---

