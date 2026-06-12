---
title: "Burning dvd from iso problem"
date: 2007-01-21
forum: Multimedia &amp; Video
---

### Post by lryer on 2007-01-21
I'm having a problem burning dvds from iso files (created with qdvdauthor and mkisofs. This has happened with several different iso files. Programs seem to lock up when preparing to burn. After either cancelling or kill process my system monito shows the growisofs process as "uninterruptible" and can't be killed without a reboot (logout doesn't do it). Both k3b and gnomebaker.
My latest attempt was direct from the terminal:
```
growisofs -dvd-compat -speed=4 -Z /dev/dvd=xxxx.iso
```
This has hung at:
```
Executing 'builtin_dd if=xxxxx.iso of=/dev/dvd obs=32k seek=0'
```

This was the same message that the other programs hung on.
Any suggestions?

Burning data dvd and audio cds seems to work fine...
Any assistance appreciated!

---

### Post by bruenig on 2007-01-21
That is the right command, perhaps that particular iso is messed up. The dvd drive is not /dev/dvd usually but is /dev/hd(something). You probably just put /dev/dvd to indicate that it was your dvd drive but if you didn't, that would be the problem.

---

### Post by lryer on 2007-01-23
I completely rebuilt the iso, but have the same problem (this time with k3b).

---

### Post by lryer on 2007-01-29
While trying to figure this out I stumbled across KMediaFactory. It works great with k3b!

---

