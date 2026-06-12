---
title: "686 kernel does not support network devices which the default 386 kernel does"
date: 2006-06-07
forum: Networking &amp; Wireless
---

### Post by one0 on 2006-06-07
I have 6.06 running on my thinkpad t60p. the default kernel supports my wireless chipset, but the 686 kernel which correctly identifies both cores of the centrino duo (the default kernel does not) does not work with the Intel WM3945AG wireless adapter. 

I haven't tried out the wired Intel PRO/1000 MT Mobile Ethernet to see if it works under either kernel. 

It would be really nice if both kernels, or at least the smp-aware 686 kernel package supported the 3845 like the default kernel does. I realize I can compile my own, but for ease of package maintenance, it would be fantastic if the standard supported kernels supported it all. 

I'm opting to stick with a single core and working networks... but I'd really like it if I could have my cake and eat it too, without compiling my own kernel. 

If I'm missing something, I hope somebody out there will set me straight.

Thanks,
Adam

---

### Post by one0 on 2006-06-07
replying to my own thread, i have figured out that installing the restricted 686 kernel package solves the problem... now the networking works and so do both processors. 

no wonder i only have one bean so far. :-)

---

### Post by ltmon on 2006-07-14
You may only have one bean, but you've saved this "Dipped in Ubuntu" user a whole lot of trouble.

Thanks for the tip, it's got my brand new Asus Z96J working just right :)

L

---

