---
title: "Rhythmbox/Banshee/Songbird becomes Unresponsive While Playing Music"
date: 2009-11-02
forum: Multimedia Software
---

### Post by Z3ro3X on 2009-11-02
This is a clean install of 9.10.  Audio works fine for every thing else.  I did have to change the audio profile from [Analog Stereo Duplex] to [Digital Stereo ( IEC958 ) Output + Analog Stereo Input] by right clicking on the speaker icon in the system tray then clicking Sound Preferences and going to the Hardware Tab.

My problem is music will randomly stop playing and the software I'm playing music with will become unresponsive.  The only way to close the program is to kill it.  This happens in Rhythmbox, Banshee and Songbird. The time it takes for this to happen and the number of mp3's played and the mp3 currently being played seems to be completely random.  The problem seemed to have initially gone away after changing my sound profile as mentioned above.  Then later that night the problem occurred again.  I logged off my account and back on and the problem went away.  Then later came back.  So I still have the issue after changing sound profiles just not as much as before.  Nothing has changed in my music collection or my hardware.  It's all the same data and hardware setup when I was running 9.04 and my music played with out issues.

Note:  Totem seems to be totally unaffected by this.  Right now I've resorted to playing music in Totem until this can be fixed.

What would likely cause this type of issue?  Can it be newer drivers?  Or is it the new audio setup in 9.10?

Here's some hardware info that might help.

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SI7012 [SiS SI7012], device 0: Intel ICH [SiS SI7012]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

lspci -v
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
	Subsystem: Elitegroup Computer Systems Device a102
	Flags: bus master, medium devsel, latency 64, IRQ 18
	I/O ports at d400 [size=256]
	I/O ports at d000 [size=128]
	Capabilities: <access denied>
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0

---

### Post by Z3ro3X on 2009-11-02
Further investigation has led me to believe this is a possible pulseaudio/alsa bug.  I found some interesting data in the user.log file when I was looking through System Log Viewer.

