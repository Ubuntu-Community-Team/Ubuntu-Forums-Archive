---
title: "Hardy - snd-via82xx - sounds cuts in and out"
date: 2008-04-25
forum: Multimedia Software
---

### Post by batman01 on 2008-04-25
Hi all,

I'm running Hardy based mythbuntu, which has been updated to within a week or so ago. Its running on a Jetway j7f2, which has the via CN700 chipset. After a long (and succesfull) battle to get XVMC working on this chipset I have run into an audio problem.

My sounds works for a period of up to a day, and then begins to cut in and out. The sound will briefly go crackly and then disappear altogether. sometimes it will never come back at all, other times it comes and goes for 2 or three seconds at a time.

I can sometimes provoke it to come back for a short while by fiddling with the DXS channel volume in alsamixer. 

/etc/init.d/alsa-utils restart also seems to bring it back for a while, but then it will misbehave again.

dmesg shows nothing
/var/log/messages shows nothing
I can't find a log specifically for alsa anywhere

Can anyone suggest how I can proceed to diagnose this problem?

Thanks all,

Pete


EDIT: here's a wierd thing. I ran speaker-test to see if I got a similar problem, which I did, so I exited speaker test after it went silent. About 4econds after I had exited the speaker test utility I got about 3 seconds of pink-noise output. I think something is going seriously wrong with buffering somewhere.

---

