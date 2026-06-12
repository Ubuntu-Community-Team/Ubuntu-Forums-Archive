---
title: "HDMI sound does not work in all applications with Intel Core i5 CPU"
date: 2011-05-14
forum: Multimedia Software
---

### Post by panamasmith on 2011-05-14
[FONT=Courier New]From what I have read in this and other forums,  I think my problem is that I don't know how to configure "ctl.!default"  correctly ](*,).
  
Thank you in advance for any help.
[/FONT]
[FONT=Courier New]With a clean install of ubuntu 11.04 (64-bit), there was no sound coming through the speakers on the HDTV with any application using the default device:
  CPU:         Intel Core i5 CPU 2500K
  Motherboard: Asus P8H67-M EVO REV 3.0
  GPU:         None
  Soundcard:   None

Specifying the device produced sound for the following:
  aplay -D plughw:0,7 <path to wav file>
  speaker-test -D plughw:0,7 -t wav=<path to wav file>
Note: plughw:CARD=PCH,DEV=7 works in place of plughw:0,7

Creating the following /etc/asound.conf produced sound using the Adobe Flash plug-in in Firefox, but not any other application:
  pcm.!default {
    type hw
    card 0
    device 7
  }
There was no sound from aplay or speader-test using the default device.

Creating the following /etc/asound.conf produce sound using the Adobe Flash plug-in in Firefox, aplay and speaker-test :p:
  pcm.!default {
    type plug
    slave.pcm "dmix:0,7"
  }

Here is a list of applications that have not produced any sound :cry::
  Banshee
  Movie Player (Flash plug-in does not produce sound just video)
  VirtualBox 4.0.6
