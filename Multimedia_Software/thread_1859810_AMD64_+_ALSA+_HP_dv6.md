---
title: "AMD64 + ALSA+ HP dv6"
date: 2011-10-14
forum: Multimedia Software
---

### Post by howcanireachthesekids on 2011-10-14
My laptop HP DV6-1020el.
uname -a
> Linux supernova 3.0.0-1-amd64 #1 SMP Sat Aug 27 16:21:11 UTC 2011 x86_64 GNU/Linux
lspci output
[http://pastebin.com/Q9ntXAFe](http://pastebin.com/Q9ntXAFe)

How do I get  my sound card to work? I tried many solutions.
How do I find what is my exact model to add to alsa-base.conf?
I tried
> options snd-hda-intel model=hp-dv6 enable_msi=1based on some guides I found online. rebooted, and the sound button in the laptop went from orange(disabled) to white(enabled). still no sound. now I removed that line and it is orange again, and no sound of course.

Any help here?
Greatly appreciated!

---

### Post by collisionystm on 2011-10-14
Open Terminal

alsamixer

Look at top for what kind of card

I.E. Mine says

 Card: HDA Intel                                      F1:  Help               &#9474;
&#9474; Chip: Realtek ALC662 rev1  



do you see anything with MM under the barS?

if so, use the keyboard to move over to it and hit the M on your keyboard. This will unmute it.

---

### Post by howcanireachthesekids on 2011-10-14
> **collisionystm said:**
> Open Terminal

alsamixer

Look at top for what kind of card

I.E. Mine says

 Card: HDA Intel                                      F1:  Help               &#9474;
&#9474; Chip: Realtek ALC662 rev1  



do you see anything with MM under the barS?

if so, use the keyboard to move over to it and hit the M on your keyboard. This will unmute it.
That did it! I want to give you a big hug right now =D>
Marking as solved.

---

