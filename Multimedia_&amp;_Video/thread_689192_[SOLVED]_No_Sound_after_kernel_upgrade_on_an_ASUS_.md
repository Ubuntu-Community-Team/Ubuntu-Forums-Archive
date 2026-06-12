---
title: "[SOLVED] No Sound after kernel upgrade on an ASUS P5B Delux Motherboard"
date: 2008-02-06
forum: Multimedia &amp; Video
---

### Post by bergersau on 2008-02-06
After updating my kernel I no longer have sound.
I can boot the old kernel and sound works fine under the old kernel.

I'm thinking that the snd-hda-intel module is not present for my new kernel?
When I try to modprobe this module under the new kernel it's not present.

Here's the data that might help troubleshooting.

C'mon all you sound guru's I could use a hand please. 
 I'm not sure where to go from here to get this working.

Gutsy 7.10 Release

New kernel details
```
% uname -a                        
Linux VADER 2.6.22.9 #1 SMP Sat Dec 22 20:03:57 EST 2007 i686 GNU/Linux

```

```
%lspci -v

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
        Subsystem: ASUSTeK Computer Inc. Unknown device 81ec
        Flags: bus master, fast devsel, latency 0, IRQ 3
        Memory at febf8000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
```


With the old kernel.

```
%aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
```


With the new kernel

```
%aplay -l                      
aplay: device_list:204: no soundcards found...
```



```
% modinfo soundcore             
filename:       /lib/modules/2.6.22.9/kernel/sound/soundcore.ko
alias:          char-major-14-*
license:        GPL
author:         Alan Cox
description:    Core sound module
srcversion:     548AA54AF08207316C104F8
depends:        
vermagic:       2.6.22.9 SMP mod_unload CORE2 

  Subdevices: 1/1
  Subdevice #0: subdevice #0
```


```
%lsmod | grep snd 
%

```

---

### Post by daniel2501 on 2008-02-06
I have the same issue with my hda-intel card. I'll report back if I find a solution. Should report this on launchpad too...

---

### Post by bergersau on 2008-02-15
Resolved now.

My own stupid fault, I'd loaded the kernel I'd tried to compile myself several weeks earlier.
That kernel was poorly confiured by me.

](*,)

---

### Post by SuperAndy on 2008-04-17
so, does a generic kernel with hardy work with this board?

---

### Post by bergersau on 2008-04-17
I'd think so, the 'generic' kernel for Gutsy works fine.
The problem was that I'd failed to correctly compile support into my home rolled kernel.

Can't comment on Hardy Herron though as I'm still running Gutsy.

Dan

---

### Post by gantellus on 2008-05-03
No way I make the same card work on Hardy.
So I'm not sure whether the kernel in hardy is bugfree.

---

### Post by bergersau on 2008-05-04
Works fine on my fresh Hardy 32 bit install, generic kernel.

---

