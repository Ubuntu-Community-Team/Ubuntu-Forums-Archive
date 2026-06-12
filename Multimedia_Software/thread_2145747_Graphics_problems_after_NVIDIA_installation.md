---
title: "Graphics problems after NVIDIA installation"
date: 2013-05-16
forum: Multimedia Software
---

### Post by ocli5568 on 2013-05-16
Hello,

Not sure whether this should be here or in another section but...

I tried to install the latest NVIDIA drivers lately and clearly didn't follow the instructions particularly well.

After installation, the grub screen turned blue (weird), the plymouth splashscreen was replaced with my original wallpaper and logging into Unity yielded a black screen. 

So I logged into the virtual console and got back to lightdm:```
sudo service lightdm start
``` I had previously installed the gnome environment and could log into a session running the gnome-shell, however the session looked like an outdated Ubuntu, with poor graphics and lots of glitches. I've tried all suggestions on the forum's I've seen so far, could anyone help me with this specific problem? What info do I need to print out to diagnose the problem etc.

So far, I've tried

```
sudo apt-get install nvidia-current
dpkg-reconfigure xserver-xorg
sudo apt-get remove --purge nvidia-current
```

then tried to download the .run from nvidia website and install
```
sudo service lightdm stop
sudo chmod a+x NVIDIA-Linux-x86_64-313.30.run
sudo sh NVIDIA-Linux-x86_64-313.30.run
```

I'm running Ubuntu 13.04 and switch between the Intel HD4000 and my current card:
```
ubuntu@ubuntu:~$ lspci | grep VGA
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Cape Verde PRO [Radeon HD 7750]

```

---

### Post by Yellow Pasque on 2013-05-16
So if you have Intel graphics, why are you trying to install Nvidia's graphics driver? The only thing I can think of is that you have hybrid/Optimus graphics, in which case, you should remove the nvidia driver and follow: [https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

Before you do that, though, make sure you have nvidia GPU as well:
```
lspci | grep VGA
```

---

### Post by ocli5568 on 2013-05-16
Ah sorry, I switch between the cards (forgot to add that). I've updated the post. I thought installing NVIDIA would enable compatability for both cards.

---

### Post by CatKiller on 2013-05-17
That's not an Nvidia card. The Nvidia driver won't work on an Ati card any better than on the Intel graphics.

---

