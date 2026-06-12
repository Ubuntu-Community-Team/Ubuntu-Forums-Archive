---
title: "Why NVidia Quadro 4000 shown as GF100 on Ubuntu 10.04 LTS?"
date: 2012-05-04
forum: Multimedia Software
---

### Post by NCMS on 2012-05-04
On Ubuntu 10.04 LTS WHY the NVIDIA Quadro 4000 showen as GF100? ;
 
**lspci**
 
>> 0f:00.0 VGA compatible controller: NVIDIA Corporation GF100 [Quadro 4000] (rev a3)
 
>> 0f:00.1 Audio device: NVIDIA Corporation GF100 High Definition Audio Controller (rev a1)
 
 
**lshw**
 
*-display
description: VGA compatible controller
**[COLOR=red]product: GF100 [Quadro 4000][/COLOR]**
vendor: NVIDIA Corporation
physical id: 0
bus info: pci@0000:0f:00.0
version: a3
width: 64 bits
clock: 33MHz
capabilities: bus_master cap_list rom
configuration: driver=nvidia latency=0
resources: irq:24 memory:ec000000-edffffff memory:e0000000-e7ffffff(prefetchable) memory:e8000000-ebffffff(prefetchable) ioport:e000(size=128) memory:ee080000-ee0fffff(prefetchable)
*-multimedia UNCLAIMED
description: Audio device
product: GF100 High Definition Audio Controller
vendor: NVIDIA Corporation
physical id: 0.1
bus info: pci@0000:0f:00.1
version: a1
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list
configuration: latency=0
resources: memory:ee000000-ee003fff

---

### Post by BicyclerBoy on 2012-05-04
That is what it is...
Quadro 4000 is similar to GTX480M or a slower GTX460.

The pro-cad cards where/are basically the same hardware.
Possibly reconfigured by micro-code/firmware & driver.

The rumour is that the pro-cad cards windows openGL drivers are better.
But it could just be mutual back-scratching by Autodesk SolidWorks & the video card vendors.

[http://en.wikipedia.org/wiki/Comparison_of_Nvidia_graphics_processing_units#Quadro](http://en.wikipedia.org/wiki/Comparison_of_Nvidia_graphics_processing_units#Quadro)

---

### Post by NCMS on 2012-05-04
THANK YOU 
 
So need not to worry then  :lolflag:

---

