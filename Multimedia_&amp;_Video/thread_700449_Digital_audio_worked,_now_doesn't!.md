---
title: "Digital audio worked, now doesn't?!"
date: 2008-02-18
forum: Multimedia &amp; Video
---

### Post by BLKMGK on 2008-02-18
Digital audio via a coax output had been working GREAT on my system, surround sound and all. After a reboot in which I'd updated an Intel VIDEO driver the sound stopped working - I do not use that video hardware. I have confirmed that the audio hardware is fine via a fresh install but I've restored this install back as its been customized for my needs.

Alsamixer shows the PCM turned on and IEC958 on as well. During my initial install I'd had to turn the IEC "on" and unmute some items. Sound _works_ via headphones but nothing I've tried, including reinstalling some alsa subsystems via package manager has helped.:confused: Replacing asound.state from a working install does nothing, it's somehting deeper I'm afraid.

The receiver shows some signal coming from the coax but it's unable to decode it or identify it and the signal is steady. Removing the coax cable stops the signal so I'm sure it's coming from the computer. Not sure if this is "normal".

```
cat /proc/asound/devices
  2:        : timer
  3:        : sequencer
  4: [ 0- 2]: digital audio capture
  5: [ 0- 1]: digital audio playback
  6: [ 0- 0]: digital audio playback
  7: [ 0- 0]: digital audio capture
  8: [ 0]   : control
```

```
aplay -L
default:CARD=Intel
    HDA Intel, ALC883 Analog
    Default Audio Device
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
null
    Discard all samples (playback) or generate zero samples (capture)
```

```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
```


I'm stumped, and would really like to have my HTPC back <sigh> I've got backups of the system at this point so I'm up for trying most anything and kicking myself for not having a backup of it in a more working state!:mad:

---

### Post by Redenbacher on 2008-02-18
Well, I don't have as great of a sound system as you on my PC, but I do have the HDA intel. I've also run in to the same problem, where sound stopped working completely after a reboot and not having changed anything

It's happened to me twice, and both times the fix involved shutting down my box, and TURNING THE POWER SUPPLY OFF, until all the LEDs go out, then starting it back up. Simply restarting or shutting down and starting back up did not work. I HAD to shut off the power supply, or unplug the PC. Give it a try if you haven't already!

---

### Post by BLKMGK on 2008-02-18
I'll try it but at this point I've gone so far as to reinstall Ubuntu from scratch, verify it worked (had to make sure it wasn't the stereo!), and then reload. Problem follows this build :( But I'll try the complete shut-off just to be sure! Worse comes to worse I load that new build back on and reconfigure everything yet again - this time I'll backup a working version!

---

