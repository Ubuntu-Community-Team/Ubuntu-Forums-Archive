---
title: "Realtime compiled Kernel: CPU always busy???"
date: 2006-10-28
forum: Multimedia &amp; Video
---

### Post by alamet on 2006-10-28
Hi all!
I have compiled a 2.6.18 kernel with the realtime patch 2.6.18-rt5, following all the instructions in the ubuntustudio tutorial.
When I use this kernel (I have a Kubuntu Edgy OS) the system is very slow, the cpu is almost busy...
I launched top, and I saw that **hald** was using 75% of resources...
So I launched dmesg, and that's the output:
SA PCIC probe: not found.
[  547.831809] Intel ISA PCIC probe: not found.
[  547.935983] Intel ISA PCIC probe: not found.
[  548.007792] Intel ISA PCIC probe: not found.
[  548.089994] Intel ISA PCIC probe: not found.
[  548.171794] Intel ISA PCIC probe: not found.
[  548.251696] Intel ISA PCIC probe: not found.
[  548.333506] Intel ISA PCIC probe: not found.
and that messages go on and on... idem in the kernel log

Maybe I require some other patches? :confused: 
Really thanks

---

### Post by andy.lamble on 2006-11-03
I had the same problem - it was caused by the PCMCIA module being executable and trying but failing to be started.. I dont have PCMCIA on this machine. Stopped the service from starting and the message goes away and cpu usage returns to normal. Just need to get ALSA working again now....

---

