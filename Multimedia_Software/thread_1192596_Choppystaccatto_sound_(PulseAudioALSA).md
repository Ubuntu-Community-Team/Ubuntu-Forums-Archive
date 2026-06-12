---
title: "Choppy/staccatto sound (PulseAudio/ALSA)"
date: 2009-06-20
forum: Multimedia Software
---

### Post by chochem on 2009-06-20
Symptoms:
[LIST]
[*]After a while of playing music or video (and sound working perfectly normal), music (and accompanying video, if any) begins progressing very, very slowly - I'd say 1/100th of 'realtime' or worse.
[*]The effect is to chop the sound up into tiny fragments delivered one at a time to a very fast beat, stacatto-like. Sounds a bit like a very boring trance track.
[*]The track/video DOES progress, though - it's not just looping the same bit. Only very slowly.
[*]The effect disappears after while after the offending program has been closed. All sound after this has occurred follows this pattern.
[*] Somewhat similar to 
[http://ubuntuforums.org/showthread.php?p=5848083&highlight=choppy#post5848083](http://ubuntuforums.org/showthread.php?p=5848083&highlight=choppy#post5848083)
[/LIST]

Context:
[LIST]
[*] Hardware: 00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02). There is only the one sound card. lsmod reports that all the usual snd_atixp modules are loaded.
[*]I've previously had working audio (ALSA and Pulse) on a recent linux install (kernel 2.6.29) - this was a built-from-the-ground Arch install that I got fed up with maintaing (it's a lot of work, that DIY-thing). It autoloaded the exact same modules that Ubuntu does, so I'm a bit at a loss.
[*]I believe the problem is the same whether using PulseAudio or 'pure' ALSA (see my atttempts at solving).
[*]The problem became apparent only after a couple of days of experimenting with the new install (didn't use any media). A fresh install playing some downloaded Ogg files soon exhibited the same symptoms.
[*] The symptoms have been the same whether using mplayer, mpd or Rhythmbox.
[*]The appearance of the problem appears completely random. It can 'strike' within a few minutes of playback or after an hour, whether I'm actively using the computer or not. htop reports no particular CPU intensive operation. dmesg is silent.
[/LIST]

Attempts to solve:
[LIST]
[*]My first assumption was that it was a pulseaudio issue, so I tried killing it and playing some music using ALSA. Seeing that that just started a new instance of pulse, I decided to remove it (apt-get remove pulseaudio). 
[*]The problem however still crops up using just ALSA. The only noticeable difference is that once the problem has struck, i can now kill the app producing the garbage sound, and play sound files in another, at least with mplayer -ao alsa. This will produce some regular 'hickups' (like once every ten-twenty seconds) but not the chopping effect. I will still not be able to play video, once the effect has set in (even trying to play the sound part of a video file - mplayer -vo null - will fail).
[*]Modules: I've tried blacklisting snd-atiixp-modem and snd-pcsp. No effect. Reviewing the alsa specific file contained it modprobe.d, I figured that it might just be a hack too far, and deleted it. This reduced the number of modules loaded - or maybe just the alsa-oss one - but did not appear to impact the problem after a reboot. 
[*]Googling: Needless to say lots of hits, very little useful information 
[/LIST]

Grateful for any suggestions.

---

### Post by can-o-worms on 2009-06-21
Unfortunately, I have nothing to offer other than to say I am having exactly the same issues on an R51e with an SB400 chip.

I've found a bunch of threads with people in the same boat, but as yet nothing close to a solution.
This thread has been the most helpful, as my next move was going to be to uninstall pulseaudio, but it would seem that is not going to fix this.

thanks

---

### Post by chochem on 2009-06-21
Well, you're welcome for what it's worth :) I know there's got to be tons of threads dedicated to the same issue but it's hard to see if it is the same as they're usually just vague symptoms reports and random configuration modifications. 

EDIT: Oops, reread previous post, information was supplied.

EDIT: A search for SB400 turned up [this thread]("http://ubuntuforums.org/showthread.php?t=1075893") which is obviously the same problem. In the interest of economy, I suggest closing this thread and continuing the older one. I'll post a link pointing back to my description.

---

