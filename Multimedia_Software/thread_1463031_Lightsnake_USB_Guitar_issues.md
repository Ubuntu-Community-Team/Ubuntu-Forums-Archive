---
title: "Lightsnake USB Guitar issues"
date: 2010-04-26
forum: Multimedia Software
---

### Post by Ghost|BTFH on 2010-04-26
I am at my wits end.  Any help will be greatly appreciated.

I recently purchased a Lightsnake STUSB10M USB audio interface cable that is supposed to allow you to record from an electric guitar (or other device) into the computer digitally via USB.

lsusb shows the item listed:

Bus 006 Device 003: ID 0d8c:0006 C-Media Electronics, Inc. Storm HP-USB500 5.1 Headset

I can select it as default sound card.  I can get music to play through the headphones section of the card.  What I cannot get, for anything, is sound to be recorded from my guitar.

I have attempted to set it as the default input device (Which is a pain in and of itself as it has a mic and line input - but only one connection)

I have used alsamixer to make sure nothing was muted...

I have even reinstalled PulseAudio (and for those of you who know me, that was a journey into hell just considering it) and attempted Jackd as well.

I don't know what else to try.  I checked the cable going to the guitar - I have continuity there, so it's not an issue with the cable...

The only other thing I can think of is doing a patch from the headphones to the input and see if I can get that to make some sound (although I doubt it seriously).

Please, any suggestions, help, walkthroughs, shared stories of hells past - please post.

Cheers,
Ghost|BTFH :guitar:

---

### Post by hoptimusPrime on 2010-05-04
i have the same usb light snake and i cant get either the sound output or recording.  

i can select it under system>preferences>sound, but from there i'm lost.

ive been trying to use that 'creox' software that comes with the ubuntu software center..

has anybody out there been able to get this to work?

---

### Post by Ghost|BTFH on 2010-05-04
News update - mine was defective.  I sent it back.  However, while I had it, I did notice that I could plug in the 1/4" to 1/8" cable into my mic jack and record my guitar without any issue at all...so...these Lightsnakes are a joke.

Don't bother, just get your money back and go make a 1/4" to 1/8" cable and rock on.

:guitar:

PS:  LMMS or Jokosher both work fairly well once you get things set up properly.

---

### Post by mmercado on 2010-05-06
I have the same problem :(

I also have an USB interface like you guys but it's not lightsnake, it is an *American Audio USB 2.0 Phono Preamp / Computer Interface* and it is seen with [FONT="Courier New"]lsusb[/FONT] as: 

[FONT="Courier New"]Bus 002 Device 002: ID 0d8c:0006 C-Media Electronics, Inc. Storm HP-USB500 5.1 Headset[/FONT]

I can also hear sounds from the computer and through the interface (it has a headphones jack to serve as musical monitor) but the computer is not "hearing" anything I play.

The sad thing is that ... ahem... it works in Windows :(.

Any help would be appreciated. I refuse to depend on Windows.

M.E.

---

