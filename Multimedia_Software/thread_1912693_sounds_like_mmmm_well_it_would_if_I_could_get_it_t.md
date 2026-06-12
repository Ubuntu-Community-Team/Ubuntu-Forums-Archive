---
title: "sounds like mmmm well it would if I could get it to work"
date: 2012-01-21
forum: Multimedia Software
---

### Post by mikejen on 2012-01-21
Hi

Forgive me if I ask the same question others have asked but Im pretty new to playing with sound on Ubuntu.

Im running LUbuntu 11.10 RT. Can get some really impressive numbers if I just use midi, 96000 sampling with 2ms delay but because the behringer uses 16 bit 41000 that does seem to slow things up a bit.

In truth I'm getting lost in all the information available and losing track and therefore understanding.

Im trying to get to grips with Alsa/Jack concerning merging two mono ports into one stereo port (2 behringer UCG106) so that I can either have two guitars on at the same time or a guitar and mic.

I did manage to get one working but never two. Now I think Ive beggered up the thing anyway in being hamfisted and trying to run before I could walk. I know that using the alternatives in qjackctl setup I can get one to work while still outputting to my onboard sound (Intel whatever).

I'm getting stuck at what point to do the merge, UDev, .asoundrec etc. I think it has to be Udev but my knowledge about it ends after the v.

Falling foul of the fact that the ports dont always load in the same order, even had my midi keyboard as the default output at one point!

So there you go

Thanks

Michael

---

### Post by marinara on 2012-01-21
can't really help you but please list the software you're using.  And what the software is not doing.

---

### Post by mikejen on 2012-01-21
as to software ...

now 

alsa
jackd1

tried

pulseaudio
jackd2
alsa

various of the music stuff but mostly guitarix (because its just an amp with add ons and will amp voice as well as guitar)

The problem is getting both behringer dongle thingys to work, jack can use one or the other at the same time as the onboard sound. If I can combine the two mono units into one stereo unit then I can use that as the alternative in jack and thereby play and sing or my friend can play too, thats if I had a friend (playing on the pc doesnt get you to meet many people).

please excuse my humour but this stuff seriously drives you mad. Couldnt a patch bay type system do the same job in a graphical way? I know, Id have to write it.

Cheers


Michael

---

