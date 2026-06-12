---
title: "microphone not working at all?"
date: 2006-07-28
forum: Multimedia &amp; Video
---

### Post by Skooj on 2006-07-28
well, i've read through the comprehensive sound problem guide thing, and various other threads, and everything they have said to do didnt work and/or didnt have the same problem as I have (i still tried their fixes). I would like to use my microphone mostly for skype and really not much else, but I find that my microphone doesn't work with anything at all (arecord, the built-in recording software with ubuntu 6.06, skype, nothing.). And I have no idea why. I can hear just fine with alsa, i've installed alsa-oss etc. I got it working in the line-in jack ONCE, but it only played in the left side of my headphones, and after that it didn't work again. In the volume control thing, it says i have 2 soundcards (as far as I know i only have one): Intel 82810AA-ICH (alsa mixer) and Cirrus Logic CS4299 rev 4 (OSS mixer). Neither of which seem to work with my microphone. Any help would be greatly appreciated.

Thanks.

Note: If there is a way to get it to work in skype and nothing else, that would be fine too.

---

### Post by encompass on 2006-08-01
try this... open the volume control...
file preferences... and make sure that you have the valone on your mike all the way up and that it is selected and not muted...
then try skype echo test...
the two sound cards are two drivers... one alsa and one oss... some programs need one and older ones need oss
make sure that you have it plug into the right port... and it could be what I had... a funky plug that worked when slightly pulled out.
and of all things skype is the worst when it comes to just working in linux.  I like ekiga better.

---

### Post by Skooj on 2006-08-01
erm, now all I get is 'problem with sound device'... i have no idea.. i tried doing something about the ac'97 thing from the comprehensive sound problem thread but that didn't seem to do anything.. uh... yea. would it maybe be easier to go out and buy an inexpensive pci card?

---

### Post by quicktime1 on 2006-08-02
I got it working right away as soon as I installed Skype. But nothing else works, not Audacity and not Sound Recorder. I get "problem with sound device" when I try Audacity, but not Skype. I read somewhere it has something to do with that Skype is using OSS I think? But yeah, no luck with ASLA for me. I have a ATI IPX sound card detected.

---

### Post by encompass on 2006-08-02
> **Skooj said:**
> erm, now all I get is 'problem with sound device'... i have no idea.. i tried doing something about the ac'97 thing from the comprehensive sound problem thread but that didn't seem to do anything.. uh... yea. would it maybe be easier to go out and buy an inexpensive pci card?

I got a cheap sb card from walmart and fixed all my problems... just disable the other one in bios first to make it easy. Or you could have both running.

---

