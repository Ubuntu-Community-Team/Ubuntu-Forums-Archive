---
title: "Surround sound in Mythbuntu with Nvidia ALC883"
date: 2008-01-11
forum: Mythbuntu
---

### Post by AlecJ on 2008-01-11
My problem is :-

I can't get surround sound from my Mythbuntu box.

Mythbuntu 7.10 64AMD
on board Nividia ALC883 7.1 with 6 jack sockets

Had the same problem with the same motherboard MSI K9N6GM (some sites put an S in the code name)

I followed this Howto

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

To update the alsa driver to 1.0.15
This works great with Gusty 64AMD and sounds sort of ok but when I try the same with Mythbuntu the result is total sound lose and the system stops reconizing the sound card. From which the only way I have found to recover is to reinstall from scratch losing all saved recordings.

Mythbuntu finds the card as HDA-intel where as Gutsy with alsa1.0.15 finds HDA-Nvidia and gives full control of each output front,side,rear and LFE.

Mythbuntu has trouble compiling the driver, loads of error 1's and 2's, but will get there in the end.

I have wondered if it's just the wrong mixer in Mythbuntu, but any upgrade there seems to also upset the sound.

I have to recompile the kernel on mythbuntu because of it won't see the Nova T-500 tuner, but I have tried doing the sound upgrade before and after this upgrade with the same results.

I'm looking to use the analog outputs

Any help would be great, it's driving me nut's with a room full of speakers doing nothing!

Thank in advance

---

### Post by laga on 2008-01-12
Well,

the best solution would be getting your ALSA drivers to compile, I suppose. Can you show us the exact error messages on Mythbuntu? Since Mythbuntu and Ubuntu shouldn't differ with regad to the kernel I don't see why we can't make it work :)

---

### Post by AlecJ on 2008-01-12
The errors are to do with ,no such file or directory, normally at the end of the driver compile.

I'm thinking I should use gksudo instead of sudo as I'm not mythtv user?

There must be some difference's with the Dir layout?

What about the mixer, the standard one shows the check boxs for front,side,center,lfe rear but there is no control. If I load the alsa mixer from sinaptic it has no effect.

---

### Post by AlecJ on 2008-01-13
The error is
configure seems to ignore the datarootsetting
which appears as one of the lines while configure is runnung.

lost it all again and had to start from scratch once more.

---

