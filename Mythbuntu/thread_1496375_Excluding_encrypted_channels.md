---
title: "Excluding encrypted channels"
date: 2010-05-29
forum: Mythbuntu
---

### Post by NautiusMaximus on 2010-05-29
I have just spent a frustrating time troubleshooting some errors in my backend log, and eventually figured out that my MythTV system had attempted to record programmes from encrypted channels, like TOPUP TV, and failed. It then threw a wobbly because it couldn't find the recording.

Is there any way, when I set a recording schedule to "record at any time on any channel", to let it know that I should exclude certain channels?

I'm using Mythbuntu 9.10.

Thanks
NM

---

### Post by ian dobson on 2010-05-29
Hi,

I think the only way to do something like that would be to disable all encoded channels. Just run myth-setup and set the encoded channels to invisible.

Regards
Ian Dobson

---

### Post by NautiusMaximus on 2010-05-29
Thanks Ian, that sounds like a sensible suggestion. I've done as you say, and the encrypted channels are no longer visible to me if I look at the EPG for scheduling recordings, so with a bit of luck they'll be invisible to MythTV as well.

Fingers crossed...

---

### Post by ian dobson on 2010-05-30
Hi,

The mythtv scheduler doesn't have xray vision, so it won't see the invisible channels either.

Regards
Ian Dobson

---