[/FONT]
Here is my output from alsa-info.sh:
[http://www.alsa-project.org/db/?f=9d1f4584ef6db88d17fd7fa9c4e23c6f6662414a](http://www.alsa-project.org/db/?f=9d1f4584ef6db88d17fd7fa9c4e23c6f6662414a)

[FONT=Courier New]Below is the output from the following commands:
  aplay -l
  aplay -L
  cat /proc/asound/version
  cat /proc/asound/cards
  cat /proc/asound/timers
  cat /proc/asound/pcm
  cat /proc/asound/modules
  lspci -v

aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

aplay -L

null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    Playback/recording through the PulseAudio sound server
default
front:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    Front speakers
surround40:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Digital
    IEC958 (S/PDIF) Digital Audio Output
hdmi:CARD=PCH,DEV=0
    HDA Intel PCH, HDMI 0
    HDMI Audio Output
hdmi:CARD=PCH,DEV=1
    HDA Intel PCH, HDMI 1
    HDMI Audio Output
dmix:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    Direct sample mixing device
dmix:CARD=PCH,DEV=1
    HDA Intel PCH, ALC892 Digital
    Direct sample mixing device
dmix:CARD=PCH,DEV=3
    HDA Intel PCH, HDMI 0
    Direct sample mixing device
dmix:CARD=PCH,DEV=7
    HDA Intel PCH, HDMI 1
    Direct sample mixing device
dsnoop:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    Direct sample snooping device
dsnoop:CARD=PCH,DEV=1
    HDA Intel PCH, ALC892 Digital
    Direct sample snooping device
dsnoop:CARD=PCH,DEV=3
    HDA Intel PCH, HDMI 0
    Direct sample snooping device
dsnoop:CARD=PCH,DEV=7
    HDA Intel PCH, HDMI 1
    Direct sample snooping device
hw:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    Direct hardware device without any conversions
hw:CARD=PCH,DEV=1
    HDA Intel PCH, ALC892 Digital
    Direct hardware device without any conversions
hw:CARD=PCH,DEV=3
    HDA Intel PCH, HDMI 0
    Direct hardware device without any conversions
hw:CARD=PCH,DEV=7
    HDA Intel PCH, HDMI 1
    Direct hardware device without any conversions
plughw:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    Hardware device with all software conversions
plughw:CARD=PCH,DEV=1
    HDA Intel PCH, ALC892 Digital
    Hardware device with all software conversions
plughw:CARD=PCH,DEV=3
    HDA Intel PCH, HDMI 0
    Hardware device with all software conversions
plughw:CARD=PCH,DEV=7
    HDA Intel PCH, HDMI 1
    Hardware device with all software conversions

cat /proc/asound/version

Advanced Linux Sound Architecture Driver Version 1.0.23.

cat /proc/asound/cards

 0 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xfe700000 irq 55

cat /proc/asound/devices

  1:        : sequencer
  2: [ 0- 7]: digital audio playback
  3: [ 0- 3]: digital audio playback
  4: [ 0- 1]: digital audio playback
  5: [ 0- 0]: digital audio playback
  6: [ 0- 0]: digital audio capture
  7: [ 0- 3]: hardware dependent
  8: [ 0- 0]: hardware dependent
  9: [ 0]   : control
 33:        : timer

cat /proc/asound/timers

G0: system timer : 10000.000us (10000000 ticks)
P0-0-0: PCM playback 0-0-0 : SLAVE
P0-0-1: PCM capture 0-0-1 : SLAVE
P0-1-0: PCM playback 0-1-0 : SLAVE
P0-3-0: PCM playback 0-3-0 : SLAVE
P0-7-0: PCM playback 0-7-0 : SLAVE

/proc/asound/pcm

00-00: ALC892 Analog : ALC892 Analog : playback 1 : capture 1
00-01: ALC892 Digital : ALC892 Digital : playback 1
00-03: HDMI 0 : HDMI 0 : playback 1
00-07: HDMI 1 : HDMI 1 : playback 1

cat /proc/asound/modules
 0 snd_hda_intel

lspci -v

...
00:1b.0 Audio device: Intel Corporation 6 Series Chipset Family High Definition Audio Controller (rev 05)
        Subsystem: ASUSTeK Computer Inc. Device 8436
        Flags: bus master, fast devsel, latency 0, IRQ 55
        Memory at fe700000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel
...

[/FONT]

---

### Post by marslert on 2011-05-16
I have the same problem too. Need help.

---

### Post by unwowed on 2011-05-16
Since you have extra HDMI device in your aplay -l, you could try probe_masking it and see if pulse handles hdmi sound correctly then.

What if you add this to /etc/modprobe.d/snd-hda-intel.conf
```

options snd-hda-intel probe_mask=0x83

```

and to your /etc/asound.conf
```

pcm.!default {
    type pulse
    hint {
        show on
        description "Default ALSA Output (currently PulseAudio Sound Server)"
         }
}

ctl.!default {
    type pulse
}


```

reboot and select HDMI device in sound preferences (if it's there)

[ftp://download.nvidia.com/XFree86/gpu-hdmi-audio-document/gpu-hdmi-audio.html]("ftp://download.nvidia.com/XFree86/gpu-hdmi-audio-document/gpu-hdmi-audio.html") this link provides more info on intel HDMI audio

---

### Post by panamasmith on 2011-05-17
unwowed, I will try this tomorrow.

Interesting, I removed PulseAudio and I managed to get the following applications to work:
  Banshee
  Movie Player
Although, this created a new issue with VirtualBox.

I don't consider removing PulseAudio to be a solution considering some of the Gnome tools require PulseAudio.

---

### Post by smariner08 on 2011-06-11
I was in the same situation with an Asus P8H67-I deluxe mobo using an i5 2500k cpu.  I was able to hear the speaker test through the HDMI audio, but setting it to HDMI in Ubuntu's system configuration did nothing.  I used the above fix to get sound in flashplayer in firefox (but not chrome or other applications).  

The [first three lines in this section]("http://omappedia.org/wiki/Ubuntu_PA#PA_through_HDMI") seemed to fix the problem: 

```

One way to route the audio through HDMI is to configure PA to use HDMI output by default. 

Comment out this line in PA configuration file (/etc/pulse/default.pa):
#load-module module-udev-detect
Then in the same file instruct PA to route audio through the HDMI ALSA device:
load-module module-alsa-sink device=plughw:0,5 sink_name=output

And make it the default:
### Make some devices default
set-default-sink output

Then just restart PA daemon to make these changes take effect.
```

---

