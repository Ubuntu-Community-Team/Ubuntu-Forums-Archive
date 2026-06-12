---
title: "No sound from external speakers"
date: 2008-09-10
forum: Multimedia Software
---

### Post by Zarniwoop79 on 2008-09-10
Hello!

I can't seem to get any sound from my external speakers in Xubuntu 8.04 on my laptop (Fujitsu-Siemens Esprimo Mobile U9200).

The sound from the internal speakers works fine, but I can't get any sound from the external speakers (connected using a 3.5mm plug).

I've tried adding upgrading the alsa-libraries, but there seems to be something wrong. The headphones-bar is there but you can't set it to anything (it looks "empty").

I've checked the box for headphones, but nothing seems to help.

Does anyone know what could be wrong? It works in Windows XP, but I have the same problem in ZenWalk. It worked in Puppy Linux 4.00 aswell.

---

### Post by Zarniwoop79 on 2008-09-10
This is the output of lspci -v:

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
        Subsystem: Fujitsu Siemens Computers Unknown device 110f
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at fc400000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [70] Express Unknown type IRQ 0

---

### Post by Zarniwoop79 on 2008-09-11
Is there really noone out there who knows what could be wrong?

I've asked in other forums, but someone else must have had this problem?

---

### Post by Zarniwoop79 on 2008-09-12
Hello!

Still noone? Well I found something else.

I found a command "alsactl -names" which should list available soundcards, but it doesn't list anything. Is this a clue?

According to the alsamixergui the soundcards name is "Realtek ALC262".

---

### Post by markbuntu on 2008-09-13
If you are having problems with the HDA card/chip on your laptop you should look here:

[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

---

### Post by Zarniwoop79 on 2008-09-13
Hello!

Thanks a lot! It worked with the solution from there!
(editing /etc/modprobe.d/alsa-base).

---

