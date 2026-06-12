---
title: "Degredation of audio quality by reencoding"
date: 2011-01-18
forum: Multimedia Software
---

### Post by perrti-y02 on 2011-01-18
Hello,

Following a discussion with a friend I was wondering what the general opinion on this matter is.

If I were to take a flac music file and convert it to alac using ffmpeg would there be any degradation  of audio quality?

I am also wondering how many people are actually able to tell the difference between a high quality MP3 and a lossless file. If I were to find a suitable place to upload a load of different files would people be willing to judge the audio quality?

Many Thanks

Tim Perrin

---

### Post by BicyclerBoy on 2011-01-18
Any conversion /transcode causes loss & introduces artifacts.

But FLAC is meant to be lossless so I'm not sure about how the above applies to FLAC.

Mp3 was not a planned music format it just happened (unfortunately). It has design deficiencies like spectral leakage between the frequency bins.
It was one of the first audio codecs with psycho-acoustic models so it has been superseded.

MP2 is a better audio quality encoding than mp3.
AAC is better than mp3 at all data rates.

AAC & ALAC are not FOSS, ogg & FLAC are

I find low data rate mp3 music very tiring/irritating to listen to. Mp3 loses detail in complex music (not indie rock).

It does depend strongly on the source material. Most modern over-engineered recordings are horrible to start with (sound like compressed FM radio).

The number of good recordings is not that large.

---

### Post by perrti-y02 on 2011-01-18
I have recently started duplicating my music collection in AAC for use on my iPod, and as far as I can tell, there are very few differences in sound quality between this very high bitrate AAC and ALAC. I can easily tell the difference on my hifi but on a piece of hardware such as the iPod the difference in quality simply can't be heard.

I do wonder how many people actually use good enough hardware to tell if the music they are listening to is a high quality lossy file or lossless.

---

### Post by Bucky Ball on 2011-01-18
Lossless files contract and expand and remain the same. If you compress a FLAC file to another FLAC file and then 'expand' it to it's previous compression rate it should be the same.

If you compress a FLAC file to an MP3 file it 'squeezes the air' out of it, ie audio data. If you then de-compress the MP3, the 'air' or audio data cannot be replaced as it is a 'lossy' file. That information is gone and that's that. This of shrinking a high quality jpg image file. If you then try to blow it up again you are left with grainy mush. The information has been squeezed out in the compression and is gone.

---

### Post by robert shearer on 2011-01-18
> Most modern over-engineered recordings are horrible to start with (sound like compressed FM radio).
+1 
  These days noise and volume substitutes for sound quality and accuracy...sigh.

Good only for pumping loud and bass heavy whilst driving the 'gangsta-mobile' through town.
 
Mediocrity is achievable, this explains it's popularity..:) 

We let the recording conglomerates re-sell us the albums we already owned with the promise of *higher fidelity* only to find that meant their profits and not sound quality. 

end rant ;)

---

### Post by Bucky Ball on 2011-01-18
Lossless files contract and expand and remain the same. If you compress a FLAC file to another FLAC file and then 'expand' it to it's previous compression rate it should be the same.

If you compress a FLAC file to an MP3 file it 'squeezes the air' out of it, ie audio data. If you then de-compress the MP3, the 'air' or audio data cannot be replaced as it is a 'lossy' file. That information is gone and that's that. 

Think of shrinking a high quality jpg image file. If you then try to blow it up again you are left with grainy mush. The information has been squeezed out in the compression and is gone.

---

### Post by Bucky Ball on 2011-01-18
> **robert shearer said:**
> +1 
  These days noise and volume substitutes for sound quality and accuracy...sigh.

Good only for pumping loud and bass heavy whilst driving the 'gangsta-mobile' through town.
 
Mediocrity is achievable, this explains it's popularity..:) 

We let the recording conglomerates re-sell us the albums we already owned with the promise of *higher fidelity* only to find that meant their profits and not sound quality. 

end rant ;)

+1. Grab the original vinyl on a good turntable with a good stylus, amp, speakers then grab the cd remake of the same vinyl, plug in a cd player to the same system instead of the turntable and see (hear) for yourself.

