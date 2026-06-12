---
title: "wine + alsa / oss"
date: 2010-01-19
forum: Multimedia Software
---

### Post by biker126 on 2010-01-19
Hi everyone

First of all I want to apologize for making yet another thread about wine (and sound) but I've read through tons of guides and other threads and I still don't get my sound settings as I'd like to.

Problem in short:
When I have a sound source running (i.e. rhythmbox playing mp3 or skype) and I start wine (more specific: World of Warcraft) I have no sound in wine (wow).
When I start wine without any other sound source active I have sound in wine but not in the rest of my linux (i.e. rhythmplayer).

My wine version is 1.1.36
My ubuntu is 9.10

In wine config, when i activate only the "ALSA driver" I have no sound. When I activate both, the ALSA and the OSS, I have sound.

"Wave output device" for alsa is "dmix6" and input is "dsnooper".
"Wave output device" for oss is "Realtek ALC882" and input is "Realtek ALC882"

my /etc/asound.conf is a complete mess *imo* and looks like this:
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

```I copy&paste a lot of stuff from a lot of guides and I guess its kinda messed up. ALSA alone is running fine I think, since I can hear sound from different sources (rhythmbox + skype) at the same time and also 5.1 output is working (as well as mic input).

my /etc/esound/esd.conf (don't know if it's relevant) looks like this:
```

[esd]
auto_spawn=1
spawn_options=-terminate -nobeeps -as 2 -d default
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=

```So basicly I'd like to know if it's even possible to use WINE without OSS or whatever other way to be able to hear sound from WINE and other sources.

Thanks in advance!

---

### Post by biker126 on 2010-01-20
bump!

Does no one has an idea what could be wrong with my system and make wine sound not working correct with ALSA??? :-(

---

### Post by Yellow Pasque on 2010-01-20
Are you running Pulseaudio? Shouldn't you be using Wine's pulse driver?

If you keep using the OSS output, maybe you could use padsp to make it mix properly: [http://linux.die.net/man/1/padsp](http://linux.die.net/man/1/padsp)

---

### Post by biker126 on 2010-01-20
god you rock!!
using the the "ESound" (pulse) driver of wine solved all my problems :-)

I've never read anything about pulseaudio until lately when I installed skype (which is using it afaik) so I didn't even know that Wine also has a pulseaudio driver.

and what the difference between alsa, oss and pulse is I don't know either... :-p
but as long as it's working I'm fine with that...

---

### Post by lkjoel on 2010-09-08
> **Temüjin said:**
> Are you running Pulseaudio? Shouldn't you be using Wine's pulse driver?

If you keep using the OSS output, maybe you could use padsp to make it mix properly: [http://linux.die.net/man/1/padsp](http://linux.die.net/man/1/padsp)
I have OSS4.x installed, and WINE doesn't work!
Could someone help me?

---

### Post by Yellow Pasque on 2010-09-08
Did you run winecfg and select OSS in the audio tab?

---

### Post by lkjoel on 2010-09-10
> **Temüjin said:**
> Did you run winecfg and select OSS in the audio tab?
Yes.
It somehow needs ALSA.

---

### Post by Yellow Pasque on 2010-09-10
> **lkjoel said:**
> Yes.
It somehow needs ALSA.

I've never had this issue with OSS4/WINE. It always worked fine for me when I selected OSS (and only OSS) in winecfg. winecfg will throw warnings when it can't find ALSA, but you can ignore those. If you still can't get it working, you might try the asound/ALSA emulation trick in the OSS4 wiki.

---

### Post by lkjoel on 2010-09-10
I did try it.
The easy way and the hard way.

---

