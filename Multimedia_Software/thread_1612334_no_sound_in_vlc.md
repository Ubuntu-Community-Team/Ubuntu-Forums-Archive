---
title: "no sound in vlc"
date: 2010-11-03
forum: Multimedia Software
---

### Post by anto47 on 2010-11-03
[SIZE=4]hey friends i am new 2 here ...........

any way ...........[/SIZE] [SIZE=4]
my problm is tht ............

i am not getting any sound in vlc player in Kubuntu      .......[/SIZE] [SIZE=4]
bt  i am getting sound in my default player(dragon) .............

wat shud i do??????????[/SIZE]

---

### Post by anto47 on 2010-11-03
[SIZE=4]smbody pls help me............
[/SIZE]

---

### Post by Zorael on 2010-11-04
What release are you running? 10.10?

Also, when you play something in VLC, try opening up a terminal and type **dmesg**. Copy the last ~10 lines and paste here.

As well as the output of '**aplay -l**', please.

---

### Post by Bloemetjesgordijn on 2010-11-11
Same issue, maybe you can help me:
here my "aplay -l"output.

```
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: ALC889A Digital [ALC889A Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CMI8770 [C-Media CMI8770], device 0: CMI8738-MC8 [C-Media PCI DAC/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CMI8770 [C-Media CMI8770], device 1: CMI8738-MC8 [C-Media PCI 2nd DAC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CMI8770 [C-Media CMI8770], device 2: CMI8738-MC8 [C-Media PCI IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

My dmsg output:

```
[  720.961683] modprobe      D 00000000ffff8e40     0   675      1 0x00000000
[  720.961689]  ffff88013ac29d48 0000000000000086 ffff880100000000 0000000000015980
[  720.961696]  ffff88013ac29fd8 0000000000015980 ffff88013ac29fd8 ffff880139ceadc0
[  720.961702]  0000000000015980 0000000000015980 ffff88013ac29fd8 0000000000015980
[  720.961711] Call Trace:
[  720.961716]  [<ffffffff81587dd7>] __mutex_lock_slowpath+0xf7/0x180
[  720.961722]  [<ffffffff81388026>] ? really_probe+0xb6/0x190
[  720.961727]  [<ffffffff81388170>] ? __driver_attach+0x0/0xa0
[  720.961733]  [<ffffffff81587cbb>] mutex_lock+0x2b/0x50
[  720.961743]  [<ffffffff813881c9>] __driver_attach+0x59/0xa0
[  720.961748]  [<ffffffff81388170>] ? __driver_attach+0x0/0xa0
[  720.961753]  [<ffffffff81387418>] bus_for_each_dev+0x68/0x90
[  720.961758]  [<ffffffff81387e4e>] driver_attach+0x1e/0x20
[  720.961763]  [<ffffffff8138770e>] bus_add_driver+0xde/0x280
[  720.961768]  [<ffffffff81388550>] driver_register+0x80/0x150
[  720.961775]  [<ffffffff8158d176>] ? notifier_call_chain+0x56/0x80
[  720.961782]  [<ffffffff812d8506>] __pci_register_driver+0x56/0xd0
[  720.961792]  [<ffffffff81084f05>] ? __blocking_notifier_call_chain+0x65/0x80
[  720.961805]  [<ffffffffa0140000>] ? alsa_card_azx_init+0x0/0x20 [snd_hda_intel]
[  720.961814]  [<ffffffffa014001e>] alsa_card_azx_init+0x1e/0x20 [snd_hda_intel]
[  720.961826]  [<ffffffff8100204c>] do_one_initcall+0x3c/0x1a0
[  720.961834]  [<ffffffff8109bc6b>] sys_init_module+0xbb/0x200
[  720.961842]  [<ffffffff8100a0f2>] system_call_fastpath+0x16/0x1b

```

I have read [here]("https://bbs.archlinux.org/viewtopic.php?pid=794771") that there seems to be competition for default sound card. But I couldnt find something like modprobe.conf...bummer


Hope you can help me

Ths in advance.

Cheerz,
Bloemetjesgordijn

---

### Post by Bloemetjesgordijn on 2010-11-11
Yeah....solved

I installed PulseAudio Volume Control (pavucontrol) & PulseAudio Volume Meter (pavumeter). Use Synaptic...KPackage couldnt find them.

I started PulseAudio Volume Control (is somewhere in Applications-> Multimedia).

As soon als VLC is started, I noticed that in Pulse Audio Volume Controle VLC was redirected to the wrong sound card. As soon as I changed this (in Pulse Audio Contole) everything was ok. This also helped me to get flash sound working in Opera & Firefox.

Cheerz

---

