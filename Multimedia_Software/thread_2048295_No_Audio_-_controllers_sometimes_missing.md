---
title: "No Audio - controllers sometimes missing"
date: 2012-08-26
forum: Multimedia Software
---

### Post by EightsAndAces on 2012-08-26
I installed Ubuntu on my 4th computer yesterday: the one I do most of my work on. It's a dual boot installation with Ubuntu 12.04 and XP. The others had a couple minor hiccups but worked nicely. On this computer I have intermittent sound issues.
 
 The ALSA mixer is not installed as it's not part of 12.04 that I can tell. Looking at the Pulseaudio Sound Settings Output tab, I intermittently have 1 to 3 controllers present like:
 
 Outputs: 
 Speakers VT8237A/VT8251 HDA Controller 
 Headphones VT8237A/VT8251 HDA Controller 
 Analog Output VT8237A/VT8251 HDA Controller 
 Digital Output VT8237A/VT8251 HDA Controller 
 Dummy Output
 
 When the Headphones controller is present, I can get front & rear headphone audio. When the Analog controller is present, I can get speaker audio. But, this changes with every boot-up. Every time I boot, different controllers appear, seemingly at random; and I haven't seen more than 3 at a time.
 
 Additionally, the front or rear microphones do not work. Most of the time I have nothing listed under the input tab. At times I have 1 or 2 of these:
 
 Inputs: 
 Analog Input VT8237A/VT8251 HDA Controller 
 Front Microphone VT8237A/VT8251 HDA Controller 
 Rear Microphone VT8237A/VT8251 HDA Controller
 
 When the Front controller is present I have front microphone, Back controller for back microphone. Again, this changes with every boot-up.
 
 I've read every help guide I can find and struck out. I'm still somewhat new to Linx. I like it and intend to keep on course, but I'm still learning. Given that, I'm not really sure what I'm looking for and what clues, if any, may be buried in this information, but maybe it's helpful:

```
                                   
vince@vince-MS-7387:~$ sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq* 
 Specified filename /dev/dsp* does not exist. 
 Specified filename /dev/seq* does not exist. 
 USER        PID ACCESS COMMAND 
 /dev/snd/controlC0:  vince      1813 F.... pulseaudio
  
 vince@vince-MS-7387:~$ sudo lshw -class multimedia  *-multimedia             
 description: Audio device 
 product: VT8237A/VT8251 HDA Controller 
 vendor: VIA Technologies, Inc. 
 physical id: 1 
 bus info: pci@0000:80:01.0 
 version: 10 
 width: 64 bits 
 clock: 33MHz 
 capabilities: pm msi pciexpress bus_master cap_list 
 configuration: driver=snd_hda_intel latency=0 
 resources: irq:17 memory:febfc000-febfffff 

 vince@vince-MS-7387:~$ sudo aplay -l 
 **** List of PLAYBACK Hardware Devices **** 
 card 0: VT82xx [HDA VIA VT82xx], device 0: ALC888 Analog [ALC888 Analog] 
 Subdevices: 1/1 
 Subdevice #0: subdevice #0 
 card 0: VT82xx [HDA VIA VT82xx], device 1: ALC888 Digital [ALC888 Digital] 
 Subdevices: 1/1 
 Subdevice #0: subdevice #0 

 vince@vince-MS-7387:~$ lspci -v | grep -A7 -i "audio" 
 80:01.0 Audio device: VIA Technologies, Inc. VT8237A/VT8251 HDA Controller (rev 10) 
 Subsystem: Micro-Star International Co., Ltd. Device 7387 
 Flags: bus master, fast devsel, latency 0, IRQ 17 
 Memory at febfc000 (64-bit, non-prefetchable) [size=16K] 
 Capabilities: <access denied> 
 Kernel driver in use: snd_hda_intel 
 Kernel modules: snd-hda-intel 
  
```The above was taken when the Digital, Headpone, and Analog controllers were all present, and no input controllers were present.
 
 I've Played with Ubuntu on my other computers to get comfortable with it but before installing it on this computer till now. I've been very impressed with Ubuntu and looking forward to the transition, but I use audio daily, namely Skype, so I have to have audio up and running.  
 
 Thanks in advance for your help.

---

