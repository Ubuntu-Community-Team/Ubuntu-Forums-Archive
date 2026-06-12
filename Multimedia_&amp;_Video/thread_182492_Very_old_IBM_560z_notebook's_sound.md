---
title: "Very old IBM 560z notebook's sound"
date: 2006-05-26
forum: Multimedia &amp; Video
---

### Post by z.siposs on 2006-05-26
Dear All,

I have installed an Ubuntu 5.10 on the notebook in title. It has an integrated ISA cs4237b soundcard (or something similar). In former days it was working under other Linux distros with kernel 2.4, using kernel module cs4232.

In Ubuntu 5.10 I have found modules snd-cs423x and snd-cs423x-lib. They can be loaded, but don't provide sound at all.

Does anyone know some tricks or I must go back to kernel 2.4?
If must change kernel, is there a way to do it with Ubuntu's tools (apt-get?) or must build it from sources?

Thank you in advance for help!

Best regards, Zoltan

---

### Post by z.siposs on 2006-05-27
Resolved!

After a little investigation I've got the solution. The rootcause was the notebook itself! Some BIOS-settings got to be stupid. After resetting BIOS (by taking out cmos-battery), the kernel module loaded and working well.

I just wrote this to give a resolution base if anyone run into the same problem.

---

### Post by Sef on 2006-05-27
Thank you for providing how you resolved your problem.

---

