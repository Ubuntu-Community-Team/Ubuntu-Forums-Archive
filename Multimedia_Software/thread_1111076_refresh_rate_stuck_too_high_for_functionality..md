---
title: "refresh rate stuck too high for functionality."
date: 2009-03-30
forum: Multimedia Software
---

### Post by veganbikepunk on 2009-03-30
I was messing around trying to get dual screens to work (there are many lines running up and down on my tv) and I set my refresh rate to something really high, like 115. The screen went to black. I restarted and the same thing happened. I went into the recovery boot and had x fix itself. It then was able to boot, but with some other driver besides FGLRX. I changed the xorg to fglrx and restarted X, well the screen went black presumably because the refresh rate was too high. I'm stuck.

---

### Post by Linoobius on 2009-03-30
Hello,

I've got a post of my own seeking help but saw yours, I'm no guru but have you tried

sudo aticonfig --initial -f

to reset the ati driver and regenerate a new xorg.conf

Linoobius

---

### Post by veganbikepunk on 2009-03-30
Guru or not, you fixed my problem.  Thank you so much!

---

### Post by Linoobius on 2009-03-30
veganbikepunk

I'm just glad to be able to give something back to the community, glad it worked.

Linoobius

---

