---
title: "Flash sound stutters over time"
date: 2010-09-29
forum: Multimedia Software
---

### Post by pokeyThePenguin on 2010-09-29
I have searched for solutions to this problem, but I haven't found any. All the results show that lots of people suffer from the same problem, but no one knows how to fix it.

Restoring sound is as simple as restarting Firefox, but this is a workaround and not a solution. If you've loaded a video that took a while to load, you don't want to refresh and reload the video.

If I have a video open in Firefox and the computer is idle for at least a couple hours, then the video and sound will stutter.

I've also noticed that if I have a video playlist, where when one video is finished the next one loads a new page and starts to play, the video and sound will start to stutter over time.

I don't know if the problem happens if I'm actively using Firefox for a stretch of a few hours. I normally close down Firefox when I'm not using it, and I usually just use it for browsing sites that tend to only be friendly to Firefox.

I don't have my computer set to do anything when it's idle. The screen stays on, it doesn't dim, the computer doesn't hibernate, etc.

Is the problem caused by a memory leak in Firefox or Flash?

Is there a solution to this problem?

---

### Post by blaktrukman on 2010-09-29
Using Ubuntu 10.04
Having the exact same problem with any sound application in Firefox, Chrome & Pandora desktop app when I'm streaming digital sound thru my SoundBlaster soundcard.   Tried updating to alsa 1.0.23 but then no sound at all.  After it stutters it drops the application altogether from the sound>applications menu.
Will replacing the soundcard fix the problem?

SOLUTION FOUND-
-  installed Pulse Audio and ALL components
-  disabled on-board Realtec audio (mobo component) in bios
-  used cmd console to check if Soundblaster card was installed & recognized..was ok
-  booted up & Pulse found several aspects of the sound card that weren't used and asked to disable them.  Did this on 3 boot ups, deleting different sound components.
-  disabled alsa sound mixer
-  launched Pandora and opened Pulse volume control panel.  Clicked "Simultaneous sound option" on device screen.

Sound works great now on all applications.  Don't use any input device so you may have to tweak this for skype apps.

---

### Post by pokeyThePenguin on 2010-09-29
```
lspci -v
```

says I have "Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)."

I use Alsa for sound.
I don't have PulseAudio installed.

---

