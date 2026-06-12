---
title: "Audio clashing?"
date: 2010-02-04
forum: Multimedia Software
---

### Post by Zyrtec on 2010-02-04
This has probably been answered before, but I can't find the exact problem from someone else in a different topic. I hope this is the right section.

I seem to be having some audio clashes. I use Exaile to play music (if that matters), and after I play music, no sound comes out of videos (not just Ubuntu, it won't work from Yahoo or MSN videos either). Then when I try to go back to playing my music on Exaile, no sound will come out of that. Likewise, if I restart the computer... the sound works again. If I instead watch a video first, there will be sound -- but as soon as I try to play music from Exaile, nothing comes out.  I was wondering if there's any particular way to fix this problem.

Thanks!

---

### Post by Zyrtec on 2010-02-05
Bump

Anyone?

---

### Post by Zyrtec on 2010-02-07
Bump, please...

I'm still having the same problem, and I'd like to be able to have sound in more than one application.

---

### Post by cottfcfan on 2010-02-07
I had a similar problem in Kubuntu.
It appeared Pulseaudio wasn`t installed properly.
I just ran sudo apt-get install pulseaudio from terminal, and it pulled in 5 packages that weren`t installed.
After that problem was solved.
don`t know if this will work for you but its worth a try.

---

### Post by Zyrtec on 2010-02-07
Thank you for the suggestion! I gave it a try, but it said everything was up to date and there was nothing to be added/upgraded.

---

### Post by llawwehttam on 2010-02-07
Try
```
sudo apt-get update ; sudo apt-get upgrade ; sudo apt-get purge pulseaudio ; sudo apt-get autoremove ; sudo apt-get install pulseaudio
```

I did that when I had a similar problem and it worked for me.
(unless it was because I sneezed )

---

### Post by Zyrtec on 2010-02-07
Uhh, this method caused more problems. After I did those commands, I rebooted... and now it says my graphical configuration is gone. I'm currently in Low Graphics settings....   What happened, and how to I get it back the way it was? x___x


Edit: I'll try reinstalling graphics drivers, I guess


doubledit: Alright, now that that's fixed... I guess I'll test the sound

---

