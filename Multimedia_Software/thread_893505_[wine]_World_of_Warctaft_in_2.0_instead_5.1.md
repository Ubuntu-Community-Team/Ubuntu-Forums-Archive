---
title: "[wine] World of Warctaft in 2.0 instead 5.1"
date: 2008-08-18
forum: Multimedia Software
---

### Post by gutko on 2008-08-18
Hi,
Im trying to get WoW sound the same way as in win xp - i mean in real 5.1 - no duplicating channels etc...
I have 8.04 with recompiled alsa 1.0.17 and Xonar DX card.
Problem is that WoW in Wine 1.1.2 detects only stereo mode as SESound.log file in wow logs says:
```
8/18 16:22:22.509   - Detected Control Panel Speaker Mode = STEREO
8/18 16:22:22.509   - Setting WoW Speaker Mode to STEREO
```

but in winxp WoW detects real 5.1 (set to 5.1 in control panel):
```
8/18 13:31:20.421   - Detected Control Panel Speaker Mode = 5.1
8/18 13:31:20.437   - Setting WoW Speaker Mode to 5.1
```

And the difference in sorrounding sound is HUGE.

As control panel's settings in Ubuntu are handled by wine i was trying to find number of channels setting in wine registry but with no luck.
Any suggestions where to look next?

---

