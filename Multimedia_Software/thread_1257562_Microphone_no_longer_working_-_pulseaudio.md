---
title: "Microphone no longer working - pulseaudio"
date: 2009-09-03
forum: Multimedia Software
---

### Post by Garibaldi3489 on 2009-09-03
I'm running Linux Mint 7, which is based on Ubuntu 9.04. I have had no problems with my audio capture or playback using Pulseaudio from day one. However, about a week ago Pulseaudio started giving me trouble. It could have been from a gstreamer update, which is the only thing I can remember of consequence coming up for update recently. Anyway, I can no longer capture audio from my internal microphone nor from an external headset. Moreover, sometimes playback will stop working - e.g. Rhythmbox will just sit at Time 0:00 and never start playing. I can remove my ~/.pulse directory and reboot to fix this, or kill and restart pulseaudio.

I tried following [url=http://idyllictux.wordpress.com/2009/04/21/ubuntu-904-jaunty-keeping-the-beast-pulseaudio-at-bay/]this guide[/code] to temporarily disable pulseaudio and assert ALSA as the default audio device. I also had trouble with this. Any suggestions or ideas on how I can diagnose and fix this?

Thanks!

---

