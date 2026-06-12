---
title: "Problem with framebuffer - geforce 6600GT - UbuntuStudio"
date: 2008-04-28
forum: Multimedia Software
---

### Post by themusicalduck on 2008-04-28
I've clean installed UbuntuStudio 8.04 on a dual-boot with Windows XP. First time running the installation, I only get a screen with random peach and white lines/blocks with flashing white blocks and no coherent GUI at all. I then reconfigure xorg using sudo dpkg-reconfigure xorg-xserver and set it to use the framebuffer. Then after using sudo /etc/init.d/gdm restart, the screen flashes a couple of times and I get an error 'Failed to open framebuffer device'.

The only time I managed to get past the splash screen to an actual usable GUI was when I used the command apt-get install ubuntu-desktop instead of using ubuntustudio-desktop on top of the CD install of ubuntu studio. For some reason I didn't get the same framebuffer error, although I did have to reconfigure the xorg.conf. The graphics resolution was also set low, and I had an error on enabling desktop effects, but I figure that's a seperate problem with drivers to fix next step..

Also, if I were to install ubuntustudio and run apt-get install ubuntu-desktop instead of apt-get install ubuntustudio-desktop, will the install still function as an ubuntustudio installation with a different theme or are there significant changes?

This is my first experience with Linux so my problem description probably isn't great (and I can't remember all error messages/text word for word) So you'll have to excuse any general noobiness :)

---

### Post by themusicalduck on 2008-04-28
Tried using the Ubuntustudio 7.10 version as well and got the same problem.

Been trying to fix this problem for days now and it's driving me mad.

Can't anyone help?

---

### Post by MatthewAPeters on 2008-04-30
There is a ticket for problems with NVidia GeForce 6600GT in Hardy Heron - you are not alone.  But not many folks are contributing to it.  Please check out the bug, see if it is what you are suffering from, and update it so it doesn't get dropped!  

[https://bugs.launchpad.net/ubuntu/+bug/211387](https://bugs.launchpad.net/ubuntu/+bug/211387)

This one is a major PITA - none of the tricks I've used in the past seem to want to work in Heron.

---

