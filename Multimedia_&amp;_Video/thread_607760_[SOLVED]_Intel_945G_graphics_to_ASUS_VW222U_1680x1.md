---
title: "[SOLVED] Intel 945G graphics to ASUS VW222U 1680x1050 LCD, screen offset to right"
date: 2007-11-09
forum: Multimedia &amp; Video
---

### Post by nix.ward on 2007-11-09
Hello, I'm having a problem with my ASUS VW222U widescreen LCD monitor in that it is shifted to the right leaving a 2" gap of unused screen on the left and 2" of hidden screen on the right.  Even when using the monitor's positioning settings this is the best I can get.  I have used the "Screen and Graphics" preferences program to select the correct resolution.

I have tried using 'sudo xvidtune' but but I get this response after making a change (clicking left or right) and clicking 'test' or 'apply':
[INDENT]"Sorry: You have requested a mode-line That is not possible, or not supported by your hardware configuration"[/INDENT]

Also I have tried manually editing the xorg.conf file.  My approach was to change the 'HSyncStart' and 'HSyncEnd' values in the mode-line of the 1680x1050 resolution.  This seemed to have no effect.

I noticed in the Xorg.0.log file that it has this section:
[INDENT](II) intel(0): Manufacturer's mask: 0
(II) intel(0): Supported Future Video Modes:
(II) intel(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) intel(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) intel(0): #2: hsize: 1280  vsize 960  refresh: 60  vid: 16513
(II) intel(0): #3: hsize: 1440  vsize 900  refresh: 60  vid: 149
(II) intel(0): #4: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
(II) intel(0): #5: hsize: 1680  vsize 1050  refresh: 60  vid: 179[/INDENT]

This makes me a bit concerned that the reason I am having this problem is because the intel 945 chip doesn't properly support this resolution at the moment?

I have attached my xorg.conf and Xorg.0.log files.  I hope someone can help.

Thanks in advance.

---

### Post by de_valentin on 2007-11-09
My pc had the same problem but it was very easy just use  the buttons on the bottom of your monitor, for me it was just "auto" and 2 seconds later it was done

---

### Post by nix.ward on 2007-11-09
I tried again just to be sure.  Using auto actually pushes it another inch to the right so that now there are 3" of black and 3" hidden.  Thanks anyway.

---

### Post by nix.ward on 2007-11-09
Can anyone help? I was hoping there would be an easy solution to this that I had missed.

---

### Post by de_valentin on 2007-11-10
Well If auto doesn't do it for you just do it manually

---

### Post by Jeff78 on 2007-11-10
I have pretty much this same problem and the "monitor" I am using is a flat panel TV with a VGA in, so I don't have any way to manually adjust the offset on the monitor itself. The only difference is that I am using an nVidia go5200 and not an intel card. A lot of people have been telling me I should manually edit the xorg file, but I really have no idea how to do this.

---

### Post by nix.ward on 2007-11-11
de_valentin, the best I can do manually still leaves a 2" gap of unused screen on the left, do you have any other ideas? thanks

Jeff78, I have attempted to edit the xorg.conf file myself but it does seem to help, [this]("http://en.wikipedia.org/wiki/Modeline") helped me to understand what to edit, although because I haven't been able to get it to work, there is probably more to it.  Hope it helps.

---

### Post by de_valentin on 2007-11-12
I'm sorry I can't be of more help, I'm not that good with the whole comandline thing. I can only follow the howto's I find sorry, best off luck anyway

---

### Post by trappist on 2007-11-14
I had to "downgrade" to the i810 driver (replace Driver "intel" with Driver "i810" in xorg.conf) and this problem was resolved.

---

### Post by nix.ward on 2007-11-19
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/116514/](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/116514/) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Thanks everyone for their help, I tried downgrading but no luck with that method for me.  I eventually found the above launch pad bug which pointed me to this [guide]("http://ubuntuforums.org/showpost.php?p=2702458&postcount=1") to fixing this type of problem.  So now I am happy!

---

