---
title: "Nvidia  7300 problems on Gutsy"
date: 2007-10-19
forum: Multimedia &amp; Video
---

### Post by Phantom784 on 2007-10-19
I am having two different problems with my Nvidia 7300 on Gutsy.  I am using the driver as provided by Ubuntu's "restricted drivers" manager.  I used the restriced driver on the same machine under Feisty, but I never encountered any problems.  I should mention I'm runing dual monitor with Nvidia's TwinView, although this is working fine.

First of all, the loading image when I'm booting Gutsy doesn't display properly.  My LCD monitor mearly states something about an "incompatible signal", and my CRT distorts the image.

The second problem is that occasionally, for no apparent reason, my LCD will go black for a few seconds.  Nothing happens on the CRT plugged in at the same time.

Thanks for any help in advanced.

---

### Post by Phantom784 on 2007-10-24
anyone?

---

### Post by mike_b on 2007-10-24
Are you using nvidia-glx or nvidia-glx-new?  I had issues with the nvidia-glx-new driver and the lrm-video script does not pass modules option configurations to the modprobe command as the normal nvidia driver does.

---

### Post by Libertine on 2007-10-24
I have the same card, but I'm not running a dual-screen setup. I also had problems until I used [Envy](http://albertomilone.com/nvidia_scripts1.html)...now everything works perfectly :D

---

### Post by wolfen69 on 2007-10-24
uninstalling the new driver and replacing with nvidia-glx should work.

---

### Post by Phantom784 on 2007-10-25
I'm not sure which drive I have, just wichever one the restricted driver manager installs.  Envy looks like the simplest solution, but will it still work even though I've already installed the driver manager version?

---

### Post by sanddgroper on 2007-10-26
If you are using the restricted driver installed by 7.10
then it should be nvidia-glx-new.A check of synaptic should
tell you what driver is installed.

Cheers
Sandy

---

### Post by Phantom784 on 2007-11-01
I installed the nvidia driver with envy instead (on a fresh install), but I'm still having both the problems with the LCD randomly going black, and the booting screen not showing up correctly.

---

