---
title: "Setting up an input with subset of channels?"
date: 2012-06-29
forum: Mythbuntu
---

### Post by NikosF on 2012-06-29
I'm embarrassed to be asking this, having used Myth since 2006, but never had to set this functionality up before.  I was a long time Fedora / self-compile person, but have now jumped on the mythbuntu bandwagon and wondering why I didn't earlier!

I have Comcast and three tuners - a HDHomerun Prime, a regular HDHomerun and an analog tuner.

I'd like to set the analog tuner to record only the HBO channels from my cable box

I'm not sure how to set this up.  All my channels are via cable - so I have only one lineup with Schedules Direct.  So - when I link my
analog tuner to my source the analog tuner wants to be able to record everything (which I don't want it to do - I want it to only record HBO
which the Prime can't do obviously).

How can I achieve this?  I feel like I've struggled through much worse (like DVB-S and -T cards before moving to the US) but this has me stumped.

---

### Post by Boppy3125 on 2012-06-29
Its all in the connections of the tuner to the source to the listing.  You create different listings, say in Schedules Direct, that have the channels you care about.  Then you create different sources, say an HBO one that uses the listing that only includes HBO.  Then that tuner gets that source.

That is all from memory, so I might have something phrased a little off, but I think that would get you close.

---

