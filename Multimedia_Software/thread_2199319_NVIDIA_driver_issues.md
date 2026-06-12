---
title: "NVIDIA driver issues"
date: 2014-01-13
forum: Multimedia Software
---

### Post by adel.ejjeh on 2014-01-13
Hello all, I have a fresh installation of Ubuntu 13.10 on my desktop with an ASUS Geforce GTX760 Graphics Card. I have two monitors connected, one using an HDMI cable, and the other one using a VGA cable and a DVI/VGA adapter (Because the graphics card doesn't have a VGA output). When I first booted up the system after installing 13.10, both monitors were working, however the VGA monitor wasn't being detected correctly by the system (I think due to the VGA/DVI adapter) and therefore was stuck at a low 1024x768 resolution. I thought that installing the NVIDIA drivers would solve this issue, so after searching online I found two ways to install the latest nvidia driver on Ubuntu 13.10, but both gave me problems:

1. The first way I tried was downloading the driver from the nvidia website, going to the tty1 console, stoping the lightdm service, and running the installer as root. After accepting the license agreement the installer gave me the following error: "The distribution-provided pre-install script failed! Continue installation anyway?" If I chose to continue installation anyway the installer exits with an error before completing the installation.

2. The second way I tried was using the xorg/edgers ppa. I tired both the nvidia-331 and the nvidia-current packages, and in both cases when the package finishes installation and I reboot, Ubuntu boots into low-graphics mode.

I would appreciate any help I can get from everyone here to solve the issue!

---

### Post by cj2008 on 2014-01-13
Having the same problem myself with 13.10 and a NVIDIA GeForce 200 card with dual monitors.

I've also tried installing nvidia-331 and nvidia-current package from xorg/edgers ppa but it doesn't seem to work; I get a "failed to load NVIDIA kernel module" error in my Xorg.0.log file. 

Other people suggest purging the nvidia modules completely and trying to use the opensource nouveau instead using the following commands. This has helped some people, so give it a try. (It didn't help me unfortunately).

```
sudo apt-get remove --purge nvidia-*
sudo rm /etc/X11/xorg.conf
echo 'nouveau' | sudo tee -a /etc/modules
```

Perhaps post your Xorg.0.log file (in /var/log) as it may contain some clues.

---

### Post by adel.ejjeh on 2014-01-13
Thanks for the tip cj, but I already did a clean re-install of ubuntu. I will keep on working with the stock VGA driver until I figure out what's the problem and how I get the NVIDIA driver to work. I am also considering going back to a previous release of ubuntu (12.04 or 12.10) because ever since I started using raring and saucy I had a feeling that they were unstable :S I'm going to wait and see if I get more comments first. By the way, any idea why the PC isn't correctly identifying the VGA monitor while connected to a DVI/VGA adapter? Is this always the case when using a DVI/VGA adapter?

---

### Post by Bucky Ball on 2014-01-13
Just an off-topic tip. If you do decide to downgrade with a clean install go for 12.04 LTS rather than 12.10. 12.04 is directly upgradeable to 14.04 LTS when it comes out in April. 12.10 is not. That would require a clean install to upgrade (LTS can always upgrade LTS>LTS leapfrogging the interim releases in between).

---

### Post by adel.ejjeh on 2014-01-13
> **Bucky Ball said:**
> Just an off-topic tip. If you do decide to downgrade with a clean install go for 12.04 LTS rather than 12.10. 12.04 is directly upgradeable to 14.04 LTS when it comes out in April. 12.10 is not. That would require a clean install to upgrade (LTS can always upgrade LTS>LTS leapfrogging the interim releases in between).

Thanks for the tip! :D I was just thinking about that before reading your post :P By the way, are there any disadvantages of going back to 12.04?

And just so we don't deviate from the topic, I'm also still looking for tips concerning the drivers and if anyone has any clue why I might be facing these problems.

---

### Post by Bucky Ball on 2014-01-13
> **adel.ejjeh said:**
>  By the way, are there any disadvantages of going back to 12.04?



Depends how you look at it, but generally speaking, no. 12.04 LTS is the most stable of the current releases and an LTS release with five years support. If it's 12.04 vs 12.10 then a no-brainer; 12.04 LTS it is. ;)

---

### Post by adel.ejjeh on 2014-01-13
> **Bucky Ball said:**
> If it's 12.04 vs 12.10 then a no-brainer; 12.04 LTS it is. ;)

lol of course! :p I meant in comparison to 13.10? Would there be any disadvantage of downgrading?

---

### Post by Bucky Ball on 2014-01-13
No. Not in my opinion (I personally always use LTS as my main install as my machine CAN'T break ... has to be stable and reliable). 13.10 can be a bit flaky, although, naturally, it has more recent versions of apps. When 14.04 LTS arrives in April all this will be neither here nor there, of course. ;)

---

### Post by adel.ejjeh on 2014-01-13
OK, so it's decided then! I'm gona install 12.10 and once I do that I'll try to get the Nvidia drivers working. If they work normally I'll close this thread if not I'll post an update :p

---

### Post by Bucky Ball on 2014-01-13
12.04 LTS you mean? 12.10 puts you in no-person's-land upgrade-wise ... :-k

> **adel.ejjeh said:**
> ... I'll try to get the Nvidia drivers working. If they work normally I'll close this thread if not I'll post an update :p

Good plan.

---

### Post by adel.ejjeh on 2014-01-13
> **Bucky Ball said:**
> 12.04 LTS you mean?

Yes, my bad! Lol :p

---

