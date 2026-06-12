---
title: "No sound on Laptop HP Compaq 6735s ?"
date: 2013-06-22
forum: Multimedia Software
---

### Post by Fred Le Rouge on 2013-06-22
Hello everyone,
I recently installed Lubuntu 13.04 64 bits on a friend's laptop HP Compaq 6735s but there is no sound. There is sound from the headphones but not from the integrated speakers. We found a lot of similar problems on the internet but the proposed solutions did not work for his laptop. Indeed most of the solutions date back from Ubuntu 8.04 or 8.10.
Here are some informations about the sound card :

HDA ATI SB
AD198x Analog
AD1984A
SBx00 Azalia (Intel HDA)
Analog Devices ID 194a
LSI ID 1040

Could you help us please?

---

### Post by Fred Le Rouge on 2013-06-23
I tried what is explained here [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) but it did not work.
I modified the file /etc/modprobe.d/alsa-base.conf by adding ```
options snd-hda-intel model=mobile
``` or ```
options snd-hda-intel model=laptop
``` at the end, I rebooted but it did not work.
Any idea?

---

### Post by Fred Le Rouge on 2013-07-03
Problem solved ! I installed Lubuntu 12.04 and then updated to 12.10 and  13.04 and it worked ! I remembered that the parameters worked in 12.04  so I updated gradually to 13.04 so that the sound parameters would not  change.

---

