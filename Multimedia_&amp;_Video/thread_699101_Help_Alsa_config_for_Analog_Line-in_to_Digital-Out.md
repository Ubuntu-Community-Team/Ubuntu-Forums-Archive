---
title: "Help: Alsa config for Analog Line-in to Digital-Out pass through"
date: 2008-02-17
forum: Multimedia &amp; Video
---

### Post by SergeiFranco on 2008-02-17
right, I have stumbled upon a problem, I have a device that I want to connect to analog in, that I want to play through digital out. I am using Alsa. I have setup dmix, dsnoop, asym and softvol. I am not sure if dsnoop works. although issuing this leads to working wav capture:
```
arecord -f cd -c 2 -Dplug:dsnoop foobar.wav
```
I need to know how I can route analog line in to digital out?
Currently it plays through analog out no problem.
Here is my .asoundrc:
```
pcm.!default {
    type            plug
    slave.pcm       "softvol"   #make use of softvol
}

pcm.softvol {
    type            softvol
    slave {
        pcm         "duplex"
    }
    control {
        name        "Master"
        card        0
    }
}

pcm.dmixer  {
   type dmix
   ipc_key 1024
   slave {
      pcm "hw:0,1"
      period_time 0
      period_size 1024
      buffer_size 8192
	rate 48000
   }
   bindings {
      0 0
      1 1
   }
}

ctl.dmixer {
   type hw
   card 0
   device 1
}
pcm.dsp {
    type plug
    slave.pcm "dmixer"     # use our new PCM here
}
ctl.mixer {
    type hw
    card 0
}

pcm.dsnooped {
    type dsnoop
    ipc_key 2048
    slave {
      pcm "hw:0,0"
      period_time 0
      period_size 1024
      buffer_size 8192
	rate 48000
    }
	bindings {
	0 0
	1 1
	}
}

pcm.duplex {
	type asym
	playback.pcm "dmixer"
	capture.pcm "dsnooped"
}

```

I had to make softvol to control volume of digital out (aka IEC958), as "front" only controls analog out.
here some other info that might be helpful:
```
sudo cat /proc/asound/pcm
00-02: ALC883 Analog : ALC883 Analog : capture 2
00-01: ALC883 Digital : ALC883 Digital : playback 1 : capture 1
00-00: ALC883 Analog : ALC883 Analog : playback 1 : capture 2

sudo cat /proc/asound/pcm
00-02: ALC883 Analog : ALC883 Analog : capture 2
00-01: ALC883 Digital : ALC883 Digital : playback 1 : capture 1
00-00: ALC883 Analog : ALC883 Analog : playback 1 : capture 2

sudo cat /proc/asound/devices
  0: [ 0]   : control
  1:        : sequencer
 16: [ 0- 0]: digital audio playback
 17: [ 0- 1]: digital audio playback
 24: [ 0- 0]: digital audio capture
 25: [ 0- 1]: digital audio capture
 26: [ 0- 2]: digital audio capture
 33:        : timer

aplay -L
front:CARD=Intel,DEV=0
    HDA Intel, ALC883 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC883 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC883 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC883 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC883 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC883 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, ALC883 Digital
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 2: ALC883 Analog [ALC883 Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1


```

---

### Post by andy555 on 2008-03-15
I've got the same problem. I'm stuck at the same point. Did you find any solution in the meanwhile? Does anybody else have an idea?

---

### Post by SergeiFranco on 2008-03-15
I just gave up

---

### Post by RDV on 2008-03-15
I do not know if this will help but I have audio capture and digital out working on my installation. In fact I have two sound cards with both digital out working (Ubuntu 7.10). I use two sound cards because the capture (line-in) on the my motherboard's sound card does not work. I used the following command line to route audio from a Line-in to a digital out. This command line helped me figure out what settings I required with the Gnome sound preferences, Audacity, Amarok, Lastfm and Totem. Here is the command line:

# Records from SB Live "Capture" and plays on Intel SPDIF IEC958
arecord -v --buffer-time=500000 -D hw:1,0 -c 2 -f S16_LE -c2 -r48000 | aplay -D hw:0,1 -c 2

Note#1 the two "hw:X,Y" parameters are the ones that specifies card and port/device e.g line in is card 1 port 0 and digital out is card 0 port 1
Note#2 the line-in capture sample rate for my set up would only work at 48,000 (-r48000). The sample rate seems to be sound card specific so use what is appropriate for your card

You can identify cards and ports using the following command line:
cat /proc/asound/devices 

I personally use my line-in to capture Vinyl records and eventually turn them into flac recordings for playback through my surround sound system.

I hope this information helps.

---

