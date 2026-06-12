---
title: "no sound in ubuntu 13:04? how do I fix this problem?"
date: 2013-07-10
forum: Multimedia Software
---

### Post by bagusdanto7 on 2013-07-10
hello .. I have NEC VersaPro VY16E/LV-X, with intel hda card, alc262 chip,  containing 13:04 ubuntu, but why when I play music, no sound and also  the same as the video?? please its support?

---

### Post by byStanderone on 2013-07-10
...would presume tht u hav a new install? if so.. try to update if possible...perhaps this may help.

---

### Post by bagusdanto7 on 2013-07-11
what needs to be updated? kernel? when the kernel, my kernel is 3.8.0-26-generic? What was lacking?

---

### Post by bagusdanto7 on 2013-07-11
aplay -l
 
code:
[TABLE="class: outer_border, width: 500, align: left"]
[TR]
[TD]**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC262 Analog [ALC262 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
[/TD]
[/TR]
[/TABLE]









cat /proc/asound/card0/codec#* | grep Codec :

code:
[TABLE="class: outer_border, width: 500, align: left"]
[TR]
[TD]
Codec: Realtek ALC262 
Codec: Realtek ALC262[/TD]
[/TR]
[/TABLE]







lspci | grep -i audio :

code:
[TABLE="class: outer_border, width: 500, align: left"]
[TR]
[TD]00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 02)

[/TD]
[/TR]
[/TABLE]





cat /proc/asound/version :

code:
[TABLE="class: outer_border, width: 500, align: left"]
[TR]
[TD]Advanced Linux Sound Architecture Driver Version k3.8.0-26-generic
[/TD]
[/TR]
[/TABLE]



In the alsamixer is see this:

code:
[TABLE="class: outer_border, width: 500, align: left"]
[TR]
[TD]cat /proc/asound/devices
  1:        : sequencer
  2: [ 0- 6]: digital audio playback
  3: [ 0- 6]: digital audio capture
  4: [ 0- 0]: digital audio playback
  5: [ 0- 0]: digital audio capture
  6: [ 0- 1]: hardware dependent
  7: [ 0- 0]: hardware dependent
  8: [ 0]   : control
 33:        : timer

[/TD]
[/TR]
[/TABLE]

---

### Post by ana551 on 2013-07-11
i think your drivers are missing...

---

