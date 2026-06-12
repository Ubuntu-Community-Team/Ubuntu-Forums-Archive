---
title: "Any advice for diagnosing an Envy24 (ice1724) sound problem - warbling effect?"
date: 2012-06-06
forum: Multimedia Software
---

### Post by Curious00 on 2012-06-06
Just recently I've had the experience that for some unknown reason the sound through my Turtle Beach Catalina audio card starts really becoming distorted. It becomes a warbling repetitive sound. It happens from all applications and the problem is contained to this one card.  Audio which comes out of the sound circuitry which came installed on the motherboad works just fine.

I'm speculating that it might have to do with a recent automatic kernel upgrade to my Ubuntu 11.10 (currently 3.0.0-20-generic)? I don't know one way or the other; that's just my first uneducated guess.

Does anyone have any suggestions as to how I might go about finding a workaround? Unfortunately, VIA doesn't have any Linux drivers for this card, and I'm just using the standard Ice 1724 driver which comes preinstalled with Ubuntu.

I have had luck with finding workarounds for other kernel modules which have malfunctioned - such as my Realtek r8169 network driver which simply needs to be reinstalled periodically when the network slows to a crawl and becomes sporadic.

Would reloading the kernel module help my ice1724 problems? If so, how can that be done while the computer is running?

---

### Post by Curious00 on 2012-06-15
Well, I just thought I should offer the update that the problem seems to have been solved - probably by another one of the many updates that Canonical sends out on a regular basis.

---

### Post by Curious00 on 2012-06-19
Oops.... no it's not fixed yet.

I'm seeing that the problem seems to happen only after the computer goes to sleep and then wakes up again. Maybe that gives folks some more information that would help them know how to help me diagnose this?

---

