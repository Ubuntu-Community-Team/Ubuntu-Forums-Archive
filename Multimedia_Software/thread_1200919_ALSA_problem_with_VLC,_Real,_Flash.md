---
title: "ALSA problem with VLC, Real, Flash"
date: 2009-06-30
forum: Multimedia Software
---

### Post by tenghoward on 2009-06-30
Hi all,

I have been using Ubuntu for quite a while, decides is time for me to change views. So I install Kubuntu x64 in my computer and KDE4 is pretty nice. However, my happy mood soon dropped that I learned that non-KDE applications (VLC, RealPlayer, Flash Player) failed to produce sound. 

After few minutes of tweaking, I managed to get VLC and RealPlayer to have sound, my Flash Player seems to be still failing.

Here are my attempts,

**VLC**
1. Attempt 1 - Switch from ALSA to OSS from VLC menu.
Works great! Sound is back and perfectly smooth.

2. Attempt 2 - Switch back to ALSA.
No sound at all.

3. Attempt 3 - Enter advanced menu and select my Nvida ALSA device.
Works like a charm. VLC is finally playing in ALSA once again.

**RealPlayer (from bin package).**

1. Attempt 1 - Using ALSA without changes in PCM path in RealPlayer's menu.
No sound at all.

2. Attempt 2 - Using ALSA with changes in PCM path according to my Nivida ALSA Path from KDE System Menu (plughw).
There is sound going on. But constant buzzing sound is driving me nuts.

3. Attempt 3 - Using OSS without changes.
Sound is back to the way it was. Though I really want to get it to play perfectly on ALSA.

**Flash Players (from Ubuntu repos)**

1. Attempt 1 - Play YouTube.
I have video only. No sound at all.

2. Attempt 2 - Install PulseAudio Device Manager and use its volume control to move stream from Flash to ALSA.
The only sound I am getting is stupid buzzing sound! Not even music!

I haven't updated my kernel yet. I will do that later (after they are unblocked). But I didn't have these problems with the same version of Xubuntu or Ubuntu before. I suspect there is a bug that affect how Kubuntu should handle ALSA (Dragon Player produces sound fine out of the box), as all non-KDE application can't find ALSA path (except VLC, manual reconfiguration seems to have these anoynning buzzling sound going on).

Anyway, is there a way to get Flash Player and RealPlayer into ALSA again?

---

