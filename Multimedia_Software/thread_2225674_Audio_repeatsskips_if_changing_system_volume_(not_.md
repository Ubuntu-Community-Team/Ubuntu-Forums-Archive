---
title: "Audio repeats/skips if changing system volume (not in application)"
date: 2014-05-22
forum: Multimedia Software
---

### Post by slooksterpsv on 2014-05-22
I've checked TOP and there's no CPU spikes, but this happens with video, music, etc. in Chrome. Exaile any music player or video player (even VLC) - NOT SPECIFIC TO FLASH. I don't know what the issue is where the CPU doesn't spike. Below I've grabbed my lspci and lshw -c Sound

```
shawn@shawn-Satellite-C75D-A:~$ lspci | grep Audio
00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Device 9840
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller (rev 02)

```

```

shawn@shawn-Satellite-C75D-A:~$ sudo !!
sudo lshw -c Sound
[sudo] password for shawn: 
  *-multimedia:0          
       description: Audio device
       product: Advanced Micro Devices, Inc. [AMD/ATI]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 1.1
       bus info: pci@0000:00:01.1
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list
       configuration: driver=snd_hda_intel latency=0
       resources: irq:80 memory:f0240000-f0243fff
  *-multimedia:1
       description: Audio device
       product: FCH Azalia Controller
       vendor: Advanced Micro Devices, Inc. [AMD]
       physical id: 14.2
       bus info: pci@0000:00:14.2
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list
       configuration: driver=snd_hda_intel latency=32
       resources: irq:81 memory:f0244000-f0247fff

```

Even updating the audio in alsamixer causes the sound to repeat/skip usually it increases in sound even if I turn it down and it goes from side to side example:

Music at 10% on left; then it starts 15% on the right, then 20% for both speakers. It's a weird issue.

No manually specified modules for modprobe.

Hmm.. I'm running pulseaudio let's see what else can I try to dig down deeper?

Xubuntu 14.04 64-bit

---

