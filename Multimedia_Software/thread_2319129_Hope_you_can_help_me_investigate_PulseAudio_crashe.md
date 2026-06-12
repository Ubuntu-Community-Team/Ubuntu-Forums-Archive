---
title: "Hope you can help me investigate PulseAudio crashes"
date: 2016-04-01
forum: Multimedia Software
---

### Post by The Bright Side on 2016-04-01
Hey guys! I've been experiencing a few too many crashes in PulseAudio lately, and I think it's time I start investigating them.

My scenario: I listen to music in 5.1 (or quadraphonic) and less frequently stereo every day, using VLC Media Player, and sometimes Parole. Sound goes through an HDMI cable from my NVidia card to my home theater system's receiver. Now, some days, everything works great all day, I can listen for 8-10 hours straight while working. On other days, it crashes either sometimes or frequently, for no apparent reason, sounding something like this:

*Woo-hoa, livin' on a Pppp [silence]*

**Things I've figured out:**

[LIST]
[*]I think I've narrowed the crashes down to PulseAudio itself. The Pavucontrol window goes blank for a moment when these crashes happen, then pops back into action, indicating PulseAudio restarts in the interval
[*]Another indicator is that VLC works again after I close and re-open it, presumably because PulseAudio restarted in the meantime
[*]It has nothing to do with the playback apps I run. Sound has crashed in the past while I was using VLC, Parole, Audacious and during Skype calls
[*]96 KHz multichannel FLAC files cause more crashes. Downconverting to 48 KHz has helped
[*]I haven't found a reliable way to reproduce this issue. Right now, for all I know, it happens whenever the PC is in a bad mood.
[/LIST]

**Things I suspect:**

[LIST]
[*]I think shutting down my PC and restarting it (not simply rebooting) helps
[*]"Heavier" files (6 channels, high resolution) might be causing more trouble than stereo MP3s
[*]I have a 4 GHz i7 CPU and 16 GB DDR3-1866 RAM, so I don't think it's a performance issue
[/LIST]

**Thing I'd like to find out:**

[LIST]
[*]In the past, I've run programs from the Terminal (like Remmina) to see their output when something goes wrong. But since PulseAudio is a service that always runs, I don't think I can do that. I wonder where it logs its events? Any ideas?
[*]Haven't yet run VLC or Parole from the Terminal to see what they put out. Will keep an eye on them in the next few days.
[/LIST]

Can you suggest other approaches to finding out what's happening? Perhaps if I understand why it crashes, I can do something about it myself - or at least file a useful bug report.

Also, anybody else had these kinds of PulseAudio crashes before?

---

### Post by Yellow Pasque on 2016-04-01
[https://wiki.ubuntu.com/PulseAudio/Log](https://wiki.ubuntu.com/PulseAudio/Log)

---

### Post by The Bright Side on 2016-04-01
Ah, that's great, thanks so much! I'll see what I can do with this. Since I can't reproduce the bug whenever I want, it might get tricky, though. Any other ideas will be appreciated!

---

### Post by SeijiSensei on 2016-04-01
Take a look in /var/log/syslog the next time it crashes to see if any errors are logged there.

---

