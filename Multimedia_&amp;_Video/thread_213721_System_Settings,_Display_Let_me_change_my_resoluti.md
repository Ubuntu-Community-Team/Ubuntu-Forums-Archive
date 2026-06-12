---
title: "System Settings, Display: Let me change my resolution!!"
date: 2006-07-11
forum: Multimedia &amp; Video
---

### Post by sadscientist on 2006-07-11
Yar!!

my monitor and graphics card seem to have been detected correctly..  (monitor: viewSonic a90f+, gfx card: ati radeon 9800 pro)

however, i'm unable to change my resolution or refresh rate. (60 Hz really "Hz" my eyes!)

Basically, I click administrator mode.. reduce the screen size slider to 1280x1024 and select 75 Hz as the refresh rate.. then it says "keep these settings?" (while showing no difference in size) and I say "yes, keep those settings." and then.. nothing happens.  Everything still looks small and blinky, yet system settings - display is reporting a reduced resolution and higher display rate.

The next time I open display - system settings, however, it stops lying and tells me, again, that it's displaying at 60 Hz and 1792 x 1344.  :|

Please help, my watering eyes will thank ye.

---

### Post by jadedknight on 2006-07-11
Yes, I would really like to change my resolution as well.

---

### Post by sadscientist on 2006-07-17
Just to conclude, I should say:

I fixed it by running 
$sudo dpkg-reconfigure xserver-xorg
and, at the resolutions screen, deselecting (with the spacebar :P) all options except the one I wanted.

---

### Post by eagletip on 2007-10-14
Dear sadscientist

Thank you foryour wisdom.
By running your command, I was abletofix my res problem.
I applaud you

Regards

Larry

---

