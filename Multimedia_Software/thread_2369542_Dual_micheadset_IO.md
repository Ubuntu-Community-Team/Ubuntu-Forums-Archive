---
title: "Dual mic/headset I/O"
date: 2017-08-24
forum: Multimedia Software
---

### Post by steevi93 on 2017-08-24
I have a Toshiba Satellite C50-B-14D laptop dual boot laptop with Ubuntu  16.04 O/S and Windows 10.  It also has a shared mic/headphone port (1  port, dual I/O).  In Windows, it works fine.  In Ubuntu, it works  headphone only, but no mic input, which I need for my side project as an  internet radio DJ.

I tried playing around with the drivers, but this ended up killing all the sound, which I have managed to fix.

I have tried the hdajackretask, and set 0x18 and 0x19 as a microphone input, but it is still showing as unplugged.

Any advice or tips?  I really would like to use this in Linux and not have to use it in Windows if I can possibly help it.

---

### Post by bcschmerker on 2017-08-24
The sort of headset ye need uses a 3.5mm TRRS plug with, respectively, Left/Mono In, Right In, Ground/Common, and +3.6V In/Mic Out from tip to body.  Alternately, splitters are also available to port the outputs on your rig's 3.5mm TRRS jack to a standard 3.5mm TRS inline jack (usually green, but black is also encountered), and the input to a second standard 3.5mm TRS inline jack (usually pink, but red is also encountered) with the tip and ring jumpered.

---

### Post by steevi93 on 2017-08-25
So there's no way to enable the mic port in the O/S?

---

### Post by nik.charles on 2017-10-09
check audio settings in alsamixer as well as pulseaudio volume control.
quite common to find alsa level for microphone input muted by default, or some extra boost for microphone required

for internet dj streaming to icecast/shoutcast would be expecting you may be using JACK audio server too?

---