There is a frequency cut off point both high and low applied to CDs. This is not the case with vinyl (or other digital files in essence) where the quality and capabilities of the reproduction equipment are the only limitation.

---

### Post by BicyclerBoy on 2011-01-18
Vinyl when I was buying it was not pressed well.
The best vinyl transfer was direct cut & in the type of plastic that does not last very long.

I have a good amp but never a good turntable set up well.

So I have a couple of recordings that sound better than the CD but I think this is caused by the sound engineer/monitors/hearing-loss & not the format.

So I think the re-make concept is the problem; the FM radio effect..

The CD standard was unfortunate in that the technology was not quite there.
So the CD should have been 48KHz & couple more bits.
The DAC anti-aliasing filters (phase error) & cost of RAM etc helped cause the 44.1KHz/16 bit limits.
A modern over-sampling CD player/HTPC does a lot better than first Philips player.

---

### Post by robert shearer on 2011-01-18
> **BicyclerBoy said:**
> Vinyl when I was buying it was not pressed well.
The best vinyl transfer was direct cut & in the type of plastic that does not last very long.

[B][COLOR="Red"]I have a good amp but never a good turntable set up well.

So I have a couple of recordings that sound better than the CD but I think this is caused by the sound engineer/monitors/hearing-loss & not the format.
[/COLOR][/B]
So I think the re-make concept is the problem; the FM radio effect..

The CD standard was unfortunate in that the technology was not quite there.
So the CD should have been 48KHz & couple more bits.
The DAC anti-aliasing filters (phase error) & cost of RAM etc helped cause the 44.1KHz/16 bit limits.
A modern over-sampling CD player/HTPC does a lot better than first Philips player.

Bingo...! if the turntable is not set up to retrieve the information then the comparison is not meaningful. GIGO. ;)

---

### Post by psusi on 2011-01-18
> **BicyclerBoy said:**
> 
So the CD should have been 48KHz & couple more bits.

Why?  The human ear can't really hear beyond 20 kHz ( most older people can't hear beyond 15 ), and how much more harmonic distortion do you really get at 16 bits than 24?

> **BicyclerBoy said:**
> The DAC anti-aliasing filters (phase error) & cost of RAM etc helped cause the 44.1KHz/16 bit limits.
A modern over-sampling CD player/HTPC does a lot better than first Philips player.

Huh?  44.1/16 is still 44.1/16 no matter what player you use.

---

### Post by BicyclerBoy on 2011-01-18
Yes it is..

The vinyl album on a ho-hum technics turntable ortofon (cart/sty) sounded better the CD.

Still listen to the CD because it so convenient.

All these issues can be overcome with excessive use of lawn mower, chainsaw & angle-grinder, not mention kids & partner.

---

### Post by robert shearer on 2011-01-18
double post

---

### Post by robert shearer on 2011-01-18
> **BicyclerBoy said:**
> Yes it is..

The vinyl album on a ho-hum technics turntable ortofon (cart/sty) sounded better the CD.

Still listen to the CD because it so convenient.

[COLOR="Red"]All these issues can be overcome with excessive use of lawn mower, chainsaw & angle-grinder, not mention kids & partner[/COLOR].

Nope, these just reduce the **amount** of information available for processing to your 'auditory receptors'. The quality of the remaining information is still subject to the normal rules of physics...:) if it's crap then that is what it is.

> 
Still listen to the CD because it so convenient.

And that is how the record companies got your $$, with your acceptance of convenience over quality. :)

---

### Post by BicyclerBoy on 2011-01-18
The chainsaw stuff was just a bit of humour..
And we are very off topic of OP.

In the days of records & tapes we did not pay for or expect the "data" to last. We did not ever buy the right to the material forever.
It was not the paradigm.
Do you serious believe digital era has really changed this..Archiving is as much about accessible data formats & mechanisms as the data itself.

I don't mind paying for music..I just don't buy very much.
The $15 for a good live concert DVD can be the best $15 dollars spent...

