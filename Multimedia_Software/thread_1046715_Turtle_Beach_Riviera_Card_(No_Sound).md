---
title: "Turtle Beach Riviera Card (No Sound)"
date: 2009-01-21
forum: Multimedia Software
---

### Post by jr_herman on 2009-01-21
Hello I've installed mythbuntu. My onboard audio works fine. However I do have a turtle beach sound card that my computer recognizes but wont play sound through it. I could really use some help in getting this issue resolved. Thanks in advance.

I used this command in the terminal
```
aplay -l
```

Here is what i received back.
> **** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 1: CMI8738 [C-Media CMI8738], device 0: CMI8738-MC6 [C-Media PCI DAC/ADC]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 1: CMI8738 [C-Media CMI8738], device 1: CMI8738-MC6 [C-Media PCI 2nd DAC]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 1: CMI8738 [C-Media CMI8738], device 2: CMI8738-MC6 [C-Media PCI IEC958]
Subdevices: 1/1
Subdevice #0: subdevice #0

Then I ran ```
lspci -v
```

Then I received...
> 04:00.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
Subsystem: C-Media Electronics Inc CM8738
Flags: bus master, stepping, medium devsel, latency 32, IRQ 20
I/O ports at d000 [size=256]
Capabilities: <access denied>
Kernel driver in use: C-Media PCI
Kernel modules: snd-cmipci
Then... ```
/proc/asound/cards
```

Gave me this...
> 0 [Intel ]: HDA-Intel - HDA Intel
HDA Intel at 0xe5200000 irq 16
1 [CMI8738 ]: CMI8738-MC6 - C-Media CMI8738
C-Media CMI8738 (model 55) at 0xd000, irq 20
-Could it be as simple as disabling the onboard sound?

I'm really a bit lost. Please Help

---

### Post by markbuntu on 2009-01-22
The problem is that the on-board card is being seen first so it becomes the default. You can fix this a few different ways

1.disable the on-board sound in bios (bad)
2. force the order of the sound devices(better)
3. use pulseaudio(best)

For 2 and 3 look in here

[http://ubuntuforums.org/showthread.php?t=922860](http://ubuntuforums.org/showthread.php?t=922860)

I don't know anything about Mythbuntu but pulseaudio is the only reasonable option for multiple sound devices.

---

### Post by jr_herman on 2009-01-26
Thanks I will give them a try now.

---

### Post by jr_herman on 2009-01-28
**SOLVED:**
Here is what I found.
Run in terminal ```
asoundconf list 
```This listed the available sound cards.
Run ```
asoundconf set-default-card CMI8738
``` 

This got my sound card working. Alsamixer wasn’t good enough to enable IEC958. So I saw somebody suggest get gnome-alsamixer. Run ```
sudo apt-get install gnome-alsamixer
``` 
I checked the box for IEC958 out. And voila! 5.1 sound every time.:guitar:\\:D/:-\"

---

### Post by garrett.steven on 2009-02-04
Are you using the analog outputs? I am having problems getting my center channel to work and I can't figure out how to change that stupid blue input from line in to center channel output. Any help would be appreciated. Thanks.

---

### Post by jr_herman on 2010-12-18
No I'm using fiber optic

---

