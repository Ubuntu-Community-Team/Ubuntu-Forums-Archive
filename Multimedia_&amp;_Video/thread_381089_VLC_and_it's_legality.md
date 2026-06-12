---
title: "VLC and it's legality"
date: 2007-03-10
forum: Multimedia &amp; Video
---

### Post by TheForkOfJustice on 2007-03-10
I need to know if VLC (even if it is GNU) is free of possible copyright problems since I heard it plays mp3s out of the box.

Should I be able to install it and its dependencies in a new distro without running afoul of lawyers?

---

### Post by ssavelan on 2007-03-10
is libxine-extracodecs legal?

---

### Post by TheForkOfJustice on 2007-03-10
> **ssavelan said:**
> is libxine-extracodecs legal?

Is that an honest question or an "Is the Pope Catholic?" statement?

---

### Post by ssavelan on 2007-03-10
No, I am honestly curious about the codec legality situation.  Maybe someone who actually knows something can set the record straight on both accounts.

My guess is that you may not package a distro that can play mp3's or dvd's and distribute it.

You could probably make a script that will do everything for the recipient after they recieve the "product."

I hope an expert posts to this thread; b/c, it is an interesting subject.

---

### Post by jswhite on 2007-03-10
Not sure if I'd qualify as an expert on the issue, but I've at least looked at it a bit. IIRC, the issue with .mp3 playback is patents. The issue with libdecss is copyrights, sorta. It violates the DMCA, in the US at least.

Install them on on your computer and you'll likely get arrested by the same people who raided your house to arrest you for those evil copyright-violating mix tapes you made when you were a kid.

---

### Post by tommcd on 2007-03-11
Zenwalk linux comes with all the multimedia codecs installed out of the box. They have libdvdcss and libdvdread in their repos. They are based in France though.

---

### Post by TheForkOfJustice on 2007-03-11
So we should watch out for the packages:

libdvdcss
libdvdread
w32codecs

I think those are the ones?  Correct?

---

### Post by Darkhack on 2007-03-11
If you want to remain perfectly legal in the United States, you must disable the multiverse repository.  The restricted repos and the non-free stuff (flash, java, ATI/Nvidia drivers) isn't free software but is all legal and you won't have the FBI knocking down your door.

For those of you who say "who cares, we aren't going to get caught", you better think again.  I was issued a cease and desist from Universal Studios for copyright infringement and was reported to the FCC which is why I've been very careful about what I do on all operating systems, but especially Linux since so many distributions are based outside the US or are so relaxed that they don't care about any violations from distributing illegal codecs.  Thankfully they aren't pressing charges and I won't end up in court but this is something that the Ubuntu community needs to take seriously and at the very least, the included default packages need to remain legal in the US.  I might even suggest disabling the multiverse repo by default.

---

### Post by TheForkOfJustice on 2007-03-11
> **Darkhack said:**
> If you want to remain perfectly legal in the United States, you must disable the multiverse repository.  The restricted repos and the non-free stuff (flash, java, ATI/Nvidia drivers) isn't free software but is all legal and you won't have the FBI knocking down your door.

For those of you who say "who cares, we aren't going to get caught", you better think again.  I was issued a cease and desist from Universal Studios for copyright infringement and was reported to the FCC which is why I've been very careful about what I do on all operating systems, but especially Linux since so many distributions are based outside the US or are so relaxed that they don't care about any violations from distributing illegal codecs.  Thankfully they aren't pressing charges and I won't end up in court but this is something that the Ubuntu community needs to take seriously and at the very least, the included default packages need to remain legal in the US.  I might even suggest disabling the multiverse repo by default.

Geez, were you a normal user or a distro-maker or installing linux on some business systems when they gave you the C&D?

---

### Post by jrusso2 on 2007-03-11
They day the FBI is knocking on the door for using my DVD on linux or playing a wmv file on linux is the day I leave.

That's just insane.


Jeanette

---

### Post by rsambuca on 2007-03-11
> **Darkhack said:**
> I was issued a cease and desist from Universal Studios for copyright infringement and was reported to the FCC

What exactly did they say you did, by the way.  Was it for DVD ripping, p2p, what?

---

### Post by rsambuca on 2007-03-11
It should be noted that VLC is shipped with the libdvdcss libraries included, and therefore the use of VLC to watch DVD's in the US is illegal under the DMCA.

For the mpeg's, you can pay a one-time fee of $2.50 to Mpeg LA for the rights to use the mpegs on a specific player.

Sorry, I don't know about mp3's.

---

### Post by ssavelan on 2007-03-13
> **jrusso2 said:**
> They day the FBI is knocking on the door for using my DVD on linux or playing a wmv file on linux is the day I leave.

That's just insane.

I agree; but I think that we should make an effort to remain legal.  Growing the open source formats is the way to go, ideally.

So, you are not supposed to be able to play a DVD on your computer without paying someone $10 or getting permission by other means?

---

