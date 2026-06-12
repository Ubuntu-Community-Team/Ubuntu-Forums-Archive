---
title: "how can i get sound in flash?"
date: 2008-05-31
forum: Multimedia Software
---

### Post by kureyamu on 2008-05-31
hello

a newby question 

my operating system is ubuntu hardy heron 8.04

i have no sound with flash

(sound with videos and cds is fine, but i have no sound on youtube or google video)

gnash has been installed and removed because there was no sound in hardy heron

adobe flash player has been installed, removed and re-installed but i have no sound in hardy heron

(adobe flash 9 plays with sound in debian and linux mint, similar operating systems, but not in ubuntu, so this is an ubuntu-specific problem, not a flash problem and not a linux problem. i dual boot ubuntu and debian on this computer, and debian has sound with flash)

when i test sound in System/Preferences/Sound/Devices ALSA does not beep on testing, so my current settings for Playback etc use ES1371 DAC1 (sound card ES1371 DAC2/ADC also beeps when tested)

so how to get sound with flash on ubuntu?

can it be configured in a terminal?

or is a specific update for this bug to be downloaded? 

all answers in clear english appreciated.

regards 

kureyamu

*[CENTER]microsoft was a popular 20th century software company[/CENTER]*

---

### Post by gandaran on 2008-06-01
kureyamu
        the flash sound problem has been discussed here many times, if you do a search you will find many help-full posts.
I don't have this problem, but by reading many post's I know some people have fixed the flash sound in different ways, others where not so lucky.
three things you could try:
1. install libflashsupport for pulse audio
2. just install flash 10, (amazingly it's works for some people)
3. forget pulse audio and set everything in you system to use alsa or oss

---

### Post by pantonio on 2008-06-01
After installing flash 10 I get sound on youtube videos.

---

### Post by kureyamu on 2008-06-01
hello gandaran and pantonio

i hope u are both well :)

me, smiling now, and surprised at the volume of youtube sound^ ^!

thank you, gandarin, for the suggestion about installing adobe flashplayer 10

i installed it and rebooted and my youtube sound was there, immediately

problem solved

best wishes

kureyamu  


*[CENTER]microsoft was a 20th century software company[/CENTER]*

---

### Post by kureyamu on 2008-06-15
hello

so Ubuntu is a big let down once again.

if the problem of "no sound in flash on youtube and bbc web sites" is common and "has been discussed many times," i wonder why it hasn't been fixed and why i can't manage to overcome the problem.

i installed the new flash player rather than the one offered by Synaptic Packet Manager and the sound worked immediately. after 3 or 4 days not using my computer, i log back in and again i have no sound in flash.

also when i first installed ubuntu hardy heron, alsa worked fine. now when i go to System/Preferences/Sound and test alsa, it gives no sound so i have to use an alternative.

the sound works on similar operating systems such as debian and linux mint, so please software developers, can't you ask them nicely for their code, and put it into ubuntu so we can have sound too?

regards
kureyamu

---

