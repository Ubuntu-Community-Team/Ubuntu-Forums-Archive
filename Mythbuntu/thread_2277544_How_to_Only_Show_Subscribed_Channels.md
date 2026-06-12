---
title: "How to Only Show Subscribed Channels"
date: 2015-05-09
forum: Mythbuntu
---

### Post by chris_g2 on 2015-05-09
I've currently changed my FiOS subscription to Local Channels, but they also give a ton of HD content for free.

I'm subscribed to Schedules Direct for the programming guide info, so I use that to populate my EPG.

It can get difficult because it has over 700 channels which we're only subscribed to maybe 100 of.  Since this is a new package for me, I really have no idea which ones we have and which ones we don't.

With that said, what's the simplest way to get MythTV Front Ends and MythWeb to only show channels I am able to see?

Thanks!

---

### Post by elliott6 on 2015-05-20
Chris,

I've been out of the "game" for a bit, but from what I remember, it was done by going into your Schedules Direct subscription (site) and then toggling on/off the channels that you have. That would dictate what was sent over/refreshed on the mythfilldatabase call.

If that's not correct, then it would need to be done on the backend channel configure, where you would need to remove the unwanted channels. Although, and this would need to be confirmed, that you could remove all channels, and then reimport based on your revised Schedules Direct feed. 

Again, apologies if the above is not correct, but life has caught up to me, and we don't spend as much time watching TV, and even less time for me caring for all of my devices. I'm looking to start back up, hence the visit, so hope this is correct/helps!

elliott

---

