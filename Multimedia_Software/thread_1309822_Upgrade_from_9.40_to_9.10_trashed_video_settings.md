---
title: "Upgrade from 9.40 to 9.10 trashed video settings"
date: 2009-11-01
forum: Multimedia Software
---

### Post by ronrafajko on 2009-11-01
Ubuntu 9.10 Karmic upgrade trashed my HP Pavilion's (dv6000) NVidia video drivers.  The /etc/x11 directory and xorg.conf file is missing.

There is an xorg.conf.new file in the root of the drive, but it is worthless.  After the initial boot with the white Ubuntu logo I get blinking text for the NTPD connection and login, which makes login impossible.

I ran "sudo dpkg-reconfigure -phigh xserver-xorg" but it did nothing constructive.

Is there a text utility to set up the video?

I guess I should have waited until more upgrade bugs were fixed.

---

### Post by ronrafajko on 2009-11-02
Shouldn't # "dpkg-reconfigure xserver-xorg" recreate the directory and file?  It appears to do nothing.

---

### Post by epek on 2009-11-02
try to do it with -plow instead of -phigh.
If that doesn´t help start aptitude and check, if all of your xorg-drivers are installed. you need the nv (nvidia driver) see man 4 nvidia for the settings, if the autodetection still doesn´t work.

Also, try to load the nvidia framebuffer - modprobe nvidiafb

still no xorg.conf after restart? "touch /etc/X11/xorg.conf"

still no success? post your /var/log/Xorg.0.log or grep for "EE" within it. grep "(EE" /var/log/Xorg.0.log

---

### Post by ronrafajko on 2009-11-02
Sorry, it did create the X11 directory, it was hidden and did not show up in an ls.  I have the xorg.conf file but it blinks if the Driver is nvidia.  If I set it to vesa I can get in but cannot run the GUI NVidia utility because it is running on the vesa driver.  I will try the solution to recompile the driver.

---

### Post by ronrafajko on 2009-11-02
I fixed the driver issue by running "envyng -t" in recovery mode and selecting the 173 driver.  It did not like the 185 driver.

---

### Post by TJ1234 on 2009-11-02
I've had some problems with my video as well. Major problems playing mkv files which I've managed to fix. But now when I play a video I see my cpu usage skyrocket and the fan seems to kick into overdrive. It did not do this until I upgraded to karmic. Does anyone know if this is a known issue? I'm on an hp dv9000.

---

