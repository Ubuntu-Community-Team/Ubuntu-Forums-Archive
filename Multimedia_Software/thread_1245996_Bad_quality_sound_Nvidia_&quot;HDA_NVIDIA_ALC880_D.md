---
title: "Bad quality sound Nvidia &quot;HDA NVIDIA ALC880 DIGITAL (ALSA) &quot; not working"
date: 2009-08-21
forum: Multimedia Software
---

### Post by kastanedowski on 2009-08-21
Hi

After days of trying everything I have found in forums I need your advice (HELP)

I have the same computer with windows and the sound quality is too different, I have gone to my sound preferences and in "automatic" I can hear the sound but not in "HDA NVIDIA".

ALSA is supposed to do the job and I actualise it but the same...

In a Spanish forum I have found that ALSA makes everything to 48Khz, that makes the system really faster but has a horrible quality and they are recommending to "jump the filter _dmix"_ so the kernel can work directly over the sound.
 
"h   t     t    p   :    //   foro.powers    .cl   /viewtopic.        php?f=1&t=256273"
 (I can not post links so join the spaces)
 
so I will ask you for your comment, why using the kernel to do the ALSA's job? wouldn't be better to change the 48Khz into 128Khz at least? 
someone has idea how?
 
 
Writing "asoundconf list" I can see that I have a NVIDIA sound card, and I am pretty sure that the Nvidia driver should work,right?
 

Here the details of my computer and system


*These are the results:*
 
 _[B]lspci -nnk | grep -iA 2 audio_
 
00:10.1 Audio device [0403]: nVidia Corporation MCP51 High Definition Audio [10de:026c] (rev a2)
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
 
 _aplay -l_
 
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC880 Analog [ALC880 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC880 Digital [ALC880 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
 
 
 _cat /proc/asound/version_
Advanced [Linux[IMG]http://images.intellitxt.com/ast/adTypes/mag-glass_10x10.gif[/IMG]]("http://www.linuxforums.org/forum/#") Sound Architecture Driver Version 1.0.18rc3.
 
 
 *and these the details of the computer:*
 
Multimedia Audio Controller
nVidia Corporation MCP51 Hidg Definition Audio 
Advanced Linux Sound Architecture Driver Version 1.0.18rc3. (rev a2)
Subsystem:Gigabyte Technology Device a102
 
GNOME  2.26.1 (Ubuntu 2009-05-06)
GCC Version Kernel  2.6.28-15-generic (#49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009)
Linux
4.3.3 (i486-linux-gnu)
Xorg version unknown (09 April 2009  02:10:02AM)
 
AMD Athlon(tm) 64 Processor 3500+
Model GeForce 6100
Graohc card information  NVIDIA UNIX x86 Kernel Module  185.18.14  Wed May 27 02:23:13 PDT 2009
 
 

I have been googling for information and tried everything I have found, any advices will be really welcome, thanks!


[http://ubuntuforums.org/showthread.php?t=843012&highlight=alsa+nvidia](http://ubuntuforums.org/showthread.php?t=843012&highlight=alsa+nvidia)

---

