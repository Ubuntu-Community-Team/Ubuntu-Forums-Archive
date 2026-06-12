---
title: "how to make igpu work after nvidia's driver installed?"
date: 2011-06-14
forum: Multimedia Software
---

### Post by cc129 on 2011-06-14
Hi everbody, 
I wonder if I can get my igpu to work after the nvidia's driver is installed.
I built a new machine with z68 mobo which has a video output that allows you to use Sandy Bridge igpu, but after I installed the a dedicated graphic cards and the driver, the X just would not start when using igpu.

I wonder if there is a way to make my igpu to work, I want my graphic cards to be dedicated doing CUDA computation tasks, that is why I want this wired configuration.


Thanks

---

### Post by cc129 on 2011-06-14
Anybody??? Give some hints please!!!

---

### Post by Yellow Pasque on 2011-06-14
Most likely, the nvidia driver created an xorg.conf that specifies the nvidia driver, so...
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```
If it still won't start, post your /var/log/Xorg.0.log

---

### Post by cc129 on 2011-06-14
> **Temüjin said:**
> Most likely, the nvidia driver created an xorg.conf that specifies the nvidia driver, so...
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```
If it still won't start, post your /var/log/Xorg.0.log

Thanks a lot!!!
It seems I tried the same thing this morning, but this time it works!

Yet my graphic cards seems not give the right result result when running my cuda test program, anyhow thanks a lot, it is big step for me to make igpu back to work!!!

---

### Post by cc129 on 2011-06-14
I think right now, my newbie question is if I can make both (igpu and dedicated graphic card)work at the same time for my desktop.

---

