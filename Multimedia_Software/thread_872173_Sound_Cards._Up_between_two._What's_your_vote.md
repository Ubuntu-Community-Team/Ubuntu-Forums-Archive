---
title: "Sound Cards. Up between two. What's your vote?"
date: 2008-07-27
forum: Multimedia Software
---

### Post by Roasted on 2008-07-27
[http://www.newegg.com/Product/Product.aspx?Item=N82E16829270003](http://www.newegg.com/Product/Product.aspx?Item=N82E16829270003)
SIIG IC-710012 7.1 Channels 24-bit 96KHz PCI Interface Surround Sound Card For Internet, DVD, MP3 and Gaming.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16829118105](http://www.newegg.com/Product/Product.aspx?Item=N82E16829118105)
Turtle Beach RIVIERA 5.1 Channels 24-bit 48KHz PCI Interface Sound Card.

There's one review for each that talk about Linux support, but I'm unsure of which distro.

One member on here posted in the testimonial section speaking highly of the Riviera.

Which would you suggest going with? The SIIG just makes me think it's got some more kahoonas to it, but I'm not sure, TB has a good reputation.

What's your vote? Looking to get the best bang for the buck here. :guitar:

---

### Post by markbuntu on 2008-07-27
Well, there is something to say for 96khz. Just make sure it is going to work before you buy it.

---

### Post by Roasted on 2008-07-27
Yeah, the 96khz is something that caught my eye. Is that a significant upgrade? I'm unsure as to how it stacks up against other cards. Sound cards aren't exactly my specialty.

I'm willing to bet if he said it works great under Linux that it's more than likely Ubuntu he used. And if not, I would assume Ubuntu would have a decent chance at being supported.

---

### Post by Roasted on 2008-07-27
Any clue on where I can find documentation on it? I'm reading reviews and looking around on google and I simply can't find much documentation that directly says "Yes, this card works. Have a nice day." :confused:


Oooooooo... Do we have a new winner here?

Diamond Xtreme Audio. Decent price, 96khz... Someone reviewed it in 2006 saying it's compatible with Alsa. I assume if it was compatible with Alsa in 2006, it'd be compatible with Alsa in 2008? Or should I just bump out a couple extra bucks and get one of the other two? 


[http://www.newegg.com/Product/Product.aspx?Item=N82E16829111001](http://www.newegg.com/Product/Product.aspx?Item=N82E16829111001)

---

### Post by markbuntu on 2008-07-28
All the Diamond cards work OOB as far as I know.

---

### Post by Melcar on 2008-07-28
Do the sound drivers (ALSA) and servers (Pulseaudio) even support 96kHz?  Everything I've seen defaults to 48kHz.  Sound is not my specialty either, so I may be wrong in my assumptions.

---

### Post by Roasted on 2008-07-28
Hm, no idea... but I ended up grabbing the SIIG card anyway... so I guess we'll find out! Then, later on if Alsa picks up additional support for 96khz and whatnot, I'd be ready.

I find that hard to believe though, that after all this time with Alsa they wouldn't have support for it. Don't X-FI cards have 192khz? I heard of SOME (but few) people getting those to work (since creative has such great support and all) and spoke highly of their quality... *shrug*

---

### Post by Melcar on 2008-07-28
*edit*

---

### Post by Roasted on 2008-07-28
I wonder how accurate this is.

The Advanced Linux Sound Architecture project (ALSA) was founded 1998 by Jaroslav Kysela. It is intended to improve sound support for Linux, thanks to an improved software design and the ability to fully utilize Linux-specific features. ALSA provides free drivers for the most popular audio cards; at the same time, its design allows multi-channel operation at 24 bit/96 kHz with very low latency and very low CPU load.

From:

[http://www.rme-audio.com/english/linux/alsa.htm](http://www.rme-audio.com/english/linux/alsa.htm)

---

### Post by markbuntu on 2008-07-29
Well yes, that is pretty accurate because jack uses ALSA and it can record up to 24 bit/192 KHz with extremely low latency when used with the real time kernel.

---

### Post by Roasted on 2008-07-29
I bought the SIIG card.

Any idea why I wouldn't have audio on CNET or youtube? mp3s and dvds work great...

---

### Post by jukingeo on 2008-09-23
> **Roasted said:**
> Hm, no idea... but I ended up grabbing the SIIG card anyway... so I guess we'll find out! Then, later on if Alsa picks up additional support for 96khz and whatnot, I'd be ready.

I find that hard to believe though, that after all this time with Alsa they wouldn't have support for it. Don't X-FI cards have 192khz? I heard of SOME (but few) people getting those to work (since creative has such great support and all) and spoke highly of their quality... *shrug*


I got the X-Fi to work.  See my link below.  I have not tested it to 192khz, but it DOES work at 96k.  However, my problem was that I wanted to use the X-Fi outside of Ubuntu/Windows.  I have other Linux distributions that I want to use (such as Dynebolic), and the card is useless in those distros.  I think the X-Fi will only work in Ubuntu Gutsy, Hardy (shoehorned in) and OpenSUSE 10.3.

The sad thing is that Creative stopped supplying the source code lately starting with the X-Fi.  The X-Fi is overall a great card and it DOES have a pro-audio spec.

Supposedly the M-Audio Delta line will play/record to 96k as well and it should be automatically detected by most Linux distributions.  I may go this route myself.  The downside is the the M-Audio Delta line is VERY stripped down.  Some cards don't have digital audio connections and midi.  There are also no mic pre-amps included as well.

Sadly, there is very little support for audio cards in Linux and it is the thing I am having the most trouble with in my conversion from Windows to Linux.

---

### Post by markbuntu on 2008-09-23
Well I got the SIIG card too. It worked out of the box and I have had absolutely no problems with it. Far too many hoops to jump through with the X-Fi for me. Besides, why give money to people who just don't support linux.

---

### Post by Roasted on 2008-09-23
Mark - I posted this in the other thread too, but I'm responding here again in case somebody runs across this thread and could my answered input.

The SIIG I'm sure works fine out of box in 32 bit. My mistake was I had 64 bit installed and completely forgot about it. I returned the SIIG out of rage before even trying 32 bit. Afterwards, I ordered the Montego, at which point I realized I wasn't running 32 bit.

I formatted, installed 32 bit, Montego arrived, popped it in, and it worked perfect. The Montego and SIIG I believe have the same audio chipset, so they should be equally supported.

So, I'd imagine the SIIG is supported (as the Montego is) under 32 bit Ubuntu. 64 bit didn't seem to be the case, though.

---

### Post by jukingeo on 2008-09-24
> **markbuntu said:**
> Well I got the SIIG card too. It worked out of the box and I have had absolutely no problems with it. Far too many hoops to jump through with the X-Fi for me. Besides, why give money to people who just don't support linux.

True on both counts, but I already had bought my X-Fi when I had Win XP.  I am sure there are many Windows to Linux converts out there that also have the same card.  So I didn't "purposely" by the card for use with Linux.

If money was no object, then I most certainly would look into something in the RME Hammerfall line.  But money is an issue right now and as such, I can't afford those cards.  Many here seem to have good results with them though.

---

### Post by markbuntu on 2008-09-24
> **Roasted said:**
> Mark - I posted this in the other thread too, but I'm responding here again in case somebody runs across this thread and could my answered input.

The SIIG I'm sure works fine out of box in 32 bit. My mistake was I had 64 bit installed and completely forgot about it. I returned the SIIG out of rage before even trying 32 bit. Afterwards, I ordered the Montego, at which point I realized I wasn't running 32 bit.

I formatted, installed 32 bit, Montego arrived, popped it in, and it worked perfect. The Montego and SIIG I believe have the same audio chipset, so they should be equally supported.

So, I'd imagine the SIIG is supported (as the Montego is) under 32 bit Ubuntu. 64 bit didn't seem to be the case, though.

I am running both 32 and 64 bit on the same machine and have experienced no problems with either using the SIIG card. A caveat. Shortly after getting the card I changed my 64 bit install to Ubuntu Studio to get the rt kernel working since it wouldn't run on my 32 bit ubuntu Studio install. 

I still have a generic 32 bit. I upgraded the 32 bit UbuStudio to Intrepid Alpha 5 which was a complete disaster....

---

