---
title: "OSS4: osstest works, but ossmix not outputting controls"
date: 2011-09-06
forum: Multimedia Software
---

### Post by jampe on 2011-09-06
Hello everybody,

Another OSS riddle for you guys. They're fun, aren't they? 
Because of the tremendous delays I encountered in PulseAudio/ALSA, I switched to OSS4 following this [guide](http://www.ubuntugeek.com/howto-install-oss4-in-ubuntu-10-04-lucid-for-better-sound-quality.html), and now audio sounds a whole lot better, although only works with certain programs, such as VLC and DeaDBeeF.

**VirtualBox tells me:**
```

00:00:00.864 Audio: Trying driver 'oss'.
00:00:00.865 Audio: set_record_source ars=0 als=0 (not implemented)
00:00:00.866 OSS: Successfully opened /dev/dsp for ADC
00:00:00.866 OSS: Failed to open /dev/dsp for DAC (Device or resource busy)
00:00:00.866 OSS: Failed to open /dev/dsp for DAC (Device or resource busy)
00:00:00.866 AC97: WARNING: Unable to open PCM OUT!

```

**ossinfo says:**
```

Version info: OSS 4.2 (b 2003/201106181017) (0x00040100) GPL
Platform: Linux/x86_64 2.6.38-11-generic #48-Ubuntu SMP Fri Jul 29 19:02:55 UTC 2011 (odin)

Number of audio devices:	3
Number of audio engines:	3
Number of MIDI devices:		0
Number of mixer devices:	1


Device objects
 0: osscore0 OSS core services
 1: oss_usb0 USB audio core services
 2: usb07632012-0 USB sound device
 3: usb07632012-1 USB sound device
 4: usb07632012-2 USB sound device
 5: usb07632012-3 USB sound device
 6: usb07632012-4 USB sound device

MIDI devices (/dev/midi*)

Mixer devices
 0: USB sound device (Mixer 0 of device object 2)

Audio devices
USB sound device play             /dev/oss/usb07632012-2/pcm0  (device index 0)
USB sound device play2            /dev/oss/usb07632012-3/pcm0  (device index 1)
USB sound device rec              /dev/oss/usb07632012-4/pcmin0  (device index 2)

Nodes
  /dev/dsp -> /dev/oss/usb07632012-2/pcm0
  /dev/dsp_in -> /dev/oss/usb07632012-4/pcmin0
  /dev/dsp_out -> /dev/oss/usb07632012-2/pcm0
  /dev/dsp_mmap -> /dev/oss/usb07632012-2/pcm0

```

**while osstest says:**
```

Sound subsystem and version: OSS 4.2 (b 2003/201106181017) (0x00040100)
Platform: Linux/x86_64 2.6.38-11-generic #48-Ubuntu SMP Fri Jul 29 19:02:55 UTC 2011

*** Scanning sound adapter #-1 ***
/dev/oss/usb07632012-2/pcm0 (audio engine 0): USB sound device play
- Performing audio playback test... 
  <left> OK <right> OK <stereo> OK <measured srate 47973.00 Hz (-0.06%)> 

*** Scanning sound adapter #4 ***
/dev/oss/usb07632012-3/pcm0 (audio engine 1): USB sound device play2
- Performing audio playback test... 
  <left> OK <right> OK <stereo> OK <measured srate 47976.00 Hz (-0.05%)> 

*** Scanning sound adapter #5 ***
/dev/oss/usb07632012-4/pcmin0 (audio engine 2): USB sound device rec
- Skipping input only device

*** All tests completed OK ***

```

**and, to my disappointment, ossmix goes:**
```

Selected mixer 0/USB sound device
Known controls are:

```

I currently have no system sounds or flash sound either, and gstreamer-properties freezes without errors when I try to test the OSS4 input.

I'm on Ubuntu 11.04 with an external M-Audio Fast Track Pro sound card.

I've been browsing for several hours and found no one with this exact predicament.

Any ideas? I appreciate it.

---

### Post by jampe on 2011-09-06
Aha! The problem with flash is solved:
[http://ubuntuforums.org/showthread.php?t=873749](http://ubuntuforums.org/showthread.php?t=873749)

---

### Post by jampe on 2011-09-06
And I solved the VirtualBox problem with kind of a botch solution:
- use OSS with PulseAudio:
```

To configure Pulseaudio with OSS4:
Edit the default configuration file: gksu gedit /etc/pulse/default.pa
Comment out the modules for automatic hardware detection.
Add the following line:
load-module module-oss device="/dev/dsp" sink_name=output source_name=input mmap=0

```

- configure VirtualBox to use PulseAudio instead of OSS

So now I only need to solve the problem with the mixer and the input sound.

---

