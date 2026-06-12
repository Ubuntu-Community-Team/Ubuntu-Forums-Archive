---
title: "Precise: Mythv Screeching white noise is back!"
date: 2012-05-03
forum: Multimedia Software
---

### Post by HRH_H_Crab on 2012-05-03
With the previous version of Ubuntu there was a well known issue with Mythv.

Some sort of resampling problem between Mythtv and pulseaudio resulted in frequent screeching white noise.

There was a fairly well documented fix for this: set the default sample rate in pulseaudios daemon.conf to 48k.

Since upgrading to precise the screeching white noise is back - perhaps even worse (more frequent) than before.

Yet since daemon.conf still has the sample rate set at 48k I am unsure how to proceed.

Anyone got any ideas?

---

### Post by BicyclerBoy on 2012-05-03
I've never had that problem..
Can you elaborate on your audio config ? analogue/spdif/hdmi etc ?

With every mythtv upgrade you need to use the frontend audio settings screen & rescan/reselect your audio devices.
It is recommended to use the alsa devices over pulse.

---

### Post by HRH_H_Crab on 2012-05-04
> **BicyclerBoy said:**
> I've never had that problem..
Can you elaborate on your audio config ? analogue/spdif/hdmi etc ?

With every mythtv upgrade you need to use the frontend audio settings screen & rescan/reselect your audio devices.
It is recommended to use the alsa devices over pulse.

It has been in the past a very common problem:

[http://www.google.co.uk/search?q=mythtv+ubuntu+white+noise&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-beta](http://www.google.co.uk/search?q=mythtv+ubuntu+white+noise&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-beta)

Ive got a built in Nvidia soundcard (analog).

I've tried using Alsa instead of pulse audio and it doesn't resolve the problem.

---

### Post by BicyclerBoy on 2012-05-04
You never mentioned the "white noise" was that occasional noise while seeking.

Running mythtv 0.24+fixes on lucid 10.04.3, I would say that noise only happens once in a month at most & that is with lots of seeking.

Half my recording are watched with AC3 audio track, other half are LATM-AAC (PC decoded to PCM).

My observation is that the seeking noise never really affected AC3 pass-thru'.

I haven't noticed the seeking screech noise using the latest MythTV (git source master) on a 12.04 box..(analogue stereo).
But it has not had much use..just testing.

Your built-in soundcard should be able to output AC3/DTS pass-thru' if that helps..

---

