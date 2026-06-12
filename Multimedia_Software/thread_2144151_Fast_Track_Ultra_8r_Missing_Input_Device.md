---
title: "Fast Track Ultra 8r Missing Input Device"
date: 2013-05-11
forum: Multimedia Software
---

### Post by swiftoid on 2013-05-11
Hi everyone.

I've just installed gnome ubuntu 13.04. Everything seems good so far apart from support for my maudio fasttrack ultra 8r (That's a mouthfull, let's just call it f8r).

The system recognizes it as an output device, and after setting up the internal routing using alsamixer it works fine for playback. The problem is, it doesn't appear as in input device. The main feature of the f8r is it's many inputs....

I was wondering if anyone can point me in the right direction. I've found a bug in launchpad from a few years back that mentions this, but I checked and the patch that fixed it was pushed upstream, and is active on my system. So it must be something differnet.

```
ubuntu-gnome@ubuntu-gnome:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: F8R [Fast Track Ultra 8R], device 0: USB Audio [USB Audio]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
```

I'm fairly linux competant, but I haven't done work in the sound area before so I'm unfamiliar with the available tools. Any help would be very much appreciated. Can anyone point me in the right difrection?

Many thanks,

James Swift

---

### Post by gordintoronto on 2013-05-11
Is a program called "Sound Settings" available in Gnome? Does it have an Input tab? Does anything appear there?

aplay -l will only show output devices. Use: arecord -l

---

### Post by swiftoid on 2013-05-11
Hi, thanks for your reply. No, there's no input devices listed in sound settings. That's actually what started me investigating in the first place. I'm not at my pc right now so I can't run arecord, but when I get back I will.

any ideas?

---

### Post by swiftoid on 2013-05-12
That's weird. arecord says:

```
james@james-desktop:~$ arecord -l**** List of CAPTURE Hardware Devices ****
card 1: F8R [Fast Track Ultra 8R], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

So arecord can see it, but the system sound dialogue doesn't list it. Not sure if this is connected, but every time I reboot the volume gets reset to 100%, which as you imagine is quite annoying. I found a possibly matching bug report on launchpad stretching back years, but there hasn't been any action on it.

---

### Post by gordintoronto on 2013-05-12
Nothing at all under System Settings, Sound, the Input tab?

---

### Post by swiftoid on 2013-05-13
> **swiftoid said:**
> No, there's no input devices listed in sound settings. That's actually what started me investigating in the first place.

Nope.

---

### Post by jgraham909 on 2013-12-28
Did you find a solution for this? 

I have the exact same problem everything checks out exactly as swiftoid describes arecord displays 

> 
jeff@feynman:~$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 2: ALC892 Alt Analog [ALC892 Alt Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Ultra [Fast Track Ultra], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
jeff@feynman:~$ 




But the there is no input device in System -> Sound.

Using pavucontrol under the configuration tab I have

M-Audio RunTime DFU but the only selectable profile is "Analag Surround 7.1 Output" there is no corresponding Input profile. 

I think this is something with Pulseaudio not knowing what to do with the fast track ultra, but I am uncertain how to diagnose or troubleshoot this further.

---

