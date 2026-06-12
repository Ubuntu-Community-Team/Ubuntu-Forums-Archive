---
title: "SPDIF dead"
date: 2006-09-23
forum: Multimedia &amp; Video
---

### Post by klockren on 2006-09-23
I just built a new computer for a friend.
The mainboard is a GigaByte GA-M51GM-S2G with integrated Realtek ALC883 Audio Codec. (Northbridge: nVIDIA® GeForce 6100, Southbridge: nVIDIA® nForce 430).

After installing Ubuntu (with Gnome and KDE), I couldn't get any sound from the SPDIF output port.
When I open Kmix on my own computer with a SoundBlaster Audigy 2, I have a switch for SPDIF output which isn't present on my friend's system.
When installing the sound driver in Windows XP, the SPDIF gives output instantly.

Is it possible to activate the SPDIF output? Is it a driver conflict that could be solved by upgrading Dapper to Edgy? Any suggestions are very welcome as he is going to use this computer as a Media Center and he will switch back to WinXP for sure if we cannot solve this :(

---

### Post by ATJ on 2006-09-24
Same problem here...:( 
I'm using Audigy 2 ZS and one day suddenly i had no sound...I think it has something to do with alsa configuration but still i have found no solution.It's like when ubuntu starts it plays the login sound for just a moment and then it's like something covers it...Any suggestions?

---

### Post by ATJ on 2006-09-26
A possible solution may be found here:
[http://www.ubuntuforums.org/showthread.php?t=205449](http://www.ubuntuforums.org/showthread.php?t=205449)

---

### Post by klockren on 2006-09-27
Thanks, I will try this out!

---

### Post by klockren on 2006-09-28
Today I made a fresh installation of Edgy Eft on his computer. After that, I coluld open alsamixer and manually unmute the SPDIF. Perfect!

---

