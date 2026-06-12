---
title: "firewire w/ .24 and Motorola Qip7200-2"
date: 2010-12-05
forum: Mythbuntu
---

### Post by hicotton02 on 2010-12-05
So I finally decide to start trying to connect my mythtv setup to my actualy TV. I have been using MythVideo excusively for over a year now.

I have a Motorola QIP7200-2 STB and I used a firewire cable to connect it to my mythtv computer. 
I have a working connection in that I can go into mythtv-setup and select capture cards and use firewire, the GUID and model comes up. I, then go to input connections and set that. Then i try to go to mythfrontend and watch tv to see if it magically works, and it does not. i chick watch tv then it tries something and kicks back to the main screen. Am i missing a configuration step?

---

### Post by hicotton02 on 2010-12-09
nothing?

/sadpanda

---

### Post by thatguruguy on 2010-12-09
Do you have a tuner in your computer?  What kind?

---

### Post by hicotton02 on 2011-01-07
whoops, didnt get an email notification that there was a response. I have a HVR-1600. But im sure that I can watch the video through the firewire itself. I did it using windows.

---

### Post by newlinux on 2011-01-08
can you currently do it using windows? They can change the Copyright protection settings on any channel at anytime in a way that a non 5C device won't be able to use the firewire.

Other than that - would need to see what's in your logs. Is you start channel a known channel where with the proper 5C settings?

---

### Post by hicotton02 on 2011-01-21
Ok so I got it working sortof. i can view some channels (both SD and HD) but there is about 40-60% of the channels that cant get a lock. I have tried playing with the bitrate and such in the mythtv-setup but to no avail.

---

### Post by newlinux on 2011-01-21
> **hicotton02 said:**
> Ok so I got it working sortof. i can view some channels (both SD and HD) but there is about 40-60% of the channels that cant get a lock. I have tried playing with the bitrate and such in the mythtv-setup but to no avail.

Are you sure those channels don't have copy content protection turned on? If they do that is why you can't lock on them.

---

### Post by Victormd on 2011-02-16
hicotton02, where did you get the info to get it up and running - even if "sort of". I have the same setup and I know that my connection is working because the test-mpeg2 script was able to capture the video for a specified channel.

I have the same problem you did where mythtv would try to do something then kick me back to the menu.

Are you using a channel changer script or the mythtv default?
How are you acquiring you channel lineup?

I have more questions but will settle for these right now.
Thanks

---

