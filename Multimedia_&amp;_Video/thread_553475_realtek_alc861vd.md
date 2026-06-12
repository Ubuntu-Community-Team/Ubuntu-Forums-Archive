---
title: "realtek alc861vd"
date: 2007-09-17
forum: Multimedia &amp; Video
---

### Post by tfarinella on 2007-09-17
heres the output of:

**sudo lshw -class sound** 

```
*-multimedia            
       description: Audio device
       product: 82801G (ICH7 Family) High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: iomemory:d0340000-d0343fff irq:22

```

if i plug in headphones i can hear sound VERY quietly with the volume at max... how can i make it:

A: play through the on-board speakers (laptop)
B: play louder through headphones
C: work in general


i did some homework on this but didnt dive into anything yet...

thanks :guitar:

---

### Post by tfarinella on 2007-09-17
hi sorry if im impatient but i need help

---

### Post by tfarinella on 2007-09-18
you know im not joking i teally do need help

---

### Post by jaygo on 2007-10-15
we're working on the same audio chipset [over here]("http://ubuntuforums.org/showthread.php?p=3536513#post3536513"), though it might be a different problem. Did you ever get this working?

---

