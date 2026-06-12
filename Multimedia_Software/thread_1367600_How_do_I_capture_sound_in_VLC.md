---
title: "How do I capture sound in VLC?"
date: 2009-12-29
forum: Multimedia Software
---

### Post by T0mmy on 2009-12-29
I want to copy a tape from an old videocamera to my computer. The video-cable is connected to my tv-card, while the audio-cable is connected to mic/line-in (I've tried both).

VLC is the only player I can get to show the video (I'm using the composite connector), and it captures and saves the video just fine.

Gnome Sound Recorder captures the sound, so I know the cables are working.

The question is: How do I capture the sound with VLC?

Video capture works both with v4l2- and pvr-mode. In v4l2-mode I can manually type in the "Audio Device", but I actually have no idea what to type here.

After some searching I tried /dev/sdp, but this only results in the following error:
Your input can't be opened:
VLC is unable to open the MRL 'alsa:///dev/sdp'. Check the log for details.

Output from "Messages":
access_alsa error: cannot open device /dev/sdp for ALSA audio (No such file or directory)
main error: no access module matched "alsa"
main error: open of `alsa:///dev/sdp' failed: no access module matched "alsa"
pulse info: No. of Audio Channels: 2

Further searching led me to a howto which explained that installing vlc-plugin-alsa for VLC would do the trick. This package seems to be outdated (not available for karmic afaik), and the "Plugins and extensions" in VLC shows "Alsa audio capture input - access demux, score 10)".

Am I missing something?

I run a fully updated Ubuntu Karmic with VLC 1.0.3 from Launchpad PPA, and have a Hauppauge PVR-500 TVcard and a Realtek/nVidia soundcard (snd-intel8x0).

---

