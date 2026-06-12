---
title: "Nvidia and nouveau cause xorg crash with sigbrt"
date: 2014-07-06
forum: Multimedia Software
---

### Post by billybigpotatoes on 2014-07-06
Hi guys. I haven't posted here before but I've been using Ubuntu now for about four years and I've loved every minute of it. But recently (ever since the upgrade to 14.04) I've had real trouble with a total crash that happens occasionally (once every three or four hours) when using the internet. Essentially the screen freezes and even the cursor won't move. Ctrl Alt F1 won't even work and I'm forced to press the power off switch. When the little box pops up the next time I switch it on, it informs me of an xorg crash with sigbrt which I don't really understand. I've tried changing the graphics drivers to other open source and proprietary ones but then I am faced with a really low resolution which I can't seem to change. I've taken a look online and can't find anybody with similar problems with the most recent edition of ubuntu (although apparently it was quite a common problem in ubuntu 12). Has anyone got any good advice for me in terms of solving this problem or coming up with some good workarounds? I'm happy to use the terminal although I'm by no means an expert. Any advice would be really really appreciated. 

All the best and thanks in advance for your help

Jon.

---

### Post by kc1di on 2014-07-06
Hi Jon and welcome to the forums,

You should file a bug report first off.  
Secondly - can you give the output of the this terminal command so we know which card your talking about:
```
lspci -v
```

may be able to help. 
Which drivers have you tried so far?

---

### Post by billybigpotatoes on 2014-07-06
Thanks for the fast response! Ok here is the relevant part for lspci 
01:00.0 VGA compatible controller: NVIDIA Corporation GT216 [GeForce GT 220] (rev a2) (prog-if 00 [VGA controller])
    Subsystem: NVIDIA Corporation Device 069a
    Flags: bus master, fast devsel, latency 0, IRQ 46
    Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    Memory at ce000000 (64-bit, prefetchable) [size=32M]
    I/O ports at dc00 [size=128]
    Expansion ROM at fbc80000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel driver in use: nouveau
I've filed a bug report too, but to no avail. Basically, the next time I turn it on after a crash I get the screen 'Ubuntu has experienced an internal error. Would you like to file a bug report' which I have done many times. I have the crash report filed in /var/crash but its really very very long. Over 5000 lines. I can send this as well if you think it will be handy. Lastly, thanks very much for your time on this, I'll be eternally in your debt if you can help me sort this out!

---

### Post by billybigpotatoes on 2014-07-06
As for the other drivers, I've tried the following and had the same problem with all of them; terrible screen resolution, which I can't seem to fix in the screen resolution menu (found in display). 
Nvidia proprietary drivers 331.38, 304.117.

---

### Post by kc1di on 2014-07-06
According to Nvidia the 331(the latest one out is 331.89, but you'd have to manually install it.)  driver should work.  Once you install it you no longer use the Ubuntu display setting but Nvidia's - there should be a Nvidia settings option added to you systems menu.

---

### Post by billybigpotatoes on 2014-07-06
Wow, I'm sure I tried this before and the screen resolution was all messed up, but this time it seems to have worked like a treat. No doubt its my own stupidity! Many thanks for your help and patience kc1di, now I'll just have to cross my fingers and hope those nasty crashes are a thing of the past. 

Thanks once again man!

---

### Post by kc1di on 2014-07-06
Good Luck -- :)

---

