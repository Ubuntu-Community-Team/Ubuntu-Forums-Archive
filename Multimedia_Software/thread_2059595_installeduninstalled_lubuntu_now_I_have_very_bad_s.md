---
title: "installed/uninstalled lubuntu now I have very bad sound"
date: 2012-09-18
forum: Multimedia Software
---

### Post by Frogster on 2012-09-18
I installed lubuntu to see if I liked it. I have an old Acer Aspire 3000 and thought it might help. 

Installing lubuntu has destroyed my sound. In ubuntu sound was good enough to stream lastfm at a decent volume. Now it seems like the volume has been turned up so much the speakers just give static.

I dont know how to correct this, I have turned volumes down in alsa but that doesnt seem to change anything.

Please help

---

### Post by Frogster on 2012-09-19
Help please

---

### Post by TenPlus1 on 2012-09-19
Go into Terminal and type:

  alsamixer

set sound levels to how you like it...

---

### Post by Frogster on 2012-09-19
Thank you for the reply. alsamixer just lets me adjust the volume. The quality of sound is terrible, just like the speakers are being played at the very top of tolerance

Any help is most greatfully recieved and if any further info is required I will supply it

---

### Post by TenPlus1 on 2012-09-20
Usually adjusting PCM to 90% and turning off SPDIF sorts a few of the grainy sound problems, failing that you could always install PulseAudio and see if that helps any after a reboot...

sudo apt-get install pulseaudio pavucontrol

---

