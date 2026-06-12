---
title: "At my wits end with geForce 8400gs"
date: 2013-01-17
forum: Multimedia Software
---

### Post by robfindlay on 2013-01-17
So I've installed 12.10 with a nvidia 8400gs, first log in everything runs, but is sluggish--doesn't Ubuntu automatically load the nvidia drivers?

I've tried installing the nvidia drivers from the software center and via command line and the same thing happens each an every time: I get to the log in splash screen just fine, plug in my password and I boot to a wallpaper with a mouse. I can right-click and add a folder to the desktop, or attempt to adjust the resolution but the unity interface simply never opens, nor do any of the windows that do open have any "decorations" i.e. maximize minimize etc.

Also booting into safe graphics mode fails and kicks me back to the same non-working desktop. 

The commands I used are as follows: 

/*
sudo apt-add-repository ppa:xorg-edgers/ppa

sudo apt-add-repository ppa:ubuntu-x-swat/x-updates

sudo apt-get update

sudo apt-get install nvidia-current nvidia-settings
*/

Has anyone gotten this card to work under 12.10?

-Rob

---

### Post by iceman30ad on 2013-03-08
Have you goten it working yet if not your going to love me... 
I went to another distro (arch and trolled there and found out the secret to getting it to work now i am going to  kang someone elses work and ill post a link to the orignal artical after 

> **Necessities for installing anything**
Couple of things here that are regulars for us Debian users, which the  Ubuntu crowd rarely post about. Mesa-Utils, and (the essential)  Module-Assistant, as it gets your headers, build-essential and all  manner of "compile-ready" bits n bobs.
[INDENT] sudo apt-get update && sudo apt-get upgrade
sudo apt-get install module-assistant mesa-utils
[/INDENT] **Module Assistant **
Module assistant will run off and fetch everything you need to compile  and load any kernel module, from graphics card drivers to wireless  firmware. This usually includes build-essential and your kernel-headers  amongst other things. So just tell it to prepare your system with a  simple:
[INDENT] sudo m-a prepare
[/INDENT] **Installing the proprietary Nvidia kernel module/driver**
[INDENT] sudo apt-get install nvidia-current
[/INDENT] Now just reboot and fire up glxgears (from the mesa-utils package) in  the terminal and watch those pretty cogs show you how fast your 3D  accelerated Nvidia card is.
[http://debianandi.blogspot.com/2012/11/ubuntu-1212-install-nvidia-geforce-8400.html](http://debianandi.blogspot.com/2012/11/ubuntu-1212-install-nvidia-geforce-8400.html)

hope it helps you as much as it helped me  heres the code i used and it runs flawlesly


```
sudo apt-get update && sudo apt-get upgrade && sudo apt-get install module-assistant mesa-utils && sudo m-a prepare && sudo apt-get install nvidia-current
```

---

