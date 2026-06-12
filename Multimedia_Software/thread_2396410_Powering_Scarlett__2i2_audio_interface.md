---
title: "Powering Scarlett  2i2 audio interface"
date: 2018-07-15
forum: Multimedia Software
---

### Post by adamstar10 on 2018-07-15
Hello all,

I am using my  audio interface (Scarlett 2i2) to run my record player, the interface is powered through usb. The problem is that the interface only is powered when a audio output is sent from the computer, I need it to power the interface eventhough no output is coming from the computer, the record player has an external signal from the computer. Is there anyway to solve this? To have a constant powering of the interface instead of only when output is coming from the computer.

Thanks!

---

### Post by kazakore on 2018-07-17
I've used a number of Focusrite Scarlett interfaces and never had this issue, it should be powered as long as it's connected. Are there any USB power saving options in BIOS? Have you any Always On USB ports? This should just work.

---

### Post by adamstar10 on 2018-07-19
It's the power saving in BIOS I think this is due to, or something like that. I am not skilled enough to locate if there are any settings where I can set to power if connected and not just when output. 

Is there anyway I can see if I have some Power save mode on my USB-ports?

---

### Post by nik.charles on 2018-08-26
Most audio interface used with Pulseaudio will power-down if no audio streams present 

Simple way to prevent a USB interface powering down is keep pavucontrol open, even if minimised

Optimal way to use a audio interface like this is in JACK rather than Pulseaudio

JACK does not power-down interface

---

