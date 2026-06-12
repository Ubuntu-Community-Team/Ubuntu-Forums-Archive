---
title: "ati radeon 9600 how to fix?"
date: 2007-04-02
forum: Multimedia &amp; Video
---

### Post by sdowney717 on 2007-04-02
click this option,
do the restart and

its dead

---

### Post by sdowney717 on 2007-04-02
[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)

following this guide, they claim 

Method 1: Install the Driver the Ubuntu Way

IMPORTANT: This method will not work with 2.6.20.* kernels. 

interesting that feisty is 2.6.20 and feisty restricted modules wont work as released by ubuntu?

following method 2, I get thru BUT seeing it as mesa.
should see this 
$fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON 9700 Generic
OpenGL version string: 2.0.6400 (8.35.5)

BUT I see this
root@scott-desktop:~# fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)

---

### Post by xodroolis on 2007-12-15
The same happens to me

instead i see this

fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: DRI R300 Project
OpenGL renderer string: Mesa DRI R300 20060815 AGP 8x x86/MMX+/3DNow!+/SSE TCL
OpenGL version string: 1.3 Mesa 7.0.1

Please some help

---

### Post by weblordpepe on 2007-12-15
I'm on a 9600.

You don't wanna see that Mesa. That's the open-source driver at work. You need to see the fglrx driver loading.

But when you say its dead, what do you mean?

You could try blacklisting the mesa driver. Umm Shyte how do you do it...
edit /etc/default/linux-restricted-modules-common and put *mesa* in where it shows you.

At least I think thats how you stop mesa from loading.

---

### Post by talon95 on 2007-12-15
Yea, be more specific on "it's dead".  Did it lock up immediately or are you just stuck at the command line on reboot?  If it's the latter, then the xorg.conf file is not set up correctly more than likely.  I just went through this install and had that problem.  

One thing I found was, DO NOT let the installers configure your xorg file automatically.  Back it up (or generate a clean one which is probably better) and then use the aticonfig program to set it up.  Primarily the following 2 lines:

sudo aticonfig --initial 
sudo aticonfig --overlay-type=Xv

Which come from here:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Edit, and here's the magic line to reset the xorg file back to defaults.

sudo dpkg-reconfigure xserver-xorg

---

### Post by sdowney717 on 2007-12-17
thanks, but it is an old thread.

What I meant by dead was ubuntu would boot up to a blank screen.

Right now It is running fine on latest ATI driver using Envy installer.
I have learned that ATI drivers are poor compared to Nvidia and will never buy ATI again.

---

### Post by weblordpepe on 2007-12-18
> **sdowney717 said:**
> :KSI have learned that ATI drivers are poor compared to Nvidia and will never buy ATI again.:KS

I shouted something similar at the moon whilst waving my fists in rage.

---

### Post by Yellow Pasque on 2007-12-18
ATI's proprietary drivers do suck, but they are in the process of releasing specs so that the open-source community can write a real driver. In fact, I have the open-source radeonhd driver installed and it does basic 2D very well without throttling the CPU, etc.

---

### Post by sdowney717 on 2007-12-18
right now using latest 7.11 driver, IF I run compiz, I get nasty flashing on google earth,
On all 3D games, I get a weird annoying periodic angular flashing shape  line thingy  on the screen.
When not running compiz, it is ok.

Do you know how to unrun compiz without rebooting?

---

### Post by weblordpepe on 2007-12-19
Yep. Its a **--replace** paramater that you can put on the end.

Go to the console and type:
**killall compiz.real**
**metacity --replace**

And later on, type **compiz --replace**

Window managers all like the **--replace** tag. So do I. Mmm.

---

### Post by Bugsy969 on 2007-12-19
I'm running a Radeon 9600 and i just got the drivers working... works amazing just gotta work at it and make you do the right method the first time haha i have to reinstall Ububtu the first time :p

this method worked for me

[http://ubuntuforums.org/showthread.php?t=569654](http://ubuntuforums.org/showthread.php?t=569654)

it's part way down the thread

---

