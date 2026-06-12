---
title: "Changed soundcard, how to set default"
date: 2006-02-11
forum: Multimedia &amp; Video
---

### Post by palomar on 2006-02-11
When I installed Kubuntu I was using the onboard soundcard on my mainboard. Now I've plugged in a SB Live PCI card. In the bios I have disabled the onboard sound, but I cant get the SB Live to work in Ubuntu.

The card is detected by Ubuntu. When i do lspci I see:

0000:00:0a.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)

But how can I set it as the default soundcard?

---

### Post by brucetan on 2006-02-11
do you which model no. of your SB Live card?  is it CT4730?

---

### Post by palomar on 2006-02-11
well, i don't know exactly. But I discovered that I did not have disabled the onboard card in the bios correctly. Now I have disabled it correctly and Ubuntu works with the SB Live automatically :-) 

So the card is detected well. But I still want to know how to choose which soundcard to use when there are 2 or more soundcards installed in a system. I tried commands like 'alsaconf' but that doesn't work.

---

