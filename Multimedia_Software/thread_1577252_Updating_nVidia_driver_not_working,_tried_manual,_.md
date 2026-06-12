---
title: "Updating nVidia driver not working, tried manual, not working, plz help!"
date: 2010-09-18
forum: Multimedia Software
---

### Post by havrelm1 on 2010-09-18
Still a little new to Ubuntu here (Ubuntustudio 10.04). I installed it on a Dell Inspiron 531 with the GeForce 6150SE nForce 430 built in video card. From the recommend driver list I installed ¨NVIDIA accelerated graphics driver (version current) [Recommended]¨

Well, turns out it should not have been recommended. I had restarted and all I got was a low res ubuntu logo and a boot right into a full screen terminal. Tried startx and got a no screens found, I look online for about an hour last night and decided to just reinstall, which takes a couple hours when installing all the packages.

I have done more research today and found to install the latest linux x64 driver from nVidias website, which I did, but it does not run. I followed some more instructions and it said to do a ´sudo chmod +x <file>´ which I did, and it starts to open and I get ´You appear to be running an X server; please exit X before installing.´

I´m starting to get a little frustrated here, guess I´m just used to a lot of the ease of windows and assumed that something like installing a graphics card driver would be easy.

Thanks in advance for any help!!!:P

---

### Post by cchhrriiss121212 on 2010-09-18
Are you using a new kernel that you installed yourself, or just the one that came with the OS?

Manual video driver installation requires that you stop GDM first, the steps are like this:
Place the file in your /home folder
Press Alt+Ctl+F2 and login
sudo service gdm stop
sudo sh./ then press tab to show the file
Agree to whatever the installer suggests, then do
sudo service gdm start

---

### Post by havrelm1 on 2010-09-18
I followed your instructions and got the following:

The installer opens and I agree to the terms.

then I get:

ERROR: The Nouveau driver is currently in use by your system. This driver is incompatible with the NVIDIA driver, and must be disabled before proceeding. Please consult the NVIDIA driver README and your Linux distribution´s documentation for details on how to correctly disable the Nouveau kernel driver.

hit ok

WARNING: The modprobe configuration file to disable Nouveau, /etc/modprobe.d/nvidia-installer-disable-nouveau.conf, is already present. Please be sure you have rebooted your system since that file was written. If you have rebooted, then Nouveau may be enabled for other reasons, such as being included in the system initial ramdisk or in your X configuration file. Please consult the NVIDIA driver README and your Linux distribution´s documentation for details on how to correctly disable the Nouveau kernel driver.

hit ok

ERROR: Installation has failed. Please see the file ´/var/log/nvidia-installer.log´ for details. You may find suggestions on fixing installation problems in the README on the linux driver download page at [www.nvidia.com](www.nvidia.com).


Whenever I do some research, I am finding inconsistencies in instructions, and since I don´t know exactly what I am doing here, I don´t want to follow some random instructions. Everything else is working perfectly, just need to install this video driver (NVIDIA-Linux-x86_64-256.53.run).

---

### Post by cchhrriiss121212 on 2010-09-19
OK, in 10.04 the Nouveau driver is installed by default, so open up synaptic package manager and remove it, then proceed with the steps.

---

