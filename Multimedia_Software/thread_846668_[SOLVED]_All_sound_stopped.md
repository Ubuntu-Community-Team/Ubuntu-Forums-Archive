---
title: "[SOLVED] All sound stopped"
date: 2008-07-01
forum: Multimedia Software
---

### Post by brad103 on 2008-07-01
Toshiba Tecra P5 - Hardy

Sound just stopped working. I can't be specific on what happened - nothing that I'm conscious of. I'm now running 2.6.24-19, but I've tried booting into -18, -17 and -16 and still no sound so can't (?) be an upgrade problem. When it first happened (about a week ago) I was using alsa-1.0.16. I tried an upgrade of that just to refresh things and am now on 1.0.17rc3 but still no joy.
I can dual-boot into Windows and sound there is fine, so not hardware.
When I've had the sound modules wrong in the past I'd get the system beep when reaching the login screen and I don't get that now.
dmesg | grep snd shows up nothing (my driver is snd_hda_intel)
I had noticed vlc was not playing sound during the first 5 or so seconds when playing video for the week or so before all sound stopped.
I'm testing the sound by running vlc or using aplay.

I installed pulseaudio today after seeing
> [00000353] pulse audio output error: Failed to connect to server: Connection refused
[00000353] pulse audio output error: Pulse initialization failed
when running vlc from the command line. That didn't help any.

I wouldn't have thought (with what little I know on pulseaudio) that it would be the problem anyway because as I mentioned earlier, aplay produces nothing also.

(I've reposted this here after deciding my original  [thread]("http://ubuntuforums.org/showthread.php?p=5271969") was probably in the wrong forum as sound *has* worked for 6 months up until now).

Any help appreciated!
Brad

---

### Post by brad103 on 2008-07-05
Unbelievable! I dual boot with Windows - boot into Windows and **unmute sound**. This fixed it. <sigh>

---

