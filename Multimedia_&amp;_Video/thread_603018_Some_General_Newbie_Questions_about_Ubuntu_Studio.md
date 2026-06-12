---
title: "Some General Newbie Questions about Ubuntu Studio"
date: 2007-11-04
forum: Multimedia &amp; Video
---

### Post by wilberfan on 2007-11-04
More out of curiosity than anything, I installed the Ubuntu Studio 7.10 this morning.    I chose the 64-bit version for my AMD64x2 4400+ box...

I had hoped to get JACK working--but I'm beginning to think that that may not be in the cards, and I'm wondering if it might be the limitations of my sound card?   It's an Audigy SE (CA0106).  Anyone know if that should work with JACK??  Or do I need a more robust sound card?

The sound card works great with XP and all the other flavors of Linux I've tried (Dapper, Edgy, Feisty, Gutsy, Sidux, PCLinuxOS, OpenSuSE, Sabayon, etc), and I can record and play back from Audacity...   I have to raise the frames/period setting in Jack just to get it from stopping prematurely.

I'm also curious why the JACK gui looks so abominable (see attached)?

I have a vague understanding of the benefits of low-latency--but what are the tradeoffs?   How will it affect my non-video/audio apps?  Just curious.

---

### Post by Drunky on 2007-11-04
Try [this]("http://www.ubustu.com/globe/2007/05/29/how-to-configure-jack-in-ubuntu-studio/") guide to setting up Jack.

I imagine you should have Jack up and running in a matter of fifteen minutes.


[edit] This guide recommends setting the Frame/Period to 64.  My machine would not work with this.  I had to set it to 128.

---

### Post by wilberfan on 2007-11-04
Been there, tried that....  even selecting 4096 gives me XRUN Callback errors...

---

### Post by Drunky on 2007-11-04
I've also heard about trouble with the Sample Rate.  Some cards are set to sample at 44.1k and I believe Jack defaults to 48k.

---

### Post by wilberfan on 2007-11-04
> **Drunky said:**
> I've also heard about trouble with the Sample Rate.  Some cards are set to sample at 44.1k and I believe Jack defaults to 48k.

I AM getting a message about "record rate different from playback rate" (or vice-versa?)...   Is there a way around this?

---

### Post by wilberfan on 2007-11-05
More evidence that my sound card is inadequate to the task?   I got a decent latency number (2.9) when I changed the Audio setting to "Playback" instead of "duplex" (see attached capture--red highlights).   (I was even able to enable the "realtime" setting.)  Absolutely no XRUN errors with these settings...

Any idea why it still says "48000" in the status window (blue highlight), when "44100" is clearly selected in the setup window?

(And why the ugly look to the GUI?)  :(

---

