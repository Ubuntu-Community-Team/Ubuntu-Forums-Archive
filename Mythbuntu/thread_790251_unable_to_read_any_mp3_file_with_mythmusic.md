---
title: "unable to read any mp3 file with mythmusic"
date: 2008-05-11
forum: Mythbuntu
---

### Post by pyrates on 2008-05-11
I use to be able to play back mp3 files just fine.  But now they have seemed to stop working.  I got everything else working.  I don't even see the count down timer of the progress of the mp3 being played anymore.  What can I do to fix this?

---

### Post by pyrates on 2008-05-13
Ok I got the audio working with myth music but now I can't watch dvd's with xine because the audio no longer works.  I have an a8n-sli deluxe motherbard with alc850 onboard sound using spdif to output.  Here is my configuration that works with myth music:

> # aplay -L
front:CARD=CK804,DEV=0
    NVidia CK804, NVidia CK804
    Front speakers
surround40:CARD=CK804,DEV=0
    NVidia CK804, NVidia CK804
    4.0 Surround output to Front and Rear speakers
surround41:CARD=CK804,DEV=0
    NVidia CK804, NVidia CK804
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=CK804,DEV=0
    NVidia CK804, NVidia CK804
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=CK804,DEV=0
    NVidia CK804, NVidia CK804
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=CK804,DEV=0
    NVidia CK804, NVidia CK804
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
null
    Discard all samples (playback) or generate zero samples (capture)

> 
# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

> 
# cat /etc/asound.conf
pcm.nforce-hw {
type hw
card 0
}

pcm.!default {
type plug
slave.pcm "nforce"
}

pcm.nforce {
type dmix
ipc_key 1234
slave {
pcm "hw:0,0"
}
}

ctl.nforce-hw {
type hw
card 0
}

MythTV General Settings:

> Audio output device: ALSA:default

Passthrough output device: Default

Max Audio Channels: 5.1 Upmix: Passive

x Enable AC3 to SPDIF passthrough
x Enable DTS to SPDIF passthrough

> mplayer -ao alsa:device=default file.mp3
speaker-test -D default -c 2 -t wav

Now if I change the /etc/asound.conf to this:

> # cat /etc/asound.conf.backup 
pcm.!default {
	type hw
	card 0
	device 2
## Uncomment the following to use "mixed-analog" by default
#  slave.pcm "dmix-analog"
## Uncomment the following to use (unmixed) "digital" by default
slave.pcm "digital-hw"
## Uncomment the following to use "mixed-digital" by default
#  slave.pcm "dmix-digital"
}

# Alias for digital (S/PDIF) output on the card
# Do not use this directly--it requires specific rate, channels, and format
pcm.digital-hw {
	type hw
	card 0
	#  device 1
	#  - Comment out "device 1" above and uncomment one of the below or create a new "device N" line as appropriate for your sound card or
	device 2
	#  device 4
}

I'm able to send ac3/dts compressed through spdif with xine with pass through selected as its default output in it.

How can I combine all this so both work?

---

