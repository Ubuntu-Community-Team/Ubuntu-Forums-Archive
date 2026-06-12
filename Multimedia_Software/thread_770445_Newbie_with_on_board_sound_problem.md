---
title: "Newbie with on board sound problem"
date: 2008-04-27
forum: Multimedia Software
---

### Post by lockettpots on 2008-04-27
Hi All

I've just installed Ubuntu Studio Hardy Heron on my computer that has an ASUS P5B-plus motherboard with soundMax.

I have no sound at all although the sound is fine in Windows XP (dual Boot)

Various commands give the following output

```
john@ubuntu:~$ aplay -l
aplay: device_list:205: no soundcards found...
john@ubuntu:~$ cat /proc/asound/cards
--- no soundcards ---
john@ubuntu:~$ lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
john@ubuntu:~$ amixer info
amixer: Control device default open error: No such file or directory

```

I've googled for the problem but I am having no success in getting sound

What can I do?

John

---

### Post by newbreed on 2008-04-27
New myself, may I ask where you might get a list of those basic commands? sorry to stray off your subject.

this is what I get:
newbreed@newbreed-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
newbreed@newbreedl-laptop:~$ cat /proc/asound/cards
 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xb0000000 irq 21
newbreed@newbreed-laptop:~$ lspci | grep -i audio
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
newbreed@newbreed-laptop:~$ amixer info
Card default 'NVidia'/'HDA NVidia at 0xb0000000 irq 21'
  Mixer name	: 'Conexant CX20549 (Venice)'
  Components	: 'HDA:14f15045'
  Controls      : 17
  Simple ctrls  : 7
newbreed@newbreed-laptop:~$

---

### Post by lockettpots on 2008-04-28
Oh dear! No replies.
Doesn't anyone have any ideas?
Or do I just have to give up and go back to Windows?

John

---

### Post by gantellus on 2008-05-03
Same problem, same sound card, same outputs of listed commands

Gonna kill myself by running into the wall, 'cause lose all hope :(

](*,)

---

