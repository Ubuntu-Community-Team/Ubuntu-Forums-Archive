---
title: "LIRC with kernel 2.6.17"
date: 2007-04-18
forum: Multimedia &amp; Video
---

### Post by JMinator on 2007-04-18
Hi,

I am beginning with Ubuntu, and I wanted to install my AVERMEDIA TV Card remote control. I've spent more than a week now, looking on every forum I could, but I am not able to do anything with it.

Actually, the result is that I do not get any response when I press a button on my remote using "irw" command.

I tought that maybe someone could give me the best way to install LIRC with Ubuntu 6.10 and an AverMedia 98 card (port 41).

Thanks a lot.

Here is what I am currently doing** (NOT WORKING)** :

```

1) Download lirc (you'll need at least version 0.8.1pre2)

sudo -s
cd /usr/src
wget http://lirc.sourceforge.net/software/snapshots/lirc-0.8.1pre2.tar.bz2
tar xvfj lirc-0.8.1pre2.tar.bz2


2)Patch lirc (http://www.g-loaded.eu/2006/09/09/kernel-2617-and-lirc_gpio-driver/)

cd lirc-0.8.1pre2/drivers/lirc_gpio
gedit lirc_gpio.c

	 #include "../drivers/char/bttv.h"
 	 #include "../drivers/char/bttvp.h"
 	 #else
	-#include "../drivers/media/video/bttv.h"
	-#include "../drivers/media/video/bttvp.h"
	+#include "../drivers/media/video/bt8xx/bttv.h"
	+#include "../drivers/media/video/bt8xx/bttvp.h"
 	 #endndif

 	 #if BTTV_VERSION_CODE < KERNEL_VERSION(0,7,45)


3) Install linux sources and other utils

cd /usr/src/
aptitude install linux-source-2.6.17 build-essential gcc-3.4
tar xvfj linux-source-2.6.17.tar.bz2
unlink linux
ln -s linux-source-2.6.17 linux
cd linux
cp /boot/config-2.6.17-10-generic .config


4) Patch Source (http://www.g-loaded.eu/2006/09/09/kernel-2617-and-lirc_gpio-driver/)

cd drivers/media/video/
cp btcx-risc.h bt8xx/btcx-risc.h


5) Patch source 2

cd /usr/src/linux/drivers/video
wget http://dl.bytesex.org/releases/video4linux/bttv-0.9.15.tar.gz
sudo tar xvf bttv-0.9.15.tar.gz
cd bttv-0.9.15
sudo cp * /usr/src/linux/drivers/video
sudo cp * /usr/src/linux/drivers/media/video
sudo cp * /usr/src/linux/drivers/media/video/bt8xx


6) Install lirc from repos 

aptitude install lirc lirc-x


7) Lirc setup

cd /usr/src/lirc-0.8.1pre2/drivers
ln -s /usr/src/linux/drivers drivers
cd ..
./setup.sh

	1 - Driver configuration
	5 - TV Card
	6 - AverMedia98 TV Card
	3 - Save configuration and run configure


7) Build and install lirc from source

cd /usr/src/lirc-0.8.1pre2
make
make install


8) Config file

cd /usr/src/
wget http://lirc.sourceforge.net/remotes/avermedia/lircd.conf.avermedia98
sudo cp lircd.conf.avermedia98 /etc/lirc/lircd.conf


9) Config File 2

cd /etc/lirc/
gedit hardware.conf

	LOAD_MODULES=true
	DRIVER="default"
	DEVICE="avermedia98"
	MODULES="lirc_gpio"


10) Test

sudo modprobe lirc_gpio
sudo /etc/init.d/lirc restart
irw

```

---

### Post by williammanda on 2007-04-18
I recently got lirc working with mythtv and some other programs as well as the mouse function. I started with this link:
 [https://help.ubuntu.com/community/Install_Lirc_Edgy](https://help.ubuntu.com/community/Install_Lirc_Edgy)

Here is the past history of my installation:
[http://ubuntuforums.org/showthread.php?p=2424848#post2424848](http://ubuntuforums.org/showthread.php?p=2424848#post2424848)

Good luck!

---

### Post by JMinator on 2007-04-18
> **williammanda said:**
> I recently got lirc working with mythtv and some other programs as well as the mouse function. I started with this link:
 [https://help.ubuntu.com/community/Install_Lirc_Edgy](https://help.ubuntu.com/community/Install_Lirc_Edgy)

Good luck!

I've already found  this link but it do not work at all with "lirc_gpio" used with AverMedia Card. I can't figure out what is wrong in my method, and I have no more ideas about it. 

Thanks for the fast reply, it is certainly appreciated !

---