Nov  1 08:59:26 defiant pulseaudio[20920]: ratelimit.c: 160 events suppressed
Nov  1 17:23:59 defiant pulseaudio[23570]: ratelimit.c: 1 events suppressed
Nov  1 17:24:08 defiant pulseaudio[23661]: pid.c: Stale PID file, overwriting.
Nov  1 17:24:15 defiant pulseaudio[23661]: alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write!
Nov  1 17:24:15 defiant pulseaudio[23661]: alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_intel8x0'. Please report this issue to the ALSA developers.
Nov  1 17:24:15 defiant pulseaudio[23661]: alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.
Nov  1 17:24:19 defiant pulseaudio[23661]: ratelimit.c: 9 events suppressed
Nov  1 17:28:58 defiant pulseaudio[23661]: ratelimit.c: 1 events suppressed
Nov  1 23:14:24 defiant gnome-screensaver-dialog: pam_sm_authenticate: Called
Nov  1 23:14:24 defiant gnome-screensaver-dialog: pam_sm_authenticate: username = [z3ro3x]
Nov  2 00:32:39 defiant gnome-screensaver-dialog: pam_sm_authenticate: Called
Nov  2 00:32:39 defiant gnome-screensaver-dialog: pam_sm_authenticate: username = [z3ro3x]
Nov  2 01:07:30 defiant gnome-screensaver-dialog: pam_sm_authenticate: Called
Nov  2 01:07:30 defiant gnome-screensaver-dialog: pam_sm_authenticate: username = [z3ro3x]
Nov  2 01:07:41 defiant pulseaudio[23661]: ratelimit.c: 41 events suppressed
Nov  2 01:39:12 defiant gnome-screensaver-dialog: pam_sm_authenticate: Called
Nov  2 01:39:12 defiant gnome-screensaver-dialog: pam_sm_authenticate: username = [z3ro3x]
Nov  2 02:35:56 defiant pulseaudio[23661]: ratelimit.c: 95 events suppressed
Nov  2 02:51:06 defiant sudo: pam_sm_authenticate: Called
Nov  2 02:51:06 defiant sudo: pam_sm_authenticate: username = [z3ro3x]
Nov  2 03:21:05 defiant pulseaudio[23661]: ratelimit.c: 106 events suppressed
Nov  2 03:24:36 defiant sudo: pam_sm_authenticate: Called
Nov  2 03:24:36 defiant sudo: pam_sm_authenticate: username = [z3ro3x]
Nov  2 15:52:44 defiant gnome-screensaver-dialog: pam_sm_authenticate: Called
Nov  2 15:52:44 defiant gnome-screensaver-dialog: pam_sm_authenticate: username = [z3ro3x]
Nov  2 15:54:08 defiant sudo: pam_sm_authenticate: Called
Nov  2 15:54:08 defiant sudo: pam_sm_authenticate: username = [z3ro3x]
Nov  2 17:35:53 defiant sudo: pam_sm_authenticate: Called
Nov  2 17:35:53 defiant sudo: pam_sm_authenticate: username = [z3ro3x]
Nov  2 17:44:43 defiant pulseaudio[23661]: ratelimit.c: 29 events suppressed
Nov  2 17:47:29 defiant pulseaudio[23661]: ratelimit.c: 29 events suppressed
Nov  2 18:16:19 defiant pulseaudio[23661]: ratelimit.c: 44 events suppressed
Nov  2 18:38:07 defiant sudo: pam_sm_authenticate: Called
Nov  2 18:38:07 defiant sudo: pam_sm_authenticate: username = [z3ro3x]
Nov  2 18:58:54 defiant gnome-screensaver-dialog: pam_sm_authenticate: Called
Nov  2 18:58:54 defiant gnome-screensaver-dialog: pam_sm_authenticate: username = [z3ro3x]
Nov  2 19:06:59 defiant sudo: pam_sm_authenticate: Called
Nov  2 19:06:59 defiant sudo: pam_sm_authenticate: username = [z3ro3x]
Nov  2 19:42:54 defiant sudo: pam_sm_authenticate: Called
Nov  2 19:42:54 defiant sudo: pam_sm_authenticate: username = [z3ro3x]
Nov  2 19:46:50 defiant sudo: pam_sm_authenticate: Called
Nov  2 19:46:50 defiant sudo: pam_sm_authenticate: username = [z3ro3x]
Nov  2 19:57:16 defiant pulseaudio[2554]: ratelimit.c: 2 events suppressed
Nov  2 19:57:21 defiant pulseaudio[2554]: alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write!
Nov  2 19:57:21 defiant pulseaudio[2554]: alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_intel8x0'. Please report this issue to the ALSA developers.
Nov  2 19:57:21 defiant pulseaudio[2554]: alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.
Nov  2 19:57:23 defiant pulseaudio[2554]: ratelimit.c: 6 events suppressed
Nov  2 19:58:10 defiant pulseaudio[2554]: ratelimit.c: 1 events suppressed
Nov  2 19:58:20 defiant sudo: pam_sm_authenticate: Called
Nov  2 19:58:20 defiant sudo: pam_sm_authenticate: username = [z3ro3x]
Nov  2 20:01:25 defiant sudo: pam_sm_authenticate: Called
Nov  2 20:01:25 defiant sudo: pam_sm_authenticate: username = [z3ro3x]
Nov  2 20:05:35 defiant pulseaudio[2187]: ratelimit.c: 1 events suppressed
Nov  2 20:05:52 defiant pulseaudio[2608]: ratelimit.c: 1 events suppressed
Nov  2 20:05:57 defiant pulseaudio[2608]: alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write!
Nov  2 20:05:57 defiant pulseaudio[2608]: alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_intel8x0'. Please report this issue to the ALSA developers.
Nov  2 20:05:57 defiant pulseaudio[2608]: alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.
Nov  2 20:06:03 defiant pulseaudio[2608]: ratelimit.c: 1 events suppressed
Nov  2 20:25:23 defiant pulseaudio[3986]: ratelimit.c: 9 events suppressed
Nov  2 20:25:25 defiant pulseaudio[4076]: pid.c: Stale PID file, overwriting.
Nov  2 20:25:34 defiant pulseaudio[4076]: ratelimit.c: 4 events suppressed
Nov  2 20:25:40 defiant pulseaudio[4076]: ratelimit.c: 3 events suppressed
Nov  2 20:32:06 defiant pulseaudio[4076]: ratelimit.c: 1 events suppressed

---

### Post by lowracer on 2009-11-12
I've got the same problem.  Been using Totem to play music.  Rhythmbox and banshee will just randomly stop playing music.  Killing process is the only way to terminate the program.

---

