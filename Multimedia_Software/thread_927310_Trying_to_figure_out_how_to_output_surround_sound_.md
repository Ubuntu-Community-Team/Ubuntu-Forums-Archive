---
title: "Trying to figure out how to output surround sound to an older amp"
date: 2008-09-22
forum: Multimedia Software
---

### Post by p-stone on 2008-09-22
Hello all. 
I have an Audigy 2 ZS platinum soundcard, and a yamaha rx-v690 amp that I'm trying to get to output surround. Presently audio is played on all my speakers, however there is no actual surround functionality. My understanding of the cause of this issue is that my audigy is processing the surround internally, and outputting it to discrete channels on the sound card. However my amp is only equipped to do it's own DSP (digital signal processing) and lacks the ability to take discrete inputs. My Audigy also has an optical output and an s/pdif, however I'm not sure how to hook those up to the amp. If someone out there knows how to either make my regular audio port output all 5.1 channels right to the amp so it can decode them there or hook up one of the outputs I'd be very appreciative. I've got the manual for the amp and would be happy to send it to anyone who cares to try helping, it's too big to attach here unfortunately.

Thanks very much in advance

---

### Post by p-stone on 2008-09-24
An additional note. If I set my stereo to one of the dolby surround pro logic presets I get no sound out of my rear speakers, if I set it to something that only does DSP I will get sound out of my rear speakers, just a clone of what's coming out the front. 
running speaker-test -Dplug:surround40 -c4 -l1 -twav duplicates these results in that I hear the "front left" test from my front and rear left speakers. I recognize that this might not be completely the most appropriate forum to ask for help on, given that the issue is only peripherally related to linux. If anyone is aware of a more appropriate place online I could seek help or do further research I would also greatly appreciate that

Thanks again

---

### Post by p-stone on 2008-09-24
Apologies for the spam, I'm kind of using this thread as a place to compile my research as well as to seek help. From what I've researched my amp processes surround using dolby surround pro logic. This works through standard 2 line channels with additional encoding to provide channels for front left, front right, center and rear (mono). I think my goal is to get my computer to encode all audio into dolby surround pro logic, to be decoded by my amp. The lower level I can do this at the happier I'll be as I imagine it could grow to be quite a pain in the *** to setup for the various applications I use. I'm very new to the world of audio in general and definitely linux audio in particular so as before, any pointers would be appreciated. Is there some sort of pulse audio configuration tool I could use to set the format of my audio output?

---

