---
title: "[SOLVED] mythtv not controling sound"
date: 2007-10-28
forum: Mythbuntu
---

### Post by supradrvr on 2007-10-28
I am using the line in on my sound card for mythtv. When going to live tv it is not turning the sound on. If I turn up the line in I have sound but that is not the correct way. I am sure its just a setting but I cant find it. Also my sound card has 5.1 jacks, will I be able to use them as well? Its a Shuttle XPC with SIS 7012 onboard sound. Thanks

---

### Post by supradrvr on 2007-10-28
Ok now I have sound. I changed my audio device from /dev/dsp to /dev/audio. However its very tinny and distorted. Any ideas on that?

---

### Post by superm1 on 2007-10-28
Don't use OSS.

Use** ALSA:default**

---

### Post by supradrvr on 2007-10-28
ok i have Alsa:default set. my volume is lower and still tinny. I have mixer set to default. /dev/dsp on the backend. pcm is set to 70 and master to 90% and its still not good. Thanks for the help.

---

### Post by supradrvr on 2007-10-28
problem solved! solution found here. 

[https://help.ubuntu.com/community/MythTV/Install/Feisty/Troubleshooting#head-573fcd94c0ad9fea7e32ad6e7532e88bdfba11d3](https://help.ubuntu.com/community/MythTV/Install/Feisty/Troubleshooting#head-573fcd94c0ad9fea7e32ad6e7532e88bdfba11d3)

Setting the deafult recording sample rate to 48000 made my audio perfect! It was at 32000 by default.

This was my last issue with my test setup! Thank you ubuntu community. Mythbuntu is the best mythtv based disto I tried and I tried them all.

---

