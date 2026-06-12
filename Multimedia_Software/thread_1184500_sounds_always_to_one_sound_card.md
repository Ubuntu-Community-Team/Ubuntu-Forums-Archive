---
title: "sounds always to one sound card"
date: 2009-06-11
forum: Multimedia Software
---

### Post by davidtuti on 2009-06-11
Hi,

I've installed Kubuntu 9.04 and I have two sounds cards: a sound blaster and the integrated realtek.

```
david@defekas:~$ grep -i live .asoundrc.asoundconf
david@defekas:~$ cat /proc/asound/cards
 0 [Live           ]: EMU10K1 - SBLive! Value [CT4832]
                      SBLive! Value [CT4832] (rev.8, serial:0x80271102) at 0xe880, irq 18
 1 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf9ff8000 irq 22
```

When I go to sound and press Test runs fine the two cards.

When I try to open a movie with vlc always sounds by the sound blaster.

I try to do:
sudo asoundconf set-default-card Intel

But the sounds always goes to the sound blaster.

Please any help?

Many thanks!

---

### Post by davidtuti on 2009-06-11
Hi again,

I realized that when I do:

asoundconf set-default-card Intel, 

The system doesn't change the sound to this card but if I reboot it's ok. 
Likewise If I do: 

asoundconf set-deafult-card Live 

When I reboot it works but I need to reboot :(

Any help?

Thanks and sorry for my english!

---

