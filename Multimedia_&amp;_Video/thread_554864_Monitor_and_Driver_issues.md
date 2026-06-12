---
title: "Monitor and Driver issues"
date: 2007-09-19
forum: Multimedia &amp; Video
---

### Post by Donut417 on 2007-09-19
Ok, I used a Olivia LCD HDTV 27in Wide screen. It works great as my tv and pc montior. I recently installed Ubuntu in a dual boot with Win XP pro. Well my montior reconizes in XP. However when Ubuntu starts to load the monitor becomes fuzzy and then goes blank and my TV says Invalid format. I use a BFG GeForce 6800. I dont have the drivers installed yet, however if I plug it in to a spare LCD mointior it works. I do have the drivers on the ubuntu desktop. But Im still new to Linux and the sudo command. Im currently running ubuntu 6.06 LTS. Im thinking of installing the newest version to see if that gives me any luck.

---

### Post by w4ett on 2007-09-19
If you upgrade to feisty fawn, the restricted drivers are included...but, seeing as how you are running 6.06 and you are unfamiliar with the command line I suggest this
:
Give Envy a try:  navigate to:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Install envy and then from the terminal type:


```
sudo envy -t
```

This will run the installation script from the terminal....follow the instructions to  install the correct Nvidia proprietary driver.

Good Luck

---

### Post by Donut417 on 2007-09-19
ok, couldnt figure out how to install envy, but I figured out how to install the driver :D

Now then. Is there any way I can get my HDTV to be supported by linux. I have both VGA and HDMI connectors on the TV.

---

