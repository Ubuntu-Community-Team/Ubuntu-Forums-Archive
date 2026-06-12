---
title: "Either Rhythmbox or YouTube... never both"
date: 2008-09-03
forum: Multimedia Software
---

### Post by j0s1ah on 2008-09-03
Strange happenings here... If start my computer and immediately open Firefox (3.0.1) and go to Youtube.com I am able to watch and hear a video.
If I, instead, immediately open Rhythmbox (0.11.5) and play an audio file, I can play and hear an audio file.

So in the above instances, they both work... the problem(s) arise when I try to watch Youtube after I have already played an audio file of Rb, or if I try to watch a video on Youtube after I have played an audio file on Rb.

Sounds absurd, and no doubt, it is... Any troubleshooters out there that can give me some help? I am a modest noob on linux.
Thanks

---

### Post by tuxxy on 2008-09-03
Are you using ALSA as the sound poutput at system > prefs > sound

---

### Post by BenFischer on 2008-09-05
I actually have the exact same problem, and I'm using ALSA.

---

### Post by bodysnatcher on 2008-09-05
yeah i get it too.

it's because your soundcard can't handle two sources at once. i have to close my current playlist on RB then restart firefox everytime i wanna hear something on the internet.

i don't think there's a way to solve it, unless anybody else knows?



matt

---

### Post by j0s1ah on 2008-09-11
> **bodysnatcher said:**
> yeah i get it too.

it's because your soundcard can't handle two sources at once. i have to close my current playlist on RB then restart firefox everytime i wanna hear something on the internet.

i don't think there's a way to solve it, unless anybody else knows?



matt

Works better than restarting the whole system. Thanks.

Bummer about the lack of ability to play while both are simultaneously open, though... I can't say that this have ever been an issue on any other OS I have used.

---

### Post by Joe of loath on 2008-09-11
it's because most of the sound systems are so old, they originated in the days you only needed one source of audio.

i would beleive it's hard to design a new one from scratch...

---

### Post by kevCast on 2008-10-02
I was able to do both in Debian Lenny. When I switched to Hardy, it's become a problem. Is there still no fix?

---

### Post by wolfen69 on 2008-10-02
```
sudo apt-get install libflashsupport
```should do the job. restart firefox if open.

---

### Post by ManyBeers on 2008-10-03
> **j0s1ah said:**
> Strange happenings here... If start my computer and immediately open Firefox (3.0.1) and go to Youtube.com I am able to watch and hear a video.
If I, instead, immediately open Rhythmbox (0.11.5) and play an audio file, I can play and hear an audio file.

So in the above instances, they both work... the problem(s) arise when I try to watch Youtube after I have already played an audio file of Rb, or if I try to watch a video on Youtube after I have played an audio file on Rb.

Sounds absurd, and no doubt, it is... Any troubleshooters out there that can give me some help? I am a modest noob on linux Thanks

I had the same problem as you,but now both can play simultaneously after 
following this guide.
[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by xngk on 2008-10-06
> **wolfen69 said:**
> ```
sudo apt-get install libflashsupport
```should do the job. restart firefox if open.
Worked perfectly, thank you for the fix.

---

