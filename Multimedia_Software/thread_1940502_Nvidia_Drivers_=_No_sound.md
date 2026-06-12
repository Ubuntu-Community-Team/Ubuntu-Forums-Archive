---
title: "Nvidia Drivers = No sound"
date: 2012-03-13
forum: Multimedia Software
---

### Post by gusbeto37 on 2012-03-13
Hi all,

I have an Nvidia GTX 560 video card and an EMU-1212m PCI audio card (not the PCIe version). 

I have checked with lspci and the driver is emu10k1 for the audio card. Used alsaconf and all to configure it. 

At some point it was working fine with everything default but with kernel 3.2.6 on Ubuntu 10.04.3 i386.

Then I decided I should install the NVIDIA Drivers to get compiz stuff. The moment I installed the drivers my audio card stopped working, I tried reinstalling all alsa using > sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2Then I tried to use alsaconf again, it saw the audio card and everything went right. Restarted, but still no audio. I followed all the steps on this guide: [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting) and still no audio. 


Any ideas?

Saludos, 
Gustavo

---

### Post by gusbeto37 on 2012-03-13
result of lshw

  *-multimedia UNCLAIMED
       description: Multimedia audio controller
       product: SB0400 Audigy2 Value
       vendor: Creative Labs
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=32 maxlatency=20 mingnt=2
       resources: ioport:afc0(size=64)


result of lscpci -v
04:00.0 Multimedia audio controller: Creative Labs SB0400 Audigy2 Value
	Subsystem: Creative Labs Device 4004
	Flags: medium devsel, IRQ 19
	I/O ports at afc0 [size=64]
	Capabilities: <access denied>
	Kernel modules: snd-emu10k1

aplay -l
aplay: device_list:252: no soundcards found...


BTW already tried using JACK and did install all the restricted extras

---

### Post by UltimateCat on 2012-03-14
I am thinking that it could be your sound card that is the problem not the Nvidia Drivers-
I saw that the output to the lshw command that you put in your terminal said" No soundcards found" 

I read that you have the GTX560 and the EMU1212m but not the PCI version.....I would do research on the EMU1212m.

I went to Google to look for you but only found the one for PCI-
Maybe the manufacture of the driver can help.

I have 10.04 plus Ultimate Edition 2.7 and help for that forum is:
[www.ultimateeditionoz.com](www.ultimateeditionoz.com)

Linux might be of help

[www.linuxquestions.org](www.linuxquestions.org)

This is a sound card website that might be of help-
[http://www.local.com/results.aspx?keyword=sound+card+driver+download&cid=18120](http://www.local.com/results.aspx?keyword=sound+card+driver+download&cid=18120)

Hope this helps

---

### Post by gusbeto37 on 2012-03-14
Hi, 

There are two models of the 1212m an older PCI version and a PCIe version, each requires different drivers. Now the 1212m is confirmed working, there is a tutorial on how to make it work (it is really just manually installing alsa drivers only for the emu10k1 model), and [here]("http://ubuntuforums.org/showthread.php?t=1661068&highlight=emu+1212m") is a guy compaining that analog outs do work and opticals do not. I cannot even get the thing to see it as a sound card! Also, there was a point where I did have sound but something went wrong and I could never recover sound. 

Right now I am installing a fresh Partition on a different HDD, and am going to fully install ALSA and see if it works. I'll keep you posted tomorrow.

---

