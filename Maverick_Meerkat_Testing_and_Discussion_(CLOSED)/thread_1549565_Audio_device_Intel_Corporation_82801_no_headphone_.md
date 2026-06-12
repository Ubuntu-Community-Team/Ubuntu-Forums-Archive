---
title: "Audio device: Intel Corporation 82801 no headphone sound or options"
date: 2010-08-09
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by buzzmandt on 2010-08-09
I dual boot lucid and maverick on this laptop.  in lucid i have headphone sound but plugging in headphones does not stop the speaker output.

In maverick i get no sound at all out of the headphones, i also have no options for headphones in mixer or alsamixer.

```
lspci |grep Audio 
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

```

```
sudo lspci -s 00:1b.0 -vn
[sudo] password for buzzmandt: 
00:1b.0 0403: 8086:293e (rev 03)
        Subsystem: 103c:360b
        Flags: bus master, fast devsel, latency 0, IRQ 45
        Memory at 94700000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
        Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
        Capabilities: [100] Virtual Channel
        Capabilities: [130] Root Complex Link
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

```

---

### Post by buzzmandt on 2010-08-10
since it works a bit better in lucid i thought i'd compare. slightly different read outs but nothing out of the ordinary as far as i can tell.

one main difference when i go to kde mixer in maverick my only settings are for 'internal audio' where in lucid it actually says hda intel.

from lucid output:
```
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

```

```
sudo lspci -s 00:1b.0 -vn
[sudo] password for buzzmandt: 
00:1b.0 0403: 8086:293e (rev 03)
        Subsystem: 103c:360b
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at 94700000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
        Capabilities: [100] Virtual Channel <?>
        Capabilities: [130] Root Complex Link <?>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel


```

---

### Post by lidex on 2010-08-11
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Enter your user password when prompted. Choose the upload option and provide a link for the output.

---

### Post by buzzmandt on 2010-08-11
from lucid
[http://www.alsa-project.org/db/?f=adcb508cf04fcfe47fcf01fcde4fe22f101195f7](http://www.alsa-project.org/db/?f=adcb508cf04fcfe47fcf01fcde4fe22f101195f7)

from maverick
[http://www.alsa-project.org/db/?f=bcfcffa49b1c4fb83637cbf663d3e3bcd577648f](http://www.alsa-project.org/db/?f=bcfcffa49b1c4fb83637cbf663d3e3bcd577648f)

wow that's a lot, what i gathered from that is irq's are listed different
```
!!Soundcards recognised by ALSA
!!-----------------------------

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0x94700000 irq 45

```
```
!!Soundcards recognised by ALSA
!!-----------------------------

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0x94700000 irq 22

```

and aplay and arecord are listing differently
```
APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
```
APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```




 
beyond that I also discovered and recognized that it's WAYYY over my head, so I'll hush now  :)

thank you lidex

---

### Post by lidex on 2010-08-11
The fix I have documented for the CQ60 follows.
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert this line at the bottom:
```
 options snd-hda-intel model=dell-vostro 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

Let me know how that goes.

---

### Post by buzzmandt on 2010-08-11
hey it worked  :)
everything is still labled the same (yeah just checked the original post, I forgot to mention it's kubuntu but it worked just the same. (guess i could put specs in sig for future reference... and I shall)

alsamixer is only showing one card hda intel
but sound is good, plugin headphones and speakers stop and headphones work

this begs the question though, is a fix coming down the pipe or am I going to be subject to editing that file on new installs from now on?

---

### Post by buzzmandt on 2010-08-11
one minor prob. it starts muted every time and i have it set to save last session.

---

### Post by lidex on 2010-08-11
> **buzzmandt said:**
> 
this begs the question though, is a fix coming down the pipe or am I going to be subject to editing that file on new installs from now on?
Good question. We need to report software problems (with the fix, if known) to the developers to make sure it gets handled upstream. Check this post on *simosx's* blog:
[http://simos.info/blog/archives/984](http://simos.info/blog/archives/984)

> one minor prob. it starts muted every time and i have it set to save last session.

Try this command after your settings are correct:
```
sudo alsactl store 0
```

---

### Post by ralpyka on 2010-08-31
> **lidex said:**
> Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```Insert this line at the bottom:
```
 options snd-hda-intel model=dell-vostro 
```Save. Close. Reboot. Check your levels in alsamixer.


This worked for me too on a Toshiba L650

---

### Post by syoavc on 2010-09-05
This worked for me too on my ThinkPad T400s (same problem).
Thanks!

---

