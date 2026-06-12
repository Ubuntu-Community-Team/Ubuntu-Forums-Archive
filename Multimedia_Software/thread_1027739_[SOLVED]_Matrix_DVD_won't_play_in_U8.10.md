---
title: "[SOLVED] Matrix DVD won't play in U8.10"
date: 2009-01-01
forum: Multimedia Software
---

### Post by skern03 on 2009-01-01
My geek cred is low enough, but now I can't figure out how to get The Matrix to play on a DVD. No self-respecting geek can live without that movie. Yikes, this drops my geek cred well below zero. Please help!

I have a new Samsung DVD R/W. I scanned the forum, and loaded SMPlayer. Neither it, nor the Movie Player work. I've loaded all of the GStreamer plugins. I also loaded Pitdll. I tried this on a Dell laptop (5 yrs old) with a built-in DVD drive and my desktop. Both fail. 

The DVD is correctly identified, and when inserted, it offers to load PC Friendly, so I know the player is working.

However, depending on the player selected, I get different errors, such as cannot mount media and media unreadable.

The track files are *.vob, and they're identified as MPEGs if you browse the DVD contents. Is it possible they're encrypted?

Any ideas?

---

### Post by 2hot6ft2 on 2009-01-01
The complete way
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Or the short way

```
sudo apt-get install ubuntu-restricted-extras
```

in a terminal.
Applications>Accessories>Terminal

You'll also need libdvdcss2
[http://packages.medibuntu.org/intrepid/libdvdcss2.html](http://packages.medibuntu.org/intrepid/libdvdcss2.html)

---

### Post by skern03 on 2009-01-01
Thanks! for the most part, your suggestion worked on both the laptop and the desktop. I had better success with SMPlayer than MoviePlayer. MoviePlayer threw several different errors, but eventually played. 

The volume was a bit tricky in SMPlayer - had to set it up in the PulseAudio Applet volume control, and even then, had to crank the hand volume control way up to hear the audio.

---

