---
title: "ubuntustudio 8.04 digital audio on  &quot;MCP55&quot; problem"
date: 2008-10-28
forum: Multimedia Software
---

### Post by alikbalik on 2008-10-28
I installed ubuntu studio 8.04 on my computer. everything about the sound seems work perfect but i cannot hear the sound coz i'm using an opitcal speaker decoder. 
i'm using the kernel "2.6.24-21-rt" and my sound card is nVidia Corporation MCP55 High Definition Audio.

the biggest problem i have is i'm not familiar to pulse audio controller. 

can you help? thanx a lot.

---

### Post by markbuntu on 2008-10-28
If you want to add a digital output to Pulseaudio, you can look here:

[http://ubuntuforums.org/showthread.php?t=776958](http://ubuntuforums.org/showthread.php?t=776958)

Since you are using ubuntustudio, you will be using jack and you will need to set the jack output to hw0:1 or hw0:2 or something like that depending on where the digital output shows up when you run aplay -l from a terminal.

---

### Post by alikbalik on 2008-10-29
ok i did what is written, pulse gets the signal from jack and also without jack (a driect connection btw. audacious and pulse). but there is still no sound.

> **** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 0/1
  Subdevice #0: subdevice #0


this is my "aplay -l" list.
the point that i wonder if is this digital is the "optic cable one" or the coaxial SPDIF one =)


thanx a lot.

---

### Post by alikbalik on 2008-10-29
ok i solved the problem. i left master volume control muted. "quiche" i am.

thanx.
:guitar:

---

