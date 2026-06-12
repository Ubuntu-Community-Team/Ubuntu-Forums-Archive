---
title: "very low volume"
date: 2008-02-03
forum: Multimedia &amp; Video
---

### Post by coool on 2008-02-03
Hi people

I just installed ubuntu 7.10 on a dv2000 series hp laptop. I am completely new to linux.
I havent tested a lot of things but the installation went ok. I have this weird problem with the sound.

When i use my speakers, i get a very low volume. But when i plug in my headphones, I get full volume through my headphones. I dont understand why this is happening. Yesterday, I was running the live cd and i got full volume through the speakers. But now speaker volume is very low.

When I go to system -> sounds, there are 2 devices that I can select.
1) HDA Intel (Alsa Mixer)
2) Conexant CX20551 (Waikki) (OSS Mixer)

Can someone give me a few suggestions to tackle this problem?

---

### Post by BennBuntu on 2008-02-03
First thing to try
open up a terminal  (applications > Accessories > terminal).

type
```
alsamixer
```

This is the same as what you're doing, but it shows all the channels,  try adjusting them from there. If that makes a difference, you should be able to add those channels into the graphical mixer.

---

### Post by motoperpetuo on 2008-03-29
I just installed Linux Mint 4.0 on a Dell Inspiron 530n (one of the preinstalled Ubuntu machines). Volume was very low after the install, but this fixed it for me. For what it's worth, I had to increase the "Side" setting to max. No idea why "Side" and not "Center" or "Front" or any of the others, but hey, it's working now, so good enough.

btw, you use the right and left arrow keys to select a parameter, and then the up and down arrow keys to raise or lower the volume (that might save someone a minute or two of figuring).

---

### Post by jmullagh on 2008-04-04
I also installed Linux Mint... and this did it for me as well using a Compaq laptop (v3000 series)! Thank You     !:)

---

