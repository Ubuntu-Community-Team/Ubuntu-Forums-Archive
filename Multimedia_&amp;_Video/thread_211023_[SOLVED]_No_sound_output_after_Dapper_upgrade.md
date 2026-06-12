---
title: "[SOLVED] No sound output after Dapper upgrade"
date: 2006-07-07
forum: Multimedia &amp; Video
---

### Post by SPW06 on 2006-07-07
Hi

I just upgraded to dapper and everythink works exept sound output! I can still record. Aalso, PCMCIA failes at boot. Everything else works fine ](*,)

---

### Post by mlind on 2006-07-07
Hi,

can you check that your user belongs to **audio** group ?

To see the groups, type this on terminal
```

groups

```

---

### Post by SPW06 on 2006-07-07
yes, it does

---

### Post by mlind on 2006-07-07
Are there any muted channels?

---

### Post by SPW06 on 2006-07-07
no

---

### Post by mlind on 2006-07-07
Does *aplay /usr/share/sounds/phone.wav* work, but just no sound?

What's output of 
```

cat /proc/asound/cards

```

---

### Post by SPW06 on 2006-07-07
It plays,no sound 

0 [V8235          ]: VIA8233 - VIA 8235
                     VIA 8235 with VIA1612A at 0xe000, irq 5

---

### Post by SPW06 on 2006-07-07
Help?

---

### Post by LordRaiden on 2006-07-08
Go through my guide in my signature then post back.

---

### Post by SPW06 on 2006-07-08
**** List of PLAYBACK Hardware Devices ****
card 0: V8235 [VIA 8235], device 0: VIA 8235 [VIA 8235]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8235 [VIA 8235], device 1: VIA 8235 [VIA 8235]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

That's what I don't get.It shows up , notthing's muted and, it worked fine till apt-get dist-upgrade. Yes, I did update my my sources.list and ran apt-get update first.

---

### Post by walding on 2006-07-08
Hi,
I had this problem.  The cause was that the upgrade didn't update the grub menu.lst file with the new kernel, but was still booting the old kernel.  AS soon as I fixed this, sound returned.  Have you checked that?

---

### Post by lj269 on 2006-07-18
I also had this problem, followed the instructions in this post [http://www.ubuntuforums.org/showthread.php?t=205449](http://www.ubuntuforums.org/showthread.php?t=205449) and then noticed that only the front chanel in alsamixer was unmuted. Unmuted everything else and then had sound again, might have only needed to do the stuff in alsamixer...

---

