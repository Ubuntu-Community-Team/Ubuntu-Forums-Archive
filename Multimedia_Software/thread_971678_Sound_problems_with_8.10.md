---
title: "Sound problems with 8.10"
date: 2008-11-05
forum: Multimedia Software
---

### Post by kentcb on 2008-11-05
Hi all,

Since upgrading to 8.10 all sound output on my laptop has been muffled and distorted. I have tried switching between the various devices available under the "Sound playback" in the "Sound Preferences" window, but to no avail.

Is this a known issue with 8.10?

Thanks,
Kent

---

### Post by kentcb on 2008-11-05
Some more info. I just found this in my syslog:

Nov  5 12:13:48 Raph pulseaudio[10874]: alsa-util.c: Device hw:1 doesn't support 44100 Hz, changed to 16000 Hz.
Nov  5 12:13:48 Raph pulseaudio[10874]: alsa-util.c: Device hw:1 doesn't support 2 channels, changed to 1.

My audio was working fine in 8.04. Is this an ALSA problem?

Thanks,
Kent

---

### Post by CPtAJ on 2008-11-05
Looks like a pulseaudio problem. Probably configuration related.

Go to system > preferences > sound - and change all the options to ALSA instead of pulseaudio. See if that helps you out in the meantime while someone helps you fix pulse.

---

### Post by kentcb on 2008-11-05
Thanks for the suggestion. I changed all sound options to use ALSA and then restarted my system. Unfortunately, it has not rectified the problem. I could be wrong, but the logs seem to indicate that PA is still being used:

[FONT="Courier New"]Nov  5 13:30:30 Raph pulseaudio[5568]: ltdl-bind-now.c: Failed to find original dlopen loader.
Nov  5 13:30:30 Raph pulseaudio[5570]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Nov  5 13:30:30 Raph pulseaudio[5570]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Nov  5 13:30:30 Raph pulseaudio[5570]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Nov  5 13:30:30 Raph pulseaudio[5570]: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
Nov  5 13:30:30 Raph pulseaudio[5570]: alsa-util.c: Cannot find fallback mixer control "Mic".[/FONT]

Any further suggestions?

---

### Post by kentcb on 2008-11-05
Er, I was hesitant to mark this as "SOLVED" because I really have no idea why it now works. All I did was install these packages: pavucontrol, pavumeter, paman, padevchooser, and paprefs. Now things seem to be at least sounding OK when I play an MP3. However, Skype still doesn't appear to like things and PA seems unstable in general.

I must say, as a fairly recently converted Ubuntu user, these kind of issues are incredibly frustrating.

Kent

---

### Post by altu on 2008-11-05
Replace Pulseaudio with esound. It's old but your sound will work as good as it did on Gutsy. It's what solved my prblems e.g. No mic in Skype e.t.c.... Note that you have to delete a couple of scripts that make pulseaudio start automatically with Gnome, otherwise you won't be able to login after removing Pulse.

---

### Post by kentcb on 2008-11-05
> **altu said:**
> Replace Pulseaudio with esound. It's old but your sound will work as good as it did on Gutsy. It's what solved my prblems e.g. No mic in Skype e.t.c....

How do I replace PA with esound? Do I just install esound and then set my preferences? Can I remove PA altogether (I just looked at dependencies and removing pulseaudio implies removing ubuntu-desktop, which scares me).

Thanks,
Kent

---

### Post by ubun_two on 2008-11-05
> **kentcb said:**
> How do I replace PA with esound? Do I just install esound and then set my preferences? Can I remove PA altogether (I just looked at dependencies and removing pulseaudio implies removing ubuntu-desktop, which scares me).

Thanks,
Kent

I just did the uninstall of pulseaudio.  Here are what I did.  Note that there are two things that still don't work for me:

- VMWare sound
- Skype (mic in)

Steps:
1, Remove pulseaudio and its dependency through Synoptic (yes, that means ubuntu-desktop, too).
2, Add esound through Synoptic.
3, Preference->Sound on Device tab, changed all audio options to ALSA.
4, Preference->Sound on Sounds tab, disabled alert and sound effects.
5, On Preference->Session, uncheck PulseAudio Session Management.
6, In /etc/X11/Xsession.d directory, make sure there is no 70pulseaudio.  If it is, move it or delete it.
7, Reboot.

I think that's it.

---

### Post by altu on 2008-11-06
This is what I did.

[i]1.In **System->Preferences->Sound** set everything to ALSA instead of pulse
2. killall pulseaudio
   sudo apt-get remove pulseaudio
   sudo apt-get install esound
3. delete "/usr/bin/pulse-session" (make a backup copy first if you want pulse back at some point)
4. delete "/etc/X11/Xsession.d/70pulseaudio" (also make a backup copy first)
5. Just to be sure unselect anything related to pulse in **System>Preferences>Session**
6. Reboot
[/i]

Note: removing pulseaudio removes the "ubuntu-desktop" package but it's only a metapackage not the Ubuntu desktop :)

My solution was compiled from this thread: [http://ubuntuforums.org/showthread.php?p=6078392](http://ubuntuforums.org/showthread.php?p=6078392)

---

