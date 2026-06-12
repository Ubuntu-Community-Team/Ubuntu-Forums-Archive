---
title: "No Sound on netbook. need assistance."
date: 2010-12-24
forum: Multimedia Software
---

### Post by ramse4 on 2010-12-24
i'm an ubuntu noob so when I installed ubuntu 10.10 on my new asus eeepc, I followed the sticky sound problem post when I coudln't get any sound but to no avail. 

I followed the first few steps and found it saying

```
card 0: Intel [HDA Intel], device 0: ALC259 Analog [ALC259 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

```
Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
    Subsystem: ASUSTeK Computer Inc. Device 841c
    Flags: bus master, fast devsel, latency 0, IRQ 46
    Memory at f7cf8000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel
```

I assumed it was the driver was hda-intel, and the snd thing didnt work so I tried to do all the alsa driver compilation however it failed and I recieved the error:

```
 &#9474; In file included from include/linux/pci.h:58,                               
 &#9474;                  from /usr/src/modules/alsa-driver/acore/memalloc.inc:13,   
 &#9474;                  from /usr/src/modules/alsa-driver/acore/memalloc.c:1:      
 &#9474; /usr/src/modules/alsa-driver/include/linux/pci_ids.h:2: fatal error:        
 &#9474; @CONFIG_SND_KERNELSRC@/include/linux/pci_ids.h: No such file or directory   
 &#9474; compilation terminated.                                                     
 &#9474; make[5]: *** [/usr/src/modules/alsa-driver/acore/memalloc.o] Error 1        
 &#9474; make[4]: *** [/usr/src/modules/alsa-driver/acore] Error 2                   
 &#9474; make[3]: *** [_module_/usr/src/modules/alsa-driver] Error 2                 
 &#9474; make[3]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'       
 &#9474; make[2]: *** [compile] Error 2                                              
 &#9474; make[2]: Leaving directory `/usr/src/modules/alsa-driver'                   
 &#9474; make[1]: *** [build-stamp] Error 2                                          
 &#9474; make[1]: Leaving directory `/usr/src/modules/alsa-driver'                   
 &#9474; make: *** [kdist_image] Error 2
```  

any help would be appreciated

---

### Post by Chronon on 2010-12-24
Check your mixer levels both in pavucontrol and alsamixer.  Maybe your outputs are just muted.

(Sorry if you tried this already.  It's not too clear exactly what you did already.)

---

### Post by ramse4 on 2010-12-24
Sorry for being a bit vague. From that sticky([SIZE=2][COLOR=navy]_**[B]Comprehensive Sound Problem Solutions Guide)**[/B]_[/COLOR][/SIZE] I basically did steps 1-4 on the general help section. In addition I followed the directions in the [SIZE=1]_**Getting the ALSA drivers from a *fresh* kernel**_[/SIZE][SIZE=2] section and [/SIZE][SIZE=1]**_ALSA driver Compilation_ **section. [SIZE=2]I also did try out looking at the alsamixer but none were muted/turned to 0, so I'm stumped as to what to try next. [/SIZE]
[/SIZE]

---

### Post by ramse4 on 2010-12-24
I just installed PulseAudio Volume Control and while when I play a video, say on youtube, the section with the output shows that the computer is reading that sound is being used. 

However, the computer still doesnt seem to be outputting any sound.

---

### Post by lidex on 2010-12-25
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

