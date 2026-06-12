---
title: "No microphone - help please"
date: 2009-08-16
forum: Multimedia Software
---

### Post by eakergd on 2009-08-16
Tried posting this in the Laptops forum, but got no response.  Hopefully, someone here can help.

Everything seems to be working with my audio, except for the microphone. This is annoying, because I like to use skype pretty regularly. I have a Sony Vaio laptop (AR150G). I am using the standard install of Ubuntu 9.04, and the only extra driver I loaded is for the video. Can anyone help me get the microphone working. Here is the chipset info:

dad@dad-laptop:~$ sudo lshw -C multimedia
[sudo] password for dad: 
  *-multimedia            
       description: Audio device
       product: 82801G (ICH7 Family) High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel
  *-multimedia UNCLAIMED
       description: Multimedia controller
       product: Fujitsu Limited.
       vendor: Fujitsu Limited.
       physical id: 4
       bus info: pci@0000:0a:04.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=64 maxlatency=64 mingnt=16


Thanks in advance.

Gary

---

### Post by eakergd on 2009-08-16
bump

---

