---
title: "Audio.....VIA 8237?  Cannot get it to work and cannot seem to find a solution"
date: 2006-06-05
forum: Multimedia &amp; Video
---

### Post by hauger on 2006-06-05
Hi.

I just installed Kubuntu 6.06 (64-bit) onto my desktop, which runs off a Soltek KT8Pro Motherboard and an AMD64 chip.  The thing is, it refuses to play any sound whatsoever.

1. The sound works and is hooked up right, as verified through booting into Windows XP

2. Kmix shows all sliders unmuted and turned up.  Same with alsamixer

3. The sound hardward shows to have detected the sound chip correctly and has no apparent issues with it.

4. Output: $ lsmod | grep -i

bison@bison-desktop:~$ lsmod | grep -i snd
snd_seq_dummy           5508  0
snd_seq_oss            38372  0
snd_seq_midi           11456  0
snd_seq_midi_event      9984  2 snd_seq_oss,snd_seq_midi
snd_seq                64088  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_via82xx            32936  1
gameport               19216  1 snd_via82xx
snd_ac97_codec        110268  1 snd_via82xx
snd_ac97_bus            4096  1 snd_ac97_codec
snd_pcm_oss            59424  0
snd_mixer_oss          20608  1 snd_pcm_oss
snd_mpu401_uart        10368  1 snd_via82xx
snd_rawmidi            31648  2 snd_seq_midi,snd_mpu401_uart
snd_seq_device         11280  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
snd_pcm               104712  4 snd_via82xx,snd_ac97_codec,saa7134_alsa,snd_pcm_oss
snd_timer              29064  2 snd_seq,snd_pcm
snd_page_alloc         13968  2 snd_via82xx,snd_pcm
snd                    68576  16 snd_seq_oss,snd_seq,snd_via82xx,snd_ac97_codec,saa7134_alsa,snd_pcm_oss,snd_mixer_oss,snd_mpu401_uart,snd_rawmidi,snd_seq_device,snd_pcm,snd_timer
soundcore              13216  1 snd


bison@bison-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 1: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 1: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


One possibility I've heard is that potentially, my Logitech USB Webcam w/Mic might be mistaken somehow as a soundcard. If that's the case, I've no idea how to verify it or how to correct it.

As far as skill level with linux goes, I know how to and am comfortable with editing config files, but not skilled enough to troubleshoot them. In otherwords, I know enough to mess up the OS if I go tinkering, but not enough to fix it.

Any help from any one would be greatly appreciated. Thanks, Rob

---

### Post by hauger on 2006-06-05
additional info:

Tried to run amarok from the terminal (to see if sound was available to root).  This is the output:

bison@bison-desktop:~$ sudo amarok
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
amaroK: [Loader] Starting amarokapp..
amaroK: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
ScimInputContextPlugin()

not sure if that provides useful information, but it seemed to point to something being amiss.

I also tried unplugging my webcam and seeing what occured.  From that, my ASUS TV FM Tuner PCI card has become the #1 "sound" card.  This means that currently:

/dev/dsp ---> ASUS TV FM Tuner PCI Card
/dev/dsp1 --> VIA 8237 Onboard AC97 sound
/dev/dsp2 --> Logitech Webcam with Mic.

Is it possible to reorder these somehow and see if listing the VIA 8237 as /dev/dsp might somehow solve the problem?

Again, any help is appreciated

---

### Post by hauger on 2006-06-06
bump.

Someone (perhaps a linux god) must have some sort of insight into this problem.

---

### Post by hauger on 2006-06-07
Update:  I found a "solution".  By opening my computer, I pulled out my TV card and unplugged my Web Camera, then rebooted.  Kubuntu then FINALLY figured out my soundcard.  I then shutdown, re-inserted my TV card, and there it was, working sound.  I've not yet hooked back up my webcam to see if things stay fixed.

I say "solution" in so much as this is a terrible fix.  A desktop user should not have to pull hardware to force proper prioritizing of hardware.  Further, most users wouldn't be able to figure out the problem to begin with, as most things looked correct on the surface (correctly identified hardware and whatnot).

Oh, and thanks for all the help guys.  45 views, 2 days, and not so much as a single reply.  Appreciate it.  That's some good community work.

---

### Post by bogaboga on 2006-06-12
I have that very VIA chipset card on my system and was facing the same problem. Try this: 
1Unplug all your periperals save the KB and mouse then reboot yr system. I am assuming that Ubuntu recognizes yr card. Mine could be seen in the device manager an when you double click the loud speaker icon and select file. I have 2 entries there both VIA devices. I made sure the ALSA option is checked. I guess you have cheked out the cables and state like "mute".

---

