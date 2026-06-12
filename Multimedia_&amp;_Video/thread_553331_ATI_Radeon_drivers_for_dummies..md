---
title: "ATI Radeon drivers for dummies."
date: 2007-09-17
forum: Multimedia &amp; Video
---

### Post by cobolt01 on 2007-09-17
I recently persuaded my mother to buy a new PC. Since I have to reformat every two months to keep the thing running otherwise, I installed Ubuntu Feisty Fawn. I'm new to using Linux, but I've installed a few distros and understand the basics of the terminal.
I had a bad experience when trying to install the Nvidia drivers on a previous installation. Now the motherboard has an on board X1250 (Radeon) chip. I've tried installing the drivers "the Ubuntu way" but, well, nothing happened. Can somebody please give me a step by step instruction link or even write it out and explain what you're actually doing so that people who read it can learn from the post. Thanks very much in advance.

---

### Post by Mud.Knee.Havoc on 2007-09-17
By "the Ubuntu way", do you mean via the Restricted Drivers Manager?  Or do you mean by the walkthroughs on ubuntuguide.org?  Or do you mean through instructions found in probably 30 threads in this forum?

The good thing about the ubuntu (or linux) way is that there are always a bunch of ways to do it. :)

But if you can tell us how you have already tried (and failed), we can take it from there.

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

To use Envy,  navigate to:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Install envy and then from the terminal type:


```
sudo envy -t
```

This will run the installation script from the terminal....follow the instructions to purge the old fglrx drivers and then  install the correct ATI  proprietary driver.

Good Luck

---

### Post by KailasNarendran on 2008-01-02
I'm running 7.10 AMD 64

I ended up following in instructions at 

[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

and they seemed to work well.

I have a GA-MA69GM-S2H motherboard that has an integrated Radeon x1250.  I've got it in a machine that i want to be a HTPC.

For some reason, however, I can't get the HDMI output to work/detect my plasma TV.  Anyone know what might be up with that?  I can open up the ATI catalyst control center, and it clearly detects my card, but doesn't see the additional display device.  I can't even get it to work over the analog (svideo) output either.

Any ideas or suggestions would be greatly appreciated!

---

### Post by lvleph on 2008-01-02
> **w4ett said:**
> I'd start by reconfiguring your xorg.conf.....boot into recovery mode.

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

To use Envy,  navigate to:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Install envy and then from the terminal type:


```
sudo envy -t
```

This will run the installation script from the terminal....follow the instructions to purge the old fglrx drivers and then  install the correct ATI  proprietary driver.

Good Luck
Envy was the only way I could get things to work.

---

### Post by Yellow Pasque on 2008-01-02
For the ubuntu fglrx drivers, I just did:

```
sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial -f --overlay-type=Xv
```

and then rebooted. I have an X1250 as well. These days, I use the open-source radeonhd driver because all I use is 2D and it seems to be a lot smoother when moving windows around, etc.

---

