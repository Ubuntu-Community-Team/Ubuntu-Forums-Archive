---
title: "no sound on ASUS P5GD1"
date: 2005-11-12
forum: Multimedia &amp; Video
---

### Post by thede on 2005-11-12
I have put Breezy on motherboard P5GD1-VM, but no sound.

From the manual, reference is made Realtek ALC861 audio driver (in reference to Widows OS).

Has anyone been in similar situation?

Thanks, Thede

---

### Post by spizkapa on 2005-11-12
I don't have the card so I can't tell you whether it will work. However, there are a couple of things you can do to find out:

1. check out the Linux hardware compatibility guide on [http://tldp.org/]("http://tldp.org/") to see if your card is supported by the kernel

2. look at /var/log/messages to see any messages regarding the card

3. the dmesg command should repeat some of the bootup messages for you to see if the card is seen

4. get a decent mixer app (alsamixer is a good one) and turn on all sound. This is in case you actually have sound but can't hear it.

5. always try sound with something simple, like a cd. It may be the case that you haven't set up playing dvds, mp3s etc

Good luck.

---

### Post by rogelin on 2006-04-24
did you solve the problem?


[QUOTE=thede]I have put Breezy on motherboard P5GD1-VM, but no sound.

From the manual, reference is made Realtek ALC861 audio driver (in reference to Widows OS).

Has anyone been in similar situation?

Thanks, Thede[/QUOTE]

---

