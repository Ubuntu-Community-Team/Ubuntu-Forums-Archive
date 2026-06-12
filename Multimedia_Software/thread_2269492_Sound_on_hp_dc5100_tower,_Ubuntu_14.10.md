---
title: "Sound on hp dc5100 tower, Ubuntu 14.10"
date: 2015-03-16
forum: Multimedia Software
---

### Post by LosAngelesNortheas on 2015-03-16
Yo so I recently installed ubuntu on my dc5100 hp tower asa dual boot with windows, basically need help to get the audio driver to work, I have tried crancking up the sound in stetings and in the alsa mixer as well... i have reinstalled alsa, no luck 


this is how my system detects the audio _ pentium@Ubuntu-1543:~$ lspci -v | grep -A7 -i "audio" 00:1e.2  Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW  (ICH6 Family) AC'97 Audio Controller (rev 03) 	Subsystem:  Hewlett-Packard Company Device 300d 	Flags: bus master, medium devsel,  latency 0, IRQ 21 	I/O ports at 1000 [size=256] 	I/O ports at 1400  [size=64] 	Memory at cfdc0400 (32-bit, non-prefetchable) [size=512] 	 Memory at cfdc0600 (32-bit, non-p

I tries everyhting in here --  except the manual instllation , i dont know where to find teh driver to try all of that...

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)


so if i get that messgage i posted above, does that mean the sound card is suported ? what else can i try??

---

### Post by Bucky Ball on 2015-03-16
*Thread moved to **Multimedia**.*

Welcome. You shouldn't need to install a driver manually for that. Ubuntu is not like Windows. Most of the drivers for generic hardware like sound are already in the kernel. 

Which release of Ubuntu are you using? Try installing Pulseaudio Volume control (pavucontrol in Software Centre) and seeing if you get more joy from that.

---

