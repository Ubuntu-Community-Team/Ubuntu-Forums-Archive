---
title: "why is does pulseaudio use so much cpu while idle?"
date: 2009-04-03
forum: Multimedia Software
---

### Post by DAllenSmith on 2009-04-03
i have noticed for a long time that pulseaudio uses around 20% cpu while the system is idle. why is this? is it normal? is there anything i can do to make it use less cpu? here is a screen shot of top

---

### Post by change_mode on 2009-04-03
The default Pulseaudio configuration isn't that good. There are topics in these forums explaining how to improve it.

Alternatively you can go to the sound options and set all the options to ALSA, so PulseAudio won't be used anymore.

---

### Post by DAllenSmith on 2009-04-03
Thanks this seems to have solved this. I can't understand why this would be set to the default if it is always using around 20% of the cpu at all times. I followed change_modes advice and went the system > pref > sound changed all options from default to ALSA. then in top (just typing "top" in terminal) I noticed pulseaudio was still running with 20% so in another terminal i issued "killall pulseaudio" 
sounds still work fine and pulseaudio does not show up in the list of top programs except when a sound is being played, then and only then will pulseaudio jump in to tops display and use only about 1 or 2 % of cpu and once the sound is done being played pulseaudio quickly falls off the list freeing up my cpu from its clutches. I do not understand why it doesnt react like this to begin with but this is something very simple i  suggest you all try.:KS:KS:KS:KS

here is a screen shot of top while the system is playing a sound and one while no sound is being played, it is very obvious what effect this will have compared to the screen shot in my first post on this thread:

---

