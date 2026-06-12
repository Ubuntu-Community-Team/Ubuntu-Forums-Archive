---
title: "No Sound from Speakers"
date: 2006-09-02
forum: Multimedia &amp; Video
---

### Post by Mudbream on 2006-09-02
Hi,
I've recently got a new PC and have installed Dapper Drake. The system has a 7.1 Channel Surround Sound Audio (on-board) Creative Labs Inspire T7900 - 7.1 Surround with Subwoofer. However, when I try listen to music etc it does not play out of the speakers but only out of the monitor speakers which is not what I want. My guess is its using the wrong settings somewhere, but I can't figure out where.
On booting I do hear some noise from the speakers so know they work, plus dual booting with Windows so know they work.

lspci | grep audio returns nothing.

lsmod | grep snd
snd_hda_intel          18964  3
snd_hda_codec         154672  1 snd_hda_intel
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              25220  2 snd_pcm
snd                    55268  10 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  1 snd
snd_page_alloc         10632  2 snd_hda_intel,snd_pcm

Anyone got any idea's?
Would be great to have the surround sound working!

thanks,

Mudbream

---

### Post by sebastfr on 2006-09-02
could you copy/paste the contents of /etc/asound.conf and/or ~/.asoundrc ?

you're meant to declare the mappings of your speakers in there. I had to do this to have 4.1 working on my creative live24 usb (well it's fake 4.1 since i can control only one stream, but better than nothing)

seb

---

### Post by Mudbream on 2006-09-02
> **sebastfr said:**
> could you copy/paste the contents of /etc/asound.conf and/or ~/.asoundrc ?

you're meant to declare the mappings of your speakers in there. I had to do this to have 4.1 working on my creative live24 usb (well it's fake 4.1 since i can control only one stream, but better than nothing)

seb

/etc/asound.conf: 
```
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

pcm.!default {
     type asym
     playback.pcm "dmixer"
     capture.pcm "dsnooper"
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

And I don't have the other files ~/.asoundrc on my system.

Thanks,

Mudbream

---

