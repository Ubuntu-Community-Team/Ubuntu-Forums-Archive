---
title: "2407wfp-hc showing wrong native resolution in NVIDIA-settings"
date: 2008-01-03
forum: Multimedia &amp; Video
---

### Post by Bogus83 on 2008-01-03
Hi all,

I've been trying everything I can think of, and every suggestion I can find, to get my Dell 24" 2407WFP-HC to display 1920x1200.  I've messed with Modelines, installed the latest NVIDIA X driver, etc, no dice.  One odd thing that I've found is that in the NVIDIA-settings config app, it shows the native resolution, and best fit resolution, as 1600x1200.  That seems kind of odd to me, since I know for a fact (and half the reason I bought it) the screen will display 1920x1200, and that's it's native resolution.  I've gotten it to work fine in XP, but Ubuntu (7.10) seems to think otherwise.

Any ideas why this might be?

BTW, I'm using a GeForce FX 5200 Ultra, and I'd be glad to post my Xorg or anything else for poking at.  Thanks!

-Bogus

---

### Post by Bogus83 on 2008-01-03
[IMG]http://i28.photobucket.com/albums/c220/bogus1983/wrongnative.png[/IMG]

---

### Post by Skerit on 2008-05-12
I have the exact same problem with my monitor, the LG 204WT
But mine's worse, it's saying 640x480 is the maximum resolution - that's a very useless resolution!

---

### Post by Bogus83 on 2008-05-12
Interestingly enough I found that this problem was non-existent in Hardy Heron.  It "just worked out of the box".  I can't explain it, but I'm not complaining either.

One thing you might want to try in your xorg.conf file is the addition of "NoMaxPClCheck" and adding the correct Mode to your modeline.  Forgive me if my terminology is off, I'm still a novice myself.  I can post a sample of my xorg.conf if that helps more.  Essentially what happens is the display won't go higher than what it believes the monitor's optimal/native resolution to be, because to do so could potentially harm the monitor.  For this reason, take care when adding that value- slip and add an extra zero and who knows how the monitor will react.  But if you know your monitor can support a higher resolution than it thinks (like in my case, I knew 100% that my monitor could do 1920x1200), the flag says "ignore the maximum pixel check, and hope nothing explodes".

Of course YMMV, depending on your hardware, drivers, OS version, etc.

---

