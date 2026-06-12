---
title: "Ekiga will not play any sound"
date: 2009-05-13
forum: Multimedia Software
---

### Post by Baodehui on 2009-05-13
Hopefully this is the correct forum... I have a netbook with a mic. I couldn't get the mic working under 8.10, but I was very pleased to discover that it works in Jaunty. I can record my voice in audacity and hear it just fine, albeit a little quietly.

So I decided to try to use Ekiga, since I also have a working webcam. In Ekiga, when I dial the echo test, I see my face, the webcam works, and if I click the volume button I see an indication that it is reading some sound from the mic. However, I do not hear anything. Not the voice telling me it's going to do an echo test, not my voice, nothing.

Worse still, if I go to edit > prefs > sound events and tell it to play me the ring.wav file, I don't hear anything. It seems that although Ekiga can capture sound and video just fine, it is totally unable to play any sound. The sound on my system otherwise works fine.

Ekiga's output device is currently set to Default (PTLIB/ALSA) but I have set it to each of the other three options in turn with no change: HDA Intel (PTLIB/ALSA); *.wav (PTLIB/WAVFile); SILENT (Ekiga/Ekiga).

Does anyone have any ideas or starting places for me to look? My google-fu is failing me and I'm just not familiar enough with linux to know how to get diagnostic information for this sort of problem.

---

### Post by sagara on 2009-07-01
Bumping this thread... I'm also facing the same problems on my fresh jaunty install.

My soundcard is Audigy 2 ZS.  Does anybody actually have ekiga working?

---

