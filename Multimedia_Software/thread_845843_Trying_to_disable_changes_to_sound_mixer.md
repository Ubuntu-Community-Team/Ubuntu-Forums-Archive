---
title: "Trying to disable changes to sound mixer"
date: 2008-07-01
forum: Multimedia Software
---

### Post by Cappy on 2008-07-01
Ubuntu Hardy (so alsa only) 64-bit.

My steam games, running in wine, keep muting my microphone (actually, my Master Capture channel). I can change to a virtual terminal and use alsamixer but it causes my game to lag.

I need some way to disable changes to my sound settings from my user. This is a single user system so system-wide changes are also possible.

Any suggestions?

---

### Post by Cappy on 2008-07-01
bump

---

### Post by markbuntu on 2008-07-01
You probably need to adjust some settings in the game if the game is doing that. I really don't know though because I don't use wine or windows. I know pulseaudio has some issues with wine and sound control but I don't think that is your particular problem.

---

### Post by Cappy on 2008-07-01
> **markbuntu said:**
> You probably need to adjust some settings in the game if the game is doing that. 

The only settings the game has is "enable microphone in-game" and "enable in-game mic boost". Turning off/on those settings don't stop my master capture from muting.

Edit: Switching to ALSA only (no OSS enabled) on winecfg kept the game from changing my settings. However, the game's sound is much better with OSS =(

---

### Post by markbuntu on 2008-07-01
Have you tried alsa-oss?
It is an alsa wrapper for oss apps. I don't know how it works with wine but it may help you to run wine in oss and help alsa handle the sound better. There is also the libasound2-plugins which include an alsa plugin for oss.

---

