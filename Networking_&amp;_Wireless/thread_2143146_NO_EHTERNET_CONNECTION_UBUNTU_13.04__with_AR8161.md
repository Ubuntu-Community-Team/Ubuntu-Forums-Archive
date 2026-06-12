---
title: "NO EHTERNET CONNECTION UBUNTU 13.04  with AR8161"
date: 2013-05-08
forum: Networking &amp; Wireless
---

### Post by perro68 on 2013-05-08
I have an HP p7-1430 machine that dual boots with windows 8

  when i installed 12.10 i installed a backport to get my ehternet adapter to work

it worked perfectly ....once i upgraded to 13.04 my ethernet once ago does not work

i downloaded compat-drivers-2013-03-15-u.tar.bz2


```
tar jxvf compat-drivers-2013-03-15-u.tar.bz2

./scripts/driver-select alx

 make
```

when i run the make command i get the following error
```

pat-drivers-3.8-1-u modules
make[1]: Entering directory `/lib/modules/3.5.0-28-generic/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/3.5.0-28-generic/build'
make: *** [modules] Error 2
```


PLEASE HELP !!!!!!!

---

### Post by chili555 on 2013-05-08
You need:```
sudo apt-get install build-essential linux-headers-generic
```Then try again.

---

### Post by perro68 on 2013-05-08
I DID THIS!!!

it still does not work

it told me:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
linux-headers-generic is already the newest version.
The following packages were automatically installed and are no longer required:
  cuneiform cuneiform-common espeak libavahi-client-dev
  libavahi-common-dev libcolorhug1 libcuneiform0 libexif-dev
  libgfortran3 libgnomecanvas2-0 libgnomecanvas2-common
  libgphoto2-2-dev libgraphicsmagick++3 libgraphicsmagick3
  libieee1284-3-dev liblapack3 liblept3 libopencv-calib3d2.4
  libopencv-core2.4 libopencv-features2d2.4 libopencv-flann2.4
  libopencv-highgui2.4 libopencv-imgproc2.4 libopencv-legacy2.4
  libopencv-ml2.4 libopencv-objdetect2.4 libopencv-photo2.4
  libopencv-video2.4 libtbb2 libtesseract3 libusb-dev libv4l-dev
  libwebp4 python-enchant python-espeak python-numpy python-opencv
  tesseract-ocr tesseract-ocr-eng tesseract-ocr-equ
  tesseract-ocr-osd
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
```


i should have mentioned i had already did that  i guess

---

### Post by perro68 on 2013-05-08
i did the follow:

```
sudo apt-get install --reinstall linux-headers-generic
sudo apt-get install --reinstall build-essential
```

---

### Post by chili555 on 2013-05-08
What does this tell us?```
sudo dpkg -s linux-headers-`uname -r`
```Those tickmarks are on the left side of my US keyboard on the same key with ~.

If it reports the headers for your running kernel version are not installed, then do:```
sudo apt-get install linux-headers-`uname -r`
```Then try the compile again.> I DID THIS!!!Please don't yell at me. I'm doing the best I can.

---

### Post by perro68 on 2013-05-08
I appreciate the help very much

but i was not yelling at you ....just showing my frustration with this thing

but i do not know if this means anything when i log in the grub menu i choose [COLOR=#ff0000]3.8.0-19-generic[/COLOR]

when i do uname -r i get

```
3.5.0-28-generic
```



sudo dpkg -s linux-headers-`uname -r`

```



dpkg-query: package 'linux-headers-3.5.0-28-generic' is not installed and no information is available
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
```

sudo apt-get install linux-headers-`uname -r`

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-headers-3.5.0-28-generic
E: Couldn't find any package by regex 'linux-headers-3.5.0-28-generic










```



please help

---

### Post by chili555 on 2013-05-08
> but i do not know if this means anything when i log in the grub menu i choose 3.8.0-19-generic

when i do uname -r i get

```
3.5.0-28-generic

```
It certainly does. You are trying to build for 3.**5**.0-28:> Entering directory `/lib/modules/[COLOR="#FF0000"]3.5.0-28-generic[/COLOR]/build'I suggest you reboot and try to get to get to 3.**8**.0-xx again.

---

### Post by perro68 on 2013-05-08
ok i just tried it 

THANK YOU VERY MUCH

i do not understand what is going on when with my grub menu

when i hit ubuntu it would talk me to the wrong kernal

when i went into advance options and choice the one at the top ...i could compile

maybe i just need to run boot-repair again?

---

### Post by chili555 on 2013-05-08
> maybe i just need to run boot-repair again? That is outside of my limited knowledge. I suggest you ask here: [http://ubuntuforums.org/forumdisplay.php?f=331](http://ubuntuforums.org/forumdisplay.php?f=331)

So your ethernet is working properly now, is that correct?

---

### Post by perro68 on 2013-05-08
It is works  but when i come back from a time out ...it suspend

it drops

and i can not reconnect

it tells me in system settings that the cable is unplugged

if i reboot ...evertything works find .....of course until ....it suspend again

---

### Post by chili555 on 2013-05-08
Please try this:```
gksudo gedit /etc/pm/config.d/config
```Add a single line:```
SUSPEND_MODULES="alx"
```Proofread carefully, save and close gedit.

After a reboot, let me know if it helps or is the same.

---

### Post by perro68 on 2013-05-08
yes creating that file  seems to have done the trick

thanks a lot

---

