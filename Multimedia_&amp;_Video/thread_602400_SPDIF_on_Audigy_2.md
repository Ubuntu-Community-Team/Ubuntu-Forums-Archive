---
title: "SPDIF on Audigy 2"
date: 2007-11-04
forum: Multimedia &amp; Video
---

### Post by sDoky on 2007-11-04
Well I've got a problem with my spdif output. I have been using this cool feature on windows xp with no problems. Now I got ubuntu and there's no way I can do it on my own. I've tried AC3 passthrough in totem, passthrough in xine, and all its pludins etc... I'm hopeless. The sound works just fine for anything but just as a PCM wave output, that's ok but not for DVD movies, for those I want passthrough to my decoder. I use ALSA and Creative Labs Audigy 2 Value, Alternatively I've got Intel High definition audio on my motherboard but I don't like that, although I've tried to use that with the exact same effect. Can you give me any advice? Thanks a lot for your help

PS: that's not problem just with ubuntu, before ubuntu I've had Fedora core 7, openSUSE 10.3 and neither on one did it work.

---

### Post by The Cokeaholics on 2007-11-04
Create ~/.asoundrc in your home:

```
# Override the default output used by ALSA.
# If you do not override the default, your default
# device is identical to the (unmixed) analog device
# shown below.  If you prefer mixed and/or digital
# output, uncomment the appropriate four lines below
# (only one slave.pcm line).
### Currently set w/digital-hw as the default output,
### comment out this entire section to use unmixed
### analog as your default
### -jarod
pcm.!default {
  type plug
## Uncomment the following to use mixed analog by default
#  slave.pcm "dmix-analog"
## Uncomment the following to use unmixed digital by default
  slave.pcm "digital-hw"
## Uncomment the following to use mixed digital by default
#  slave.pcm "dmix-digital"
}

# Alias for analog output on the Audigy (hw:0,0)
# - This is identical to the device named "default"--which
# always exists and refers to hw:0,0 (unless overridden)
# - Therefore, we can specify "hw:0,0", "default", or "analog"
# to access analog output on the Audigy
pcm.analog {
 type plug
 slave.pcm "analog-hw"
}

# Control device (mixer, etc.) for the Audigy card
ctl.analog {
 type hw
 card 0
}

# Alias for (rate-converted) mixed analog output on the
# Audigy (hw:0,0)
#  - This will accept audio input--regardless of rate--and
# convert to the rate required for the dmix plugin
# (in this case 48000Hz)
pcm.mixed-analog {
 type plug
 slave.pcm "dmix-analog"
}

# Control device (mixer, etc.) for the Audigy card
ctl.mixed-analog {
 type hw
 card 0
}

# Alias for (rate-converted) digital (S/PDIF) output on the
# Audigy (hw:0,0)
#  - This will accept audio input--regardless of rate--and
# convert to the rate required for the S/PDIF hardware
# (in this case 48000Hz)
pcm.digital {
 type plug
 slave.pcm "digital-hw"
}

# Control device (mixer, etc.) for the Audigy card
ctl.digital {
 type hw
 card 0
}

# Alias for mixed (rate-converted) digital (S/PDIF) output on the
# Audigy (hw:0,0)
#  - This will accept audio input--regardless of rate--and
# convert to the rate required for the S/PDIF hardware
# (in this case 48000Hz)
pcm.mixed-digital {
 type plug
 slave.pcm "dmix-digital"
}

# Control device (mixer, etc.) for the Audigy card
ctl.mixed-digital {
 type hw
 card 0
}

# The following devices are not useful by themselves.  They
# require specific rates, channels, and formats.  Therefore,
# you probably do not want to use them directly.  Instead use
# of of the devices defined above.

# Alias for analog output on the Audigy (hw:0,0)
# Do not use this directly--it requires specific rate,
# channels, and format
pcm.analog-hw {
 type hw
 card 0
 # The default value for device is 0, so no need to specify
}

# Control device (mixer, etc.) for the Audigy card
ctl.analog-hw {
 type hw
 card 0
}

# Alias for digital (S/PDIF) output on the Audigy (hw:0,0)
# Do not use this directly--it requires specific rate,
# channels, and format
pcm.digital-hw {
 type hw
 card 0
 device 0
}

# Control device (mixer, etc.) for the Audigy card
ctl.digital-hw {
 type hw
 card 0
}

# Direct software mixing plugin for analog output on
# the Audigy (hw:0,0)
# Do not use this directly--it requires specific rate,
# channels, and format
pcm.dmix-analog {
 type dmix
 ipc_key 1234
 slave {
   pcm "analog-hw"
   period_time 0
   period_size 1024
   buffer_size 4096
   rate 48000
 }
}

# Control device (mixer, etc.) for the Audigy card
ctl.dmix-analog {
 type hw
 card 0
}

# Direct software mixing plugin for digital (S/PDIF) output
# on the Audigy (hw:0,0)
# Do not use this directly--it requires specific rate,
# channels, and format
pcm.dmix-digital {
 type dmix
 ipc_key 1235
 slave {
   pcm "digital-hw"
   period_time 0
   period_size 1024
   buffer_size 4096
   rate 48000
 }
}

# Control device (mixer, etc.) for the Audigy card
ctl.dmix-digital {
 type hw
 card 0
}
```

Note that you should use the Xine engine Movie Player. In this applic, click Edit, Preferences, Audio tab, Audio output type: AC3 Passthrough. Kaffeine works fine as well. I have a fully working Audigy2ZS with Livedrive connected over SPDIF to SoundWorks DTT2500. (I am still struggling with the remote control with LIRC.) Good-luck with your soundboard! 

Robert

---

### Post by sDoky on 2007-11-05
Thanks man but that did not help. I will keep looking for an advice. Say where did you create the file? in your home directory? I mean /home/<username>/ and there create a file named '.asoundrc'? Cause that's what I've done.

---

### Post by The Cokeaholics on 2007-11-06
Yes, the file .asoundrc is in /home/<username>/ 

I remember it was quite a pain getting this working at that time. I installed Totem Xine through Synaptics and then tried the different settings in it (sometimes clicking/cracking sound) until I had it right and Dolby Digital lid up on AC3. I guess you are using the Xine and not gstreamer version of Totem? It never worked in VLC for me either.

Robert

---

### Post by sDoky on 2007-11-07
That's right, I'm using xine version, I'll try that. Thanks

> **The Cokeaholics said:**
> Yes, the file .asoundrc is in /home/<username>/ 

I remember it was quite a pain getting this working at that time. I installed Totem Xine through Synaptics and then tried the different settings in it (sometimes clicking/cracking sound) until I had it right and Dolby Digital lid up on AC3. I guess you are using the Xine and not gstreamer version of Totem? It never worked in VLC for me either.

Robert

---

