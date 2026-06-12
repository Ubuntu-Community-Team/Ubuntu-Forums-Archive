---
title: "Nvidia Driver GLX not loading"
date: 2007-02-17
forum: Multimedia &amp; Video
---

### Post by Phatrabbit on 2007-02-17
Paste Bins are here

/var/log/Xorg.0.log
[http://paste.ubuntu-nl.org/6213/](http://paste.ubuntu-nl.org/6213/)

/etc/X11/xorg.conf
[http://paste.ubuntu-nl.org/6209/](http://paste.ubuntu-nl.org/6209/)

How i started

I used the command

sudo dpkg -i nvidia-glx_1.0.8776+2.6.15.12-28.1_i386.deb to install my drivers

and then the command below to check if my drivers were up to date
sudo apt-get install nvidia-glx nvidia-kernel-common

Reading package lists... Done
Building dependency tree... Done
nvidia-glx is already the newest version.
nvidia-kernel-common is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

I then followed the rest of the steps from 
[http://ubuntuguide.org/wiki/Dapper#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Dapper#How_to_install_Graphics_Driver_.28NVIDIA.29)

However after i  done the command

sudo nvidia-glx-config enable

and then checked /etc/X11/xorg.conf

It looked like this 

[http://paste.ubuntu-nl.org/6219/](http://paste.ubuntu-nl.org/6219/)

However it still said Driver "vesa" so i had a friend edit the /etc/X11/xorg.conf to [http://paste.ubuntu-nl.org/6209/](http://paste.ubuntu-nl.org/6209/) 

tried to restart xserver and it would not load and gave me an error 

[http://paste.ubuntu-nl.org/6213/](http://paste.ubuntu-nl.org/6213/)

Can anybody give me any tips on how to get my drivers running. 

I have been trying for the last 6 hours straight with no luck 

Thanks ! Cheers !

---

