---
title: "video_ts plays fast with VDPAU"
date: 2009-11-10
forum: Mythbuntu
---

### Post by Boppy3125 on 2009-11-10
I have a 8400GS, I think it is.  When I use one of the VDPAU playback settings, my recordings seem to work fine.  But when I try and play my movies that are ripped just to video_ts folders, the playback is speed up.  I can select change the time stretch and change it back to fix it.  But that is just messed up, and my wife doesn't think that is much of a workaround.  Anyone else seeing this?

---

### Post by Dewey_Oxberger on 2009-11-10
I have an 8300 based board and I was seeing it.

I made a custom playback profile that used only the Bob deinterlacer.  Then I installed cpufrequtils and tinkered with cpufreq-info and cpufreq-set.  I set the min freq to 1.8G.

Somewhere in all that tinkering it started working so I installed cpufreqd and changed the cpufreq.conf to set the ac power = on profile to have a min of 1.8G.  It works now.

---

### Post by jyavenard on 2009-11-11
it's a bug in mythtv...

doesn't occur with just vdpau

---

