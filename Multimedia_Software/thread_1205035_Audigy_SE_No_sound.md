---
title: "Audigy SE No sound"
date: 2009-07-05
forum: Multimedia Software
---

### Post by dlmarti on 2009-07-05
Ubuntu 9.04 no sound.

I have no sound out of my audigy SE card.

I'm just using this card with a set of analog speakers (tested the speakers).

I ran some diagnostics:

lspci: [http://www.terabytecode.com/sound_prob/lspci_output.txt](http://www.terabytecode.com/sound_prob/lspci_output.txt)
lsmod: [http://www.terabytecode.com/sound_prob/lsmod_output.txt](http://www.terabytecode.com/sound_prob/lsmod_output.txt)
aplay: [http://www.terabytecode.com/sound_prob/aplay_output.txt](http://www.terabytecode.com/sound_prob/aplay_output.txt)

The diagnostics show the card present, the correct modules loaded, and the devices present.

I tried the alsamixer fix: [http://www.terabytecode.com/sound_prob/alsamixer.png](http://www.terabytecode.com/sound_prob/alsamixer.png)

Still no go.  I get absolutely no sound out.

Any help would be appreciated, I'm at a complete loss.

---

### Post by dlmarti on 2009-07-05
I'd be interested in hearing from anyone that has gotten this card working (Analog mode).

---

### Post by dlmarti on 2009-07-06
Output from aadebug: [http://www.terabytecode.com/sound_prob/aadebug.txt](http://www.terabytecode.com/sound_prob/aadebug.txt)

I did get one error from the script: 
*"cat: /proc/asound/hwdep: No such file or directory*"

---

### Post by wbee on 2009-07-06
dlmarti,

I also have a Creative Soundblaster Audigy SE card.

Allow me to mention two things that you may have tried already,but I want to be through.

1.As silly as this sounds,make sure your output is not muted. When the volume is at its lowest setting,it is muted.

2.When I installed my card,I was using XP,and the creative driver overrode the on board audio.

--**But the Ubuntu driver did not over ride it. I went into the bios,disabled the on board audio,and it worked well.

Good luck to you.

------------

W

---

### Post by kostkon on 2009-07-06
> **dlmarti said:**
> Ubuntu 9.04 no sound.

I have no sound out of my audigy SE card.

I'm just using this card with a set of analog speakers
Then, try this: Right-click on the speaker in your system tray and select *Open Volume Control*. Select the *Switches* tab and make sure that the *Analog/Digital* switch is not enabled.

Hope that helps.

---

### Post by dlmarti on 2009-07-06
> 1.As silly as this sounds,make sure your output is not muted. When the volume is at its lowest setting,it is muted.

2.When I installed my card,I was using XP,and the creative driver overrode the on board audio.



> **kostkon said:**
> Then, try this: Right-click on the speaker in your system tray and select *Open Volume Control*. Select the *Switches* tab and make sure that the *Analog/Digital* switch is not enabled.

Hope that helps.

Thanks for the reply.  The last time I owned a copy of windows it was called 3.1  :)
So no windows for me, I've been a linux guy for a long time but this new sound system has me perplexed.

Is this the right setup?????
[http://www.terabytecode.com/sound_prob/alsamixer.png](http://www.terabytecode.com/sound_prob/alsamixer.png)

---

