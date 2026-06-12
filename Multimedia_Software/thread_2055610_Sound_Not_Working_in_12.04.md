---
title: "Sound Not Working in 12.04"
date: 2012-09-09
forum: Multimedia Software
---

### Post by Hoogs on 2012-09-09
A few days ago, the sound on my Ubuntu netbook just stopped working out of the blue. When I go to the sound settings it now says "Dummy Output". I can't think of anything that might've caused this, except it seems like it started after changing my theme using Ubuntu Tweak, but changing it back doesn't help and it could've easily just been a coincidence...

More Info:

The sound/volume control icon in the toolbar at the top of the screen has disappeared as well, although the keyboad controls for changing the volume still work.

Entering the command "aplay -l" in terminal yields "no soundcards found...".

However, "lspci -v | grep -A7 -i "audio"" DOES recognize a soundcard.

I've followed the troubleshooting guides in the sticky thread, including reinstalling ALSA drivers, and all to no avail. I really am a beginner with Linux/Ubuntu and have pretty much zero programming knowledge. I know how to enter commands into the terminal, and that's about it. Thanks in advance.

---

