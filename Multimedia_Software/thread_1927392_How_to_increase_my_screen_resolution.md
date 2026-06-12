---
title: "How to increase my screen resolution?"
date: 2012-02-17
forum: Multimedia Software
---

### Post by marcoharder on 2012-02-17
I'm currently stuck at 1024x768, but I know that my monitor can go beyond this as when I plug it into my Windows laptop, it can support higher configurations. On my Ubuntu desktop though, the 'Monitors' option under 'Preferences' only shows 1024x768 as the highest possible resolution. 

Anyone care to help? Thanks!

---

### Post by pbpersson on 2012-02-17
Tell us what version of Ubuntu you are using, what type of graphics card you have, and post the output of the following command so we can see what video driver Ubuntu is using:

```
sudo lshw -C video
```

---

### Post by marcoharder on 2012-02-18
Oh shoot, sorry I forgot to put that in:

Ubuntu 10.04

Here's the output of the command:

  *-display               
       description: VGA compatible controller
       product: N10 Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:46 memory:f0200000-f027ffff ioport:30c0(size=8) memory:e0000000-efffffff memory:f0100000-f01fffff

---

### Post by pbpersson on 2012-02-18
Then we would need to know what is really in your computer or the brand and model number so we can Google what other people have done with your model of computer or graphic card to increase the resolution.

---

### Post by pbpersson on 2012-02-18
FYI, I was looking at the instructions on [this page]("https://help.ubuntu.com/community/BinaryDriverHowto")

Here are the questions which must be answered:

1.  What graphics card or chip is in your machine?
2.  Did Ubuntu install the correct driver?
3.  Is there a proprietary driver available in System->Administration->Hardware Drivers and have you tried that?
4.  If this does not help, what have other people done who are using your same hardware?

---

