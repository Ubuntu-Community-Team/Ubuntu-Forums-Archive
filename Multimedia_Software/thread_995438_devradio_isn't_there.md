---
title: "/dev/radio isn't there"
date: 2008-11-27
forum: Multimedia Software
---

### Post by Deutscher Alex on 2008-11-27
I have a TV tuner card of some sort in my computer.
Could someone tell me how to configure the card so that I can use it?? I've been searching for a solution but can only find unanswered threads...
Using gnomeradio or gradio gives me the error "/dev/radio: No such file or directory"
(there is no /dev/radio0 either)

lshw output below:
```
alex@alex-desktop:~$ sudo lshw -C multimedia
  *-multimedia            
       description: Audio device
       product: 82801H (ICH8 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel
  *-multimedia
       description: Multimedia video controller
       product: Conexant
       vendor: Conexant
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 0f
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress pm vpd msi bus_master cap_list
       configuration: driver=cx23885 latency=0 module=cx23885

```

---

### Post by Deutscher Alex on 2008-11-29
bump... can anyone offer any sort of insight on this problem?
how do i get /dev/radio to be mounted?

---

