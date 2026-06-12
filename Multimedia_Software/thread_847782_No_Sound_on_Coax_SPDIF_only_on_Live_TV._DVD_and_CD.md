---
title: "No Sound on Coax SPDIF only on Live TV. DVD and CD are fine"
date: 2008-07-02
forum: Multimedia Software
---

### Post by ferdies on 2008-07-02
Hi

Hope someone can help me...Been trying to solve problems for days but to no avail.

I have posted in mythtv and Linuxmce but no help has been offered. Hopefully, you guys can help me.

I have no sound on Live TV...Other features of Linux MCE like watching DVD, music do have sound.

I already followed some of the instructions from these sites: 
[http://www.mythtv.org/wiki/index.php..._Digital_Sound](http://www.mythtv.org/wiki/index.php..._Digital_Sound)
[http://www.mythtv.org/wiki/index.php..._AC3_and_SPDIF](http://www.mythtv.org/wiki/index.php..._AC3_and_SPDIF)

Since I am using Digital Coax/SPDIF for my sound system (solved this problem based on this [http://forum.linuxmce.org/index.php?topic=5539.0](http://forum.linuxmce.org/index.php?topic=5539.0))


Some details:
linuxmce@dcerouter:~$ uname -r
2.6.22-14-generic

I have this output:
----------------------
linuxmce@dcerouter:~$ aplay -L
front:CARD=Intel,DEV=0
HDA Intel, ALC880 Analog
Front speakers
surround40:CARD=Intel,DEV=0
HDA Intel, ALC880 Analog
4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
HDA Intel, ALC880 Analog
4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
HDA Intel, ALC880 Analog
5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
HDA Intel, ALC880 Analog
5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
HDA Intel, ALC880 Analog
7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
null
Discard all samples (playback) or generate zero samples (capture)
---------------------------

linuxmce@dcerouter:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC880 Analog [ALC880 Analog]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC880 Digital [ALC880 Digital]
Subdevices: 1/1
Subdevice #0: subdevice #0
--------------

Any idea on what to put in the MythTV frontend?

On Mythfrontend Utilities/Setup->Setup-General go to the Audio page and set your audio device as
Audio output device = ALSA:default
Passthrough outputdevice = default
Enable AC3 to SPDIF passthrough check
Enable DTS to SPDIF passthrough check


My .asoundrc in /home/mythtv contains the following:
-----------
cm.IntelHDA-hw {
type hw
card 0
}

pcm.!default {
type plug
slave.pcm "IntelHDA"
}

pcm.IntelHDA {
type dmix
ipc_key 1234
slave {
pcm "hw:0,1"
period_time 0
period_size 1024
buffer_size 4096
rate 44100
}
}

ctl.IntelHDA-hw{
type hw
card 0
}

----------------------


I also have asound.conf in /etc/
---------------
pcm_slave.convert48k {
pcm "spdif"
rate 48000
}

pcm.spdif_playback {
type plug
slave convert48k
}

pcm.asym_spdif {
type asym
playback.pcm "spdif_playback"
capture.pcm "plughw:0,1"
}

pcm.asym_analog {
type asym
playback.pcm "plug:dmix"
capture.pcm "plughw:0"
}
pcm.!default asym_spdif
--------------


My sound in /etc/modprobe.d contains:

----------
alias snd-card-0 snd-hda-intel
options snd-hda-intel index=0
--------------------

Please advise if I still need anything or I am overdoing it. I need to have sound for my live TV in MythTV. Thanks.

---

