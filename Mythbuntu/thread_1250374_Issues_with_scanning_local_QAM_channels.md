---
title: "Issues with scanning local QAM channels"
date: 2009-08-26
forum: Mythbuntu
---

### Post by wallawalla313 on 2009-08-26
Hi all,

I'm a new MythTV user, although an experienced Linux user. I just picked up a Hauppauge HVR-1250 based on all the positive feedback out in the community. However, I'm having some trouble getting it to work properly with Time Warner.

My setup:
Hauppauge HVR-1250
Jaunty Jackalope + Mythbuntu packages installed via Synaptic
Display: nVidia PCIE graphics card (DVI to TV)
Time Warner San Diego - I'm subscribed to data service only - no cable TV

Here's what I got working:
I plugged a rabbit ears antenna into the Hauppauge before I realized I could get the same channels for free through TW. I was able to do a full channel scan and detect some channels, but a few (Fox, CBS) were poor quality due to all the valleys around here. I then plugged the Hauppauge directly into TW's program and did a rescan (QAM-256, Cable options selected). MythTV added dozens of new channels, most of which didn't work at all. However, it left the existing channels I had detected and the quality was perfect.

Seeing the quality difference, I returned the rabbit ears to Radioshack and kept fiddling. In an attempt to get the listings with schedule direct, I deleted all the channels and did a rescan. This is where the problems began. I'm now no longer able to get any of the terrestrial channels that worked before (5, 8, etc.) Although I was able to get a better signal through TW than through the rabbit ears, doing a full scan doesn't pick them up at all. I've tried scanning with Cable, Cable HRC, Cable IRC, and the various other options to no avail. I also tried adding the channels back manually, but it doesn't seem to work. When I go back to the front end, it just blinks when I click on "Watch TV". Note that the full scan DOES pick up all the dozens of non-working channels it did before, just none of the lower channels.

Any advice here on getting the scan to work or manually adding the channels back? Do I need to go buy the rabbit ears again just to get the channels detected into MythTV?

Thanks!

---

### Post by novellahub on 2009-08-26
Try deleting your tuner and then do the re-scan after you set it back up.

---

### Post by LowSky on 2009-08-26
you say you dont pay for cable service, its probably the reason you dont get any channels. Even with Cable you pay for the local channels. TimeWarner probably saw the glitch and fixed it. Happens all the time.

---

### Post by wallawalla313 on 2009-08-28
I tried deleting the tuner and re-adding with no luck. I also went back and purchased a set of rabbit ears to re-add the channels, and then plugged it back into the wall. No luck!

I guess Time Warner must have had me on basic service by accident after all. I'm really surprised they were able to "detect" that and make the change. I guess I'll be paying them after all... :(

Thanks for the info!

---

### Post by mitchell2345 on 2009-08-28
fyi, even if you had cable service scanning your OTA channels and then plugging into your cable is never going to work....its broadcast in a completely diff matter and channel/freq.

Mitchell

---

