---
title: "No Sound After Update [solution]"
date: 2010-05-06
forum: Mythbuntu
---

### Post by novellahub on 2010-05-06
I did a update to my machine today (Mythbuntu 10.04 32-Bit + Mythbuntu repo).  After I applied the updates, the machine came back up without sound.  I did a "aplay -l" (Without quotes) in the terminal and it said "no devices found".  Running "alsamixer" gave a error back saying that it could not find the mixer. Running "alsamixer" as root worked showing the sound card volume settings.  The solution I had to do was add my normal user to the audio group.

```

sudo adduser username audio

```

Just replace username with our own user name and reboot. :)

---

### Post by stormb on 2010-06-30
Awesome, thanks!

No idea how this happened on my Acer Revo, but today was the first time I rebooted in a few weeks (and I have done various Ubuntu updates over those few weeks). I also have Mythbuntu 10.04 32-bit and the Mythbuntu PPA (0.23+fixes).

Discovered my audio was not working after the reboot. I also seem to have been removed from the audio group. This fixed it!

Will

---

### Post by idrinkwhisky on 2010-07-01
thanks. i had same problem and your solution worked perfectly.

does anybody know why this happened and what was wrong with the update?

---

