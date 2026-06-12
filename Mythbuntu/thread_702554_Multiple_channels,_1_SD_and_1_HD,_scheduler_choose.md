---
title: "Multiple channels, 1 SD and 1 HD, scheduler chooses both"
date: 2008-02-20
forum: Mythbuntu
---

### Post by dannyboy79 on 2008-02-20
I have a SBE with a PVR-500 (cable directly hooked to tuner) and a MBE with a PVR-350 (s-video in from STB). I have a digital lineup from Time Warner Milwaukee, WI (using Schedules Direct). I get the same channels like 24 (SD) 524 (HD) and so on. channel 4 call sign is WCGV and 524 callsign is WCGVDT.

The problem is that when I go to the scheduler and tell it to record UFC Wired at any time on any channel, it'll set to record it on channel 24 on tuner 2 (one of the pvr-500 tuners) and it'll set to record it on 524 on tuner 1 (the pvr-350 with s-video in).

So how can I solve this issue? Picture quality isn't an issue because I am capturing the 524 HD channel downconverted thru the s-video cable so it's no worse or better than the PVR-500. I just don't need both tuners being used to record the same show. Please help me solve this issue. Thanks

---

### Post by foxbuntu on 2008-02-20
> **dannyboy79 said:**
> I have a SBE with a PVR-500 (cable directly hooked to tuner) and a MBE with a PVR-350 (s-video in from STB). I have a digital lineup from Time Warner Milwaukee, WI (using Schedules Direct). I get the same channels like 24 (SD) 524 (HD) and so on. channel 4 call sign is WCGV and 524 callsign is WCGVDT.

The problem is that when I go to the scheduler and tell it to record UFC Wired at any time on any channel, it'll set to record it on channel 24 on tuner 2 (one of the pvr-500 tuners) and it'll set to record it on 524 on tuner 1 (the pvr-350 with s-video in).

So how can I solve this issue? Picture quality isn't an issue because I am capturing the 524 HD channel downconverted thru the s-video cable so it's no worse or better than the PVR-500. I just don't need both tuners being used to record the same show. Please help me solve this issue. Thanks

If you open mythtv-setup (Backend Setup) you can change the priority number of one of the tuners and it should limit the recordings to a single tuner.

---

### Post by dannyboy79 on 2008-02-20
that's not my goal. isn't there a way to change the callsign to be the same for each channel or whatnot. I thought I read that but wanted to ask before I screwed something up. like I said, it doesn't matter if Lost gets recorded on 512 or 12, it's just that when I tell the scheduler to record a show at any time on any channel, it sets it to record it both on channel 12 and 512.

---

### Post by dannyboy79 on 2008-02-22
bump

---

### Post by dflipb on 2008-02-23
I found I got this same problem, I fixed it by changing the frequency of the recording, I think changed it to something like  only on this channel, or something like that, you can also set the preference of the tuner in your scheduler.

Hope that helps

---

