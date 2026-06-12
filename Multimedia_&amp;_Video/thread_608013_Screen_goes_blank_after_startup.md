---
title: "Screen goes blank after startup"
date: 2007-11-09
forum: Multimedia &amp; Video
---

### Post by AndreGerber on 2007-11-09
Hello,

I have been running Gusty for the last few weeks, and all of a sudden - after I restarted - I cannot see a thing after the loading screen.

After the Ubuntu loading screen, the screen goes to terminal mode and the computer keeps trying to open the GUI. After a while it just gives up, it seems, and then just...nothing.

Everything works fine when I select the "Generic" option from the Grub menu, but the standard one doesn't work.

I have a GeForce FX5200 graphics card and Ubuntu installed all my drivers automatically.

I also want to know, what is the difference between the "Generic" option and the "Standard" option.

Thank you so much!

---

### Post by carlinuxlearner on 2007-11-09
Did you do an update right before this happened?

C@RL

---

### Post by AndreGerber on 2007-11-10
Yes, I did.

(By the way, thank you for the reply!)

---

### Post by carlinuxlearner on 2007-11-10
Well when you do an update and it updates your kernel, you have to reinstall your Nvidia driver so the new kernel has a module for it. 
Boot up into the "Standard" recovery mode kernel, and (assuming you have a internet connection) execute this "sudo apt-get install nvidia-glx-new" it should install the driver for you, if not just post here.

C@RL

---

### Post by satx on 2007-11-10
All,

Finally solved my problems w/Ubuntu 7.10 and my NVidia GeForce 7300 LE by installing Envy. After struggling with xorg.conf, correct NVidia driver selection, and using baseball bat to keep my graphics setting right, I downloaded this package. It automatically sensed the correct video card, installed all the right libraries, and correctly configured my card to provide 1280 x 1024 X 32 at 56Hz.

Go to:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

SATX

---

### Post by AndreGerber on 2007-11-11
> **carlinuxlearner said:**
> Well when you do an update and it updates your kernel, you have to reinstall your Nvidia driver so the new kernel has a module for it. 
Boot up into the "Standard" recovery mode kernel, and (assuming you have a internet connection) execute this "sudo apt-get install nvidia-glx-new" it should install the driver for you, if not just post here.

C@RL

Unfortunately that didn't work. It moaned at me and said that it was already installed, so I removed is with "sudo apt-get remove nvidia-glx-new", and then after it was done, I installed it again to no avail.

---

### Post by carlinuxlearner on 2007-11-11
Well do as "satx" said install "Envy" Heres a how to I wrote.

HOW TO: install your Nvidia driver in Ubuntu 7.10

1.1 
Go to your (System>>Administration>>Software Sources) make sure you have all your repositories enabled. (Check mark them all)

Download "Envy" to your Desktop (to make thing easy) [http://albertomilone.com/ubuntu/nvidia/scripts/legacy/envy_0.9.8-0ubuntu10_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/legacy/envy_0.9.8-0ubuntu10_all.deb)
(if this link does not work, just visit this web site and download the latest version [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html) )

1.2
Double click on the file you just downloaded and tell it to install

1.3
If all those steps went well then Envy should be installed and you should be able to find it on your "Applications" menu under "System tools", just run it and you should be able to install your driver all by your self very easily.

C@RL

---

### Post by AndreGerber on 2007-11-12
> **carlinuxlearner said:**
> Well do as "satx" said install "Envy" Heres a how to I wrote.

HOW TO: install your Nvidia driver in Ubuntu 7.10

1.1 
Go to your (System>>Administration>>Software Sources) make sure you have all your repositories enabled. (Check mark them all)

Download "Envy" to your Desktop (to make thing easy) [http://albertomilone.com/ubuntu/nvidia/scripts/legacy/envy_0.9.8-0ubuntu10_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/legacy/envy_0.9.8-0ubuntu10_all.deb)
(if this link does not work, just visit this web site and download the latest version [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html) )

1.2
Double click on the file you just downloaded and tell it to install

1.3
If all those steps went well then Envy should be installed and you should be able to find it on your "Applications" menu under "System tools", just run it and you should be able to install your driver all by your self very easily.

C@RL

Unfortunately that didn't work. I still can't boot into standard mode. I let it install the Nvidia driver automatically, but I'm afraid I still get the Black Screen Of Death. ;)

---

### Post by dabl on 2007-11-12
On the "Black Screen of Death", do Alt-F1 and/or Ctrl-Alt-F1 and you should get a CLI terminal.  Log in and then issue ```
startx 
```and you'll get an error message that should be informative. :)

---

### Post by carlinuxlearner on 2007-11-12
Did you install the driver WHILE YOU WERE IN "standard" mode??????
Please boot up into "Generic" mode and execute this in a terminal 
"sudo nano -w /etc/X11/xorg.conf" 
find the "Device" section 
and the part that says  "Driver "nvidia"" 
change "nvidia" to "nv"
press CTRL+X to save and exit.
restart your computer into "standard" mode and see if you get a GUI (Graphic User Interface) 
then please open up "Envy" and reinstall your driver.

C@RL

---

### Post by AndreGerber on 2007-11-13
Thank you so much for all your help. I really appreciate it. Everything works perfectly now. You guys  are really very helpful.:KS

---

### Post by carlinuxlearner on 2007-11-14
Great!

C@RL

---

### Post by satx on 2007-11-29
Hooah! Glad to have been of assistance. Went through same pain as you did until I used Envy. Now I can do all the cool CompizFusion features. Life is good.

SATX

---

