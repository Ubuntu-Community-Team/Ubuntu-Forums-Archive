---
title: "prebuffering problems"
date: 2009-09-23
forum: Mythbuntu
---

### Post by dano1 on 2009-09-23
am having prebuffering problems on my mythbuntu setup; stuttering playback on live feeds. Have tried all tips on the myth page as well as searches. Have used both onboard sound and cmi soundcard with no success. Any one have any tips?

See my myth logs. 

TIA, danny

---

### Post by dano1 on 2009-09-28
bump.

---

### Post by SiHa on 2009-09-29
Now I'm no expert on the various causes of the infamous 'Prebuffering Pause', but yours all seem to be preceeded by "Write Audio: Buffer Underrun". Have you tried enabling the 'Agressive Soundcard Buffering' option in the frontend setup?

---

### Post by scottcrawford on 2009-09-29
I had a similar problem. I had enabled realtime priority, and enabled extra audio buffering in myth. Turned out that when I unchecked the extra audio buffering option, my playback became smooth and no more prebuffering pause errors. Also, I don't have aggressive buffering enabled.

---

### Post by dano1 on 2009-09-30
> **scottcrawford said:**
> I had a similar problem. I had enabled realtime priority, and enabled extra audio buffering in myth. Turned out that when I unchecked the extra audio buffering option, my playback became smooth and no more prebuffering pause errors. Also, I don't have aggressive buffering enabled.

that was the ticket. thanks. smooth as silk now.'

---

