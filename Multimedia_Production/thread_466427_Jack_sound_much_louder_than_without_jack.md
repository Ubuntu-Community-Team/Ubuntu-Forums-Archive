---
title: "Jack sound much louder than without jack"
date: 2007-06-06
forum: Multimedia Production
---

### Post by Suthern on 2007-06-06
No, I'm not practicing bad English! LOL! The issue is thus: When I play a mp3 file without jack running, it's at a comfortable level with all volume levels set in the middle.

When I start jack server and play the mp3 file it is really loud and horribly distorted. There are no other programs mapped in Jack. The connection is GStreamer -> pcm_out. Nothing inbetween.

Originally the levels were comparable, then I fooled around with a few programs (adding echo, reverb, flange..etc) and had a few xruns in the proccess. (and crashed the client programs too). Now the problem is as stated above: The Jack sound levels are MUCH higher.

I've tried restarting the whole computer, logging out/in, changing jack server settings to no avail. Are there some hidden settings in Jack or some hidden connectors? Perhaps configuration files that I could delete or reset to the defaults? The JACK website was not completely helpful in this area.

Thanks!
-Suthern

---

