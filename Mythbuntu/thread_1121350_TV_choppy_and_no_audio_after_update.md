---
title: "TV choppy and no audio after update"
date: 2009-04-09
forum: Mythbuntu
---

### Post by korgman on 2009-04-09
So I did a mythbuntu update tonight.  Its been about 2 months since I did.  Then I manually updated the nvidia drivers to 180.44.  Video is very choppy now, and I have no sound over HDMI.  I get this:

matt@mythbuntu:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: Invalid argument

I used to get this:
matt@mythbuntu:/etc$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

but now I don't even see the HDMI device.  I only see device 0 and 1

---

### Post by korgman on 2009-04-10
The last few hours have been painful. I updated my mythbuntu system after 2 months of just leaving it alone. I reinstalled the Nvidia 180.22 drivers and got vid working immediately. But I now I no sound over HDMI and I have fought for the last 3 hours to get it back.

I reinstalled ALSA using the script here:
[http://ubuntuforums.org/showthread.p...10#post6589810](http://ubuntuforums.org/showthread.p...10#post6589810)

I ran alsa -l and got:
matt@mythbuntu:~$ aplay -l
Code:

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


So it is seeing the HDMI output! Good, but it used to look like this (subdevices are different numbers):
Code:

matt@mythbuntu:/etc$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

I used to get sound using this command, but my receiver won't acknowledge there is any audio input:
Code:

speaker-test -Dplughw:0,3 -c2

I use this asound.conf file that I know is overkill. I found it on the net months ago and it worked for me so I just left it.
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

ctl.!default hdmiout

pcm.optical {
        type hw
        card 0
        device 1
}

ctl.optical {
        type hw
        card 0
        device 1
}

pcm.hdmiout {
        type hw
        card 0
        device 3
}

ctl.hdmiout {
        type hw
        card 0
        device 3
}

pcm.multi {
        type multi
        slaves.a.pcm "hdmiout"
        slaves.a.channels 2
        slaves.b.pcm "optical"
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

When I run alsamixer I get this new problem:
Code:

matt@mythbuntu:~$ sudo alsamixer
[sudo] password for matt: 

alsamixer: function snd_ctl_open failed for default: Invalid argument

I am really mad that I upgraded a working MythTV system. WTF was I thinking? Any ideas?

MAtt

---

