---
title: "Partial recording of conflicting programs"
date: 2014-08-02
forum: Mythbuntu
---

### Post by hhveluj on 2014-08-02
Hello, 

  To my surprise, it looks like mythTV is completely skipping the recording of a conflicting program, even if the overlap is only few minutes. Is there a way to tell mythTV that it is okay to record partial programs? Let's say I have a recording A set for 8:00-9:30 and recording B for 9:00-11:00. Instead of recording just A, I would like to have recording A and the last hour and a half (from 9:30 till 11:00) of recording B. How do I do that? 

Thank you very much!

---

### Post by Gillingham on 2014-08-02
I assume you have read the howto on the mythtv wiki about scheduling [http://www.mythtv.org/wiki/Scheduling_Recordings]("http://www.mythtv.org/wiki/Scheduling_Recordings")

Conflicting programs is not one I have had too often as I have several tuners.  But should the situation come up I think my way around this would be to manually schedule program B, remembering that mythtv by default adds some extra time to the recordings to allow for overruns, this can be set to zero (or indeed less than zero if programs regularly finish early) on a schedule by schedule basis. 

David

---

### Post by hhveluj on 2014-08-04
Hello David,

 Thank you for the reply! Yes, I've read the howto.
Manual solution is possible, but cumbersome. It seems that this is a very straightforward task/need - just start the next recording if the current one is done, even if the next one is not from the beginning. Every commercial DVR I've had does this by default, and they don't have 1/100th of the options and features that mythTV provides. I am extremely impressed with mythTV's possibilities, but surprised it can't do such basic thing.

---

