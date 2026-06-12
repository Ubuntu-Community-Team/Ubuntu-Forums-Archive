---
title: "No sound in Edgy after AC97 driver install"
date: 2007-02-19
forum: Multimedia &amp; Video
---

### Post by josno on 2007-02-19
Hi,

My sound stopped working after I tried to install the Realtek AC97 drivers for my sound card (on an nVidia nForce4 motherboard). I reinstalled libasound2 but that didn't solve my problem. I then followed the steps in the [Comprehensive Sound Problem Solutions Guide](http://ubuntuforums.org/showthread.php?t=205449) sticky. After working through it, I eventually got to the ALSA driver Compilation stage which went ok. However, going back to general step 4, after pressing enter on sudo modprobe snd-intel8x0 nothing happens - it asks me for my password and then seemingly does nothing for a long time. I ctrl-c out of it in the end. aplay -l still says "aplay: device_list:222: no soundcards found..."

Can anyone help?

Thanks

---

### Post by josno on 2007-02-22
Can anyone shed any light on this?

---

### Post by josno on 2007-02-22
Ok, well I've tried the ac97_quirks thing and that doesn't seem to make any difference (tried 0-4 rebooting each time). Interestingly, I've found if I boot into 2.6.17.10 the sound works perfectly, so it's just in 2.6.17.11 it doesn't work. Unfortunately I have no idea what that means :p

---

### Post by briguy on 2007-02-27
Same here with sound broken in the new kernel.  Intel i810 sound card in a Gateway 200 laptop.

---

### Post by omyar on 2007-03-03
Got the same problem here after the kernel upgrade. I'm using a 82801G (I think) sound card on a thinkpad x60. I think it uses a similar driver to eh i810.

---

