---
title: "Pulseaudio and ALSA in Hardy"
date: 2008-07-07
forum: Multimedia Software
---

### Post by Speckay on 2008-07-07
Hi everyone... So I've had a few problems with sound before and I've started to narrow things down. I have Hardy installed and have the sound settings pretty much default right now. I installed the extras for pulseaudio (like the device chooser and the manager). I've never been able to have sounds work via ALSA or as default config ("autodetect" in Sound Preferences). I'm hoping to get the sounds working so that I don't have to use OSS and be limited to one program at a time producing sound.

If I try to run an mp3 from a terminal with VLC, this is what happens:

vlc Electric\ Six\ -\ Danger\ \(High\ Voltage\).mp3 
VLC media player 0.8.6e Janus
W: module-alsa-sink.c: Got POLLERR from ALSA

and the sound stops. VLC is set to use pulseaudio and the Sound Preferences (the first three) are also set to pulseaudio. Also, if VLC is set to default, and I run pulseaudio from a terminal, I get the POLLERR in pulseaudio's terminal. And finally, sometimes pulseaudio displays the POLLERR immediately when I start it (after I've ended the process after logging in).

If I kill pulseaudio and change my Sound Preferences to "ALSA", I get a broken pipe error.

I'm still relatively new to Linux... Any ideas?

---

### Post by t-o-c on 2009-01-07
Did you end up resolving this issue?

I have a similar issue in Intrepid:
Jan  7 21:35:18 x pulseaudio[22367]: module-alsa-sink.c: Got POLLERR from ALSA
Jan  7 21:35:19 x last message repeated 20 times
Jan  7 21:35:19 x kernel: [260051.256598] r8169: eth0: link up
Jan  7 21:35:19 x kernel: [260051.256605] r8169: eth0: link up
Jan  7 21:35:19 x pulseaudio[22367]: module-alsa-sink.c: Got POLLERR from ALSA
Jan  7 21:35:39 x last message repeated 501 times
Jan  7 21:35:39 x pulseaudio[22367]: sink-input.c: Failed to create sink input: too many inputs per sink.
Jan  7 21:35:39 x pulseaudio[22367]: module-alsa-sink.c: Got POLLERR from ALSA
Jan  7 21:36:00 x last message repeated 529 times

---

