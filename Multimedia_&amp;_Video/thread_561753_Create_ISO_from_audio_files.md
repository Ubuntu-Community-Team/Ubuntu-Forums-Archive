---
title: "Create ISO from audio files"
date: 2007-09-27
forum: Multimedia &amp; Video
---

### Post by pofigster on 2007-09-27
Howdy!  Here's my story of craziness.

A friend needed me to copy an audio CD for me.  My CD burner is in my dead Windows SFF which I don't feel like opening up and taking out.  So, I'm just reinstalling Windows on that machine.  Since I didn't have a burner, I just ripped the audio into FLAC on my Ubuntu box and figured I'd just burn it from here.  But...it doesn't have a burner - the windows box does, and I can't find a program for XP that will burn FLAC to CD.

So, my question is, can I "burn" an ISO of the FLAC audio on this box and just move the ISO over to my windows box to burn to a CD and have it turn out an audio CD?  If I can, how do I?  Thanks!

PS I know this seems really dumb and I should prob just move the burner, but really, that SFF was hard to assemble, I don't want to take it apart.

---

### Post by eye208 on 2007-09-28
> **pofigster said:**
> So, my question is, can I "burn" an ISO of the FLAC audio on this box and just move the ISO over to my windows box to burn to a CD and have it turn out an audio CD?
No, because ISO files contain file systems in ISO 9660 format. Audio CDs do not have any file systems.

You could produce a BIN file instead, but that would be larger than the corresponding raw PCM audio data. Since all CD writing tools can write audio CDs from WAV files, I'd suggest you convert the FLAC to WAV and then burn that on the Windows box.

---

### Post by pofigster on 2007-09-28
Alright, thanks for the quick answer!

---

