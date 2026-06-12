---
title: "card needs recording to stop/restart to correctly tune"
date: 2015-08-26
forum: Mythbuntu
---

### Post by zagor on 2015-08-26
Hi,

I'm on Mythbuntu 14.04 64bit, mythtv 0.27, with a WinTV-NOVA-T-Stick.
It used to work flawlessly but it is now giving me an issue.

When a recording starts, the card hangs with the message "tuning" and never actually tunes.
I found out that if I stop the recording and restart it, it tunes and records correctly.
Also, if the card is "tuning" and I start a second recording on the same mux, the latter records fine, whereas the former stil hangs in a "tuning" state.

Once it starts recording correctly, all other schedules are recorded correctly.
If I restart the PC or use mythwelcome to start the PC and record, it hangs in the "tuning" state and fails the recording. Again, I need to manually start another recording to let the card tune.

I've changed the DVB tuning delay from the initial 0 (used to work, though!) to 500ms, but no changes.
Signal timeout is set to 7000ms, tuning timeout is set to 10000ms.

Any suggestions?

Thanks

---

