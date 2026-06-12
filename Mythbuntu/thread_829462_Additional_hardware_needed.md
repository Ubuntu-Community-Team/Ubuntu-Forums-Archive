---
title: "Additional hardware needed?"
date: 2008-06-14
forum: Mythbuntu
---

### Post by CrimsonEclipse on 2008-06-14
I am still new to Ubuntu and Mtyhbuntu, so some of my questions may simplistic to many of you.

Back ground:
I have a computer with:
AMD 1700+ @2.3GHZ
512MB SDRAM
Either a NVidia 4200 128MB (with analog or digital output) or
NVidia (Gigabyte) V8200T2/Delux 64MB with Svid out or dongle with the G/R/B connectors.

TV is an older analog tube TV
Cable is digital but uses a converter for the older TV.
The cable provider is Comcast.

That is what I have to work with.

What I don't know is:
1. Do I need a tuner card or can I hook up directly to the vid card?
2. Assuming a DO need a tuner card, should it be a digital tuner?
2a. if so, any suggestions?
2b. are there USB variations?
3. Which of the 2 vid cards is better to use?
4. Comcast blocks my recording using a VCR unless I configure the 
converter for each show? is this normal?
4a. Would a digital tuner bypass this limitation?
4b. Would a digital tuner be able to be displayed on my old POS TV?
4c. Finally, can my system even HANDLE a digital setup?

The hardware and service available to me are a bit strange but it is all
I have to work with. 

I also have a Intel Dual Core laptop available to me. 
Do you think a USB digital tuner would work on it?

Thanks to anyone who will help me with this setup.

Sincerely.

CE

---

### Post by CrimsonEclipse on 2008-06-17
Nothing?
Did I ask the questions wrong?

(*sigh*)

CE

---

### Post by danbodoh on 2008-06-17
I can't really answer digital questions, because I've only got an analog tuner.

 Yes, you need a tuner.  Your video card is probably just TV-out.

 I have the Hauppauge PVR USB-2 for analog running on a Dell laptop.  See the [http://mythtv.org/wiki/index.php/Category:Hardware](http://mythtv.org/wiki/index.php/Category:Hardware).  Spend some time on the mythtv site, it may answer some of your questions.

 Not sure why you'd want to use the disk space and compute requirements for digital when you only have an analog TV.

 Your system would easily handle analog.  Again, I'm not a digital expert. 

Dan Bodoh

---

### Post by Lindsay.Mathieson on 2008-06-18
> 
1. Do I need a tuner card or can I hook up directly to the vid card?

You definitely need  a Tuner card :) your video card is only for output.

> 2. Assuming a DO need a tuner card, should it be a digital tuner?

Preferable - digital is better quality and actually a (much) lighter load on the CPU seeing as its already digitalised :) Digital is definitly the way of the future for Myth.

> 2a. if so, any suggestions?
2b. are there USB variations?

This is a trickier area, and depends on the signal you're getting. My experience is with Free To Air, I'm not familiar with cable. In general PCI cards seem better supported than USB cards. I'd suggest the WinFast 1000T and/or the Nova-500 but I don't know if they work with cable.

> 3. Which of the 2 vid cards is better to use?
Probably the 4200, the 8200 is pretty flaky under linux I believe.

> 4. Comcast blocks my recording using a VCR unless I configure the 
converter for each show? is this normal?
4a. Would a digital tuner bypass this limitation?

dunno :(

> 4b. Would a digital tuner be able to be displayed on my old POS TV?

Yes, I did that myself before I got a plasma. The tuner is only for recording the signal, the video card is what matters for display. And yes it is worth displaying digital on a analog TV, the quality is better and you get stereo sound as well.

> 4c. Finally, can my system even HANDLE a digital setup?

Yes, should be fine - Digital is actually *less* of a load than Analogue. 

I'd probably bump your RAM to 1G if you can though.



> I also have a Intel Dual Core laptop available to me. 
Do you think a USB digital tuner would work on it?

No reason why not. Depends if the Tuner is supported under linux. Probably best if your PC and/or Laptop have USB 2.0

Cheers,

Lindsay

---

