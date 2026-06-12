---
title: "MPEG audio playback dies after a few days"
date: 2009-02-11
forum: Multimedia Software
---

### Post by ChrisC on 2009-02-11
I have a strange and annoying problem.  MPEG audio (mp3 and m4a) playback will work for me, and then suddenly not work.  I can reboot the machine and all is well again.  At some point after hours or days or perhaps weeks if I'm lucky, the playback simply stops working.  Playback that previously worked in audacious, totem and rhythmbox now works with NONE of those programs, with each program hanging on the file at the 0:00 mark and going nowhere.

I ALREADY HAVE THE DRIVERS AND IT WORKS IF I JUST REBOOT.  But it stops after a while.

"aplay -l" detects the NVidia CK8S chipset

"lspci -v" detects the "nForce3 250Gb AC'97 Audio Controller"

What else can I do at the command line to isolate this further?

---

### Post by ChrisC on 2009-02-13
Bump?

FYI, audio in general is fine; for example, I can hear Youtube clips.

---

### Post by ChrisC on 2009-02-13
One last try before I take it up to a general forum where maybe more people are looking ...

---

### Post by kostkon on 2009-02-13
What version of Ubuntu do you have?

---

### Post by mc4man on 2009-02-13
If you are using 8.10 and if you are using pulseaudio then it's possible pulseaudio is crashing.
Run top in a terminal when playing an audio file and see what up. (or when sound stops then try to play a file, open top and see if pulseaudio is running

---

### Post by ChrisC on 2009-02-14
Ah, sorry.  I'm running 8.04 .

Pulseaudio is indeed running on my system, and it continues to run right now with the system in this "won't play MPEG" state.  The file loads in the player (whichever one I try) and looks like it's starting to play, but it never advances past 0:00 .

Is there something in the MPEG decoding area that I can check for?

---

### Post by kostkon on 2009-02-14
Have you tried following [this guide]("http://ubuntuforums.org/showthread.php?t=789578") to better setup *PulseAudio*? Also, you should install *Flash 10* if you have *Flash 9*, since *Flash 9* blocks the card and prevents *PulseAudio* to use it and you get symptoms like the ones you have.

To do it, first of all, go to *System &#8594; Administration &#8594; Software Sources* and make sure that the *Partner* repository is enabled (*Third-Party Applications* tab).

Then in *Synaptic* remove completely the *flashplugin-nonfree* (this is *Flash 9*) package and then, search for the *adobe-flashplugin* (this is *Flash 10*) and install it.

---

### Post by ChrisC on 2009-02-14
Thanks kostkon.  That's an awesome write-up that you linked to.  Alas, there are a couple things there that scare me.  He wants me to link to his repository and then do a dist-upgrade?  Ouch.  I'm trying to keep my system as simple and clean as possible, because otherwise every ELSE breaks and spins out of control.  Ugh.  Well, I'll tackle it soon.  In the meantime, I'll reboot :(

---

### Post by kostkon on 2009-02-14
> **ChrisC said:**
> Thanks kostkon.  That's an awesome write-up that you linked to.  Alas, there are a couple things there that scare me.  He wants me to link to his repository and then do a dist-upgrade?  Ouch.  I'm trying to keep my system as simple and clean as possible, because otherwise every ELSE breaks and spins out of control.  Ugh.  Well, I'll tackle it soon.  In the meantime, I'll reboot :(
You can skip part B and do only Part A and the Appendixes.

It is important that you do part A so that ALSA sounds pass through PulseAudio. But since you are skipping Part B you'll not get optimal perfomance, but a decent one.

After that you may need to reconfigure the sound configuration of some programs and some apps may have problems (e.g. for Skype: If you follow Part B it will work OK, if not, you may have problems with it).

Also, it is important that you install Flash 10.

Hope that helps.

---

