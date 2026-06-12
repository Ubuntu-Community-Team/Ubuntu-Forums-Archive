---
title: "Changing audio output device settings for a system user"
date: 2012-05-18
forum: Multimedia Software
---

### Post by jwbrase on 2012-05-18
I'm running Ubuntu 10.04, and have the timidity-daemon package installed, which has timidity set up as my ALSA midi sequencer. The problem is that, since the daemon is run as user "timidity", it is not affected by my audio preferences (which are, of course, set per-user), and thus timidity outputs to the wrong audio device (internal speakers instead of USB headphones). If I run the daemon as myself from a shell, it uses my audio preferences and the output is sent to the correct device.

Is there any way to edit the audio preferences for the timidity user account (or the system defaults for all users) so that timidity outputs to the correct audio device?

---

