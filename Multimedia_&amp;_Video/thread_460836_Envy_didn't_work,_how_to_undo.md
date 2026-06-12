---
title: "Envy didn't work, how to undo?"
date: 2007-06-01
forum: Multimedia &amp; Video
---

### Post by josesanders on 2007-06-01
I tried installing the NVidia driver via the Envy script, and my xserver wouldn't start up again after a reboot.  I was able to get the xserver to start again by automatically reconfiguring the xorg.conf, but now I'm stuck at 1024x768.  I used to be able to get higher resolutions.  Can anyone help?  I should mention that I'm running the low latency kernal for Ubuntu Studio (maybe that's why the envy script failed?).

Thanks,

---

### Post by nutz on 2007-06-29
Envy didn't work for me either and I have the standard Ubuntu. Are there any instructions online for undoing the changes it made?

---

### Post by josesanders on 2007-07-02
I had a difficult time solving this problem.  I uninstalled the NVidia driver with Envy, but it still didn't work.  I tried to recreate my xorg.conf file using the command:

$ sudo dpkg-config -phigh xserver-xorg

That worked to get the x server back, but no matter what I did, as I mentioned below, I couldn't get the resolution above 1024x768.

There's surely a better way to do this, but since I know that when I boot the live CD, the resolution is good, I decided to boot the live CD, copy the xorg.conf file to a usb memory stick, and then reboot back into my system and replace the xorg.conf file with the one from the live CD boot.  There must be a better way, but I couldn't think of it.

---

### Post by MCSE_Crossover on 2007-07-02
Make sure that the restrictred repositories are enabled

sudo aptitude install nvidia-glx

sudo aptitude upgrade

sudo nvidia-xconfig

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_setup_nvidia_drivers_in_7.04](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_setup_nvidia_drivers_in_7.04)

You may have to edit the /etc/X11/xorg.conf to ensure the driver has changed from "nv" to "nvidia"

Also, ensure that your needed resultions are entered within the file.

---

