---
title: "Compilation of ATI 200m driver instructions"
date: 2006-07-02
forum: Multimedia &amp; Video
---

### Post by xolot1 on 2006-07-02
Ive been on and off this forum trying to get my ATI Xpress 200M chip working.
Since it can be done, and yet i havent been able to do it, i fear i have been following the wrong directions. OR even worse, messing up installations by mixing techniques.

I was hoping to get a comprehensive set of instructions covering every relavent file/command.  So by starting with the wiki instructions listed below, I'd be very grateful if you would edit the instructions to include specific commands that youve heard of/got your card working.


```

sudo apt-get update
sudo apt-get install module-assistant build-essential 
sudo apt-get install fakeroot dh-make debconf libstdc++5 gcc-3.3-base
chmod +x ati-driver-installer-8.26.18-x86.run
./ati-driver-installer-8.26.18-x86.run --buildpkg Ubuntu/dapper
sudo dpkg -i xorg-driver-fglrx_8.26.18-1_i386.deb
sudo dpkg -i fglrx-kernel-source_8.26.18-1_i386.deb
sudo dpkg -i fglrx-control_8.26.18-1_i386.deb
sudo rm /usr/src/fglrx-kernel*.deb
sudo module-assistant prepare
sudo module-assistant update
sudo module-assistant build fglrx
sudo module-assistant install fglrx
sudo depmod -a
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv

```

by editing and reposting more and more detailed and comprehensive instructions, hopefully we can get more people with the 200m chip working.

---

### Post by xolot1 on 2006-07-02
[QUOTE=xolot1]

```

[COLOR="Red"]
sudo vi /etc/default/linux-restricted-modules-common
         --> DISABLED_MODULES="fglrx"
sudo dpkg-reconfigure xserver-xorg  [using the ati driver
[change video memory to UMA only]
sudo dpkg -r xorg-driver-fglrx
sudo apt-get install --reinstall libgl1-mesa (<- is this correct?)
sudo mv /usr/lib/libGL.so.1 /usr/lib/libGL.so.1.backup
sudo mv /usr/lib/libGL.so.1.2 /usr/lib/libGL.so.1.2.backup
sudo dpkg -r --force-all xorg-driver-fglrx  (<- redundant?)
sudo updatedb
locate fglrx
sudo rm [all references]
[/COLOR]
sudo apt-get update
sudo apt-get install module-assistant build-essential 
sudo apt-get install fakeroot dh-make debconf libstdc++5 gcc-3.3-base
chmod +x ati-driver-installer-8.26.18-x86.run
./ati-driver-installer-8.26.18-x86.run --buildpkg Ubuntu/dapper
sudo dpkg -i xorg-driver-fglrx_8.26.18-1_i386.deb
sudo dpkg -i fglrx-kernel-source_8.26.18-1_i386.deb
sudo dpkg -i fglrx-control_8.26.18-1_i386.deb
sudo rm /usr/src/fglrx-kernel*.deb
sudo module-assistant prepare
sudo module-assistant update
sudo module-assistant build fglrx
sudo module-assistant install fglrx
sudo depmod -a
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv

```

[/QUOTE]
one revision

---

### Post by d-E-a-D on 2006-07-05
Ok, after more than 10 formats and thousand tries to make it work, i get 8.26 drivers working on my hp pavilion dv5172 with ati radeon Xpress 200m.
***_I'm using UMA+SIDEPORT 128Mb._***
It gives me the right fglrxinfo:

OpenGL vendor string: ATI technologies Inc.
OpenGL renderer string: RADEON XPRESS 200M Series Generic
OpenGL version string: 2.0.5879 (***_8.26.18_***)

Now my issue is that glxgears and fglx_gears hangs when i try to run it _***but things like screensaver and games do it great on OpenGL and fps.***_ but it is unstable. sometimes crash, others not.

The worst issue is that it seems that it doesn't refresh the image, everything just is it seems that the windows are over ones of the others, I see the images overlapped, icones disappears when I open something over them and closes.
To read console i have to underline the mouse over the letters. but if i maximize the console i can read it all great.

Now the steps.
Fresh Install of Ubuntu 6.06
update
distro-upgrade
restart
follow this thread but ***_WITH 8.26.18 DRIVER DOWNLOADED FROM ATI_***:
[http://www.ubuntuforums.org/showthread.php?t=199421&page=2&highlight=ati+8.24+200m]("http://www.ubuntuforums.org/showthread.php?t=199421&page=2&highlight=ati+8.24+200m")
restart

For now i can't go further... does anyone goes further than this with 8.26.18 drivers?

NOTE: 8.24.18 drivers worked for me with the thread i said. but i can't get XGL and COMPIZ working. And with fglx_glxgears i just see one piece rolling, the others don't appear like in glxgears.

If someone have this 200M card working well and with XGL and COMPIZ please give us a HOW-TO step by step !!!!

SORRY MY BAD ENGLISH.

Cumps

---

