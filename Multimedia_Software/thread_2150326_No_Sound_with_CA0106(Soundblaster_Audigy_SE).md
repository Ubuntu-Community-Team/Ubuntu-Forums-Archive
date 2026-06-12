---
title: "No Sound with CA0106(Soundblaster Audigy SE)"
date: 2013-05-31
forum: Multimedia Software
---

### Post by wbee on 2013-05-31
Hello,

When I was using the previous LTS OS,a 32 bit version,the CA0106(Creative Soundblaster Audigy SE) sound card worked beautifully.

When I upgraded to 12.04 LTS,64 bit version,with a new build,I installed the sound card,disabled the Azalea Audio in the motherboard BIOS and got no sound at all with the card.

I went back into the BIOS,changed the setting to "AUTO" which lets me select between the card and the on-board sound from opening the speaker icon on the panel.

With the speakers fed from the motherboard light green out,with the setting  on-board audio,I'm getting sound. So the speakers and source(VLC) are working fine.

With the speakers fed from the card's light green out,with the setting on the sound card,nothing.

So,I used the terminal to go into the alsamixer,and nothing is muted and the outputs are fine on both card options.

I do not have Gnome-alsamixer installed. Is there any difference other than cosmetic?

What should I try next?

---

### Post by Yellow Pasque on 2013-06-01
> I do not have Gnome-alsamixer installed. Is there any difference other than cosmetic?
No.

> What should I try next? 
Try toggling Audigy Analog/Digital Output Jack in alsamixer. Also make sure you have the Audigy selected as the output in Ubuntu's sound control (or use pavucontrol).
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by wbee on 2013-06-01
Temüjin,

Thank you. The toggle to analogue solved the problem.

:-)

((Just an edit to bump the thread.))

---

