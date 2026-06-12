---
title: "tried to use fdisk, didn't format my sd card and now i can't use svideo to tv again"
date: 2010-01-25
forum: Multimedia Software
---

### Post by Robert John Kelly on 2010-01-25
i have no idea if anyone can help. linux has been nothing but a hassle for me. i just wanted something that wouldn't be affected by viruses. 
to the point though. i read an thread on here about using fdisk to format sd cards. tried everything it said, not only did it not work but now my svideo to my tv no longer works. i have ubuntu 8.04 (yes i would upgrade but i can't bc for some reason anything newer won't work on my laptop) if anyone could shed some light it would be greatly appreciated. thanks in advance

---

### Post by ajgreeny on 2010-01-25
> **Robert John Kelly said:**
> i have no idea if anyone can help. linux has been nothing but a hassle for me. i just wanted something that wouldn't be affected by viruses. 
to the point though. i read an thread on here about using fdisk to format sd cards. tried everything it said, not only did it not work but now my svideo to my tv no longer works. i have ubuntu 8.04 (yes i would upgrade but i can't bc for some reason anything newer won't work on my laptop) if anyone could shed some light it would be greatly appreciated. thanks in advance
How did you try to use fdisk, what command did you use, and what error messages did you see, if any?

Without more information on exactly what you did, and what happened when you did it, it is impossible to answer.

---

### Post by efflandt on 2010-01-26
sudo fdisk can add/remove/view partitions, but it does **not** format them.  You can change partitions and format them with **gparted** if you install that package.

But I don't see how that could possibly affect S-Video.  Did you have your TV on with S-Video selected on it before booting your computer?  If not, X might not know it is there or connected (unless you use xrandr).  Does /var/log/Xorg.0.log show any sign of your TV out?

---

### Post by Robert John Kelly on 2010-01-27
i don't know what i did really. i just followed all the steps in the thread i found on this site. it was for a 4gb sd card though. i have an 8gb card. it didn't work like it said on the thread but i just kept going with the steps. 
yes my tv was hooked up at the time and it was working. i've had issues with this before. the only thing that worked  was re-installing ubuntu. i don't know why but i can't mount a newer version either. 
either way i can't format the sd card and i can't use svideo anymore. if there is a specific way i can find out what i did i will. if not i guess i'm screwed.
wether you can help or not, thank you very much for taking your time to try

---

