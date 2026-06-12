---
title: "Kaffeine no longer launches, and video too bright"
date: 2006-12-16
forum: Multimedia &amp; Video
---

### Post by darehanl on 2006-12-16
ONE.
Hi, I use Ubuntu Edgy.

I've been trying to get kaffeine (0.8.2-0ubuntu2) to play a certain .mp4 file and have been installing and removing a number of packages (mplayer, gstreamer, etc.). I don't remember how I did it, but now kaffeine fails to launch. It just gives:

darehanl@yulgok:~$ kaffeine
darehanl@yulgok:~$

That's it. No error messages, no crashes, no nothin'. Clicking on the Kaffeine icon from KMenu > Multimedia > Kaffeine just gives me an hourglass that silently goes away after a few seconds. Ditto for "rightclick > Open With.. > Kaffeine." ](*,) 

I've tried --purge, dpkg-reconfigure, tried removing ~/.kde/share/apps/kaffeine, but nothing works;-(

I know I don't HAVE to use kaffeine, kmplayer is able to play videos just fine. It's just that I like the UI of kaffeine the most, and I miss it already.

-------------------------
TWO.
All the videos that I play on my machine have washed out colors. To see a decent image I need to lower the brightness and/or contrast. Anyone know what I need to do? I use an Intel embedded graphics card (i945 I think).

---

### Post by x64Jimbo on 2006-12-16
This might sound dumb, but you did kill the kaffeine process before attempting to start another instance, right?

---

### Post by darehanl on 2006-12-16
No, it was NOT a dumb question at all!! It seems that Kaffeine crashed sometime, and KDE saved the session for the crashed Kaffeine. That was the reason why all the later instances of Kaffeine did not run:
```
 darehanl@yulgok:~$ ps aux | grep kaffeine
darehanl  4615  0.2  1.1  32768 11564 ?        S    09:48   0:00 kaffeine -session 10e8e06c67000116625799500000045680048_1166309985_195540
```
All I needed was a **killall kaffeine**, and now my Kaffine is back! Thanks a million!:D


I'm still stuck with the "too bright of a video image problem," though.:mrgreen:

---

### Post by x64Jimbo on 2006-12-17
Is it only the videos you play, and not your windows, desktop, icons, etc? If so, you might be able to adjust your colors, brightness, and contrast in your media player directly.

---

### Post by darehanl on 2006-12-20
Yeah, it's just the video. VLC on windows play just fine, but xine or mplayer on Edgy is like that. It's just that adjusting them everytime I view a video is a bit annoying, nothing more:-)

Thanks a lot though.

---

### Post by x64Jimbo on 2006-12-21
desktop windows, not MS Windows. Is your video screwed up in all aspects of your monitor, or is it limited to videos you play in a media player?

---

### Post by solderhead on 2006-12-25
> **darehanl said:**
> No, it was NOT a dumb question at all!! It seems that Kaffeine crashed sometime, and KDE saved the session for the crashed Kaffeine. That was the reason why all the later instances of Kaffeine did not run:
```
 darehanl@yulgok:~$ ps aux | grep kaffeine
darehanl  4615  0.2  1.1  32768 11564 ?        S    09:48   0:00 kaffeine -session 10e8e06c67000116625799500000045680048_1166309985_195540
```
All I needed was a **killall kaffeine**, and now my Kaffine is back! Thanks a million!:D


I'm still stuck with the "too bright of a video image problem," though.:mrgreen:
I had the same problems with Kaffeine, and the "killall" solution solved my problem.  Thanks!

---

### Post by ilpirata on 2007-01-15
I had the same problems... fixed! Thank you.

---

### Post by darkasecas on 2007-01-25
> **ilpirata said:**
> I had the same problems... fixed! Thank you.
Same here, thank you very much =D

---

