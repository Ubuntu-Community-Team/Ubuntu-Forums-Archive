---
title: "Sound stuttering with Nvidia chipset on ASUS M3N78 motherboard"
date: 2008-08-14
forum: Multimedia Software
---

### Post by entropius42 on 2008-08-14
I'm having severe sound stuttering/desynchronization problems for all sources of audio (boot sound, .wav's played by the console, Audacity, everything) in Ubuntu 8.04.

I'm using the onboard sound on an Asus M3N78 motherboard.

lshw says:
> 
wfreeman@carnavah:~$ sudo lshw -C sound
  *-multimedia
       description: Audio device
       product: nVidia Corporation
       vendor: nVidia Corporation
       physical id: 7
       bus info: pci@0000:00:07.0
       version: a1
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list
       configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2 module=snd_hda_intel


The "coarseness" of the stuttering is affected by things like the prebuffer length in Audacity. Oddly enough, switching tasks with Alt+Tab or doing anything that requires the CPU to do work for a jiffy (like minimizing windows, switching windows in Firefox, etc.) will momentarily reset the stutter, such that audio actually plays properly when I hold down Alt+Tab to rapidly switch between windows. 

Oddly enough, I remember observing this same behavior on an old computer running a software synthesizer -- sometimes the audio would become desynched and would crackle, but alt-tabbing back and forth would clear it.

Any ideas what's going on here? Any help would be appreciated.

---

### Post by bcn17 on 2008-08-22
leslie1@lesubuntu:~$ sudo lshw -C sound
  *-multimedia            
       description: Audio device
       product: nVidia Corporation
       vendor: nVidia Corporation
       physical id: 7
       bus info: pci@0000:00:07.0
       version: a1
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list
       configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2 module=snd_hda_intel


SAME OUTPUT- same problem. I'm looking for a fix- thinking about trying the newest ALSA drivers soon.

---

### Post by nostar on 2008-08-30
Same problem here, same motherboard. I am actually on Fedora, but still looking for a solution.

---

### Post by nunquamsecutus on 2008-08-31
Same output, same issues.  I'm running a gigabyte GA-M750SLI-DS4 mobo though.  I can also confirm that causing the cpu to work will clear up the issue.  The more load you put the cpu under, the better the audio sounds.  When I have only Exaile open playing a song it is completely unrecognizable.

Output of asoundconf list is:
> 
$ asoundconf list
Names of available sound cards:
NVidia


Output of lspci -v is: (Just the audio part)
> 
sudo lspci -v
00:07.0 Audio device: nVidia Corporation Unknown device 0774 (rev a1)
	Subsystem: Giga-byte Technology Unknown device a002
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 21
	Memory at f8100000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [44] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
	Capabilities: [6c] HyperTransport: MSI Mapping


---

### Post by Bennykurns on 2008-09-11
> Same output, same issues. I'm running a gigabyte GA-M750SLI-DS4 mobo though. I can also confirm that causing the cpu to work will clear up the issue. The more load you put the cpu under, the better the audio sounds. When I have only Exaile open playing a song it is completely unrecognizable.

I have that exact same problem. Any solutions yet?

---

### Post by esatap on 2008-09-11
8.10 Alpha5 solved the problem for me.

---

