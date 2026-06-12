---
title: "Freshly built sound module still won't insert"
date: 2007-02-06
forum: Multimedia &amp; Video
---

### Post by trevva on 2007-02-06
Hello,

I'm trying to get the sound working on a freshly installed version of Fluxbuntu (Ubuntu 6.05 LTS (Dapper) is the core of this distribution) on a Compaq Armada 3500 with a built in ESS1869 audiodrive soundcard.

Previous attempts to get this working came close, and even worked on one occasion, but somewhere along the line I messed it all up. After numerous attempts at fixing it, I gave up and reinstalled it afresh. Here is what  I have done since.

1. Configured apt-get to the dapper repositories
2. Upgraded the kernel to 2.6.15-27.686
3. Followed the instructions in the Ubuntu comprhensive sound problems guide:
[http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide]("http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide")

I was unable to see the card via either aplay-l, or lspci (it is a isa on-board chip). I then skipped over the "get drivers from a fresh kernel" section - my kernel and install was fresh, after all, and proceeded on to driver compilation using alsa-source and module-assistant. Everything ran fine, and there were no errors whatsoever - striaght through, first time.

When the module assistant had finished running, I ran lsmod and noted that the alsa, snd and snd-es18xx modules were all installed and looked to be running fine. I then rebooted the machine and attempted to insert the snd-es18xx module to get everything up and running so I could test the sound - unfortunately, it didn't work - all I get now when running sudo modprobe snd-es18xx is the error:
```

FATAL: Error inserting snd_es18xx (lib/modules/2.6.15-27-686/updates/alsa/isa/snd-es18xx.ko): No such device
```

Why won't it insert? Clearly rebooting without testing the sound was a mistake, but how do I get back that point where all the modules were inserted and appeared to be working fine?

Cheers,

Mark

---

### Post by trevva on 2007-02-06
Here's a bit more info that may or may not be helpful.

I'm trying to load the module at run time - I have it listed in /etc/modules. However, it doesn't seem to do that, as you can see from the following code:
```
mark@mark-laptop:~$ dmesg | grep alsa
[17179612.920000] ALSA /usr/src/modules/alsa-driver/isa/../alsa-kernel/isa/es18xx.c:1702: es18xx: unable to grap ports 0x0-0xf
[17179612.924000] ALSA /usr/src/modules/alsa-driver/isa/../alsa-kernel/isa/es18xx.c:2196: ESS AudioDrive ES18xx soundcard not found or device busy

```

Can anyone tell me what "unable to grap ports 0x0-0xf" might mean? It is loading the rest of the sound modules though....:

```
mark@mark-laptop:~$ lsmod | grep snd
snd_pcm               108388  0 
snd_page_alloc         11912  1 snd_pcm
snd_opl3_lib           12928  0 
snd_timer              28516  2 snd_pcm,snd_opl3_lib
snd_hwdep              10464  1 snd_opl3_lib
snd_mpu401_uart         8928  0 
snd_rawmidi            28288  1 snd_mpu401_uart
snd_seq_device          9644  2 snd_opl3_lib,snd_rawmidi
snd                    69324  7 snd_pcm,snd_opl3_lib,snd_timer,snd_hwdep,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore              10784  1 snd
mark@mark-laptop:~$ 

```

Any ideas?

Mark

---

