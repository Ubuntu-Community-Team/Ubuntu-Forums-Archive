---
title: "dmix and spdif problems with ICH5/AC97"
date: 2006-12-24
forum: Multimedia &amp; Video
---

### Post by brokenladder on 2006-12-24
I've tried a million different /etc/asound.conf configurations, and I can't get anything to work.  My analog out works, but only one program can use it at a time.  My digital out doesn't work at all -- the optical red light isn't even visible.  Yet I get sound through it if I do:

aplay -D plug:iec958 /usr/share/sounds/startup.wav

Incidentally, if I watch the connector, it puts out that red light for a few seconds when it plays this, but then goes right back off.

**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I have had the SPDIF working before, with the analog part used for my VoIP headset, with a different configuration that I've lost at this point.  But dmix never worked for either.  Only one program could access each device at a time.  Here's the latest /etc/asound.conf I've tried:

# Override the default output used by ALSA.
# If you do not override the default, your default
# device is identical to the (unmixed) analog device
# shown below. If you prefer mixed and/or digital
# output, uncomment the appropriate four lines below
# (only one slave.pcm line).
pcm.!default {
type plug
## Uncomment the following to use mixed analog by default
#slave.pcm "dmix-analog"
## Uncomment the following to use unmixed digital by default
# slave.pcm "digital-hw"
## Uncomment the following to use mixed digital by default
slave.pcm "dmix-digital"
}

# Alias for analog output on the nForce2 (hw:0,0)
# - This is identical to the device named "default"--which
# always exists and refers to hw:0,0 (unless overridden)
# - Therefore, we can specify "hw:0,0", "default", or "analog"
# to access analog output on the nForce2

pcm.analog {
type plug
slave.pcm "analog-hw"
}

# Control device (mixer, etc.) for the nForce2 card
ctl.analog {
type hw
card 0
}

# Alias for (rate-converted) mixed analog output on the
# nForce2 (hw:0,0)
# - This will accept audio input--regardless of rate--and
# convert to the rate required for the dmix plugin
# (in this case 48000Hz)
pcm.mixed-analog {
type plug
slave.pcm "dmix-analog"
}


# Control device (mixer, etc.) for the nForce2 card
ctl.mixed-analog {
type hw
card 0
}


# Alias for (rate-converted) digital (S/PDIF) output on the
# nForce2 (hw:0,4)
# - This will accept audio input--regardless of rate--and
# convert to the rate required for the S/PDIF hardware
# (in this case 48000Hz)
pcm.digital {
type plug
slave.pcm "digital-hw"
}

# Control device (mixer, etc.) for the nForce2 card
ctl.digital {
type hw
card 0
}

# Alias for mixed (rate-converted) digital (S/PDIF) output on the
# nForce2 (hw:0,4)
# - This will accept audio input--regardless of rate--and
# convert to the rate required for the S/PDIF hardware
# (in this case 48000Hz)
pcm.mixed-digital {
type plug
slave.pcm "dmix-digital"
}

# Control device (mixer, etc.) for the nForce2 card
ctl.mixed-digital {
type hw
card 0
}

# The following devices are not useful by themselves. They
# require specific rates, channels, and formats. Therefore,
# you probably do not want to use them directly. Instead use
# of of the devices defined above.

# Alias for analog output on the nForce2 (hw:0,0)
# Do not use this directly--it requires specific rate,
# channels, and format
pcm.analog-hw {
type hw
card 0
# The default value for device is 0, so no need to specify
}

# Control device (mixer, etc.) for the nForce2 card
ctl.analog-hw {
type hw
card 0
}

# Alias for digital (S/PDIF) output on the nForce2 (hw:0,4)
# Do not use this directly--it requires specific rate,
# channels, and format
pcm.digital-hw {
type hw
card 0
device 4
}

# Control device (mixer, etc.) for the nForce2 card
ctl.digital-hw {
type hw
card 0
}

# Direct software mixing plugin for analog output on
# the nForce2 (hw:0,0)
# Do not use this directly--it requires specific rate,
# channels, and format
pcm.dmix-analog {
type dmix
ipc_key 1634
slave {
pcm "analog-hw"
period_time 0
period_size 1024
buffer_size 4096
rate 44100
}
}

# Control device (mixer, etc.) for the nForce2 card
ctl.dmix-analog {
type hw
card 0
}


# Direct software mixing plugin for digital (S/PDIF) output
# on the nForce2 (hw:0,4)
# Do not use this directly--it requires specific rate,
# channels, and format
pcm.dmix-digital {
type dmix
ipc_key 1235
slave {
pcm "hw:0,4"
period_time 0
period_size 1024
buffer_size 4096
rate 44100
}
}

# Control device (mixer, etc.) for the nForce2 card
ctl.dmix-digital {
type hw
card 0
}

---

### Post by brokenladder on 2007-01-07
Dear Sweet God, I FINALLY got this working, thanks to something I realized from talking to an alsa uber-genius who goes by the IRC handle of "crimsun".  Whomever I copied the file above from, I never noticed that he had the rate set incorrectly on the digital!  Ugh.  Just take that line out entirely, and it WORKS!!

Voila!  ICH5 with dmix on Ubuntu.

And two years of my misery now OVER!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

/me stomps on the ICH5

---

### Post by shelbydz on 2007-01-22
I'm getting the exact same thing. When I set all of my options in the Sound Preferences to Intel ICH5 - IEC958, the sound stops playing through the analog plug. When I run: 
aplay -D plug:iec958 /usr/share/sounds/startup.wav I hear the sound or see the red light from the optical plug. 

However, I've tried the above /etc/asound.conf file, omitting the rate 44100 line, but Gnome freaks out and doesn't recognize any sound card at all. 

Is Dmix on the repositories? I can't seem to find it. Is this going to give me digital output from Cedega? 

thanks for the help.

---

