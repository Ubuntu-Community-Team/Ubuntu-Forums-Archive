---
title: "Tuning Hauppage WinTV-HVR 950Q"
date: 2009-02-11
forum: Multimedia Software
---

### Post by slick666 on 2009-02-11
Hi everyone

I think I have my card installed correctly but I'm trying to tune some channels in and I can't figure out how. Everyone seems to think the VLC can do the trick but I'm nto put that on my ot sure how to do it. All the tutorials are for Mythtv and I'm not quite ready to put that on my laptop.

Does anyone know how to setup VLC to read a capture card?

---

### Post by wolfen69 on 2009-02-12
the following was written for ubuntu 7.10, but may work for you. from [HERE]("http://www.technetra.com/2008/07/01/over-the-air-digital-tv-with-linux/")

First, enable universe and multiverse package repositories by selecting &#8220;System->Administration->Software Sources&#8221; from the GNOME desktop menu. Click on the tab labeled Ubuntu Software, and make sure the boxes are checked for Community-maintained Open Source software (universe) and Software restricted by copyright or legal issues (multiverse). Click Close.

Next, apply all latest updates from Ubuntu by selecting &#8220;System->Administration->Update Manager&#8221; from the GNOME desktop menu, apply all system updates, and reboot the system.

Then, in a terminal, do sudo su to become the root user. Install the necessary packages to build em28xx kernel modules:

> ```
aptitude install mercurial build-essential linux-source

```
Download firmware version 4, necessary for USB tuner cards:

> ```
wget -q http://konstantin.filtschew.de/v4l-firmware/firmware_v4.tgz \
-O /usr/local/src/firmware_v4.tgz
```

Unpack the firmware files into /lib/firmware:

> ```
tar xzf /usr/local/src/firmware_v4.tgz -C /lib/firmware
```

Grab the latest copy of the V4L DVB source code from mcentral.de:

> ```
cd /usr/local/src
```
> ```
hg clone http://mcentral.de/hg/~mrec/v4l-dvb-kernel
```

Compile the V4L DVB drivers:

> ```
cd /usr/local/src/v4l-dvb-kernel
```
> ```
make
```
> ```
make install

```
And, finally, reboot the system.


I used tvtime to evaluate the analog TV performance. The picture quality was significantly better for stations with transmission towers that were geographically closer. Initially, sound did not work in tvtime. Using sox to route audio from tvtime to the default ALSA sound device solved the problem. Research on the Web indicated that many others have faced this same issue when using tvtime.

---

### Post by cmargolin on 2009-02-12
I use Kaffeine with my 950Q.

---

### Post by jwkolberg on 2009-02-13
After going through all the steps, the last one gave me this error:

```
root@user:/usr/local/src/v4l-dvb-kernel# make install

running ./build.sh install

./build.sh install
cp: cannot stat `sharp/s921.ko': No such file or directory
cp: cannot stat `drx3973d/drx3973d.ko': No such file or directory
cp: cannot stat `tvp5150/tvp5150.ko': No such file or directory
cp: cannot stat `lgdt3304/lgdt3304.ko': No such file or directory
cp: cannot stat `mt352/mt352.ko': No such file or directory
cp: cannot stat `zl10353/zl10353.ko': No such file or directory
cp: cannot stat `cx25843/em28xx-cx25843.ko': No such file or directory
cp: cannot stat `xc3028/tuner-xc3028.ko': No such file or directory
cp: cannot stat `xc5000/tuner-xc5000.ko': No such file or directory
cp: cannot stat `em28xx.ko': No such file or directory
cp: cannot stat `em28xx-audioep.ko': No such file or directory
cp: cannot stat `em28xx-aad.ko': No such file or directory
cp: cannot stat `em28xx-audio.ko': No such file or directory
cp: cannot stat `em28xx-dvb.ko': No such file or directory
cp: cannot stat `qt1010/qt1010.ko': No such file or directory
cp: cannot stat `mt2060/mt2060.ko': No such file or directory
cp: cannot stat `modules/*': No such file or directory
depmod -a

```

Couldn't find any help for this anywhere. I'm guessing its something pretty simple?

---

### Post by markackerman8@gmail.com on 2010-03-21
I got a few errors about missing files or permissions and was surprised that the card loaded fine anyways.

---

