---
title: "ALSA having problems, I think."
date: 2007-03-12
forum: Multimedia &amp; Video
---

### Post by Commodore Guff on 2007-03-12
Hi, I'm pretty new to Ubuntu, as well as Linux in general, and I've been having some problems.
Whenever I try to run most music making programs (VKeyBd, Horgand, MusE), I get something like the following error:
"ALSA lib seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
horgand: seq.c:2185: snd_seq_create_port: Assertion `seq && port' failed.
Aborted (core dumped)"
or
"ALSA lib seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
ERROR: can't open sequencer device"

I am running Ubuntu Edgy, if that helps at all.

Thanks, and I hope I posted this in the right place.

---

### Post by Commodore Guff on 2007-03-13
Can anybody help? :(

---

### Post by pixeldotz on 2007-03-13
a little more info is needed. what kind of card do you have?

you might have to install the latest ALSA from the ALSA site with configurations suited for your site. this is not hard at all and we can walk you through it if we had some more info on your card.

---

### Post by Commodore Guff on 2007-03-13
> **pixeldotz said:**
> a little more info is needed. what kind of card do you have?

you might have to install the latest ALSA from the ALSA site with configurations suited for your site. this is not hard at all and we can walk you through it if we had some more info on your card.

Just the integrated audio.  [This]("http://www.foxconnchannel.com/EN-US/Product/motherboard_detail.aspx?id=en-gb0000139") is my motherboard, if it helps.

Thanks.

---

### Post by Commodore Guff on 2007-03-14
Hello?

---

### Post by cd7 on 2007-03-18
I fixed with:
```
sudo modprobe snd-seq
```

dario

---

### Post by Commodore Guff on 2007-03-19
> **cd7 said:**
> I fixed with:
```
sudo modprobe snd-seq
```

dario

Thank you for responding.
It allows MusE to start without any problems, which is good.  However, Horgand causes my machine to freeze completely, and Vkeybd does not seem to work.
Strike that last part.  Vkeybd does work.
Any help would be greatly appreciated.

---

