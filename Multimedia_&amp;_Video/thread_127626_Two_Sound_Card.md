---
title: "Two Sound Card"
date: 2006-02-09
forum: Multimedia &amp; Video
---

### Post by Heavy_Master on 2006-02-09
Hi everyone!

I've got two different sound card on my desktop pc (OB and PCI): The PCI one isn't supported (Creative X-FI Xtreme Music), the OB one is on a K8V-X motherboard.  How can I make the sound system know that he should use the OB card?

Thanks!

---

### Post by maxdevis on 2006-02-09
disable the onboard soundcard in your bios

---

### Post by Heavy_Master on 2006-02-09
No I can't because the PCI one isn't supported (It's a Creative XFI). I would like to know a SOFTWARE method to choose the card to use.

---

### Post by maxdevis on 2006-02-09
did you try?

---

### Post by FarEast on 2006-02-10
Hi Heavy Master,
Does the on-board one appear when you execute the command?
$ cat /proc/asound/cards

If it does not, it may be on ISA bus.  Do you know which sound chip it is?

---

### Post by Heavy_Master on 2006-02-10
Wait a sec :) : I've no problem with the OB card, but since I've been plugged in the new pci card it stops working. 

I only need to find a way to choose the card which I want to work! What can I do? (Please don't say that I've to unplug the pci device :D:D:D)

The PCI card is a XFI and I'm using it as a 5.1 sound system support on windows (Call of Duty II sounds better on 5.1 than on a 2.0 ;))

---

### Post by FarEast on 2006-02-10
> I've no problem with the OB card, but since I've been plugged in
> the new pci card it stops working. 

I see, Heavy Master.
Describe the following in /etc/modprobe.d/sound , execute
'sudo update-modules' and restart the system.

options *module name for on-board sound chip* index=0

---

### Post by Heavy_Master on 2006-02-12
Argh, Damned italian internet providers...

Thank you FarEast now everything "sounds :) " good!

---

### Post by FarEast on 2006-02-12
I'm glad to know that.
Oh, you live in Pisa... Thanks to Italy for the wonderful olympic games!

---

### Post by krol on 2006-05-28
hi i have got the same problem (also x-fi card but different motherboard - asus a8v)  could you explain more user friendly how to enable my onboard sound, card sorry but i am a newbie in linux

---

### Post by viz_e on 2006-05-28
No way to get the X-fi working?

---

### Post by krol on 2006-05-28
**May 18, 2006 -- Creative plans to make proprietary (closed source) drivers available for the X-Fi series of sound cards in the second quarter of 2007. These drivers will have full support for ALSA (playback, recording, mixer, MIDI, synthesis) and OpenAL 1.1 (with EAX effects).**
Thats from creative website and they will not help people from ALSA project to build opensource drivers as far as i know.

---

### Post by cLawhammer on 2006-07-19
> **krol said:**
> hi i have got the same problem (also x-fi card but different motherboard - asus a8v)  could you explain more user friendly how to enable my onboard sound, card sorry but i am a newbie in linux

I have this motherboard to.
It disables the onboard ac97 when detect the x-fi. This mode can't be changed in bios ( At least in the official bios published by ASUS )
Yes, this is a [COLOR="White"]stupid[/COLOR] limitation. ](*,) ](*,)

---

