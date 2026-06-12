---
title: "MythTV and Hauppauge  HVR-1250 not working?"
date: 2011-05-25
forum: Multimedia Software
---

### Post by JD32 on 2011-05-25
So ive been doing alot of reading (and yes ive searched all i can before asking) but i cant seem to get my HVR-1250 card working with mythTV, my system see's it but i cant get myth TV to recognize it? it doesnt come up in the "probed info" in the backend, do i have to just plug in the right info and not worry about that or what? 

sudo lshw -C multimedia output: 


```
*-multimedia
       description: Multimedia video controller
       product: Hauppauge Inc. HDPVR-1250 model 1196
       vendor: Conexant Systems, Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 04
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress pm vpd msi bus_master cap_list
       configuration: driver=cx23885 latency=0
       resources: irq:17 memory:fe800000-fe9fffff

```


ubuntu 10.04 32 bit
AMD Atholon dual core

---

### Post by wolfen69 on 2011-05-25
I know that during setup, you need to choose the correct firmware from a pull down menu.

---

### Post by JD32 on 2011-05-26
> **wolfen69 said:**
> I know that during setup, you need to choose the correct firmware from a pull down menu.

What setup? in MythTV or setup for the actually card?... when i plugged it in there was no setup?

---

### Post by wolfen69 on 2011-05-26
> **JD32 said:**
> What setup? in MythTV or setup for the actually card?... when i plugged it in there was no setup?

In the MythTV setup.

---

### Post by poe503 on 2011-05-27
Have you seen my tutorial? [[COLOR="Green"]http://ubuntuforums.org/showthread.php?t=1648472[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1648472")

Is your card recognized in the manner I have described?

---

