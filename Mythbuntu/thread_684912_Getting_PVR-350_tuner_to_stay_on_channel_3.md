---
title: "Getting PVR-350 tuner to stay on channel 3"
date: 2008-02-01
forum: Mythbuntu
---

### Post by andrewb78 on 2008-02-01
I have just set up changing channels on my cable box, which in itself is working fine.  When I try to watch TV, however, I just get "snow."  I did not have this problem before when I tuned my PVR-350 to channel 3 and just used the cable box remote to change channels, so my suspicion is that the hardware tuner isn't getting set to channel 3.  In the setup for MythBackend, I did set "Preset tuner to channel" to 3 in the Input Connections menu for the only video source I'm using.  However, in /var/log/mythtv/mythbackend.log, I see lines like:

```
2008-02-01 15:18:48.102 TVRec(1): HW Tuner: 1 -> 1
```

which suggests to me that the backend sets the tuner to channel 1.

Suggestions?  What do you need to troubleshoot this?  I'm probably missing something obvious.

---

### Post by andrewb78 on 2008-02-01
I actually found an ad-hoc solution in another thread:

```
ivtv-tune -c 3 -d /dev/video0
```

This fixes the problem, and I can watch TV fine now.  Now, how do I get this to happen automatically?

---

