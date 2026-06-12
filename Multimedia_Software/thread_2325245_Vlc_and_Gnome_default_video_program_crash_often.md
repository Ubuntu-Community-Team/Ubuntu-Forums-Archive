---
title: "Vlc and Gnome default video program crash often"
date: 2016-05-20
forum: Multimedia Software
---

### Post by nigro.orlando on 2016-05-20
Hi!
I have experienced some problems with all kind of video-files.The program (both VLC and the default one, VLC seems to crash more often) crashes leading sometimes to all desktop freezing. I usually solve it using CTRL-ALT-F1 and then I can reboot in the shell. 
It's very annoying. I also have similar problem with programs like OPENSHOT but not with Kdenlive. 
It's Ubuntu Gnome 16.04.

---

### Post by ajgreeny on 2016-05-20
What is your hardware, particularly the graphic card, and what driver is it using?

If you're not sure run command ```
sudo lshw -c display
``` and post back here the output in code tags.
To use **Code-Tags** for terminal output see my signature below for a **How-to**

---

### Post by nigro.orlando on 2016-05-20
Hi! here is the output:

```
 *-display               
       description: VGA compatible controller
       product: Fiji [Radeon R9 FURY / NANO Series]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: c8
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=amdgpu latency=0
       resources: irq:63 memory:c0000000-cfffffff memory:d0000000-d01fffff ioport:e000(size=256) memory:fea00000-fea3ffff memory:fea40000-fea5ffff


```

---

### Post by nigro.orlando on 2016-05-24
Yesterday the desktop froze twice while watching youtube and today it just froze all of a sudden... 
I don't understand this issue. I was told that the AMDGPU would work very well with the AMD fiji GPUs

---

### Post by nigro.orlando on 2016-06-05
I still have this issue, may it be a gnome-thing?

---

### Post by yoshii on 2016-06-07
You should initiate a RAM hardware check from your BIOS during bootup.  
The types of issues you are describing are sometimes just from corrupted RAM hardware.    
If it finds an error, you will need to replace the broken RAM chip(s).  

I had a similar problem with a used laptop.  
The thing about RAM errors is that sometimes they are avoided just by luck until a large program or file is loaded up; then the bad RAM is selected and it crashes data/system/program.

---

