---
title: "Writing New MythCommFlag"
date: 2016-02-27
forum: Mythbuntu
---

### Post by gga96 on 2016-02-27
I am investigating what may be involved in writing a new mythcommflag. 

Finding frames to test would be at say every 100 frames (4s) until a change in state is found, then a binary search to fine tune the target. Random seek to a frame is required.

I have some questions:
Q 1: Does one of the **mythconverg **tables indicate when a video recording has finished being indexed? 
Q 2: Could you please explain the meaning and use of two fields** mythconverg.recordedseek.mark** and **offset**? (I am confused, ffmpeg uses a time reference to seek a random frame)
Q 3: Is a function providing TimeToOffset and OffsetToTime available?
Q 4: How close to the transition frame program/comm, is considered an acceptable time error?

Thanks.

Regards
Glen

---

