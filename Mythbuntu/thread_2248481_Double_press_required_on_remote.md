---
title: "Double press required on remote"
date: 2014-10-15
forum: Mythbuntu
---

### Post by ceesquared on 2014-10-15
This is not a killer problem, but I would like to resolve it. My LIRC file contains:-
begin
    remote = mceusb
    prog = mythtv
    button = KEY_RECORD
    config = R
    repeat = 0
    delay = 0
end
In order to record a programme I have to press KEY_RECORD twice, the first press seems to have no effect. If I use a keyboard then only one press is required. This does not occur with any other key on the remote. What is going on? I guess it could be solved by repeating the config=R line but this cures the symptom not the cause. Does anyone know what is going on?

---

### Post by ceesquared on 2014-10-30
Solved! Its the remote at fault (one 4 all). It does not transmit on the first press!

---

