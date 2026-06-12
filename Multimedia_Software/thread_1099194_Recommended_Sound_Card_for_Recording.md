---
title: "Recommended Sound Card for Recording"
date: 2009-03-17
forum: Multimedia Software
---

### Post by pgmer6809 on 2009-03-17
I am putting together a new system. After a year of trying to get recording to work on my Audigy ZS card, I am now more careful about the hardware I buy.
I need a card that will do simple stereo playback and RECORD at 24bit 96/192 KHz samples with good SNR.
RECORDING is the key. There is a real shortage of info out there on what works reliably.
Any one have personal experience with a decent sound card doing recording under ubuntu?
pgmer6809

---

### Post by Reeman on 2009-03-18
> **pgmer6809 said:**
> I am putting together a new system. After a year of trying to get recording to work on my Audigy ZS card, I am now more careful about the hardware I buy.
I need a card that will do simple stereo playback and RECORD at 24bit 96/192 KHz samples with good SNR.
RECORDING is the key. There is a real shortage of info out there on what works reliably.
Any one have personal experience with a decent sound card doing recording under ubuntu?
pgmer6809

The M-audio delta 24/96 is a good place to start. It has rock solid linux support and has a great s/n. It does not have an onboard mic pre-amp so it has no pops, hiss, or drop trouble.
It is a simple pci that has the well supported ice1712 chip from via. It is simple plug and play with any os. 

I have used them for over 5 years and found that they out perform anything else on the market. They are simple and easy to use. They record at 24/96 and the envy24control is part of alsamixer and is native to the environment. They do not do dolby 7.1 but they will support 5.1 i/o through the digital breakout which is supplied with the card.

You can gang up to 3 of them and do 6 channel 24/96 multitrack a-d with ardour or 4 channel with two of them and with the Windows ware from Ableton G Live that they come with in the retail box. They sell for around 100bucks or you can find them used for less.... usually without software.


They have one quirk...they will sound off when you shut down the computer as the line level pre-amp out is quite hot and as you power down the pc it switches off the neutral grounding before it powers down the pci bus..so you hear your drives spinning down!

To me this is a feature that tells me that the pre-amp on the card is working just fine!

Dollar for dollar they are the best card on the market. I record from analogue mixed condenser mics and find that the S/N and high gain pre-amps are whisper quiet...every bit as good as the more expensive stuff that studios use. Sure they are not rated at 105+ db on the a-d side but the quality of the card more than makes up for the lower gain when recording. They easily handle hot pre-amp input and do not start to push the distortion envelope till you get right up to the top of the line level 1.5 volt threshold.

I have never had a software or hardware issue with them.

The supplied spdif, midi i/o breakout is good quality and you can put a Phillips 5 pin midi connection directly in or out..... it does not matter which OS you use the drivers will all recognize midi or digital i/o flawlessly! With the exception of FreeBsd the support is complete and even with bsd and sun solaris there are ways to do it.

Even though the card is getting long in the tooth it is still the best bang for the buck going. If you are looking for 7.1 and all of the latest Dolbly stuff then check out the newest stuff from M-Audio it will cost more but is still less expensive than most of the gamer centric creative squawk boxes ...

Avoid the expensive pci express Asus and Creative crap. They are nothing but overpriced trouble with jack sensing stupidity, mike pre-amps and circuit designs that cause all sorts of distortion and unwanted crap.

M-Audio product are simple, well supported and most important, reliable and quiet!

---

### Post by pgmer6809 on 2009-03-18
> **Reeman said:**
> The M-audio delta 24/96 is a good place to start. It has rock solid linux support and has a great s/n. It does not have an onboard mic pre-amp so it has no pops, hiss, or drop trouble.
It is a simple pci that has the well supported ice1712 chip from via. It is simple plug and play with any os. 

I have used them for over 5 years and found that they out perform anything else on the market. They are simple and easy to use. They record at 24/96 and the envy24control is part of alsamixer and is native to the environment. They do not do dolby 7.1 but they will support 5.1 i/o through the digital breakout which is supplied with the card.

You can gang up to 3 of them and do 6 channel 24/96 multitrack a-d with ardour or 4 channel with two of them and with the Windows ware from Ableton G Live that they come with in the retail box. They sell for around 100bucks or you can find them used for less.... usually without software.


They have one quirk...they will sound off when you shut down the computer as the line level pre-amp out is quite hot and as you power down the pc it switches off the neutral grounding before it powers down the pci bus..so you hear your drives spinning down!

To me this is a feature that tells me that the pre-amp on the card is working just fine!

Dollar for dollar they are the best card on the market. I record from analogue mixed condenser mics and find that the S/N and high gain pre-amps are whisper quiet...every bit as good as the more expensive stuff that studios use. Sure they are not rated at 105+ db on the a-d side but the quality of the card more than makes up for the lower gain when recording. They easily handle hot pre-amp input and do not start to push the distortion envelope till you get right up to the top of the line level 1.5 volt threshold.

I have never had a software or hardware issue with them.

The supplied spdif, midi i/o breakout is good quality and you can put a Phillips 5 pin midi connection directly in or out..... it does not matter which OS you use the drivers will all recognize midi or digital i/o flawlessly! With the exception of FreeBsd the support is complete and even with bsd and sun solaris there are ways to do it.

Even though the card is getting long in the tooth it is still the best bang for the buck going. If you are looking for 7.1 and all of the latest Dolbly stuff then check out the newest stuff from M-Audio it will cost more but is still less expensive than most of the gamer centric creative squawk boxes ...

Avoid the expensive pci express Asus and Creative crap. They are nothing but overpriced trouble with jack sensing stupidity, mike pre-amps and circuit designs that cause all sorts of distortion and unwanted crap.

M-Audio product are simple, well supported and most important, reliable and quiet!

Thank you VERY much. I will be not be needing the fancy guitar or midi inputs as I will be feeding from the 'tape-out' jacks on my stereo/turntable system. 
But that kind of user feedback is what I need, and simple and quiet is exactly what I am looking for.

M-Audio have a 'newer' card, Audiophile 192 that seems to have just a tad more features than the 2496. 
Do you suppose it is also supported in ALSA?

pgmer6809

---

