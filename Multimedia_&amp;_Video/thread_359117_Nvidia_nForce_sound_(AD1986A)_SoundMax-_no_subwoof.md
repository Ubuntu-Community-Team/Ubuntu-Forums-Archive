---
title: "Nvidia nForce sound (AD1986A) SoundMax- no subwoofer"
date: 2007-02-11
forum: Multimedia &amp; Video
---

### Post by mdurkin on 2007-02-11
Hi All,
I have ubuntu 6.10 installed on an asus A8N-VM CSM motherboard. The install works pretty much flawlessly, but I am unable to get any sound out of the subwoofer when playing audio files. Everything sounds pretty tinny as a result.
Does anyone have any idea how to get normal 2 channel sound to (mp3s mostly) to use the sub. Nothing is using the sub right now...
Thanks,
Matt

---

### Post by Berylfun on 2007-03-12
It's the same problem that i'm trying to solve for the past 4 days.
Pretty newbie to linux i've been lost to google for this issue  but i came out with nothing :(

---

### Post by mdurkin on 2007-05-27
Has anyone actually found a definitive answer to solving the intel HD Audio problems?
By playing around with /etc/modprobe.d/alsa-base options (adding options snd-intel-hda index=0 model=3stack), I managed to get the sub going, but with nothing but a high pitched scream from the left speaker.
I've searched the web and found loads of people with similar problems, but no real definitive solutions :(

Anyone got any good ideas?

---

### Post by mdurkin on 2007-05-31
So - same problem with 7.04, and 7.04 feisty. I even compiled and installed the latest alsa drivers. if anything it got worse - now i have audio from one speaker and screaming from the other. Nothing from the sub.
Must say - I'm really tearing my hair our with this!

---

### Post by Manatherin on 2007-10-02
i have a different asus motherboard with the same sound card and the same problem, but i recently noticed that the asus motherboard cd actually has some linux audio drivers so mabye u should check ur cd out. hope this helps can u let us all know if u get this fixed

---

