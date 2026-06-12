---
title: "IEC958 / SPDIF working only if muted"
date: 2011-01-30
forum: Multimedia Software
---

### Post by salazarcrumb on 2011-01-30
Hello, everyone. My system is Ubuntu 10.04 LTS (I also use Debian Lenny, with the same issue)

I have this onboard soundcard (lspci):

```
0:04.0 Multimedia audio controller: nVidia Corporation CK804 Ac'97 Audio Controller (rev a2)
```and this is the output of aplay -l:

```

*** Lista de PLAYBACK dispositivos hardware ***
Tarjeta 0: CK804 [NVidia CK804], dispositivo 0: Intel ICH [NVidia CK804]
Subdispositivos: 1/1
Subdispositivo #0: subdevice #0
Tarjeta 0: CK804 [NVidia CK804], dispositivo 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
Subdispositivos: 1/1
Subdispositivo #0: subdevice #0
```Here is my asoundrc (taken -and adapted- from here: [http://www.mythtv.org/wiki/Configuring_Digital_Sound](http://www.mythtv.org/wiki/Configuring_Digital_Sound)):

```
# ALSA configuration file

##### USAGE #####
# Save this file as "~/.asoundrc" (for user-specific sound configuration) or
# "/etc/asound.conf" (for system-wide sound configuration) and specify ALSA
# device names ad described in the next section.


##### DEVICE NAMES #####
# This configuration file defines four devices for use by the user.  Those
# devices are "analog", "mixed-analog", "digital", and "mixed-digital".  The
# user may also re-define "default" to be identical to one of the above-named
# devices (i.e. to send all sound output to the digital output unless otherwise
# specified).  Use the device names as described below:
#  - "analog" outputs to the analog output directly and (at least on software
#  sound cards) blocks other audio output.  After playback completes, "queued"
#  sounds are output in sequence.
#  - "mixed-analog" mixes audio output from multiple programs into the analog
#  output (so you can hear beeps, alerts, and other noises while playing back
#  an audio stream).
#  - "digital" outputs to the digital output directly.  Since most (all?)
#  digital outputs expect 48kHz PCM audio, this may not work for some playback
#  (i.e. CD's--which are 44.1kHz PCM audio--or 32kHz audio streams from TV
#  recordings, etc.).
#  - "mixed-digital"

# All other devices created within this file are used only by the configuration
# file itself and should /not/ be used directly.  In other words, do not use
# the devices "analog-hw", "dmix-analog", "digital-hw", or "dmix-digital".


##### IMPORTANT #####
# To make this ALSA configuration file work with your sound card, you will need
# to define the appropriate card and device information for the "analog-hw" and
# "digital-hw" devices below.  You can find the card and device information
# using "aplay -l".


##### Configuration File #####

# Override the default output used by ALSA.  If you do not override the
# default, your default device is identical to the (unmixed) "analog" device
# shown below.  If you prefer mixed and/or digital output, uncomment the
# appropriate four lines below (only one slave.pcm line).
#
# Note, also, that as of ALSA 1.0.9, "software" sound cards have been modified
# such that their default "default" device is identical to the "mixed-analog"
# device.  Whether using an ALSA version before or after 1.0.9, it does no harm
# and has no affect on performance to redefine the device (even if the
# redefinition does not change anything).  Also, by using this ALSA
# configuration file, you once again have access to unmixed analog output using
# the "analog" device.
pcm.!default {
  type plug
## Uncomment the following to use (unmixed) "analog" by default
#  slave.pcm "analog-hw"
## Uncomment the following to use "mixed-analog" by default
#  slave.pcm "dmix-analog"
## Uncomment the following to use (unmixed) "digital" by default
  slave.pcm "digital-hw"
## Uncomment the following to use "mixed-digital" by default
#  slave.pcm "dmix-digital"
}

# Control device (mixer, etc.) for the card
ctl.!default {
  type hw
  card 0
  }

# Alias for (converted) analog output on the card
# - This is identical to the device named "default"--which always exists and
# refers to hw:0,0 (unless overridden)
# - Therefore, we can specify "hw:0,0", "default", or "analog" to access analog
# output on the card
# - Note that as of ALSA 1.0.9, "software" sound card definitions redefine
# "default" to do mixing, meaning this device is different from "default" and
# allows playback while blocking other sound sources (until playback
# completes).
pcm.analog {
  type plug
  slave.pcm "analog-hw"
  hint {
    show on
    description "Analog Output - Use analog outputs, converting samples, format, and rate as necessary."
  }
}

# Control device (mixer, etc.) for the card
ctl.analog {
  type hw
  card 0
}

# Alias for (converted) mixed analog output on the card
# - This will accept audio input--regardless of rate--and convert to the rate
# required for the dmix plugin (in this case 48000Hz)
# - Note that as of ALSA 1.0.9, "software" sound card definitions redefine
# "default" to do mixing, meaning this device is identical to "default" for
# "software" sound cards.
pcm.mixed-analog {
  type plug
  slave.pcm "dmix-analog"
  hint {
    show on
    description "Mixed Analog Output - Use analog outputs, converting samples, format, and rate as necessary. Allows mixing with system sounds."
  }
}

# Control device (mixer, etc.) for the card
ctl.mixed-analog {
  type hw
  card 0
}

# Alias for (converted) digital (S/PDIF) output on the card
# - This will accept audio input--regardless of rate--and convert to the rate
# required for the S/PDIF hardware (in this case 48000Hz)
pcm.digital {
  type plug
  slave.pcm "digital-hw"
  hint {
    show on
    description "Digital Output - Use digital outputs, converting samples, format, and rate as necessary."
  }
}

# Control device (mixer, etc.) for the card
ctl.digital {
  type hw
  card 0
  }

# Alias for mixed (converted) digital (S/PDIF) output on the card
#  - This will accept audio input--regardless of rate--and convert to the rate
#  required for the S/PDIF hardware (in this case 48000Hz)
pcm.mixed-digital {
  type plug
  slave.pcm "dmix-digital"
  hint {
    show on
    description "Mixed Digital Output - Use digital outputs, converting samples, format, and rate as necessary. Allows mixing with system sounds."
  }
}

# Control device (mixer, etc.) for the card
ctl.mixed-digital {
  type hw
  card 0
  }

# The following devices are not useful by themselves.  They require specific
# rates, channels, and formats.  Therefore, you probably do not want to use
# them directly.  Instead use of of the devices defined above.

# Alias for analog output on the card
# Do not use this directly--it requires specific rate, channels, and format
pcm.analog-hw {
  type hw
  card 0
  # The default value for device is 0, so no need to specify
#  - Uncomment one of the below or create a new "device N" line as appropriate
#    for your sound card
#  device 1
#  device 4
}

# Control device (mixer, etc.) for the card
ctl.analog-hw {
  type hw
  card 0
}

# Alias for digital (S/PDIF) output on the card
# Do not use this directly--it requires specific rate, channels, and format
pcm.digital-hw {
  type hw
  card 0
#  - Comment out "device 1" above and uncomment one of the below or create a
#    new "device N" line as appropriate for your sound card
  device 2
#  device 4
}

# Control device (mixer, etc.) for the card
ctl.digital-hw {
  type hw
  card 0
}

# Direct software mixing plugin for analog output on the card
# Do not use this directly--it requires specific rate, channels, and format
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

# Control device (mixer, etc.) for the card
ctl.dmix-analog {
  type hw
  card 0
}

# Direct software mixing plugin for digital (S/PDIF) output on the card
# Do not use this directly--it requires specific rate, channels, and format
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

# Control device (mixer, etc.) for the card
ctl.dmix-digital {
  type hw
  card 0
}

```The issue is that I only get digital sound (spdif, coaxial) when, AFTER launching, i.e., mplayer:

```
mplayer -ao alsa:device=hw=0.2 file.mp3
```I have to MUTE the IEC958 channel, by alsamixer or amixer:
```
amixer set IEC958 off
```Notice the "off" (not mute). Also, the same issue happens if mplayer launches an avi with AC3 soundtrack.

Of course, analog output works without problems of any kind

Although my issue is described and solved here:
[http://ubuntuforums.org/showthread.php?t=659562](http://ubuntuforums.org/showthread.php?t=659562)
those proposed solutions have not worked for me.


Thanks in advance.

---

