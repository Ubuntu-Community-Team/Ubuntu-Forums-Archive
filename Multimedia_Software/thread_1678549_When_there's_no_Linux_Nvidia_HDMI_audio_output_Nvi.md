---
title: "When there's no Linux Nvidia HDMI audio output Nvidia"
date: 2011-01-30
forum: Multimedia Software
---

### Post by Linux90's on 2011-01-30
Apart from no audio over hdmi to the tv - Ubuntu 10.10 maverick worked beautifully
This fix worked for me

Gigabyte GA 73PVM-S2H
Nvidia GeForce 7100 / nForce 630i 
Linux-x86_64 Ubuntu 10.10 maverick 64-bit
Kernel Linux 2.6.35-22-generic

Nvidia Driver version 260.19.06 (current recommended additional driver)
X Server version      11.0
  vendor version      1.9.0
  NV control version  1.24


Alsa version 1.0.23

--------------------------------------------------

Terminal commands to run:

[First]
sudo killall pulseaudio

[Second]
alsamixer

Make sure that the HDA NVidia card has been selected,
if not, press F6 and select 
0   HDA NVidia

Make sure the S/PDIF's are unmuted.

Scroll right and unmute S/PDIF, S/PDIF D, S/PDIF 1

Press m to unmute and MM should change to OO

ESC to exit alsamixer

---------------------------------------------------

Next we edit the following file as su:

/etc/pulse/default.pa

use nano or vi or any other editor

eg. sudo vi /etc/pulse/default.pa
or
eg. sudo nano /etc/pulse/default.pa


Goto lines 44 & 45 and unmark and edit as follows

load-module module-alsa-sink
load-module module-alsa-source device=hw:0,3

exit and save changes

Choose the relevant HDMI output you need in Sound Preferences (System->preferences->sound)

i didn't reboot and it started working.


[If this works for you too, please leave a comment so others know it worked...thanks]


Extra info:
-----------

@ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC889A Digital [ALC889A Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 0/1
  Subdevice #0: subdevice #0


@ubuntu:~$ cat /proc/asound/devices 
  2:        : timer
  3:        : sequencer
  4: [ 0- 3]: digital audio playback
  5: [ 0- 2]: digital audio capture
  6: [ 0- 1]: digital audio playback
  7: [ 0- 1]: digital audio capture
  8: [ 0- 0]: digital audio playback
  9: [ 0- 0]: digital audio capture
 10: [ 0- 3]: hardware dependent
 11: [ 0- 0]: hardware dependent
 12: [ 0]   : control



@ubuntu:~$ ls pci -v
00:09.0 Audio device: nVidia Corporation MCP73 High Definition Audio (rev a1)
    Subsystem: Giga-byte Technology Device a002
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
    Memory at e7000000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

---

### Post by Linux90's on 2011-02-01
UPDATE:

Had some problems with my wubi installation, once that was back up and running - no sound!
**Waiting for sound system to respond**

opened default.pa and #'d the two lines edited before and the sound returned....

go figure :)

---

### Post by kokoman on 2013-01-31
worked for me, thanks ;)

---

### Post by lisati on 2013-01-31
A lot can change in two years.

Old thread closed.

---

