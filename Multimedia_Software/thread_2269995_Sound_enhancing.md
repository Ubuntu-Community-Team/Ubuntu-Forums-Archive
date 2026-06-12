---
title: "Sound enhancing"
date: 2015-03-19
forum: Multimedia Software
---

### Post by Nirdala on 2015-03-19
Hi,
I was wondering if there is such a program like Asus Sonic Focus for Ubuntu( I have Asus laptop so I got it with drivers)? I used that program on Windows and it really and very noticeably enhanced sound quality globally but I'm afraid that it is not possible to make it running on Linux enviroment. 
Can you recommend some similar tools for improving overall sound quality across system?Speakers within laptop are Altec Lancing.

---

### Post by tgalati4 on 2015-03-19
I'm not familiar with Sonic Focus, but it either applies a simple equalization (EQ) or it performs a software digital signal processing (DSP) to make the speakers sound "bigger" like Sony's "Mega Bass".  If you do some research, you can probably find out what Sonic Focus is doing and then you can write a filter to perform a similar function.

So what is the transform that Sonic Focus applies to your speakers?

---

### Post by Nirdala on 2015-03-19
It applies DSP. Since the difference in sound quality is very notable on first hearing between the modes when Sonic Focus is ON and OFF.
From manufacturer : 
"Sonic Focus Stereo post-processing IP has been successfully implemented  by leading PC manufacturers to deliver a rich, compelling audio  listening experience for end users. The Sonic Focus Stereo IP solutions  extend this benefit into low-power DSP and cost-effective embedded  stereo audio applications, delivering enhanced performance in ultra-thin  speaker-based designs. In addition, by using the new Synopsys Sonic  Focus logo on their products, OEMs and ODMs can further differentiate  their leading consumer multimedia products that take advantage of this  unique audio technology."

---

### Post by tgalati4 on 2015-03-19
That's nice.  But what processing do you think it is doing?  To simulate bass (30 Hz), for instance, higher harmonics are produced at 60 and 120 Hz to give the psycho-acoustic impression of 30 Hz with a 2" speaker.  Interesting trick that is called "Mega Bass".  

Install *audacious* and look through the effects tab.  Play a standard mp3 track and turn the various effects on and off until you find something you like.  Once you have the effect and settings, you need to associate that processing with every sound source in *pulseaudio*.

For system-wide EQ as a start:  [http://www.webupd8.org/2013/03/install-pulseaudio-with-built-in-system.html](http://www.webupd8.org/2013/03/install-pulseaudio-with-built-in-system.html)

Old thread, but many useful ideas dealing with system-wide sound:  [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

If you can describe what Sonic Focus is doing, then there is a way to write a dsp algorithm to perform something similar.  Send an email to ASUS for linux support.  I need some humor today.

---

### Post by Nirdala on 2015-03-20
Unfortunately I described it the best I can since I'm not a sound technician and the program is not open source so I do not really know what he specifically do or how he does it. This is the interface. It only has those three sliders as you can see in the picture and thats it.
[ATTACH=CONFIG]260763[/ATTACH]

---

### Post by Rob Sayer on 2015-03-20
Well, I looked at their site and on wikipedia and they don't really describe it all that well either.  BTW software EQ *is* DSP.

I agree that what you were talking about is just EQ.  "Vocal clarity enhancement" is usually just a mid or presence bump.  Or a smiley face curve, which is an extremely common way mfrs use to give the illusion the device has a lot more clarity than it actually has.  Some very expensive speakers do this.

---

### Post by Nirdala on 2015-03-20
I bought this laptop 3 years ago for about 400 euros , I would not say that these speakers are expensive xD Or are they , honestly I do not keep record of speakers market.
I wish you tried this crazy little , powerfull software so you could fully understand what kind of magic it does to sound. 
I listen music when I'm working and when I dont and maybe I'm overreacting but I needed to try to find something to replace it, and honestly this program is the only thing I miss from Windows. It really ,as you said , makes my speakers sound expensive with that crazy sound quality boost :)

---

### Post by tgalati4 on 2015-03-20
As Rob Sayer suggests, vocal clarity is probably a midrange EQ bump with a "crystalizer" added to crisp-up the sibalence or "s" sound.  The Surround Sound can be achieved by cross-feeding the phase of stereo signals, there are standard plug-ins that do this.  The Bass bump is probably a combination of EQ bump at the low end with a Sony Mega Bass treatment that I descibed earlier.  Not sure what adaptive sound is, perhaps it is a compressor so that loud sounds get compressed and don't overdrive the small speakers.

Again, research is key to finding out exactly what is going on so that you can replicate it.  Many cell phones have similar boost functions to make their crappy speakers sound less crappy.

---

### Post by Rob Sayer on 2015-03-21
> **Nirdala said:**
> ... I wish you tried this crazy little , powerfull software so you could fully understand what kind of magic it does to sound...

I wish you would believe me when I tell you that it is doing NOTHING crazy or powerful and there is likely not one thing it does that you couldn't do yourself.

It's like all those gasoline additives that make magic claims.  If they actually were that good every company that sold it would have them because all the auto manufacturers would require them as part of the warranty contract.

Just play with EQ a bit.

---

