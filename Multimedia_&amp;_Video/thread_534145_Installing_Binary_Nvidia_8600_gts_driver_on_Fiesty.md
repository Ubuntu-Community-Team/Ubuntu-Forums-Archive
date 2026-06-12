---
title: "Installing Binary Nvidia 8600 gts driver on Fiesty"
date: 2007-08-24
forum: Multimedia &amp; Video
---

### Post by rluk23 on 2007-08-24
Hello, I am very new to linux and new to this forum, so if my vocabulary or linux lingo isn't so sharp, please bare with me.  So far I have followed the instructions from this post on the forum.

[http://ubuntuforums.org/showthread.php?t=514161](http://ubuntuforums.org/showthread.php?t=514161)...

all the way until I run the nvidia installer.   When I get into the installer, I get a message saying,

"No precompiled kernel interface was found to match your kernel; would you like the installer to attempt to download a kernel interface for your kernel from the Nvidia site?"  And then if I choose yes it still won't find the right kernel.  After that message I get "You do not appear to have libc header files installed on your system.  Please install your distro's libc development package"

Can someone please help me out?  I am an complete noob and sorry if all this is very trival to you.  I have been stuggling with this graphics card for weeks now.  Any help would be greatly appreciated.  Thanks

---

### Post by w4ett on 2007-08-24
One of the easiest ways for a newcomer to install video drivers for the Nvidia Card is to use the installation script 'Envy"

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

