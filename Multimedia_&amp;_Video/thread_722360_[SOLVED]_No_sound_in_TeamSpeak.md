---
title: "[SOLVED] No sound in TeamSpeak"
date: 2008-03-12
forum: Multimedia &amp; Video
---

### Post by Holy Cheater on 2008-03-12
Sound Card: Creative Labs Sound Blaster Live! Value EMU10k1
OS Version: Ubuntu 7.10 Gutsy Gibbon

Sound works in OS, but not in TS.. Search through forums didn't gave me any clue to a solution.
1) If I just launch TS I have my mic and headphones muted
2) If I launch teamspeak through alsa-oss (aoss teamspeak), my headphones are not muted, but I still don't hear any sound and my mic is muted.
3) If I launch teamspeak through esd (esddsp teamspeak), it is like I launch with no options
Mic is selected correctly in the mixer: capture and mic recording are on (at least I hear myself in headphones)
The results doesn't depend on if I use any other sound app (amarok) or no.

If I should provide any other info for diagnostics, tell me.

---

### Post by Holy Cheater on 2008-03-13
bump

---

### Post by Holy Cheater on 2008-03-15
Well, I've solved my problem..
First, I've replaced esound daemon with pulseaudio
**pulseaudio-esound-compat** package automatically replace it (esound) with pulseaudio..
Second, edit the **/etc/pulse/daemon.conf **file
```

sudo gedit /etc/pulse/daemon.conf

```Find this line:
```

; resample-method = src-sinc-fastest

```Replace it with:
```

resample-method = src-sinc-best-quality

```with sinc-fastest resampling methong *teamspeak* would.. ermm.. croak
Third, I've selected *PulseAudio Sound Server* as a default playback/capture device for all devices in **System - Preferences - Sound **menu
You should also install **pulseaudio-utils** package and launch teamspeak through Pulse's OSS wrapper
```

padsp teamspeak

```This helped to me, hope it will help to someone who have the same problem.

---

### Post by Shadowfire on 2008-03-31
This did not work for me  :(

---

### Post by Dolmio on 2008-04-13
> **Holy Cheater said:**
> Well, I've solved my problem..
This helped to me, hope it will help to someone who have the same problem.

I have the same problem with Teamspeak and sound and I never found a solution to it. So, when I want to play ET, I have to use Windows.

I will try out your solution when I get the time. It sure would be nice if it would work.

/Dolmio

---

### Post by mriedel on 2008-04-27
padsp teamspeak works for playback, but teamspeak doesn't receive any input from my microphone. It works in other apps and in pulse itself though (checked volume meters etc).

**Update:**

I seem to have fixed this issue. Check [http://ubuntuforums.org/showthread.php?t=767515&page=2](http://ubuntuforums.org/showthread.php?t=767515&page=2).

---

### Post by fatalGlory on 2008-04-28
After a long winded go at making teamspeak play nice with pulseaudio, I finally googled for other options and found [mumble]("http://mumble.sourceforge.net")

It is a good (maybe better) replacement for teamspeak or ventrilo that works on windows and linux (and experimental mac osx support).  The linux version uses alsa and it worked painlessly on my fairly fresh install of hardy.

Yay!  DotA and Voice Chat for me!  Discovered it on my birthday too, yay!

---

### Post by mriedel on 2008-04-28
Thanks for the link and congratulations :)

---

