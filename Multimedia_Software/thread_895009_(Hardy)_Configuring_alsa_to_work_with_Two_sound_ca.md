---
title: "(Hardy) Configuring alsa to work with Two sound cards for recording and playback"
date: 2008-08-19
forum: Multimedia Software
---

### Post by Lordrath on 2008-08-19
Ok I got ddo working with my mic now, it took me a few weeks of trial and error but basically what I gather is that DDO is not able to detect oss drivers for more than one sound card, so I had to rewrite my .asoundrc file to enable duplex for dmix. Now I have two sound cards so this wont work for everyone.

1. Open Terminal and type *aplay -l* you should get something that looks like this.

[I]**** List of PLAYBACK Hardware Devices ****
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
[/I]

Remember the letters in the first set of brackets [] because that is your sound driver.

Then go back to terminal and type sudo gedit ~/.asoundrc

2. Copy and Paste this into the file:

[I]# Set default sound card
# Useful so that all settings can be changed to a different card here.
pcm.snd_card0 {
type hw
card 0
device 0
}

pcm.snd_card1 {
type hw
card 1
device 0
}

# Allow mixing of multiple output streams to this device
pcm.output {
type dmix
ipc_key 1024
ipc_perm 0660 # Sound for everybody in your group!
slave.pcm "snd_card0"

slave {
# This stuff provides some fixes for latency issues.
# buffer_size should be set for your audio chipset.
period_time 0
period_size 1024
buffer_size 8192
# buffer_size 4096
# buffer_size 2048
}

bindings {
0 0
1 1
}
}

pcm.input {
type dsnoop
ipc_key 2048
slave.pcm "snd_card0"

## Possible artsd full duplex fix:
# slave {
# period_time 0
# period_size 1024
# buffer_size 8192
# }

bindings {
0 0
1 1
}
}
# Allow reading from the default device.
# Also known as record or capture.
pcm.input1 {
type dsnoop
ipc_key 2049
slave.pcm "snd_card1"

## Possible artsd full duplex fix:
slave {
period_time 0
period_size 1024
buffer_size 8192
# buffer_size 4096
# buffer_size 2048
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
playback.pcm "**Primary Sound Driver (Sound device 0)**"
capture.pcm "**Secondary Sound Driver (Sound device 1)**"
# capture.pcm "input1"
}

###################
# CONVERSION PLUG #
###################
# Setting the default pcm device allows the conversion
# rate to be selected on the fly.
# duplex mode allows any alsa enabled app to read/write
# to the dmix plug (Fixes a problem with wine).
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
slave.pcm "output"
}

#
pcm.dsp1 {
type plug
slave.pcm "output1"
}
[/I]

Please take note of the bold lettering, you will have to change those two values to the driver of the sound devices you discovered in step 1.

3. Go to System - Preferences - Sound and change all the sound devices to ALSA (not sure if there are any consequences for not doing this but I usually do it anyway.)

4. Go back to your terminal and type winecfg

5. Click on the audio tab and go to alsa and see if the names of your sound cards are under the Waveout and Wavein.

6. Then you should be able to start up DDO and go to your audio options and both sound cards will be detected under the advanced audio button.

(Dont forget to check and make sure all your sound is turned up in ubuntu or your mic will not work and you will spend the next two days banging your head on the desk trying to figure it out.)

Thats it kiddies good luck and happy gaming

-LR

---

