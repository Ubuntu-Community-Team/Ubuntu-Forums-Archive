---
title: "Interesting sound problem"
date: 2007-11-06
forum: Multimedia &amp; Video
---

### Post by Liberi on 2007-11-06
Err...this is interesting. My ATi SB450 card, by all means, *should* be working fine. It's unmuted, properly installed (as far as I can tell), my account has the proper rights, and higher then 0% volume.

But there's no sound. At all. Any fixes for this for Gutsy?

And for the record, I **have tried** the "sudo rmmod snd-hda-intel // sudo modprobe snd-hda-intel probe_mask=8 mode=auto" fix...and that broke the sound. I also know it should be working thanks to the Sound Guide.

---

### Post by FNDII on 2007-11-06
Is this ATi SB450 a PCI card? Try plugging the speaker cord into the onboard sound card. 

I had a problem in feisty where the sound would jump from card to card at will. Now in gutsy the problem is back and I cant fix it.

---

### Post by Liberi on 2007-11-06
It's onboard, but so are the speakers. Gateway MT3707 laptop.

Tried the headphone trick, and still nothing (plug in headphones, listen to what comes out)

---

### Post by FNDII on 2007-11-06
You said you tried,
I have tried the "sudo rmmod snd-hda-intel // sudo modprobe snd-hda-intel probe_mask=8 mode=auto" fix...and that broke the sound

What was the original problem that prompted you to try that fix?

---

### Post by Liberi on 2007-11-06
All lights green, but no sound what-so-ever. Played CDs, Youtube vids, even ran tests. Nothing is coming out of the speakers or headphones, *even though Ubuntu is saying it is.* It's really odd.

---

### Post by FNDII on 2007-11-06
Did you have sound before you put that command into the terminal?

---

### Post by Liberi on 2007-11-06
No sound, before or after. Before, Ubuntu thought I had something. After, it thought I had nothing.

---

