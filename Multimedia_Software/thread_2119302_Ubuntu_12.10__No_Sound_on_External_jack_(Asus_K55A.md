---
title: "Ubuntu 12.10 : No Sound on External jack (Asus K55A)"
date: 2013-02-23
forum: Multimedia Software
---

### Post by EESauce on 2013-02-23
Alsa Info Script output : [http://www.alsa-project.org/db/?f=2fa56a7ab39c2c829c1d8f32f63f1b9412010fdf](http://www.alsa-project.org/db/?f=2fa56a7ab39c2c829c1d8f32f63f1b9412010fdf)

 I have a Asus K55A model dual booting windows 8 and Ubuntu 12.10. The sound coming out of the jack is not working. Any help please, I am new to Linux.

---

### Post by varunendra on 2013-02-23
Post moved to its own Thread.

---

### Post by rreyes3713 on 2013-02-23
Please help us, I have the same laptop ( lol ).

I could have sworn it used to work though. I think it stop working when I was fiddling around installing / uninstalling media apps. Not sure, maybe all along it never worked.

built-in speakers work, eaphones work under Window 8.

---

### Post by gossfunkel on 2013-03-07
Same here. Tried fiddling with alsa conf settings a bit, no change.

Headphones working fine in Windows 7, but in Ubuntu 12.04 absolutely none.

My sound got a bit messed up when I installed steam but I think it's back to normal now- except for the missing tray icon. Also, it's recently stopped playing through headphones again.

No obvious cause, obviously is rather inconvenient.

---

### Post by voluhar on 2013-06-20
I had same isuues tried multiple settings in /etc/modprobe.d/alsa-base but figured out that most efficent way to try out different setting is to shut down computer. Resets does not work for me and this was solution for me in two issues when headphones jack didnt work.

my current  /etc/modprobe.d/alsa-base is

options snd slots=snd-hda-intel
alias snd-card-0 snd-hda-intel
options snd-hda-intel model=asus position_fix=1



but i dont think that is relevant, since only shutdown for longer time worked.

---

