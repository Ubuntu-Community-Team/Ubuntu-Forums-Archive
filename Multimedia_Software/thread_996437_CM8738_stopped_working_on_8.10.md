---
title: "CM8738 stopped working on 8.10"
date: 2008-11-28
forum: Multimedia Software
---

### Post by bunny_basher on 2008-11-28
Hi, since upgrading to 8.10 my sound card has stopped working!

lspci:
03:01.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)

Any Ideas?
Marcus

---

### Post by cariboo on 2008-11-28
Could you paste the output of:

```
sudo lshw -C multimedia
```

in your next post?

Jim

---

### Post by bunny_basher on 2008-11-30
marcus@Bunny-Basher-Linux:~$ sudo lshw -C multimedia
[sudo] password for marcus: 
  *-multimedia UNCLAIMED  
       description: Audio device
       product: 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 04
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
  *-multimedia UNCLAIMED
       description: Multimedia audio controller
       product: CM8738
       vendor: C-Media Electronics Inc
       physical id: 1
       bus info: pci@0000:03:01.0
       version: 10
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64 maxlatency=24 mingnt=2
marcus@Bunny-Basher-Linux:~$ 

It's the second one i want working, neither are recognised though :S

Sorry for the late reply
Marcus

---

### Post by markbuntu on 2008-11-30
What does aplay -l tell you?

---

### Post by cariboo on 2008-11-30
I have looked around and it seems the driver was pulled form the kernel due to licensing issues. There are no drivers available from the manufacturer for Windows or Linux.

I did find a driver, but it seems you will have to compile a custom kernel in order to use it, or you could reinstall hardy,  which ever you find easier.

Jim

---

### Post by markbuntu on 2008-11-30
I have a C-Media pci 8768 card and it is using the snd_cmipci module in Intrepid which is the same module for the 8738. I think you may have been misinformed.

---

