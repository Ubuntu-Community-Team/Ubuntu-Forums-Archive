---
title: "Works by default!"
date: 2009-12-06
forum: Multimedia Software
---

### Post by OlympicSoftworks on 2009-12-06
Ok, I am thinking with all the people asking for advice on handling problems with various sound cards that stutter, will not record, just don't work, or don't work with all applications; it would be well to have a thread to run down all the cards that people are using that DO work...fully...by default.

I run a non-profit org that builds computers for single-parent families that can't afford a computer, the elderly in our community, and I work with the orphan organisations in the Olympia area...but I am totally out of sound cards and the ones that are built-into MoBos are also not fully supported.  I need to know what to order as funds become available, or what to ask for as donations.

The only card I have found so far that is guaranteed to work 100% of the time is the very old "Sound Blaster Live!" cards.  But they are aging and are no longer in production.  So please help a brother out here.

Thank you;
   Dave

---

### Post by hansdown on 2009-12-06
Hi OlympicSoftworks.

Congrats on what you are doing.

Nvidia has very good support for ubuntu.

---

### Post by OlympicSoftworks on 2009-12-07
Thank you Hansdown.:D

Aye, for graphics adapters NVidia is mostly what I use...unless the MoBo has built-in Intel stuff.  Then I may let it ride and not put in a standalone if streaming video is not too choppy.  Any reasonably fast computer should not have choppy YouTube/Hulu stuff these days.

Good idea, lets start with some easy ones:
For graphics then: almost anything made by NVidia is a near 100% success 'out of the box'.   As does Intel adapters pretty much, although some Intel integrated chipsets seem more handicapped than others to me.

---

### Post by VertexPusher on 2009-12-07
> **OlympicSoftworks said:**
> Ok, I am thinking with all the people asking for advice on handling problems with various sound cards that stutter, will not record, just don't work, or don't work with all applications; it would be well to have a thread to run down all the cards that people are using that DO work...fully...by default.
Most of these problems are caused by PulseAudio. You can't fix them by replacing the sound card.

---

### Post by OlympicSoftworks on 2009-12-08
Many of them are, yes.  But some hardware just works better with Pulse than others.  Some cards, such as the ones using the ca0106 chip(the 24bit soundblaster economy cards) from Creative are not fully supported for one reason or another for recording, regardless of the sound server being used.  So software phones, teamspeak, and such things will not work.

My goal would be to encourage people to post what sound cards they are using IF they worked for playback and recording by default...right out of the box(or with minimal fuss).  The alsa site has this damned enormous list of what chipsets are supposed to be supported and what are not, but actual experiences of Ubuntu users would be a great cross reference to something like that list.

---

### Post by VertexPusher on 2009-12-08
> **OlympicSoftworks said:**
> actual experiences of Ubuntu users would be a great cross reference to something like that list.
The problem with user reports is that most users can't tell where the issues come from. They just know that there are issues.

Many times I've seen people blame their sound cards until they removed PulseAudio and realized that all the issues had disappeared.

The RealTek ALCxxx series (aka Intel HDA) is probably the most frequently used onboard audio interface today. It is shipped with all Intel desktop and laptop chipsets. I've had several of these over the years, and they all worked flawlessly with ALSA. They natively support at least 44100, 48000 and 96000 Hz sample rates and both 16 and 32 bit sample widths. If you install a realtime kernel, you can reduce latency below 4 ms. Without a RT kernel you can get down to 12 ms which is still sufficient to play ZynAddSubFX live over a MIDI keyboard.

If your system is set up to use ALSA or Jack, this card is as trouble-free as it gets. But if you use PulseAudio, you will experience the same issues and glitches as with any other card. That's why you will see people complain about this card as well. The default sound setup of Ubuntu makes sound card reviews largely useless.

---

### Post by OlympicSoftworks on 2009-12-10
Pulse audio is an ambitious project to allow incorporation of sound sources, sinks, and applications to share in the audio stream.  It makes perfect sense and is something that proprietary systems can never even approach due to copyright concerns.

It is also not actually the card that is responsible for performance(or lack of it) with pulse, it is the drivers; and these can grow and develop into full compliance.  Many cards work perfectly well with pulse, and many do not.  I am trying to encourage people to do a quick post if their sound system worked 'by default', or at least with only very minor adjustments with the standard Ubuntu install.  This would include pulse.

---

