---
title: "MPD can't access sound device after pausing the player"
date: 2009-09-28
forum: Multimedia Software
---

### Post by oneindelijk on 2009-09-28
Hi, 

I'm on Karmic Koala Alpha 6 (I think). Using Ario as an MPD client. 
Since I noticed that Ario sometimes didn't want to play a song while Exile did, I installed mpc and start fiddling around with it.
Sometimes when I want to start a song it says "ERROR: problems opening audio devices" just after booting up.
Sometimes it works, but then it stops working after a while and sometimes it stops working after a "mpc pause" & "mpc play" command.
Sometimes I can get it working by killing mpd (MPD --kill as root), alsa-reload (as root) and mpd (as user).
MPD then says something about finding ALSA and succesfully connecting (always) but it only still works sometimes...

If anyone can help me, please tell me what logs you need (or should I file a bug report ?)

thx
Sam

---

