---
title: "USB stereo stopped working in alsa mode after upgrade"
date: 2009-05-27
forum: Multimedia Software
---

### Post by HontoniLinux on 2009-05-27
Hello,

After upgrading (via a reinstall) to the latest Ubuntu 9.04 I have been unable to get my USB stereo (Philips MC-M570) to work again in alsa mode. I had the same problem a while back (or at least I think it was the same) with gentoo.

Ubuntu detects my stereo (which shows as a separate sound card) perfectly and it's able to gell when it is connected/disconnected. Audio works in OSS mode. When I test it with alsa mode under sound preferences I get the following error:
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.

I've tried setting it as the main sound card via asoundconf but this doesn't help either. Tried starting the OS with stereo turned on/starting it later but it doesn't seem to have any effect. Before the latest ubuntu release/when I used gentoo the last time I haven't had any issues to get the USB stereo to work under any linux distibution. 

Any ideas what the issue might be or suggestions for what I should try?

Personally I'm suspecting some kind of bug with the alsa software seeing it happened after using more recent releases and alsa versions.

---

