---
title: "Live TV - Can't change channels"
date: 2007-10-26
forum: Mythbuntu
---

### Post by kerwin007 on 2007-10-26
Hello everyone,

I'm running mythbuntu 7.10, installed smoothly. My hardware is
- Ati X800
- Hauppauge PVR150

I installed a Front/Back combo on the same machine. I selected the pvr 150 as a mpeg-2 capture card instead of v4l. I'm saying that because I know it can cause problems otherwise.

My problem is, when I start live-tv, I get a black and white screen and I can't change channels. I pushed every single key of my keyboards, could pause , fast forward, but impossible to change the channel !

Any ideas ?

---

### Post by Robocoastie on 2007-10-26
WOW! Thanks to your post "live tv" actually works now. I had been using v4l so was just getting a blank screen. Now I just have channel problems. Only 1-12 is coming in rather than the Time Warner listings one....

As for why you're getting the problem you have I bet it's similar to mine in that its conflicting between what to tune.

--update---

I have tv working now. The problem was I had input set to us-bdcast instead of us-cable. Have you cheked that kerwin?

---

### Post by kerwin007 on 2007-10-27
I'm glad you found it helpful :)

I'm gonna try to change the input type but I think I already tried that.

EDIT: ok, I can change channels but some are in colour but others (many of them) are in B&W. Should I manually edit the frequency table ? Or is it possible that half of the channels are PAL and others are NTSC or something like that ?

EDIT2: ok , problem solved. The channel table europe-west is slightly off what my cable provider broadcasts. By editing the channel frequencies manually, I could correct the problem. Now everything is fine.

---

### Post by Robocoastie on 2007-10-27
glad you got it kerwin! 

Turns out my problem is far from over. Sometimes a tv channel comes on, other times I get colored snow. Recordings are even worse, I managed to get a couple shows recorded last night but they won't transcode right, and just like live tv, sometimes they work, sometimes they don't.

I give up... back to MCE2005.

---

### Post by robert114 on 2008-07-31
> **kerwin007 said:**
> I'm glad you found it helpful :)

I'm gonna try to change the input type but I think I already tried that.

EDIT: ok, I can change channels but some are in colour but others (many of them) are in B&W. Should I manually edit the frequency table ? Or is it possible that half of the channels are PAL and others are NTSC or something like that ?

EDIT2: ok , problem solved. The channel table europe-west is slightly off what my cable provider broadcasts. By editing the channel frequencies manually, I could correct the problem. Now everything is fine.

One question How much did you change the channel frequencies?

---

