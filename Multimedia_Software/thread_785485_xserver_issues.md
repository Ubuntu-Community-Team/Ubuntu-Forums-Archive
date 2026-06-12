---
title: "xserver issues"
date: 2008-05-07
forum: Multimedia Software
---

### Post by mudcow007 on 2008-05-07
hello all

im a complete newbie at this so bear with me

i have just installed feisty on a machine and want to install xserver too

i have an nvidia 7200gs video card

when i run ```
sudo dpkg-reconfigure xserver-xorg[\CODE] i follow the on screen prompts but it seems to crash and displays the error

[CODE]xserver-xorg postinst warning: overwriting possibly-customised configuration file; backup in /etc/X11/xorg.conf
```

anybody any ideas?

thanks

---

### Post by Patb on 2008-05-07
Mudcow, that message is standard.  The English equivalent is "I'm going to write a new  /etc/X11/xorg.conf file and I'll back up your old one in the same directory in case you want to revert".   

If your display is now okay, the process has functioned correctly.  If it is not, please post details.  If you are still in a terminal, try "startx". 

Cheers, Pat.

---

### Post by mudcow007 on 2008-05-08
thanks for the reply pat

right thanks for the clear up, I have just run the startx command and now a small dialogue box roughly the quarter the size of my screen and the rest of the screen is grey and it has a black X in the middle.

the black box looks like a command prompt but the machine is now unresponsive

the graphics card is a Nvidia 7200gs if that makes any difference?

i selected the nv driver at the beginning of the xserver setup

---

### Post by Patb on 2008-05-08
Mudcow, I'm out of my depth now.  I don't use nvidia so I won't try to guess.  But you may wish to run through the reconfigure process again with different parameters.  

Any other suggestions out there?? 

Cheers, Pat.

---

### Post by Patb on 2008-05-08
> **mudcow007 said:**
> i have just installed feisty on a machine and want to install xserver too....
...screen is grey and it has a black X in the middle...
Mudcow, just a thought:  Have you done a standard install?  If you have, xorg (ie "xserver") should automatically be installed.  You shouldn't have to install it separately.  If you have done a minimal install, you will probably not yet have a window manager or desktop environment installed.  

Cheers, Pat.

---

### Post by Lamb Chop on 2008-05-09
After installing you should select the "nvidia" driver. The nv driver is the opensource driver which has less functionality. Also, before starting X make sure you have a desktop system and a login manager installed. For example to install a plain KDE with X and a login manager you would do:

"apt-get install x-window-system-core kdm kde-core"

Also, make sure you have your nvidia drivers installed. If you have a recent nvidia card you would need

"apt-get install nvidia-glx-new"

To set your X server settings run
"dpkg-reconfigure xserver-xorg" and select the nvidia driver

You can then reboot or manually start your login manager
"/etc/init.d/kdm start"



Good luck :)

---

### Post by mudcow007 on 2008-05-09
sorry guys quick update....as a last ditched attempt at tryng to get it to work i installed gnome and now all seems to be well :)

stange as X didnt seem to be working correctly, im guessing that Gnome uses X to funtion?

thanks all for your help

mudcow007

---

### Post by Patb on 2008-05-09
> **mudcow007 said:**
> i installed gnome and now all seems to be well :)
Mudcow!! What are you doing to us! ;) I wonder if Lamb Chop laughed as loud as I did when I realised you didn't have a desktop environment.  Xorg on its own won't get you far.  :)

Search around a bit for things like "minimal install", "desktop environment" and "window managers" - it's fun to learn the ropes.  

Good luck, Pat.

---

