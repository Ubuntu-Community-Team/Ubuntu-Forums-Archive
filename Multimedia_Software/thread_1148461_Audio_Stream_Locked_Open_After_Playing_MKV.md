---
title: "Audio Stream Locked Open After Playing MKV"
date: 2009-05-04
forum: Multimedia Software
---

### Post by insanewords on 2009-05-04
Using Jaunty 9.04 and the latest ALSA drivers, I've found that occasionally after playing a MKV video (using XBMC or builtin media player), the audio stream appears to stay locked open after the movie has stopped playing.  After stopping the video, my amp continues to register a PCM 48Khz signal and my speakers usually (but not always) emit a high pitch whine.  After this happens, the only sound I can get out of the system is from other MKV videos.  Divx, Xvid, wav, mp3, etc will play, but I get no sound.  I'm sometimes able to break the lock by rebooting, but I've also had to delete the /etc/asound.state file to kill the PCM 48KHz stream.  This does not happen every time I play a MKV file and it does not always happen with the same file.

I've looked around for a solution, but I've been unable to find one so far.  Being a linux noob, I'm not sure how to troubleshoot this.  I'm using HDMI for audio/video (NVidia 9500GT).  aplay -l shows two devices: ALC883 analog and digital.  I think the sound driver I'm using is snd_hda_codec_realtek.

I've yet to configure a .asoundrc file as I read it was not neccessary and I was already getting DTS/5.1 out of the system.  Would creating this file help, and if so, how?

Thank you.

---

### Post by insanewords on 2009-05-06
bump

---

### Post by alexweber15 on 2009-05-25
bump + 1


this happened to me too and I don't have the .state file apparently... someone please help!

---

### Post by Gh0stface on 2009-08-20
It took me about 2 hours before finally finding any useful information on this damn bug:

> You can fix the sound by entering "iecset audio 1"
> This is a known bug [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/25632](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/25632)
> It appears to be fixed in 9.10 (Karmic)

For me, this happend after watching an mkv file (with AC3 Sound) in XBMC. After that I only got sound when playing mkv files - nothing else worked.

---

