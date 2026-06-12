---
title: "Sound &quot;pops&quot; Randomly during media such as Youtube or Music"
date: 2013-09-12
forum: Multimedia Software
---

### Post by Der_Scuple on 2013-09-12
Hello all, I've been reading a few threads but each problem seems to be slightly different. 

More or less I hear a rather intrusive "pop" or "spit" in audio typically at the start of media - like when I start a youtube video or song.  I will also hear these "pops" or "spits" when I'm listening to music or watching a video, and start to multi-task. Opening another program, Alt+Tabbing to a different window, ect.ect. If I just sit there and WATCH a video or LISTEN to a song with no multi tasking, it seems okay. 

I was looking on the forums for a few solutions and found a few ideas, such as modifying the code line:

```
options snd-hda-intel power_save=10
``` in the file: ```
/etc/modprobe.d/alsa-base.conf
``` 

But no such line exists in mine, and I doubt simply 'adding' it in there will fix the problem.

I also tried modifying the intel power management file having to deal with portable devices, but it didn't seem to work either, as expected, since I'm on a desktop.

I'm sort of stumped for solutions - I had this problem before on a old computer back a few years ago, and my solution was to uninstall the RealTek drivers and let the default windows drivers take over.

I should also note that I'm dual-booting Win7/Ubuntu. On the Windows 7 side of things, everything is fine. However I am using the "RealTek HD Audio Center" drivers and Software, where on Ubuntu I have no idea what drivers are running. Might be the problem, unsure how to fix it.

Any help would be GREAT

---

