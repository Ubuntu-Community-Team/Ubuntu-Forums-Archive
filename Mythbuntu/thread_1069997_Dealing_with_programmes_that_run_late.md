---
title: "Dealing with programmes that run late"
date: 2009-02-14
forum: Mythbuntu
---

### Post by NautiusMaximus on 2009-02-14
I've just watched a recording that finished before the programme did. I assume (although I can't be sure) that this was because the programme was running late.

I'm sure I had a video recorder about 15 years ago that could cope with programmes that ran late and adjust recording times appropriately. Surely MythTV can do this?

Is there some option I need to set somewhere to tell it to adjust recording times if a programme is running late? I'm using Mythbuntu 8.10.

Thanks
NM

---

### Post by ian dobson on 2009-02-15
Hi,

There is an option in the recording profiles that allows you to get mythtv to start recording early and end late. When I get onto my mythtv box I'll have a look for it.

Edit: If you go to Configuration,TV,General on the 4th page (General Extended) there are2 options for early start and late end.

Regards
Ian Dobson

---

### Post by NautiusMaximus on 2009-02-15
Thanks, I think I've found the option. I can tell it to run a time of my choosing after the end of the scheduled finish time for all recordings. 

That will no doubt help, but still seems a bit unsatisfactory. Apparently it gets ignored if another programme is scheduled to start recording immediately after the first programme, which means I could still miss the end of a programme. And sometimes, for example if there was a football match that ran into extra time earlier in the evening, programmes can run more than just a few minutes late.

Can't the system tell if a programme is running late? My video recorder of 15 years ago could do it via a system called programe delivery control, although of course that was in the days before digital TV. 

Is there not an equivalent for digital TV? Or is it just that MythTV can't make use of it? Or is there an option hidden deep inside the configuration screens that I have yet to discover?

Thanks
NM

---

### Post by ian dobson on 2009-02-15
Hi,

With a digital tuner, just enable multirec and record 2 or more programs at the same time from the same multiplex. Just go to myth-setup, tuners and select your digital tuner. Then set the number of programms that can be recorded to 2 or more.

Don't trust the EPG 100%. My provider has the nasty habit of saying that a program starts at 8:15 then about 10 minutes before the recording starts they send new EPG that says the program starts at 8:17 and then at 8:15 they send EPG that the program starts at 8:14.

Regards
Ian Dobson

---

### Post by newlinux on 2009-02-15
> **NautiusMaximus said:**
> Thanks, I think I've found the option. I can tell it to run a time of my choosing after the end of the scheduled finish time for all recordings. 

That will no doubt help, but still seems a bit unsatisfactory. Apparently it gets ignored if another programme is scheduled to start recording immediately after the first programme, which means I could still miss the end of a programme. And sometimes, for example if there was a football match that ran into extra time earlier in the evening, programmes can run more than just a few minutes late.

Can't the system tell if a programme is running late? My video recorder of 15 years ago could do it via a system called programe delivery control, although of course that was in the days before digital TV. 

Is there not an equivalent for digital TV? Or is it just that MythTV can't make use of it? Or is there an option hidden deep inside the configuration screens that I have yet to discover?

Thanks
NM

There is a separate setting that you can enable per recording schedule or per recording that will make it record longer regardless... but it may cause another show not to get recorded - depending on how you have your recording priorities set.

---

