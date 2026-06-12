---
title: "Audio problems forcing daily reboots"
date: 2008-06-13
forum: Multimedia Software
---

### Post by Synival on 2008-06-13
No response from Hardware & Laptops, reposting here.

I'm running a Gateway MT6728 laptop with snd_hda_intel for audio.  The longer things are running, the worse things get.  Typically I'm running Pidgin and look at videos on YouTube quite often in Firefox.  At some point (not sure when), sound from Pidgin gets backed-up and will either not play at all, or will play all at once sometime later.

But that's not my problem.  The big problem is that at some point, audio stops working, and it causes applications to crash, freeze, or simply not run altogether.  Firefox refuses to open, and when running gnome-terminal the window will come up but a command prompt never appears.  Ctrl+alt+backspace does not solve the problem; at this point, everything will freeze after I attempt to log in.  Only a complete reboot seems to fix it.

Any thoughts?  Linux audio seems like a big complicated mess to me and I have no idea how it works or how to troubleshoot it.

---

### Post by diaa on 2008-06-13
Regarding the audio problem, I've just modified ALSA to use pulseaudio and now I'm running audio simultaneously from Firefox(flash 9), mplayer and the command-line paplay and even games without problems

Follow the instructions on the following page:
[https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)

and may be you can also check

[How To: The (almost) Perfect Pulse Audio Setup]("http://ubuntuforums.org/showthread.php?t=776739")
[Why you should care about PulseAudio (and how to start doing it)]("http://www.linux.com/feature/119926")

---

### Post by Synival on 2008-06-16
Hmm, after following every instruction on those tutorials, things are definitely working better!  But sound did eventually shut-off and certain applications using audio started crashing, namely Flash movies in Firefox.  A ctrl+alt+backspace didn't fix the problem, everything froze after logging in, leaving me with a mouse cursor and a salmon-colored background.  But it's a step up, things seem to be running more smoothly in general.

Any other ideas?

---

### Post by markbuntu on 2008-06-16
This is a flash 9 problem and is fixed in flash 10 and the libasound2 update.

---

### Post by Synival on 2008-06-24
Well, it looks like that did it :)  Now flash is crashing often, but all it takes is a restart to Firefox and everything's back to normal.  Not ideal, but I can definitely deal with it.  I remember dealing with this before on another computer, it sounded like yet another linux flash bug...  But hey, progress is progress.  Thanks!

---

### Post by diaa on 2008-06-25
> **Synival said:**
> Well, it looks like that did it :)  Now flash is crashing often, but all it takes is a restart to Firefox and everything's back to normal.  Not ideal, but I can definitely deal with it.  I remember dealing with this before on another computer, it sounded like yet another linux flash bug...  But hey, progress is progress.  Thanks!

That's strange, I'm running pulseaudio with ALSA configured to use pulseaudio too and I can play videos inside flash and outside and play games at the same time, for example right now I'm running amarok and a video on youtube, I don't know why you're having these crashes.

EDIT:
I didn't do anything special for flash btw, it's flash 9

---

