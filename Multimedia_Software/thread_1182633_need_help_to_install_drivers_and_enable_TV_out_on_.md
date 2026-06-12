---
title: "need help to install drivers and enable TV out on nVidia Riva TNT2"
date: 2009-06-09
forum: Multimedia Software
---

### Post by hurtstotalktoyou on 2009-06-09
EDIT:  Drivers have been installed; now I just need to enable the TV out port.

ORIGINAL POST:

My video card is an Asus V3800 Ultra Deluxe, with the nVidia Riva TNT2 chipset.  It has a TV-out port which I would very much like to enable.  However, I don't seem to be able to install the proprietary drivers for the card.

I'm running Xubuntu 9.04, but I don't mind downgrading to something else if it would help.

The restricted drivers manager in Xubuntu is blank; it doesn't seem to recognize the video card.  There is driver file called "NVIDIA-Linux-x86-71.86.09-pkg1.run" available from [the nVidia website](http://www.nvidia.com/object/linux_display_x86_71.86.09.html), but when I try to "sudo sh NVIDIA-Linux-x86-71.86.09-pkg1.run" I get an error telling me I need to log out of the X server.  How in the world do I do that?

I've tried installing nvidia-settings, but when I run that, it just tells me that no drivers are installed.

Any help would be much appreciated!

---

### Post by sandy8925 on 2009-06-09
As it says you need to stop the x server. For that first close any programs that are open. Then hit ctrl + alt + F1. It will take you to a terminal with login. Enter your username and password. Then you will get a prompt. The command to stop the server is:

sudo /etc/init.d/gdm stop

It may or may not ask you for your password. After executing it gives the output:

Stopping Gnome display manager ......

then it will return to the prompt.

Then go to the directory where the installer is and execute the file as you tried to earlier.

After the installation is finished you can start up the x server again by executing:

sudo /etc/init.d/gdm start

Now the normal login screen should come up.If it doesn't hit ctrl + alt + F7. 

That's it ! Now the driver will be installed and nvidia-settings will show you the driver version when you start it.

---

### Post by hurtstotalktoyou on 2009-06-09
Wow, that was painless.  Thanks!

So the drivers have been installed.  Now I must figure out how to enable the TV out port.  Any ideas?

---

