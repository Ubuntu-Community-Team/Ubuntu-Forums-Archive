---
title: "Cant get bulit in video card working!( I cant tell what it is!)"
date: 2008-12-13
forum: Multimedia Software
---

### Post by Dwiman89 on 2008-12-13
Hey,
   I recently installed ubuntu 8.10 on a friends computer. Its working fine as far as I can tell, other then I cant get any video acceleration or effects because of the video card. Its built in to the mother board as far as I can tell. The processor is AMD(although ubuntu wont tell me exactly what it is ether)  

As  far as I can tell its probably using vesa drivers. I had to manually configure xorg.conf to even get it off a 800x600 resolution. because any higher resolution wasnt available...

Even it may not be fully supported by ubuntu is there a way I can at least tell what the video card is in order to TRY to get it to work?

Im not used to these kind of issues because my video card is nvidea and works fine....

Thank you.

---

### Post by cariboo on 2008-12-13
To tell what cpu you computer is running in a terminal type:

```
cat /proc/cpuinfo
```

To find out what type of video adapter the motherboard has, in a terminal type:

```
lspci | grep VGA
```

it will print out something similar to this:

```
lspci | grep VGA
03:00.0 VGA compatible controller: nVidia Corporation GeForce 8400 GS (rev a1)
```

and also in the same terminal:

```
sudo lshw -C video
```

the output should look something like this:

```
 sudo lshw -C video
[sudo] password for jim: 
  *-display               
       description: VGA compatible controller
       product: GeForce 8400 GS
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=nvidia latency=0 module=nvidia
```

Jim

---

### Post by Dwiman89 on 2008-12-14
Okay it just says AMD Athlon Processor(MHz 1300.037

and for the video card it says its a;

s3 Inc. ProSavage KM133 (rev 03)


Is there any hope of getting video acceleration and getting this stuff working better?

---

