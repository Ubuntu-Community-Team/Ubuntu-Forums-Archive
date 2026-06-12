---
title: "I broke my sound"
date: 2006-02-10
forum: Multimedia &amp; Video
---

### Post by RonJohnson on 2006-02-10
I don't know what I've done. I followed some alsa howto the other day here on these forums although i'm having problems finding the links now. The howto was on how to get sound to work with multiple sound sources. That worked for awhile then I started working on getting World of Warcraft to work. Sometime between fixing my sound and trying to get WoW to work I broke my sound. I can't figure out what I've done or how to get it back...

Any and all help is greatly appreciated.

---

### Post by Mustard on 2006-02-10
I'd just mention that sound problems are a bitch to troubleshoot. :)

There are so many settings to check its hard to know where to start.  Is there anyway you can find out what you have done so far?  Perhaps look through your bash history file to see what commands you entered in terminal?  Some idea of what state you have the configuration in might help.

---

### Post by RonJohnson on 2006-02-11
Ok, I did as you suggested. After looking through the .bash_history I found the following commands that were run:

apt-get install libesd-alsa0
nano -w /etc/esound/esd.conf
nano -w /etc/asound.conf
nano -w /etc/libao.conf

esd.conf
```

[esd]
auto_spawn=1
spawn_options=-terminate -nobeeps -as 2 -d default
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=

```

asound.conf
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

libao.conf
```

default_driver=alsa

```

The other thing I remember in the instructions was to uncheck the start the sound server option under System > Properties > Sound. I have gone back and checked that and that seems to give me default ubuntu sounds but still no sounds from other apps. I'm so confused :???: 

I have looked for the original thread, not hard I hate to admit, but haven't found it. Thanks for the help you've already given!!

---

### Post by RonJohnson on 2006-02-11
BTW if anyone knows of how to restore my sound to default configuration that is better than no sound

---

### Post by FarEast on 2006-02-12
Hi RonJohnson,

Here are contents of mine.

/etc/esound/esd.conf
[esd]
auto_spawn=1
spawn_options=-terminate -nobeeps -as 2 -d default
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=

/etc/asound.conf
(does not exist)

/etc/libao.conf
default_driver=esd

---

### Post by stulesnett on 2006-05-19
I have installed 5.10 and do not seem to any sound.  I did a CAT /proc/asound/cards and the return status was ---no sound cards---.  Old version of Red Hat 6.+ sound worked fine.  I have run Automatix but still have nothing.  I would appreciate any assistance.

Stu

---

