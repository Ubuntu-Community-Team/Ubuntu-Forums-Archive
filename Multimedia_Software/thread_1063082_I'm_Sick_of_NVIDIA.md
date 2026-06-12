---
title: "I'm Sick of NVIDIA"
date: 2009-02-07
forum: Multimedia Software
---

### Post by vgrisham on 2009-02-07
I'm ready to dump my NVIDIA GeForce 7600ES. The driver issues are driving me nuts. 

Would someone please recommend a good video card that works well with Ubuntu?

---

### Post by overdrank on 2009-02-07
> **vgrisham said:**
> I'm ready to dump my NVIDIA GeForce 7600ES. The driver issues are driving me nuts. 

Would someone please recommend a good video card that works well with Ubuntu?

Hi and if I may ask, which driver are you using and what are the issues? I have just install the 7800 and no issues what so ever. :)

---

### Post by vgrisham on 2009-02-07
The 177 driver causes lines in AWN and is misdrawing window borders. I've just installed the 180.11 driver and it seems to be working for the time being. Until today, I would build the 180 beta driver and it would work okay until there was a kernel update at which point I would lose my graphical interface. 

I just want a stable video card that I don't have to mess with.

---

### Post by overdrank on 2009-02-07
I do remember seeing some threads about the window borders on Intrepid. I have not used Intrepid with nvidia since testing. 
I do have the same issue with kernel updates and I just reinstall the nvidia drivers and all is well.

---

### Post by oblidor on 2009-02-07
> **vgrisham said:**
> I'm ready to dump my NVIDIA GeForce 7600ES. The driver issues are driving me nuts. 

Would someone please recommend a good video card that works well with Ubuntu?

ATI HD4850 or HD4870

I have the latter and have no problems. Good chance there will be a nice open source driver soon too as ATI is releasing documentation.

---

### Post by vgrisham on 2009-02-07
Well, the problem that I've been running into after 180.16 is that all has not been well after reinstalling the driver. In fact, I just had to reinstall Ubuntu completely after I couldn't get it out of low graphics mode. Others are having this problem as well and there is more info on the NVIDIA Linux forum. 

What I found out after this latest failure is that by installing dropping into th TTY4 shell and installing by coding

>  apt-get install nvidia glx nvidia glx-180-dev nvidia-180-modaliases nvidia-180-kernel-source nvidia-glx-180

The restricted driver manager installs 180.11, which works well. I would imagine since I've installed this via APT that it might even survive a kernel upgrade. So maybe I should stop whining. I've just had to constantly babysit this video card since going to Intrepid and it's gotten old.

---

### Post by vgrisham on 2009-02-07
> **oblidor said:**
> ATI HD4850 or HD4870

I have the latter and have no problems. Good chance there will be a nice open source driver soon too as ATI is releasing documentation.

Thanks for the tip. I'll check it out.

---

