---
title: "6200ch works in LiveTV, but recordings fail to change channel"
date: 2008-02-28
forum: Mythbuntu
---

### Post by rabbitsnake on 2008-02-28
I have a Haup 150 card pulling video/sound from my DCT6200 over coax and I am trying to change channels using firewire, instead of a IR blaster.

I set the external channel change command as 6200ch in the input connection and everything seems to work great.

6200ch changes channels correctly from within LiveTV and from the terminal on my DCT6200, however any scheduled recording fails because it cannot change the channel. 

The event in MythBackend.Log is below. 

Channel(/dev/video1): SetInputAndFormat() failed
TVRec(7) Error: Failed to set channel to 750. Reverting to kState_none


Is there something I am missing for the recording to work?

Thanks.

---

### Post by rabbitsnake on 2008-03-03
Fixed my own problem. 

I completely removed all capture cards, video sources, and input connections from my host and then recreated them all  and it works now. I also made sure that I choose Fetch Listing from Channel Source on the Input Connection to ensure that the XMLTV ID appears correctly in the database.

---

