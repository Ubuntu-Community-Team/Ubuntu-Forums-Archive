---
title: "HDMI Audio"
date: 2011-10-22
forum: Multimedia Software
---

### Post by t_wright on 2011-10-22
Hi,

I've just installed Ubuntu 11.10 (64 bit) on my PC, using Wubi in Windows 7 64bit.

It's working fine, except for the HDMI audio output. I have a GTX 285 outputting through an HDMI cable to a 40" Sony HDTV. Internally, i've installed an S/PDIF adapter from the graphics card to the S/PDIF output on the P6T Motherboard. In Windows 7, this is recognised in the sound settings as 'HDMI Audio' and it all works fine. In Ubuntu, it doesn't work - there is no profile for HDMI audio or if there is my knowledge of Linux is insufficient to find it! I've installed the nVidia graphics driver for Linux through the Additional Drivers in settings.

Can anyone help me?

Thanks.
Tom

---

### Post by BudworthTDog on 2011-10-22
I'm not the greatest with these things but I did get mine running. When you go into additional drivers do you see 2 options for nVidia drivers? I had to install the "post-release" driver to get everything up and running. After that when I went into settings -> sound -> select your HDMI device -> I found multiple HDMI "profiles" on the dropdown menue at the bottom of the page. I went through them and used the test speakers until I found on that worked. In my case it was "digital Stereo (HDMI) nr 4 Output"

Then in sound setting I went to the Output tab and selected the HDMI sound output

On top of that in VLC I had to go into the audio settings and select the HDMI output. Ever since then things have been okay. I know it's kind of a vague and open ended post but hopefully it helps a little.

---

### Post by BicyclerBoy on 2011-10-22
If you use the S/PDIF adapter cable to link the mobo soundcard to videocard, you are pre-azalia pre HDA-intel audio.

The audio output/control is just via the mobo soundcard; there is no 'real' HDMI audio device.
You can only output S/PDIF digital audio modes:
- stereo PCM (up to 192K 24bit)
- matrix encoded multi-channel AC3/DTS. (48KHz)

aplay -l
speaker-test -c 2 -r 44100 -D iec958

---

### Post by t_wright on 2011-10-24
Hi,

Thanks for your replies. I did get it to work by setting 'Digital Output' in PAVU Control, but then I went into Sound Settings and it went out again. I can't get the sound back now!

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
card 1: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
tom@tom-Desktop-Ubuntu:~$ speaker-test -c 2 -r 44100 -D iec958

speaker-test 1.0.24.2

Playback device is iec958
Stream parameters are 44100Hz, S16_LE, 2 channels
Using 16 octaves of pink noise
Rate 44100Hz not available for playback: Invalid argument
Setting of hwparams failed: Invalid argument
tom@tom-Desktop-Ubuntu:~$ 

The results of the speaker test.

Trying to run PAVU Control from terminal gives this error: DEBUG: Failed to initialize device manager extension: No such extension


Thanks,
Tom

---

### Post by BicyclerBoy on 2011-10-24
I would guess pulse audio server crashed..

You could try
speaker-test -c 2 -r 44100 -D hw:1,1

I guess that card0 is the intel iCPU codec ?? or do you have a discrete soundcard ?

I've never used a wubi install..

---

### Post by t_wright on 2011-10-24
Just tried that. Didn't hear anything.

Card0 is my Soundblaster Audigy soundcard. Since setting up the s/pdif installation, I do not use this. It is simply set up to output from the onboard soundcard, via s/pdif to the graphics card, and then out the HDMI to the TV.

It's really wierd, I'm trying all sorts of things, changing back to Analogue duplex and back to digital etc. Very occasionally I can get the sample warning sounds to play, but nothing on YouTube will play. Then suddenly I can't even get the warning sounds to play!  There's a bar on the Output tab of PAVUControl which shows there is sound playing when I select one of the Alert noises in the Sound settings, but I can't hear them.

It's not a Wubi installation anymore. I've installed Ubuntu 11.10 on its own partition.

---

### Post by BicyclerBoy on 2011-10-24
I thought CA0106 was a Soundblaster or a bug..odd that it comes up first..

speaker-test -c 2 -r 44100 D iec958:CARD=Intel,DEV=1
speaker-test -c 2 -r 48000 D iec958:CARD=Intel,DEV=1


The pulse audio (pavucontrol & sound prefs) in 11.10 seems to be problematic..

I would not recommend 11.10 to my friends..

Better post the 
aplay -L
(capital L) so can check the aliases.

---

### Post by t_wright on 2011-10-25
Nope still nothing.

tom@tom-Desktop-Ubuntu:~$ aplay -L
null
    Discard all samples (playback) or generate zero samples (capture)
pulse
    Playback/recording through the PulseAudio sound server
default
front:CARD=CA0106,DEV=0
    CA0106, CA0106
    Front speakers
rear:CARD=CA0106,DEV=0
    CA0106, CA0106
    Rear speakers
center_lfe:CARD=CA0106,DEV=0
    CA0106, CA0106
    Center and Subwoofer speakers
side:CARD=CA0106,DEV=0
    CA0106, CA0106
    Side speakers
surround40:CARD=CA0106,DEV=0
    CA0106, CA0106
    4.0 Surround output to Front and Rear speakers
