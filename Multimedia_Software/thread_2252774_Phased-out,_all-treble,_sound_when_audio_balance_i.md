---
title: "Phased-out, all-treble, sound when audio balance is centered"
date: 2014-11-14
forum: Multimedia Software
---

### Post by pdesjardins on 2014-11-14
I'm using Ubuntu 14.04.1 LTS on a System76 laptop. I use headphones very frequently and I have been experiencing an odd, intermittent problem with phased-out sound lately. When the audio balance is centered, the sound is quiet and washed out, as if it's coming through a long garden hose. When I pan the balance to either the left or right, the missing frequencies (bass primarily) return in both headphone earpieces. It still doesn't sound correct when the balance is to one side, just better.

This is not a constant problem. It happened about a week ago, then mysteriously went away, and is back now. I've tried restarting ALSA and pulseaudio using commands from other postings, nothing seems to work except waiting for the mysterious self-repair.

The problem is not related to particular software, I hear it when the audio is coming from a browser or various other audio replay programs. Also, the headphones work properly in other devices and wiggling the jack or plugging it in again does not help.

Has anyone else experienced this? I have updated all software packages and restarted a few times today. No help.

Thanks!

Peter

---

### Post by pdesjardins on 2015-10-02
Updating this thread in case it matters to someone in the future.

I still have this problem on a regular basis, same system and many package updates later. But I found a way to reliably fix the problem! And it's weird! Here's what I do:

1. Notice that the sound has become quiet and all bass has been filtered out. Another frequent symptom is that one channel will go silent.

2. Open the sound settings (I click the speaker icon and then Sound Settings). Select Allow Louder than 100%. If one channel has gone silent, pan all the way to that channel.

3. Remove headphones from head (important!)

4. In the sound settings, increase the output volume to its maximum. When the sound in the headphones (which are in your lap) gets really loud, bring the output volume back down to the minimum.

5. Problem solved! Now the sound works just fine, both channels, all frequencies. And with just a little damage to your headphones.

---

