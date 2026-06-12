---
title: "DVB-T stick - can compile and install modules, but still not working?"
date: 2013-04-09
forum: Multimedia Software
---

### Post by dtordrup on 2013-04-09
Hi all, 

Can anybody provide feedback on this issue: I have successfully compiled and installed drivers for my device previously, an ARM device (Cubox) which runs Ubuntu 10.04 (2.6.32.9 kernel), but now that I'm retracing my steps with a new Ubuntu 10.04 install I can't get the device to work. 

Info on the V4L driver (which previously worked fine) is from [http://linuxtv.org/wiki/index.php/ITE_IT9135](http://linuxtv.org/wiki/index.php/ITE_IT9135) and the firmware has been extracted and placed in the correct location as described in the link.

This is what I did:


```

cd /usr/src
sudo wget https://github.com/rabeeh/linux-2.6.32.9/archive/master.zip
sudo unzip master.zip
cd linux-2.6.32.9-master/
su
zcat /proc/config.gz > /lib/modules/2.6.32.9-dove-5.4.2/build/.config
make oldconfig
make prepare // this does gives error related to some x86 file it's looking for, but honestly, I don't know what this command is supposed to do (suggested by a previous make error together with make oldconfig) and the following steps happily complete


sudo make modules_prepare
sudo make headers_install (http://www.solid-run.com/phpbb/viewtopic.php?f=12&t=597)
cd
git clone git://linuxtv.org/media_build.git
cd media_build
make clean
sudo ./build
sudo make install

```


Everything compiles and installs fine. However, the modules don't seem to be loaded when I insert the DVB stick (which as mentioned has worked before with this driver and firmware). I then tried to load modules manually:


```

lsmod dvb-usb-it913x 
lsmod it913x-fe

lsmod output:
Module                  Size  Used by
it913x_fe              28951  0
dvb_usb_it913x          4223  0
binfmt_misc             6269  1
sg                     17137  0

```


But dmesg still gives the same output (no joy) when stick inserted. 


lsusb gives:
Bus 001 Device 008: ID 048d:9005 Integrated Technology Express, Inc.


There's no trace in /dev/ of any dvb devices when plugged in. I have the correct firmware (dvb-usb-it9135-01.fw) in /lib/firmware. Basically, don't know what else to try. Output of dmesg is: 


```

[31301.573800] usb 1-1.4: new full speed USB device using orion-ehci and address 8
[31301.684717] usb 1-1.4: not running at top speed; connect to a high speed hub
[31301.694729] usb 1-1.4: New USB device found, idVendor=048d, idProduct=9005
[31301.694747] usb 1-1.4: New USB device strings: Mfr=1, Product=0, SerialNumber=3
[31301.694763] usb 1-1.4: Manufacturer: ITE Technologies, Inc.
[31301.694776] usb 1-1.4: SerialNumber: AF0102020700001
[31301.696297] usb 1-1.4: configuration #1 chosen from 1 choice
```


Desparate for ideas...?

---

