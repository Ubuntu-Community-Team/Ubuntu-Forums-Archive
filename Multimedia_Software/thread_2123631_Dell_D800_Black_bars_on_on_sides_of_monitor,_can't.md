---
title: "Dell D800: Black bars on on sides of monitor, can't get full screen"
date: 2013-03-08
forum: Multimedia Software
---

### Post by zx2max on 2013-03-08
I am running Ubuntu 12.04 on an old Dell D800 laptop and it doesn't fill my whole screen. I have black bars on both sides and I have not been able to figure out how to make is full screen. While I have been using Ubuntu for a couple years, I still consider my self an amatuer. I did not have this problem when I was running an earlier version of Ubuntu. Any help would be great. Thanks.

---

### Post by gifford on 2013-03-08
Have you tried setting a new screen resolution in system settings, displays?

---

### Post by zx2max on 2013-03-08
Yes, it is currently set to 1024x768 (4.3) and the only other option makes the screen even smaller.

---

### Post by gifford on 2013-03-08
What type of video card is installed? Are you running proprietary drivers for it?

---

### Post by zx2max on 2013-03-08
It's a Nvidia GeForce4 Ti 4200 Go AGP 8x. How do I tell if I am running any proprietary drivers?

---

### Post by gifford on 2013-03-08
Go to system settings and then to additional drivers, click on and it will search and let you know what you are using and what is available. Or, open a terminal and type fglrxinfo to see if a proprietary driver is installed. This will also work to show what is now being used sudo lshw  -c video

---

### Post by zx2max on 2013-03-16
The additional drivers I have are nvidia_96 (activated but not being used), NVIDIA binary Xorg driver kernel module and VDPAU library (not activated), nvidia_current (activated but not being used), and Broadcom STA wireless driver. 

When I run lshw -c video I get:
*-display UNCLAIMED     
       description: VGA compatible controller
       product: NV28 [GeForce4 Ti 4200 Go AGP 8x]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 vga_controller bus_master vga_palette cap_list
       configuration: latency=32 maxlatency=1 mingnt=5
       resources: memory:fc000000-fcffffff memory:f0000000-f3ffffff memory:fd000000-fd01ffff

---

### Post by zx2max on 2013-03-19
Should I try to use one the these proprietary drivers that are activated but not currently being used? If so, how do I make that change? Thanks.

---

### Post by zx2max on 2013-03-20
gifford or anyone else have any ideas how I correct my display so it's full screen or how I change my video card driver if that's the problem?

---

### Post by zx2max on 2013-03-22
So is there anyone on this forum that can offer some help or am I just wasting my time and should go back to Winblows?

---

### Post by ManamiVixen on 2013-03-23
Ubuntu 12.04 will not run on that laptop. The X.Org and kernel are too new for the correct Nvidia driver to work."activated but not currently being used" is the result of that. You'll have to use an older version of Ubuntu. 11.10 or older will work.

---

### Post by zx2max on 2013-03-23
Thanks ManamiVixen. I was hoping I wouldn't have to do that but oh well time to downgrade to 11.10. I appreciate your help.

---

