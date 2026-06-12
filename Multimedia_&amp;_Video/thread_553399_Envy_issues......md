---
title: "Envy issues....."
date: 2007-09-17
forum: Multimedia &amp; Video
---

### Post by digital_exhaust on 2007-09-17
I'm sure there have been numerous threads started regarding my issue... but I have been unable to find the answer to my questions.... 

Specs first..

P4 3g, 1g ram, X1950pro 256m AGP, 80g Seagate, 120g WD, 500w Ultra psu...

Ok, so I have followed the install instructions for Envy, installed on a clean updated 7.04 install, and everything goes fine, until I restart the system.... and I am greeted with a black screen following the Ubuntu start screen.. the one with the scrolling orange bar thing....

I have attempted this three times, and I am getting the same results (surprise.. same thing in, same thing out:))... 

My question is this... Is hardware the issue here? Is my card not supported or what? Am I overlooking something in the install process?? The guide I have been using is the one found [here]("http://www.albertomilone.com/nvidia_scripts1.html")... 

Any help would be greatly appreciated, and thanks in advance all......

---

### Post by w4ett on 2007-09-17
I'd start by reconfiguring your xorg.conf.....boot into recovery mode.

From the command line type:


```
sudo dpkg-reconfigure -phigh xserver-xorg
```

This will give you the interface to modify the driver and resolutions. Controls are UP and DOWN cursor keys move the cursor and scrolls through available options, the space selects options, and <enter> confirms selections.

Select [COLOR="Red"]"vesa" or "ati"[/COLOR] as the driver and press <enter>, then at the next screen you can enable any addttional resolutions that you want to use.....then use the cursor keys to highlight {OK} and <spacebar> to select the resolutions and press <enter> to save the selections as prompted, then type:


```
startx
```

This should  get you to a GUI desktop.

There are three ways to install the restricted drivers for your card:

1. Use the restricted drivers manager in Ubuntu, System.>Administration>Restricted Driver Manager.[COLOR="Blue"] (try this option first)[/COLOR]

2. Use an installation script called Envy: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) ( this is MY preferred method because it uses the most up to date driver)

3. Compile your own driver modules from AMD/ATI [http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)


A lot of users find they have better luck running Envy from the terminal.....also purge your old driver before trying to reinstall.

```
sudo envy -t
```

This will run the installation script from the terminal....follow the instructions to purge the old fglrx drivers and then  install the correct ATI  proprietary driver.

Good Luck

---

