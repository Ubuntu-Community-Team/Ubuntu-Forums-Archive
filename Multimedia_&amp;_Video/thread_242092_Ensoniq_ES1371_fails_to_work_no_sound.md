---
title: "Ensoniq ES1371 fails to work: no sound"
date: 2006-08-23
forum: Multimedia &amp; Video
---

### Post by evadave on 2006-08-23
I have installed Ubuntu 6.06 LTS on an older box, a dual Pentium 3, and mostly everything works. The only thing which didn't work was sound and during bootup when loading hardware drivers the system hanged for up to a minute.

I searched around trying to get ALSA to find my sound card and tried to modprobe snd-ens1371 (the correct driver). I then finally removed the module first with rmmod and then modprobed' the module. This is what took so long on boot as the modprobe sits there for a long time, dumping this to syslog:

```

Aug 23 11:39:54 neon kernel: [ 1008.642628] codec read timeout (final) at 0x6f14, reg = 0x7c [0x0]
Aug 23 11:39:59 neon kernel: [ 1013.580939] codec read timeout (final) at 0x6f14, reg = 0x7e [0x0]
Aug 23 11:40:05 neon kernel: [ 1020.081947] codec read timeout (final) at 0x6f14, reg = 0x0 [0x0]
Aug 23 11:40:10 neon kernel: [ 1024.988226] codec read timeout (final) at 0x6f14, reg = 0x7c [0x0]
Aug 23 11:40:15 neon kernel: [ 1029.845731] codec read timeout (final) at 0x6f14, reg = 0x7e [0x0]
Aug 23 11:40:20 neon kernel: [ 1034.767096] codec read timeout (final) at 0x6f14, reg = 0x7c [0x0]
Aug 23 11:40:25 neon kernel: [ 1039.667657] codec read timeout (final) at 0x6f14, reg = 0x7e [0x0]
Aug 23 11:40:25 neon kernel: [ 1039.667679] AC'97 0 access is not valid [0x0], removing mixer.
Aug 23 11:40:25 neon kernel: [ 1039.681005] ENS1371: probe of 0000:00:10.0 failed with error -5
```

Eeeek. Anybody know why this would happen? Anybody know how to get my sound working? ](*,) 

lspci output:

```

0000:00:10.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 06)

```

Thanks in advance.

---

