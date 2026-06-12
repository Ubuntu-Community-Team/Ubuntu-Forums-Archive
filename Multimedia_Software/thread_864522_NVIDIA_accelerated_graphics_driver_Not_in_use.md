---
title: "NVIDIA accelerated graphics driver: Not in use"
date: 2008-07-19
forum: Multimedia Software
---

### Post by Nightmist on 2008-07-19
Hello,

I have recently installed a new version of Ubuntu. When I started Hardware Drivers and found my NVIDIA device, it was listed as Not in use. I tried to check the enabled box, but after a restart it was still Not in use.

Useful stuff to know:

Ubuntu 8.04 (Kubuntu) KDE4, 32 bit
GeForce 8800 GT
Conan fan

---

### Post by Nightmist on 2008-07-20
I tried clicking the enable box again after updating my drivers, and X wouldn't start. I re-installed the latest drivers (used envy) and it worked again, but the NVIDIA driver was not in use. So I guess they mean that the default driver is not in use? Is that what it means?

---

### Post by Duranxl on 2008-07-20
Try deleting xorg.conf and then running sudo nvidia-xconfig

---

### Post by Nightmist on 2008-07-20
> **Duranxl said:**
> Try deleting xorg.conf and then running sudo nvidia-xconfig

command not found.

---

### Post by Duranxl on 2008-07-20
> **Nightmist said:**
> command not found.

sudo apt-get install nvidia-settings
now try again

---

### Post by Nightmist on 2008-07-20
> **Duranxl said:**
> sudo apt-get install nvidia-settings
now try again

The installation worked, but the nvidia-xconfig command still doesn't work.

---

### Post by Duranxl on 2008-07-20
> **Nightmist said:**
> The installation worked, but the nvidia-xconfig command still doesn't work.

It worked for me and i used EnvyNG too
You are running it via terminal right?
Maybe you need to install it separately via apt-get? (i never had to do this)

---

### Post by Nightmist on 2008-07-20
> **Duranxl said:**
> It worked for me and i used EnvyNG too
You are running it via terminal right?
Maybe you need to install it separately via apt-get? (i never had to do this)

I have removed what envy installed as I got a black screen in KDE4. I am running my commands from a failsafe terminal now. I'll try installing the drivers from envy, but now that KDE is completely black (I can log in with a GUI, nothing more) I think have bigger problems. No matter what old xorg.conf I use, nothing changes. Still black screen.

Any idea what's wrong? Maybe I should make a new thread since this is somewhat a new problem.

---

### Post by Nightmist on 2008-07-20
At least nvidia-config worked after using envy again, and I got a new xorg.conf.

KDE is still black as a bat, though... Seems to be unrelated to what xorg.conf file I use and what nvidia driver I use. I have uninstalled any driver, still black screen in KDE. I have used an old xorg.conf file from when I had no problems, still black screen. And I have installed the latest nvidia driver, and still black screen in KDE...

I can see my mouse pointer, though :P

---

