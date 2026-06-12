---
title: "ck8s surround sound issue in jaunty"
date: 2009-09-19
forum: Multimedia Software
---

### Post by paintonhisface on 2009-09-19
So, I've tried several of the usual methods of enabling surround sound, but still can't get it to work.  I have an onboard audio card (CK8S, which supports 7.1 setups) When I was running Intrepid on this same comp, I had success with these methods.

First, I used volume control within the volume applet to show all pertinent channels (surround, center, lfe) and make sure they weren't muted.  Additionally, I added the options 'Surround Jack Mode' and 'Channel Mode' setting the former to 'Independent' and the latter to '8ch'.

This had no effect. So, on top of that, I changed /etc/pulse/daemon.conf, setting the default channels to 8.  Reloading pulse audio by killing and restarting it from the terminal, or alternatively by restarting the computer, makes the sound all crackly and slow (shifted in frequency).  I get the error

```
Device front:0 doesn't support 44100 Hz, changed to 48000 Hz
```

whether or not the daemon.conf is set to 2 or 8 channels.  Also, surround sound doesn't work (only my front two speakers produce sound).

I've checked out several forum postings, including the tutorials, and haven't found a solution.

---

### Post by paintonhisface on 2009-09-28
**bump**

plz help.

---

