---
title: "VIA K8M890 Chrome9 Driver (cheap on board video)?"
date: 2006-09-28
forum: Multimedia &amp; Video
---

### Post by ozp on 2006-09-28
[http://www.via.com.tw/en/products/chipsets/k8-series/k8m890/](http://www.via.com.tw/en/products/chipsets/k8-series/k8m890/)

[http://www.viaarena.com/default.aspx?PageID=420&OSID=32&CatID=2810&SubCatID=164](http://www.viaarena.com/default.aspx?PageID=420&OSID=32&CatID=2810&SubCatID=164)
Drivers for some others linux distros but not ubuntu nor debian


My ubuntu says that my video is VESA :(

I know that its possible to create a .deb from source files, and they give the source on their website
But I´m just a user, not expert or developer...

This is sad because this chipset is very common around here.
Many people use it because its cheap

So because its cheap its not fast and thats why its so important to have the driver, to achieve the max performance

Please give me some direction to make this work

Regards

---

### Post by rudykovanda on 2006-12-05
I have MB Asus K8V-VM witch K8M890CE (3230) graphics and in Kubuntu 6.10 I have this same problems, in "vesa" is very slow. I use Google :) and read this :

[http://www.hombrepac.com.ar/software-libre/linux/el-bendito-video-de-via-k8m890-chrome-9-igp-y-linux-xorg-ubuntu-y-tal-vez-otros/#more-188](http://www.hombrepac.com.ar/software-libre/linux/el-bendito-video-de-via-k8m890-chrome-9-igp-y-linux-xorg-ubuntu-y-tal-vez-otros/#more-188)

and make:


sudo apt-get remove xserver-xorg-video-via xserver-xorg-video-unichrome

sudo apt-get install build-essential libxinerama-dev x11proto-xinerama-dev libxvmc-dev sysutils tofrodos

sudo apt-get build-dep xserver-xorg-video-via

sudo apt-get build-dep xorg


(if question about install/remove say Y)

dovnload souce from 

[http://www.viaarena.com/Driver/CN_CX700-CN800XORG40071-kernel-src_20061107.tgz](http://www.viaarena.com/Driver/CN_CX700-CN800XORG40071-kernel-src_20061107.tgz)


and as root (or sudo)

# tar zxvf CN_CX700-CN800XORG40071-kernel-src_[fecha].tgz

# cd CN_CX700-CN800XORG40071-kernel-src_[fecha]/src

# ./makedriver

type your release and select procesor architecture


its make DIR CN_CX700-CN800XORG400xxx (xxx - release)


# ldconfig

# ./vinstall_2D

- this install via_drv.so and modify xorg.conf

and startx - in x86 via driver loaded, screen is very faster that "vesa", but screen is very unstable, has bug, broken pixels etc...

in 64bit driver not load, I not remember error, I test x86.... 

Any idea ?

---

### Post by Z(L)o on 2006-12-07
> **rudykovanda said:**
> I have MB Asus K8V-VM witch K8M890CE (3230) graphics and in Kubuntu 6.10 I have this same problems, in "vesa" is very slow. I use Google :) and read this :

[http://www.hombrepac.com.ar/software-libre/linux/el-bendito-video-de-via-k8m890-chrome-9-igp-y-linux-xorg-ubuntu-y-tal-vez-otros/#more-188](http://www.hombrepac.com.ar/software-libre/linux/el-bendito-video-de-via-k8m890-chrome-9-igp-y-linux-xorg-ubuntu-y-tal-vez-otros/#more-188)

and make:


sudo apt-get remove xserver-xorg-video-via xserver-xorg-video-unichrome

sudo apt-get install build-essential libxinerama-dev x11proto-xinerama-dev libxvmc-dev sysutils tofrodos

sudo apt-get build-dep xserver-xorg-video-via

sudo apt-get build-dep xorg


(if question about install/remove say Y)

dovnload souce from 

[http://www.viaarena.com/Driver/CN_CX700-CN800XORG40071-kernel-src_20061107.tgz](http://www.viaarena.com/Driver/CN_CX700-CN800XORG40071-kernel-src_20061107.tgz)


and as root (or sudo)

# tar zxvf CN_CX700-CN800XORG40071-kernel-src_[fecha].tgz

# cd CN_CX700-CN800XORG40071-kernel-src_[fecha]/src

# ./makedriver

type your release and select procesor architecture


its make DIR CN_CX700-CN800XORG400xxx (xxx - release)


# ldconfig

# ./vinstall_2D

- this install via_drv.so and modify xorg.conf

and startx - in x86 via driver loaded, screen is very faster that "vesa", but screen is very unstable, has bug, broken pixels etc...

in 64bit driver not load, I not remember error, I test x86.... 

Any idea ?


I have a related question too:
while doing this

sudo apt-get build-dep xserver-xorg-video-via
i am getting an error message that the source can not be found
ANY IDEAS how should I modify the sources.list or?

thanks

---

### Post by piel69004 on 2006-12-14
Hi, you might want to have a look at this :

[OpenChrome]("https://help.ubuntu.com/community/OpenChrome")

---

### Post by kipeloff on 2007-03-13
Additionaly to the previous post, if drivers are installed from viaarena webpage, where I found the latest driver for the particular chipset, then follow the instructions given by rudykovanda, but files './makedriver' and './vinstal2d' should be modified.
Open them on any texteditor and find 'Ubuntu' (Edgy 6.10), then change listed kernel version to the result of 'uname -r' on your system.
Driver was installed successfully after I have applied these modifications.

---

