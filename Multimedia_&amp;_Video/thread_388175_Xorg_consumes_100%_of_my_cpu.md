---
title: "Xorg consumes 100% of my cpu"
date: 2007-03-19
forum: Multimedia &amp; Video
---

### Post by WesleyWex on 2007-03-19
I'm using Xubuntu at work, and somedays when I get to the office I see the CPU at 100%, top shows me Xorg is the process using most of it (98%), this is odd because nobody was using the computer (today it was idle for 3 days).

This only happens when it's idle for a long time, and goes away if I kill X.

I don't know if this matters, but I use the 'blank screen' screen saver, and it was active locking the screen.

Any ideas on how I can trace this problem to solve it?

---

### Post by somafm on 2007-03-20
Hello,

I had the cpu usage problem with Xorg a while back. It would happen randomly and I would have to restart, but then it would just come back later.

I fixed it by installing [**_Envy_**]("http://albertomilone.com/index.html") as recommended by another thread. Envy will basically detect your video card, install the latest/correct drivers, and configure your xorg.conf file properly.

That seemed to fix the problem considering I have not seen the high cpu usage again and the machine has been up for about a week now, and acting good.

I have been going around looking for people with a similar problem posting this info, so I hope it helps you like it helped me. Best of luck!

---

### Post by radioraheem on 2007-03-23
See, that's weird because I never had the same problem listed here until after I installed the driver with Envy.

I'm also using Beryl.  I tried switching the window manager back to xfce when away from the workstation for a long time but even that didn't help.

---

