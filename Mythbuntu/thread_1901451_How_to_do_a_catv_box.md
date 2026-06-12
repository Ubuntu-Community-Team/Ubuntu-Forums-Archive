---
title: "How to do a catv box?"
date: 2011-12-28
forum: Mythbuntu
---

### Post by RideMan on 2011-12-28
Okay, I know I can do this, and I have tested the elements, but I can't find any instructions to make it work.  This has got to be simple...

I have a Motorola DCH3200 CATV box.  The box changes channels, but I can't get any video out of it.

I have a Hauppauge tuner card with an S-Video input, and I can get video and audio out of that if I change channels manually.

I want this to be the system's third-line tuner...so first the ATSC tuners, then the NTSC tuners, then the cable box if all else fails.

1) Do I need to set up the S-Video input of the tuner card as a fifth interface card?  Or should I just use the S-Video input on the existing #4 tuner?

2) How do I tell MythTV to use Firewire to change channels and S-Video for video?  I see that a lot of people are doing this, but I don't see any instructions for combining the inputs...

---

### Post by RideMan on 2012-01-02
Okay, now I get it. Apparently while mybuntu now contains a copy of 2600ch that is not accessible. I ended up recompiling 2600ch and then calling it as an external channel changer.

---

