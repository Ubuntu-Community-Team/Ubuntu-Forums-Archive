---
title: "Sound problems"
date: 2009-11-13
forum: Multimedia Software
---

### Post by Dmjthomas on 2009-11-13
Hi I am new to the Linux world. I installed Ubuntu, and all seemed to be running well. I shut down my laptop, then when I turned it back on I had no sound.
I have tried to follow the advice given on other troublehooting pages on the Ubuntu sites such as: [https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats](https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats)

I believe that I have two problems based on this checklist:

1:

david@David-laptop:~$ dmesg | grep -i hda
[   10.991859] HDA Intel 0000:00:14.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   11.458052] hda_codec: ALC883: BIOS auto-probing.
[   11.458779] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:14.2/input/input7
david@David-laptop:~$ 

I am getting a message saying BIOS auto Probing, so I installed the ["linux-backports-modules-alsa-karmic-generic]("apt://linux-backports-modules-alsa-karmic-generic")" and rebooted bu nothing seemed to happen.

2:
The volume control lists a dummy output so I tried checking whether another process was locking the soundcard:

david@David-laptop:~$ sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
[sudo] password for david: 
                     USER PID ACCESS COMMAND
/dev/snd/controlC0:  Slmodemd   1242 F.... slmodemd
/dev/snd/pcmC0D6c:   Slmodemd   1242 F...m slmodemd
/dev/snd/pcmC0D6p:   Slmodemd   1242 F...m slmodemd
david@David-laptop:~$ 

using the instructions I tried to kill slmodemd, but I got the following message:

david@David-laptop:~$ killall slmodemd
slmodemd(1242): Operation not permitted
slmodemd: no process found

I don't know what to do next, can anyone help?

---

### Post by Dmjthomas on 2009-11-14
Right!

I have fixed it. I was trying to think of the last time I heard sound on my laptop and it was when I got asked to activate my modem. So I did.

All I've done now is go to system->administration-> hardware drivers and disabled it. Straight away the volume control in the top right reloaded and the 'dummy' message has been replaced with Internal 'Analog Audio Stereo'.

So my sound issues are resolved... That is until I try to install my creative x-fi SB soundcard...

---

### Post by stuntant on 2010-02-17
This was my problem too. Thanks for posting, this was driving me crazy.

---

### Post by mihamtalamac on 2010-02-23
that solved my problem :) thanks for posting :D:D:D:D:D

---

### Post by bubbabeernuts on 2010-03-02
I had the same problem, too.  I cleared it up by uninstalling that modem driver.

But here's what's going on now.  Whenever I log in to Ubuntu Studio, the audio icon is automatically muted.  I have to right-click and go to Properties and unmute it there.  It won't unmute from the right-click menu.

Anybody run into this?  And if so, have you found a solution?

---

