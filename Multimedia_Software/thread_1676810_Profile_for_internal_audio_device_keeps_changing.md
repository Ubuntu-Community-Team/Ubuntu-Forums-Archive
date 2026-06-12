---
title: "Profile for internal audio device keeps changing"
date: 2011-01-27
forum: Multimedia Software
---

### Post by fiendishpaladin on 2011-01-27
I can get sound out of my machine just fine, but for some reason, no matter what audio player I use, every time I change the song or pause playing half my speakers will kill sound and it will seem like the sound profile has reverted to Analog Surround 5.0 Output.  When I check my sound configuration it still lists 5.1, and I have to select another setting then change it back to 5.1 to get my speakers all functioning again.

Currently running Maverick.

---

### Post by lidex on 2011-01-27
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

