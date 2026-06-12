---
title: "What Sound Card?"
date: 2010-11-22
forum: Multimedia Software
---

### Post by Rocket J Squirrel on 2010-11-22
I'm looking for a high-quality 96kHz 24-bit PCI or USB two-channel analog sound card that works with Ubuntu. I can't seem to find a list of cards that are known to work. Ubuntu 10.10

---

### Post by cchhrriiss121212 on 2010-11-22
M-Audio Audiophile 2496 (PCI) would be a good choice. The Asus Xonar Essence range also has good support.

See here for supported cards:
[http://www.alsa-project.org/main/index.php/Matrix:Main](http://www.alsa-project.org/main/index.php/Matrix:Main)

---

### Post by Rocket J Squirrel on 2010-11-22
Who's your avatar there -- George Clinton? Excellent.

I've looked at that ALSA sound card matrix page but didn't know how to interpret it. It provides clickthroughs to pages detailing the cards from the various manufacturers, but I could not tell if those were just handy lists of available cards, or whether the listed cards worked or not. 

For example, the listing for the M-Audio Delta Audiophile 2496 on

[http://www.alsa-project.org/main/index.php/Matrix:Vendor-MAudio](http://www.alsa-project.org/main/index.php/Matrix:Vendor-MAudio)

simply says: ICE1712 (Envy24) Details    [PCI] [ANALOGio] [RCAio]

No word whether the thing works under ALSA or not. 

Anyway, thank you for the recommendations!

---

### Post by cchhrriiss121212 on 2010-11-22
Anything you see listed on the database will work on Ubuntu to varying degrees. To translate:
   [PCI] - It's a PCI card
[ANALOGio] - Analogue input and output works
[RCAio] - RCA input and output works

My avatar is Bootsy Collins BTW.

---

### Post by Rocket J Squirrel on 2010-11-22
Oh well now, Bootsy. Superb. :D

I see, I was thinking that something like "[ANALOGio]" meant the card had analog(ue) I/O, it never occurred to me that it meant that that feature works. The things I learn. 

Many thanks for clearing that up. Someone might want to put an explanatory note on the wiki page for numbskulls like me. 

The next thing I want to find is a quiet 2-in, 2-out card with balanced ins and outs that ALSA supports.

---

### Post by cchhrriiss121212 on 2010-11-23
> The next thing I want to find is a quiet 2-in, 2-out card with balanced ins and outs that ALSA supports.
Here's my response from another thread for someone with the same question:
[http://ubuntuforums.org/showpost.php?p=10152397&postcount=19](http://ubuntuforums.org/showpost.php?p=10152397&postcount=19)

---

### Post by Rocket J Squirrel on 2010-11-23
Thank you. Yes, I saw that writeup. I also saw that "At 96 Khz, the device is either capture or playback only." and I need full duplex @ 96kHz.

---

### Post by cchhrriiss121212 on 2010-11-23
A PCI card would be a better choice then as they handle higher loads better. Take a look at post #20 and #21 on that same thread.

---

### Post by Rocket J Squirrel on 2010-11-23
Hmm, well. 

The M-Audio Delta 66. Its spec page says, "software configurable for +4dBu and -10dBV signal level." No mention on ALSA matrix whether that feature is supported. 

On post # 21's comparison chart link, looking for balanced (TRS) cards, I find the Echo Mia which offers balanced analog I/O, but no mention of that card on the ALSA matrix.

The Delta 44 is also listed but it shares the software configurable signal level feature with the Delta 66.

Next is the Creative Labs E-mu 1212, about which ALSA says, "Support arriving in 1.0.14." I'm running 1.0.23, but hesitate to purchase a $150 card without a better idea about whether support has been implemented. 

The M-Audio Audiophile 192 apparently has not had its input tested, according to the ALSA matrix. 

Jeepers. If it's not one thing, it's another! ;)

---

### Post by cchhrriiss121212 on 2010-11-23
I own a Delta 44 and can confirm that it works fully (aside from a bug with pulse that takes a few minutes to fix). The 66 is essentially the same device with digital ins/outs.

The Emu stuff I have no experience of, but I have seen various users on the forums who confirm they work. If the ALSA page says the device is supported, then you can assume it is correct, I think ALSA 1.0.14 is quite old by now.

---

### Post by Rocket J Squirrel on 2010-11-23
Yeah, I expect that ALSA 1.0.14 is pretty old. The matrix page must be older than that, then. 

So, just to confirm, you can select between +4dBu and -10dBV on the Delta 44 in ALSA?

If so, that looks like a suitable card!

---

### Post by cchhrriiss121212 on 2010-11-23
> **Rocket J Squirrel said:**
> 
So, just to confirm, you can select between +4dBu and -10dBV on the Delta 44 in ALSA?

Yes, on Linux ICE1712 chipsets are controlled with a GUI program called envy24control. Under the hardware settings tab there is an option for either professional (+4dBu) or consumer (-10DbB) output as well as some other settings.

---

### Post by Rocket J Squirrel on 2010-11-23
Well, that pretty much answers my questions! Many thanks for your kind assistance.

---

