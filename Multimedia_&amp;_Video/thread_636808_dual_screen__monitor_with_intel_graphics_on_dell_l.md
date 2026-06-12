---
title: "dual screen / monitor with intel graphics on dell laptop"
date: 2007-12-10
forum: Multimedia &amp; Video
---

### Post by bro on 2007-12-10
Hi, 
I have intel 965 graphics on a Dell d830 with 1680x 1050 resolution. I would like to work with another (second)  monitor, but I can't. For presentations and such it is a must to have at least cloned output. I can tell my machine what monitor the second is (acer al1711) but it won't give me the option to use it. 
is this at all possible?

---

### Post by public_void on 2007-12-10
I'm not aware of any software that can do this. However it is possible, but you have to have two copies of /etc/X11/xorg.conf, one configured for clone and one for dual screen. You'd have to create a very simple script that would swap the xorg.conf files then restart x. First thing is to create the two different xorg.conf files and have different names for them. For example xorg.conf.clone and xorg.conf.dual. Then you need a simple script to swap the files. This checks the first argument, if it equals clone then copies the clone xorg.conf, else if it equal dual, copy that.

```
#!/bin/bash

if [ $1 = "clone" ] ; then
    cp /etc/X11/xorg.conf.clone /etc/X11/xorg.conf
elif [ $1 = "dual" ] ; then
    cp /etc/X11/xorg.conf.dual /etc/X11/xorg.conf
else
    echo "Unknown argument"$1
fi


```I'm not too good at scripts so check its right then test by swapping some unimportant files. Now you need to edit the xorg.conf files for each situation. Search for guides about editing xorg.conf, because getting it wrong can be trouble. Therefore create backups of xorg.conf after you make changes so you can change back if you encounter any problems.

---

### Post by Neap on 2007-12-11
Since you're using an intel card, consider using xrandr. You don't need to restart X that way.

If you want to let it auto-configure your monitors, run the following in the terminal
```
xrandr --auto
```
running "xrandr" with no arguments in the terminal will give you a list of attached displays, which you can use to fine-tune things if need be.

I personally have a shell script that handles turning on and off the second monitor on my ATI radeon 9600.

---

### Post by bro on 2007-12-11
Okay, thanx, I'm going to try it out with xrandr. I'm not good with scripting at all and besides that I have the kind of 'principle' that I shouldn't need to do that. I just wonder why ubuntu greys out the second monitor, (but that might have to do with my relatively new intel graphics, i did a small tweak to get desktop effects going as well). 
I'll report back if it works (and if it doesn't).

---

