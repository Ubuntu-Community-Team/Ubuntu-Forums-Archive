---
title: "nVIDIA and dual displays"
date: 2007-08-24
forum: Multimedia &amp; Video
---

### Post by davidhn on 2007-08-24
I have just installed ubuntu, dual-booting with XP which I had been running previously. I was very impressed with the ease with which ubuntu installed, recognizing my three printers and scanner without any difficulty (yes, a scanner installed without problems!!!!). However, having previously being used to using two displays with the latest nVIDIA software in XP, I have been disappointed that I have not been able to do the same in ubuntu.

I have downloaded the shell script  "NVIDIA-Linux-x86-100.14.11-pkg1.run"  from the nVIDIA site and tried to run it in accordance with their instructions ie Type "sh NVIDIA-Linux-x86-100.14.11-pkg1.run" to install the driver. This produces the following:

root@david-desktop:~# sudo sh NVIDIA-Linux-x86-100.14.11-pkg1.run
sh: Can't open NVIDIA-Linux-x86-100.14.11-pkg1.run


What am I doing wrong. I think it self-evident that I have little knowledge of Linux.

---

### Post by brett_baudin on 2007-08-24
Try this link for a how to on NVidia.

[http://www.cs.cornell.edu/~djm/ubuntu/#nvidia-driver](http://www.cs.cornell.edu/~djm/ubuntu/#nvidia-driver)

Brett

---

### Post by w4ett on 2007-08-24
From the command line type:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

This will give you the interface to modify the driver and resolutions. Controls are UP and DOWN cursor keys move the cursor and scrolls through available options, the space selects options, and <enter> confirms selections.

Select "nv" as the driver and press <enter>, then at the next screen you can enable any addttional resolutions that you want to use.....then use the cursor keys to highlight {OK} and <spacebar> to select the resolutions and press <enter> to save the selections as prompted, then type:

```
startx
```

This will get you to a GUI desktop. then go to:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Install envy and then from the terminal type:

```
sudo envy -t
```

This will run the installation script from the terminal....follow the instructions to remove the old attempted driver installation and then install the correct Nvidia proprietary driver.

Good Luck

---

### Post by davidhn on 2007-08-26
Thanks to Brett and w4ett.

Following these ideas I have installed 1.0-9755, but this does not give me the option for dual displays which I had hoped to get from 100.14.11

davidhn

---

### Post by davidhn on 2007-08-26
Having paid closer attention to the nVIDIA setup screen I have managed to get dual displays. Thanks again for your help.

HOWEVER

I cannot now open the  terminal  - Applications/Accesories/Terminal produces the 'timer' but no terminal

Davidhn

---

### Post by _simon_ on 2007-08-26
Can you open terminal this way?

ALT F2

gnome-terminal

Sorry I didn't see this thread sooner, I run dual screens with an nvidia card.

---

### Post by davidhn on 2007-08-26
Yes, tries that - no joy

Davidhn

---

### Post by _simon_ on 2007-08-26
Have you tried reinstalling it?

If you pop into synaptic and search for gnome-terminal, right click and mark for reinstallation, may as well also reinstall the  gnome-terminal-data as well.

Hopefully that will fix it.

---

### Post by ircmaxell on 2007-08-26
I'm actually having the same problem.  I tried re-installing the terminal, and no joy.  It still doesn't load (it opens the "Loading Terminal" bar, but then that disappears and nothing happens...

---

### Post by davidhn on 2007-08-27
Thanks for the suggestion. I reinstalled gnome-terminal and gnome-terminal-data as suggested but without success.

davidhn

---

