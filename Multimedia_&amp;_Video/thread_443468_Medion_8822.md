---
title: "Medion 8822"
date: 2007-05-14
forum: Multimedia &amp; Video
---

### Post by ProMaster on 2007-05-14
Hi,

I've bought the ALDI Medion 8822 last month and now I'm trying to get the TV card to work. I yanked it out of the computer to see what kind it was and it read:

Medion TV/DVB-T Combo card
CTX953_V.1.4.3
p/n 20033283
Philips SAA7131E/03/G

Now I need to find out what the card type is according to SAA7134. When I look in DMESG I see that the card is identified as -2, but this is not correct because TVTIME doesn't give me anything.

Has anybody got this card to work and under what number?

Greetz, Paul.

---

### Post by ProMaster on 2007-05-20
Hurray!!! I found a website where they suggested using card=81. It works!!! I've got tellie on my Linux machine. Only the sound doesn't work yet. But hay, one down, one to go!

:popcorn:

---

### Post by Djoef on 2007-07-18
could you also say where you found this ?
i have also a medion tv -tuner card, but cant install it :)
tnx

---

### Post by rhllardie on 2007-08-07
please can you also say where you found this

---

### Post by ProMaster on 2007-10-29
Okay, I've been doing some digging again. Turns out the card works very well with card=96. But audio still is a problem.

---

