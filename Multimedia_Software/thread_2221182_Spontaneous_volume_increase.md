---
title: "Spontaneous volume increase"
date: 2014-05-01
forum: Multimedia Software
---

### Post by freek_zero on 2014-05-01
Since installing 14.04 the master volume spontaneously jumps up a few ticks every so often (averages once every few minutes, but isn't regular). It doesn't seem to be attached to any particular action (keyboard, mouse, running application) and happens both when listening to music via Rhythmbox and watching Youtube. Sometimes it is a very brief glitch and goes back down in a fraction of a second, other times it stays at the higher level until I turn it down again. I've seen it happening while watching the Sound preferences window and it is definitely the master volume.

I'm on a pretty standard install, using Pulse.

---

### Post by freek_zero on 2014-05-01
I can't seriously be the ONLY one that has experienced this? It is driving me completely up the wall. I can't listen to music when I work now for obvious reasons, and even using voip is treacherous.

Is there any way to get debug level output that would show what is triggering/requesting the volume increases?

---

### Post by freek_zero on 2015-02-24
So the issue mysteriously went away after some time... only to return months later, now on 14.10 of course.  I watched PulseAudio Volume Control and actually saw the volume changing there, so it doesn't appear to be a hardware level issue. Saw it switch from Headphones to Analog profile, but also saw the volume change (go up _and_ down) without changing the profile.

Only other mention I've seen of this issue resolved it by installing Pulse volume control but that didn't help for me.

Guessed at the notorious Skype being the culprit, but still happens when Skype isn't running.

Anyone?

---

### Post by MikeMecanic on 2015-02-24
February2015

I think your main problem is [COLOR=#000000] Rhythmbox Player:  [/COLOR]**See in Ubuntu Software Center the reviews of users**.  Try uninstall it and see the different.  I also don't use Pulse Audio: Analog Output/Built-in Audio instead.  While installing Ubuntu, did you click on additional audio driver?   I didn't.   Rhythmbox Player is a heavy application.  Always shoot for MAC compatible devices (our terminal cousin) and try to used simple tools that over time remain constant..  **Video Player ( 3.10.1 made by Totem) or VLC Media Player (2.1.4 Rincewind)** do the job without any complications.

---

### Post by freek_zero on 2015-02-26
Thx for the reply Mike.

Deleted Rhythmbox but no change in behaviour. I don't use PulseAudio's volume control either, just tried installing it based on another advise, then deleted again after it didn't fix the problem. Couldn't tell you about additional drivers since installed years ago. Driver in use appears to be snd_hda_intel which sounds correct.

This issue happens regardless of the source of the audio stream btw. Chrome, FireFox (via Flash), Rhythmbox, Totem, Skype, SFLPhone all do the same.

---

### Post by freek_zero on 2015-02-26
Finally found a fix per [http://tombuntu.com/index.php/2010/05/09/fix-volume-range-issue-in-pulseaudio/](http://tombuntu.com/index.php/2010/05/09/fix-volume-range-issue-in-pulseaudio/)

Set load-module module-udev-detect ignore_dB=1 in /etc/pulse/default.pa

---

