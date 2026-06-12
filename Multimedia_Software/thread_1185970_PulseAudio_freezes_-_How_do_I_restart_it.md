---
title: "PulseAudio freezes - How do I restart it?"
date: 2009-06-12
forum: Multimedia Software
---

### Post by webkris on 2009-06-12
First off - restarting my PC every few days to get sound back is getting old.
How do I kick PulseAudio to get going again after a combination of my mp3 player and/or Firefox kill it?

I'm on Intrepid 8.04
Latest Updates
Latest Firefox
XMMS
VirtualBox (with sound disabled)

This is literally the only apps running on my desktop.
After 3 or 4 days of solid up-time - Audio stops coming from my machine.
I close firefox and it tells me it's still running when I shut down.
I try to play music with XMMS and it freezes.
This signals me to restart the PC.

What commands should I try to get it going again without rebooting?
Further research - What can I do to fix it?
Thanks!
- Kris

---

### Post by webkris on 2009-06-19
n/m I got it...

```
sudo apt-get remove pulseaudio

sudo apt-get install esound
```

Hopefully the pulseaudio server won't freeze any more, stop accepting connections, and prevent me from listening to mp3's or YouTube videos.
[B]
You can't fix a problem by making it more complex.[/B]
- Kris

---

### Post by webkris on 2009-07-17
**Bonus points:** An update after running Pulse free for a while.

Firefox: I know now that Firefox, after running for a day, kills audio.
Now it just kills itself and not all the audio on my system.

VirtualBox: Audio is great and stable for days now. When Firefox dies - I move to watching YouTube videos with Firexox on my VirtualBox!!!
Yeah - when my Virtual OS, Windows XP, running INSIDE Ubuntu is more stable then the host OS... It really pains me in my decision to move to Linux. :(

XMMS: Flawless now.

- Kris

---

### Post by igorzwx on 2009-07-17
Friends!
Why so strange?
Averythig works well with OSS4

but USB audio devices are not supported

---

