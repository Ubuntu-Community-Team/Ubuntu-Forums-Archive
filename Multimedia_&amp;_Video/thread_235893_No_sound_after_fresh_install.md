---
title: "No sound after fresh install"
date: 2006-08-13
forum: Multimedia &amp; Video
---

### Post by nowindows on 2006-08-13
Hi, I just installed Dapper today, and the sound was working fine.
However, after a few updates, and a reboot, the sound is no longer working.
I already followed what I could of the Comprehensive Sound Problem Guide, but as I am new to linux, I am not very competent in solving problems yet.

My sound card does not appear to be installed as per the following
```
aplay: device_list:221: no soundcards found...
```
Although I believe that Ubuntu can detect it.

```
sudo modprobe snd-intel8x0
```
was also unsuccessful.

I would really like to get to know Ubuntu, but for a new user, a problem like this is somewhat discouraging.
Any help is greatly appreciated.

UPDATE
After getting the courage to try the harder bits of LordRaiden's guide, I somehow managed to compile the drivers from ALSAproject, and now I have sound again :D 
I guess my first day with Ubuntu wasn't so bad after all. Cheers

---

