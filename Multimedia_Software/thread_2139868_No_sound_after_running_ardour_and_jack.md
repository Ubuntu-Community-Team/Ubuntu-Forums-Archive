---
title: "No sound after running ardour and jack"
date: 2013-04-28
forum: Multimedia Software
---

### Post by Warlon on 2013-04-28
Hi,

I installed ardour and jack sound server and sound is working fine in ardour, but I get no sound from any other app. Stopping jack with qjackctl does not help either. Only thing that helps is a reboot. It seems that jack reserves the sound card for itself or something like that, so how can I restore sound without rebooting?

I'm running 13.04.

---

### Post by Kylerobhew1 on 2013-04-28
Try 'dpkg-reconfigure -p high jackd'

---

### Post by Warlon on 2013-05-26
> **Kylerobhew1 said:**
> Try 'dpkg-reconfigure -p high jackd'

Tried this. Did not help. Any other suggestions?

---

### Post by yamagami on 2013-06-02
Had the same problem - jackd is still running.  
In a shell run: 

```
ps -Af | grep jack
```

Find the process id of jackd and kill it

That should do it.

---

### Post by marcelwally on 2013-09-15
Hi everybody ! I used to work with Ardour under 12.04. I couldn't listen to other app's sound while I was using Ardour (and therefore Jack).But when I left Ardour, everything was ok, no need to reboot. When I upgraded to 12.10 it began to keep on blocking other app's sound even after Ardour was closed. I moved to 13.04 hoping that this new problem would be solved. But no ! I tried to close Jack but it is still with no sound. What happened ? Why jack follows on now whereas it was not doing it on 12.04 ? Mysteries...

---

### Post by rudolfbyker on 2013-10-06
I have the exact same problem. No process named anything similar to "jack" is running...

---

