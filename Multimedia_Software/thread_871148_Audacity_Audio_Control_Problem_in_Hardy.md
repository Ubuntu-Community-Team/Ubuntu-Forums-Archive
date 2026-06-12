---
title: "Audacity Audio Control Problem in Hardy"
date: 2008-07-26
forum: Multimedia Software
---

### Post by hookzilla on 2008-07-26
(I hope I have this in the correct forum.)
I have installed Hardy 8.04.1 on two PC's, along with Audacity.  One PC has an onboard Ensonic PCI sound system, while the other has both an onboard Via sound system and a SB Audigy PCI card.  On the second PC, I use the Audigy card.   In both instances, I can't get the sound controls in Audacity to work - neither record or playback, neither volume or balance.  I use the line input on both systems to record from LP. I've used Audacity previously on 7.10 with n o problem. Can anyone offer any suggestions?

Thanks

---

### Post by hookzilla on 2008-07-31
Anybody have any ideas?

---

### Post by Bush_Roo on 2008-09-05
Had the same problem, but fixed it with:

sudo apt-get remove jackd

(I didn't know jackd was installed, so I went looking why Audacity wasn't working... dau)

---

### Post by pgmer6809 on 2008-10-01
I have heard that Audacity uses PulseAudio under Heron and that this combination does not work. Not sure what the fix is. Apparently audio under Heron is so bad that people have gone back to Gutsy.

I am trying to Audacity to record from my Audigy 2 ZS card under Gutsy.
(For LP's like you).
You say you had it no problem, but I cannot get it to work.
I know the connections are OK, because I can hear the source via the Audigy headphone.
Alsamixer volume controls work for everything also.

Audacity can play fine, just not record.
How did you do it?

pgmer6809 <at> yahoo dot com

---

### Post by eye208 on 2008-10-01
You can [remove PulseAudio](http://ubuntuforums.org/showthread.php?t=885437). This will fix Audacity and several other sound issues.

---

