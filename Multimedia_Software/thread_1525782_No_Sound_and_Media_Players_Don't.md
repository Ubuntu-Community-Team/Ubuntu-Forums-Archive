---
title: "No Sound and Media Players Don't"
date: 2010-07-07
forum: Multimedia Software
---

### Post by Zayfox on 2010-07-07
Only a few minutes ago, my sound just seemed to disappear while I was listening to some Dream Theater.

The onboard sound is disabled in the BIOS as I'm using another card.
Rhythmbox won't play anything. Starting a song just leaves the progress bar sitting at the start.
Sound preferences shows everything up at full. I tried modding the volume, but I can't move it (It moves for like a millisecond then hits 100% again).

It's a C-Media sound card. It was working perfectly prior to a few minutes ago.

What's goin' on here?

**Edit:**
I'm using some combination of PulseAudio and ALSA. PulseAudio is installed and I believe that's my primary 'driver'.

---

### Post by Rhemat on 2010-07-07
Start your Media Player in terminal (just type in rhythmbox, or amarok, banshee, or whatever you're using), and watch what the terminal readout is.  Chances are that PulseAudio quit on you.  The unfortunate bit, is that the only way I've found to fix it, is to purge PA, and then reinstall it, and hope it doesn't quit for a while.  I've found guides on how to fix PA permanently, but they never worked for me.

---

### Post by Zayfox on 2010-07-07
```
elliot@Apollo:~$ rhythmbox
```
Nothing after that, even if I attempt to play a song.

---

### Post by lidex on 2010-07-08
Try this:
```
killall pulseaudio
```
or reboot

---

