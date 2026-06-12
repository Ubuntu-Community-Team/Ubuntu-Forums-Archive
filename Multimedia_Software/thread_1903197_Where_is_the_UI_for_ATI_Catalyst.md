---
title: "Where is the UI for ATI Catalyst?"
date: 2012-01-01
forum: Multimedia Software
---

### Post by PeterTaps on 2012-01-01
Folks,

I have installed ATI catalyst drivers for my AMD A75 CPU that has integrated Radeon 6550D GPU.

apt-get install fglrx fglrx-updates fglrx-updates fglrx-amdcccle-updates

My audio and video is working.

My machine is set up for dual boot - Windows 7 and Ubuntu 11.10.

On Windows 7, ATI Catalyst has a nice UI for changing audio/video parameters. 

Is there an equivalent UI under Ubuntu? Where can I get it from?

Thank you in advance for your help.

Regards,
Peter

---

### Post by DS McGuire on 2012-01-01
I got the ATI Catalyst software when I installed the driver for my HD 5450 graphics card. Use additional drivers and make sure you have a ATI driver installed.

---

### Post by MoreOrLess on 2012-01-02
You can run from the terminal:
```
amdcccle
```
Use gksu (or kdesudo or whatever) before the command if you need administrative privs.

---

### Post by collisionystm on 2012-01-02
> **PeterTaps said:**
> Folks,

I have installed ATI catalyst drivers for my AMD A75 CPU that has integrated Radeon 6550D GPU.

apt-get install fglrx fglrx-updates fglrx-updates fglrx-amdcccle-updates

My audio and video is working.

My machine is set up for dual boot - Windows 7 and Ubuntu 11.10.

On Windows 7, ATI Catalyst has a nice UI for changing audio/video parameters. 

Is there an equivalent UI under Ubuntu? Where can I get it from?

Thank you in advance for your help.

Regards,
Peter
apt-get install fglrx fglrx-updates fglrx-updates fglrx-amdcccle-updates

This entire line can me simplified to 

sudo apt-get install fglrx-updates

---

