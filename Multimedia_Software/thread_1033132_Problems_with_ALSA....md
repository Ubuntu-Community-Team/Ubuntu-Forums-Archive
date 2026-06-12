---
title: "Problems with ALSA..."
date: 2009-01-07
forum: Multimedia Software
---

### Post by Chaos_Spear on 2009-01-07
So in an attempt to fix my sound issues with WINE, I started futzing with my sound, and, of course, broke it.  After some vigorous re-installing to try to get everything back to the way it was, I can now play music fine, but videos are a little wonky: mplayer gives an error, but plays, and VLC only works when OSS is specified.

mplayer error in terminal:
AO: [pulse] Failed to connect to server: Connection refused
[AO_ALSA] alsa-lib: pcm.c:2162:(snd_pcm_open_conf) Cannot open shared library /usr/lib/alsa-lib/libasound_module_pcm_pulse.so
[AO_ALSA] Playback open error: No such file or directory

Which looks like a pulseaudio thing, but when I go to uninstall pulse, it's not there?  Very confused, this is my first Linux machine.  I'm using Kubuntu Intrepid 8.10, and I have an Intel ALC889 sound card.

Thanks for any help you can give!

---

### Post by Chaos_Spear on 2009-01-07
Anyone?  Please help!

---

