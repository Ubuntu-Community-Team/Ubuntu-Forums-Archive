---
title: "No audio with SLiM"
date: 2009-11-23
forum: Multimedia Software
---

### Post by listerofsmeg1 on 2009-11-23
So.....
I installed SLiM (Simple Login Manager) but now I don't have any audio.  In Gnome or Xfce.  The only audio device listed is "Dummy Output Pulseaudio mixer".  When using gdm instead audio is fine and the devices listed are "PnP Audio device Alsa" and "CM6501 Analog Stereo".

Does anyone know why SLiM wouldn't load the audio devices?

---

### Post by sisco311 on 2009-11-23
Add your user to the audio group:
```
sudo adduser username audio
```
replace username with your login name.

slim is not in the repos. How did you install it?

---

### Post by listerofsmeg1 on 2009-11-23
That worked like a dream.  You ROCK!! Thanks :)

I installed it from the Jaunty repos.  Found a post here somewhere that said it worked great.

Slightly related question.  Using the commands reboot or halt in SLiM do nothing.  A friend of mine said I'd need to add my username to the "power" group, but "power" doesn't seem to exist.

---