Convenience (& credit) is mantra of modern life is it not ..

---

### Post by robert shearer on 2011-01-18
@BicyclerBoy;10373709]> The chainsaw stuff was just a bit of humour.. 
Yes, hence the smilies..:)
> And we are very off topic of OP.

Apologies to OP..though we are discussing encoding/recoding and sound degradation

> In the days of records & tapes we did not pay for or expect the "data" to last.
As I upgrade electronics I continue to 'open the window' and access more information from records I bought **35** years ago.
 That is the beauty of analogue, it is all there and as technology improves more is able to be retrieved.
With digital what you get is all you will ever get.

>  We did not ever buy the right to the material forever.
It was not the paradigm.
Agreed.

> Do you serious believe digital era has really changed this..Archiving is as much about accessible data formats & mechanisms as the data itself.

To true, convenience traded for quality.

> I don't mind paying for music..I just don't buy very much.
The $15 for Pink Floyd Pulse DVD is the best $15 dollars I ever spent... 
Each to their own...:D

> Convenience (& credit) is mantra of modern life is it not ..
Unfortunately perhaps...


regards, Bob...:)

---

### Post by Bucky Ball on 2011-01-19
The rest are called overtones ... not all humans (or other animals) hear the same frequency. There is a 'normal' range, but that is only half the story. MP3 DO NOT provide overtones ...

---

### Post by cascade9 on 2011-01-19
> **perrti-y02 said:**
> If I were to take a flac music file and convert it to alac using ffmpeg would there be any degradation of audio quality?
  
  In theory, no. Its possible that you could get degradation from a poor FLAC decoder (unlikely) or a poor ALAC encoder. 
 
 > **perrti-y02 said:**
> I have recently started duplicating my music collection in AAC for use on my iPod, and as far as I can tell, there are very few differences in sound quality between this very high bitrate AAC and ALAC. I can easily tell the difference on my hifi but on a piece of hardware such as the iPod the difference in quality simply can't be heard.
 
 I do wonder how many people actually use good enough hardware to tell if the music they are listening to is a high quality lossy file or lossless.
 
 Agreed. I can hear the difference between flac and high bitrate lossy (both converted to CD-DA) on a good stero, but on any portable media player I've tried I cant tell the difference.


> **robert shearer said:**
> +1 
  These days noise and volume substitutes for sound quality and accuracy...sigh.

Good only for pumping loud and bass heavy whilst driving the 'gangsta-mobile' through town.
 
Mediocrity is achievable, this explains it's popularity..:) 

We let the recording conglomerates re-sell us the albums we already owned with the promise of *higher fidelity* only to find that meant their profits and not sound quality. 

end rant ;)

+lots and lots.

[http://www.cdmasteringservices.com/dynamicrange.htm](http://www.cdmasteringservices.com/dynamicrange.htm)

See below for more though... 

> **BicyclerBoy said:**
> Yes it is..
 
 The vinyl album on a ho-hum technics turntable ortofon (cart/sty) sounded better the CD.
 
 Still listen to the CD because it so convenient.
 

That doesnt make vinyl better than CD. I dont even want to get into the digital/analog argument. I just remember reading an interview with (IIRC) the sound engineer for 'steely dan'. He was writing about an experience where he had done the masting on a new album, and sent the master of for test pressings. He got a sample back, put it in the CD player- horrible. Loudness boosted everywhere, dynamic range gone, etc..

He ended up finding out that the CD plant was adding loudness, 'because the CD is to quiet'. They pretty much refused to return the CD back to original mastering levels.    

I wish I had never lost that link. :( 

To bring it back to the CD/vinyl debate, if CD plants are adding loudness if the recording isnt squished to within an inch of its life (which they sure appear to be doing) that would explain why so many CDs are awful. Even CDs by bands that tradionally have good dynamic range, and have memebers who know what they are doing involved in the remasterign process (eg, Led Zeppelin)

---

### Post by Bucky Ball on 2011-01-19
'Everthing Must Go' would be the only Steely album I can think of that sounds quite that compressed. ;)

---

