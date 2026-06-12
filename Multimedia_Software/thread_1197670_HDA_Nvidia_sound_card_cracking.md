---
title: "HDA Nvidia sound card cracking"
date: 2009-06-26
forum: Multimedia Software
---

### Post by liberalist on 2009-06-26
Hi everyone, 

I have an annoying cracking sound card on my Kubuntu 9.04 installation. It seems to be kernel-related, from what I've read so far. I have tried "regular" Ubuntu 9.04 to see if it mattered, but it gave the same problems. Adjusting the sliders didn't help either. A thread suggested to install linux-backports-modules-jaunty-generic, which did not solve the problem. 

My soundcard: 
jonathan@ubuntu:~$ sudo lshw -C multimedia 
[sudo] password for jonathan: 
  *-multimedia 
       description: Audio device 
       product: MCP65 High Definition Audio 
       vendor: nVidia Corporation 
       physical id: 7 
       bus info: pci@0000:00:07.0 
       version: a1 
       width: 32 bits 
       clock: 66MHz 
       capabilities: pm msi ht bus_master cap_list 
       configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2 module=snd_hda_intel 


The sound problem solution guide seems rather complex. If somebody could help me or explain why my card is not properly supported that would be very much appreciated.

---

### Post by getmealive on 2010-03-05
hello

I have installed Kubuntu 9.10 and have had problem with sounds cracks on my HP pavilion dv6618eo with HD nVidia audio. but I fixed this by installing the following packages:

1. gedit: the official text editor of Gnome.
2. gksude: installed this through Terminal

after installion,I then entered the  following code in terminal: 

gksudo gedit /etc/modprobe.d/alsa-base.conf

and then changed the following code in Alsa-config:

options snd-hda-intel power_save=10 power_save_controller=N

changed to: 
options snd-hda-intel power_save=0 power_save_controller=N

after all restarted the pc, and all was successfull, and the cracking sound fixed.

in ubuntu, no need to install gksudo and gedit. just open terminal and paste in the following code:

sudo gedit /etc/modprobe.d/alsa-base.conf

or 
gksudo gedit /etc/modprobe.d/alsa-base.conf

then change the power save from 10 to 0.
 and restart pc.

---