surround41:CARD=CA0106,DEV=0
    CA0106, CA0106
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=CA0106,DEV=0
    CA0106, CA0106
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=CA0106,DEV=0
    CA0106, CA0106
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=CA0106,DEV=0
    CA0106, CA0106
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=CA0106,DEV=0
    CA0106, CA0106
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=CA0106,DEV=0
    CA0106, CA0106
    Direct sample mixing device
dmix:CARD=CA0106,DEV=1
    CA0106, CA0106
    Direct sample mixing device
dmix:CARD=CA0106,DEV=2
    CA0106, CA0106
    Direct sample mixing device
dmix:CARD=CA0106,DEV=3
    CA0106, CA0106
    Direct sample mixing device
dsnoop:CARD=CA0106,DEV=0
    CA0106, CA0106
    Direct sample snooping device
dsnoop:CARD=CA0106,DEV=1
    CA0106, CA0106
    Direct sample snooping device
dsnoop:CARD=CA0106,DEV=2
    CA0106, CA0106
    Direct sample snooping device
dsnoop:CARD=CA0106,DEV=3
    CA0106, CA0106
    Direct sample snooping device
hw:CARD=CA0106,DEV=0
    CA0106, CA0106
    Direct hardware device without any conversions
hw:CARD=CA0106,DEV=1
    CA0106, CA0106
    Direct hardware device without any conversions
hw:CARD=CA0106,DEV=2
    CA0106, CA0106
    Direct hardware device without any conversions
hw:CARD=CA0106,DEV=3
    CA0106, CA0106
    Direct hardware device without any conversions
plughw:CARD=CA0106,DEV=0
    CA0106, CA0106
    Hardware device with all software conversions
plughw:CARD=CA0106,DEV=1
    CA0106, CA0106
    Hardware device with all software conversions
plughw:CARD=CA0106,DEV=2
    CA0106, CA0106
    Hardware device with all software conversions
plughw:CARD=CA0106,DEV=3
    CA0106, CA0106
    Hardware device with all software conversions
front:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, AD198x Digital
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    Direct sample mixing device
dmix:CARD=Intel,DEV=1
    HDA Intel, AD198x Digital
    Direct sample mixing device
dsnoop:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    Direct sample snooping device
dsnoop:CARD=Intel,DEV=1
    HDA Intel, AD198x Digital
    Direct sample snooping device
hw:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    Direct hardware device without any conversions
hw:CARD=Intel,DEV=1
    HDA Intel, AD198x Digital
    Direct hardware device without any conversions
plughw:CARD=Intel,DEV=0
    HDA Intel, AD198x Analog
    Hardware device with all software conversions
plughw:CARD=Intel,DEV=1
    HDA Intel, AD198x Digital
    Hardware device with all software conversions

---

### Post by BicyclerBoy on 2011-10-25
That's useful...

The alias IEC958 is the soundblaster S/PDIF
The alias iec958 is the mobo codec (routed to HDMI) S/PDIF

Check you user is a member of the groups: audio & pulse.

You already tried
speaker-test -c 2 -r 44100 -D iec958 (& it did not work)


Try:
speaker-test -c 2 -r 44100 -D hw:1,0
speaker-test -c 2 -r 48000 -D hw:1,0
speaker-test -c 2 -r 48000 -D plughw:1,0

11.10 does not seem to be working very well (audio).
Before giving 11.10 away...
[https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules](https://wiki.ubuntu.com/Audio/InstallingLinuxAlsaDriverModules)

If you have not invested to much in 11.10, I would forget it & use 11.04 or 10.10 & upgrade later..

---

### Post by t_wright on 2011-10-25
Hmm, still nothing. I get this when trying to install the alsa driver modules as described in that link..

E: Unable to locate package linux-alsa-driver-modules-3.0.0-12-generic
E: Couldn't find any package by regex 'linux-alsa-driver-modules-3.0.0-12-generic

I've added my user to the audio and pulse group and rebooted several times. One thing i've noticed now since adding my user to the group is that I don't have the Digital Output options for the Internal Audio device now - only Analogue In, Out and Duplex. Still not a peep!

If I were to install 11.04 instead, is that a reformat job?

---

### Post by BicyclerBoy on 2011-10-25
Sorry that audio devs ppa does not have packages for 11.10

These have 11.10 builds
alsa:
[https://launchpad.net/~ubuntu-audio-dev/+archive/alsa-daily](https://launchpad.net/~ubuntu-audio-dev/+archive/alsa-daily)
pulse audio:
[https://launchpad.net/~ubuntu-audio-dev/+archive/pulse-testing](https://launchpad.net/~ubuntu-audio-dev/+archive/pulse-testing)

All ubuntu distros should run on the partition/grub/kernel you have currently installed.
But distro package management will not allow this configuration i.e. you have to allow the later kernel..
I don't know how to get around this..

---

### Post by Lumsdoni on 2011-10-26
Dont know if this helps but I lost hdmi audio when I upgraded to 11.10 and only way I got it back was following this link.

[http://askubuntu.com/questions/67113/fast-video-playback-with-no-sound]("http://askubuntu.com/questions/67113/fast-video-playback-with-no-sound")

---

### Post by t_wright on 2011-10-26
Ok thanks. 

Would that solution work even though I have an nVidia graphics card?

---

### Post by BicyclerBoy on 2011-10-27
Extremely unlikely.

---

