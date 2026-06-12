---
title: "XGL or AIGLX works on S3 Savage?"
date: 2006-05-31
forum: Multimedia &amp; Video
---

### Post by e_liming on 2006-05-31
Hi all,

I have a IBM T23 notebook and it comes with an S3 Savage video card. I use the Xorg 'savage' driver. 

Everything is acceptable when works the default way. However, if I turn the Composite extension on, the GUI becomes dramatically slow.

So I wonder, any chance for this card to run XGL or AIGLX? Is it going to make it faster becoz of the OpenGL acceleration?

BTW, I guess it has no other drivers except the one comes Xorg, am I correct?

TIA

---

### Post by kronepils on 2006-05-31
AIGLX is your only hope, AFIAK.

But if X is slow with composite on, it doesn't look good... Do your have direct rendering??
> glxinfo | grep direct

Have you tried to follow the aiglx howto? You can easily find it in this forum.


Good luck!

---

### Post by e_liming on 2006-05-31
I think I'd better wait for Xorg 7.1... just don't know whether dapper will upgrade to 7.1 release.. hmm

---

### Post by nalthien on 2006-05-31
It might find its way into backports; but 7.1 will not be part of Dapper.

---

### Post by e_liming on 2006-05-31
Is backports repo only available when dapper officially announced? 

I only hope 7.1 comes with a better S3 Savage driver. At the moment it's only usable @16bit color in Xfce when Composite is enabled. The difference in 24bit and 16bit mode is about 100%.

BTW, can AIGLX be used together with Xfce?

---

