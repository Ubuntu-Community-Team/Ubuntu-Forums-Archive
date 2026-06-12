---
title: "No Sound with Message Update Info!!!"
date: 2009-06-28
forum: Multimedia Software
---

### Post by drifter2502 on 2009-06-28
I switched on my computer today and was met with the following message--Refresh Advanced Linux Sound Architecture (ALSA) configuration presets

New Advanced Linux Sound Architecture (ALSA) configuration presets have been added.  Please execute the asoundconf(1) set-default-card macro in a Terminal now to refresh your user's configuration presets.  You may accomplish this task by executing the following command in a Terminal: asoundconf set-default-card

AND NO SOUND!!

If I do this in a termnal I get this with all permutations...
tc4@tc4-desktop:~$ asoundconf set-default-card
You have omitted a necessary parameter.  Please see the output from `asoundconf list`, and use one of those sound card(s) as the parameter.

tc4@tc4-desktop:~$ asoundconf list
Names of available sound cards:
M5461
Phone
Live
tc4@tc4-desktop:~$ M5461 asoundconf set-default-card
bash: M5461: command not found
tc4@tc4-desktop:~$ 

It took me weeks to set my sound up and now I have lost everything. Can someone help me please as to how I tackle this problem. I have been very patient with sound problems in ubuntu but this kind of thing is beginning to sap my interest.

Anyway,why wasn't this update sent via the update manager?

---

### Post by kostkon on 2009-06-28
You can do it like this
```
asoundconf set-default-card M5461
```
but if you have a recent version of Ubuntu the above will not make any difference.

What version of Ubuntu do you have?

---

