---
title: "Creative Lab's Soundblaster Audigy 2"
date: 2006-06-10
forum: Multimedia &amp; Video
---

### Post by spikedupback529 on 2006-06-10
Hi,
I started off linux on a Dell laptop with Breeze Badger, and the sound was fine. I put it on my computer, and no sound! I have, as suggested, a creative lab's soundblaster audigy 2 sound card. I upgraded to Dapper Drake with still no luck. Any suggestions?

Thanks,
Dale

---

### Post by _simon_ on 2006-06-10
Yes :)

From Terminal, type alsamixer

Right, I have an Audigy 2 ZS Value (same as ZS but with 2 less ports I believe) with 5:1 surround sound speakers and have the following set:

Master
Bass
Treble
PCM
Front
Surround
Center
Audigy A (turned on - press M on your keyboard)

Also, if your motherboard has onboard sound then you will need to go into your BIOS and turn that off.

---

### Post by _simon_ on 2006-06-10
sorry - double post

---

### Post by spikedupback529 on 2006-06-10
thank you so much!

---

### Post by spikedupback529 on 2006-06-11
I had to restart Ubuntu because of some updates, and the sound settings were back to the default. I followed the instructions again, and the sound works now. Anything I could do to make those settings default or something?

Thanks
Dale

---

