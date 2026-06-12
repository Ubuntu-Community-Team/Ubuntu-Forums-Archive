---
title: "Installing NVIDIA graphics drivers"
date: 2009-11-25
forum: Multimedia Software
---

### Post by Bliner56 on 2009-11-25
Could someone please walk me through what I need to do to install the latest NVIDIA drivers for my 7800 GT card?  Thanks.  I tried to activate driver which didn't work.

I tried downloading a NVIDIA-Linux-x86_64-190.42-pkg2.run and then I did

chmod +x NVIDIA-Linux-x86_64-190.42-pkg2.run
sudo ./NVIDIA-Linux-x86_64-190.42-pkg2.run

It seemed okay.  Then I restarted my computer and I got no display.  I reinstalled ubuntu and then my display came back.  Am I doing something wrong with the graphics card driver installation?

---

### Post by gradinaruvasile on 2009-11-25
First of all removing the /etc/X11/xorg.conf file would have been enough to solve your problem...

The idea was good. But follow these steps: 
1. Make sure u havent touched the restricted driver activation thing.
2. Stop the GDM (graphical server) - first make sure you havent got any documents in works, save everything - This will stop the graphical interface. 

In a terminal:

sudo service gdm stop

You will be taken to text mode display. Press ctrl+alt+f1
Login in text mode.

type:

sudo [COLOR="Red"]/path/to/driver/drivername[/COLOR]

Of course /path/to/driver/drivername this is the path/name of your driver (the .sh file from the net).
Watch out for compilation errors! Write them down if exist.

make sure you select "yes" for the auto configuration at the end.

now you can start the gdm server back:

sudo service gdm start

If not taken automatically to the graphical login, press ctrl+alt+f7.

Hope it helps

---

### Post by lvlo on 2009-11-25
> **Bliner56 said:**
> Could someone please walk me through what I need to do to install the latest NVIDIA drivers for my 7800 GT card?  Thanks.  I tried to activate driver which didn't work.

I tried downloading a NVIDIA-Linux-x86_64-190.42-pkg2.run and then I did

chmod +x NVIDIA-Linux-x86_64-190.42-pkg2.run
sudo ./NVIDIA-Linux-x86_64-190.42-pkg2.run

It seemed okay.  Then I restarted my computer and I got no display.  I reinstalled ubuntu and then my display came back.  Am I doing something wrong with the graphics card driver installation?If you want to install nVidia drivers from their site - install this first:```
sudo apt-get install linux-headers-`uname -r` binutils pkg-config build-essential  xserver-xorg-dev
```

---

