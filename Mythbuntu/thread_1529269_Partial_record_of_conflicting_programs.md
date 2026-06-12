---
title: "Partial record of conflicting programs"
date: 2010-07-12
forum: Mythbuntu
---

### Post by R3M3 on 2010-07-12
I was a bit frustrated when I discovered that MythTV decided it wasn't going to record a program which ran 8:00pm-9:00pm because it was "conflicting" with a slightly-higher priority show on another channel which ran 8:59pm-10:00pm. In other words, because I wouldn't have been able to see the credits and the after-show adverts, MythTV decided I wasn't interested in the other 98% of the program.

Is there some setting which I can turn on to tell MythTV to record partial programs anyway? Ideally I'd be able to set a threshold, (e.g. "If the programs overlap by more than 5 minutes, then only record one, but if it's less than 5 minutes, then give me the partial program.") but I'll take a simple "always record partial programs" switch. I'd prefer the switch to be global, but I'll take a per-recording-rule option to.

Thanks.

---

### Post by ian dobson on 2010-07-12
Hi,

What tuners are you using? If you've got digital tuners you could enable multirec which allows you to record several programs from the same multiplex at the same time.

The only other thig to do is set the record early start/delayed end to 0 minutes. Or just let mythtv try and workout whats going on and record a repeat of one of the programs.

Regards
Ian Dobson

---

### Post by newlinux on 2010-07-12
You can also check your upcoming recordings (you could use mythtv-status to email you as well). You will be notified of any conflicts and can adjust start/end times appropriately. If it is a recurring set of overlaping programs you could permanently adjust their recording schedules to not overlap.

---

### Post by LowSky on 2010-07-12
> **ian dobson said:**
> Hi,

What tuners are you using? If you've got digital tuners you could enable multirec which allows you to record several programs from the same multiplex at the same time.


I didn't know this was possible with Myth... Too bad I live in the US, and we have very restricted QAM in place. I only get local channels without using a cable box. and if this works the way I think... there isn't anything I want to record on the channels using the same mutiplex 

For example 7_1 is ABC, and 7_2 is ABC Weather. Not something I want to record.

---

### Post by newlinux on 2010-07-12
> **LowSky said:**
> I didn't know this was possible with Myth... Too bad I live in the US, and we have very restricted QAM in place. I only get local channels without using a cable box. and if this works the way I think... there isn't anything I want to record on the channels using the same mutiplex 

For example 7_1 is ABC, and 7_2 is ABC Weather. Not something I want to record.


Those are most likely the numbers the actual stations are mapped to using PSIP, not what multiplex you are on. For instince for me 11.1 is CW and 13.1 is Fox, but they are on the same multiplex as other stations are (The 111- multiplex). You may want to check the frequency as it is possible you have more channels per multiplex than you think. (of course you may not - this varies greatly).

---

### Post by LowSky on 2010-07-12
> **newlinux said:**
> Those are most likely the numbers the actual stations are mapped to using PSIP, not what multiplex you are on. For instince for me 11.1 is CW and 13.1 is Fox, but they are on the same multiplex as other stations are (The 111- multiplex). You may want to check the frequency as it is possible you have more channels per multiplex than you think. (of course you may not - this varies greatly).

Yeah I'm going to check this out when I get home... my HVR-2250 might be much more valuable than I thought it was, lol.

---

### Post by R3M3 on 2010-07-12
> **ian dobson said:**
> 

What tuners are you using? If you've got digital tuners you could enable multirec.

The only other thig to do is set the record early start/delayed end to 0 minutes. 

Or just let mythtv try and workout whats going on and record a repeat of one of the programs.


I only have one digital tuner, and it only handles one channel. Multiplex is set up, so I can simultaneously record, say 22.1 and 22.2, but that wouldn't help in the situation I encountered, where simultaneous recording needed to happen on both 4.1 and 22.1

Start/end delay is already set to 0 min. What I encountered was the TV station showing one of those "plus sized" episodes with an actual listed starting time of 8:59 (thus overlapping a single minute with the program scheduled to 9:00 on another channel).

Luckily, the episode I did miss will repeat, but I can't blithely assume that will always be the case - many shows only have the one showing, and won't repeat until we get into re-runs several months later. (Or, since we're already in re-run season, won't repeat at all.)

I'd also prefer not to have another thing to check on every morning. (When I first set up the box, I did regularly check the upcoming recording screen for conflicts, but that got old fast, and regular checking is a hassle for once-in-a-blue-moon conflicts like the one-minute overlap I just encountered.) 

Isn't there a way just to tell MythTV to record the partial program anyway?

---

### Post by ian dobson on 2010-07-13
Hi R3M3,

With mythtv a recording is an all or nothing thing. I can't think of a way to tell mythtv it's OK if you miss the first X minutes (where X is a variable that depends on user/program to be recorded/phases of the moon).

The simplest solution is to get a second tuner.

Regards
Ian Dobson

---

### Post by LowSky on 2010-07-13
> **ian dobson said:**
> 
The simplest solution is to get a second tuner.


This is the exact reason I purchased a HVR-2250, it has 2 tuners built into one card. And the reason I might buy another one, lol.

---

### Post by newlinux on 2010-07-13
> **ian dobson said:**
> Hi R3M3,

With mythtv a recording is an all or nothing thing. I can't think of a way to tell mythtv it's OK if you miss the first X minutes (where X is a variable that depends on user/program to be recorded/phases of the moon).

The simplest solution is to get a second tuner.

Regards
Ian Dobson

Or if this happens on a couple of specific shows either setup manual recordings or set the back to back recording rules up so that they don't overlap.

Also, please note that with QAM the channel number does not necessarily tell you what multiplex a channel is on (The channel numbers are most often the result of PSIP mapping of the frequency). While most likely 4.1 and 22.1 aren't on the same multiplex there is no reason they couldn't be.

---

