---
title: "Xubuntu Sound Driver"
date: 2009-01-26
forum: Multimedia Software
---

### Post by jrm19852007 on 2009-01-26
Hi I recently started using Xubuntu and I ve got everything working great except my sound wont work.
I really would appreciate the help. Let me know what infomation is needed to get the help. Im such a noob.

---

### Post by cariboo on 2009-01-26
Could you paste the output of:

```
sudo lshw -C multimedia
```

in your next post. THe above command must be run in an Applications-->Accessories-->Terminal.

When pasting the output from terminal  commands please use the [noparse]```

```[/noparse] tags.

Jim

---

### Post by jrm19852007 on 2009-01-26
*-multimedia            
       description: Audio device
       product: 82801G (ICH7 Family) High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel

---

### Post by Linuxdork on 2009-01-26
This fixed my sound problems [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

