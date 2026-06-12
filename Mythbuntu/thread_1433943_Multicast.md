---
title: "Multicast"
date: 2010-03-19
forum: Mythbuntu
---

### Post by archeryrob on 2010-03-19
I do some work with video in my job, security stuff. The video is all multi-cast and will gum up a network fast. We have to use L3 switches to direct traffic or on supplier has a L2 switch that uses IGMP-L2 to direct traffic on an L2 switch and prevent multi-casting.

Basically, without using Mythbuntu yet, If I setup a back end and cat6 cables to front ends at TV's so you can watch TV or upload a video, does it Milti-cast or Uni-cast or does it vary per application? Like TV multi-cast because it does not know who might want it and just uni-cast a video when requested by a device?

I am trying to figure if the TV's and AV stuff should be on a separate 8 port switch to kind of make a parallel network to try and contain the AV stuff away from the computer stuff, but still allow both access to the net and each other.

---

### Post by timconradinc on 2010-03-19
It's unicast. It's just a single stream between the backend and the frontend.

---

### Post by archeryrob on 2010-03-19
And I can have several fronts end to only one back end?

---

### Post by tgm4883 on 2010-03-19
> **archeryrob said:**
> And I can have several fronts end to only one back end?

Yes

---

