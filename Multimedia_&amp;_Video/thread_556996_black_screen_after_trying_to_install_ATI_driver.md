---
title: "black screen after trying to install ATI driver"
date: 2007-09-22
forum: Multimedia &amp; Video
---

### Post by quigbrew on 2007-09-22
I've been trying the plethora of ATI installation guides found on the internet for the past few hours now, but after trying [http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide), ubuntu loads to a black screen where I can't do anything.  From browsing these forums I see other people have this same problem.  In fact I see another post that even has my same video card X1300.  i want to go through that post and try everything in it, but first I need to figure out how to revert back to my old settings and get rid of this black screen!

So, does anyone know how I can get rid of this black screen and get back into ubuntu once again?

I'd of course appreciate any help I can get!

---

### Post by mziskandar on 2007-09-22
after installation..

$ sudo aticonfig --initial
$ sudo aticonfig --resolution=0,1024x768

Whereby: 0 as your screen, 1024x768 as your resolution.

---

### Post by quigbrew on 2007-09-22
thanks for the response.

when I type **sudo aticonfig --initial**  it reports back:** sudo: aticonfig: command not found**

Is there anyway to delete the ati driver and reset the driver back to ubuntu's default again?

thanks

---

### Post by quigbrew on 2007-09-22
is there a way I can revert back to the original ubuntu settings?  Then at least I could try the process again.

---

### Post by w4ett on 2007-09-22
boot into recovery mode.

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

---

