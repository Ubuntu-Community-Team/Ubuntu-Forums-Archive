---
title: "[SOLVED] NVIDIA Driver Problems"
date: 2007-09-04
forum: Multimedia &amp; Video
---

### Post by tman elite on 2007-09-04
Months ago I enabled "NVIDIA accelerated graphics driver" using the "Restricted Drivers Manager."  Now it shows it not in use, so I tried to enable it.  Everything went fine, but when I rebooted my computer, it said "Failed to start the x-server (your graphical interface.)  It is likely that it is not set up correctly."  A few times per minute this would pop up on the screen:

"bcm43xx: Error: Microcode "bcm43xx_microcode2.fw" not available or load failed."

Somewhere I saw "using /etc/X11/xorg.conf" so I opened it and read something like "If this file has been modified, use the command "sudo dpkg-reconfigure -phigh xserver-xorg" so I tried it.  I used NVIDIA as the driver and rebooted, but the exact same thing happened.  This time I used nv as the driver and the computer booted normally, but I still cannot enable the NVIDIA driver.

Anybody know what's wrong?

I have been using ubuntu for a while, but I still have a very limited understanding of how things work here, so please be patient.

---

### Post by w4ett on 2007-09-04
I'm assuming you upgraded the kernel this week as part of the normal updates.  When you do a kernel update, you will have to reinstall the Nvidia driver, since the driver modules are built to work with a particular kernel.  try this:

From the command line (or terminal) type:

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

This will run the installation script from the terminal....follow the instructions to remove the old attempted driver installation and then install the correct Nvidia proprietary driver.  You will have to do this proceedure every time you install an updated kernel.

Good Luck

---

### Post by steveneddy on 2007-09-04
Why not run the 9755 nvidia driver from the repos?

I like this driver, it works very well, and I don't have to recompile every time there is a new kernel update.

---

### Post by tman elite on 2007-09-04
> [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Install envy and then from the terminal type:

```
sudo envy -t
```

This will run the installation script from the terminal....follow the instructions to remove the old attempted driver installation and then install the correct Nvidia proprietary driver.  You will have to do this proceedure every time you install an updated kernel.

Good Luck

I successfully removed my old installation "attempt," but when I try to re-install, the download always stops when it is 29% done.  I'll keep trying it though, as it's probably a temporary problem.

**edit**: scratch that.  After 6 straight failed download attempts, it completed this time.

---

### Post by tman elite on 2007-09-04
Thank you w4ett, it worked perfectly.  My driver is now enabled.

---

### Post by w4ett on 2007-09-04
No problem.....Envy can be a little reluctant sometimes, but it comes through in the end....the old adage applies "If at first you don't succeed....."  :)

Good Luck

---

