---
title: "Installing Latest Nividia drivers"
date: 2009-07-24
forum: Multimedia Software
---

### Post by Amof on 2009-07-24
Pretty simply asked, how do I do it? I see Nvidia releasing all these awesome drivers yet I don't know how to install them. These are not the drivers from the repository they are from Nvidia's FTP.

Anyone?

---

### Post by HappyFeet on 2009-07-24
Here's an example:
First I download the driver, [NVIDIA-Linux-x86-185.18.14-pkg1.run]("http://us.download.nvidia.com/XFree86/Linux-x86/185.18.14/NVIDIA-Linux-x86-185.18.14-pkg1.run")
and put it in my home folder. Open a terminal and do:
```
sh NVIDIA-Linux-x86-185.18.14-pkg1.run 
```
Then just follow the prompts. Easy enough?

---

### Post by Amof on 2009-07-30
I have tried this, and most of the time I consider myself lucky if I can recover my system afterwards. They NEVER install correctly.

---

### Post by Arup on 2009-07-30
Please take the apt steps, remove older drivers, do a sudo apt-get --purge remove nvidia* do a sudo apt-get --purge remove linux restricted modules 

do a sudo apt-get install build-essentials then log out by doing ctrl+alt+F1 login and then do a sudo /etc/init.d/gdm stop after that do a sh NVIDIAxxxxxxxx and make sure the driver is in your home folder.

Follow the prompts and hit yes for all, after that do a sudo reboot and you are all set.

---

### Post by rainwalker on 2009-07-31
[http://ubuntuforums.org/showthread.php?t=990978](http://ubuntuforums.org/showthread.php?t=990978) is what I follow
185.18.14 is what works for me, 185.18.29 kills my system at the login screen (just letting you know, it may work perfectly for you)

---

### Post by Amof on 2009-08-01
Well that was simple enough. I guess my mistake was not uninstalling the old drivers first.

---

### Post by Raffles10 on 2009-08-01
Is there any noticeable performance enhancement in using the nvidia 185.**.** drivers compared to the 180.**.** propriety drivers enabled by Ubuntu ?

I've always used the default driver and get very good performance especially with games like NWN. Any reason to change ?

---

### Post by Amof on 2009-08-01
Thus far I notice better framerates and that nasty vsync bug seems to be resolved. Nvidia is on the front of linux display drivers right now so it's not a bad idea to check out their updates. It'd be nice if someone had a repo for all the nvidia display drivers but this is simple enough.

---

### Post by dano1 on 2009-08-01
> **Amof said:**
> Thus far I notice better framerates and that nasty vsync bug seems to be resolved. Nvidia is on the front of linux display drivers right now so it's not a bad idea to check out their updates. It'd be nice if someone had a repo for all the nvidia display drivers but this is simple enough.

jya's repo has many of them:

[http://www.avenard.org/media/Home.html](http://www.avenard.org/media/Home.html)

---

