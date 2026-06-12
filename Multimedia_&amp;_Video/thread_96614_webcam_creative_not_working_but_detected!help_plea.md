---
title: "webcam creative not working but detected!help please!"
date: 2005-11-29
forum: Multimedia &amp; Video
---

### Post by blakken on 2005-11-29
I recently bought a creative webcam live pro but unfortunately using xawtv ,didn't detect it neither gnomeeting.
I did some lsusb and it shows:
Bus 004 Device 005: ID 041e:4038 Creative Technology, Ltd
Bus 004 Device 004: ID 045e:0024 Microsoft Corp. Trackball Explorer
Bus 004 Device 003: ID 05e3:0702 Genesys Logic, Inc. USB 2.0 IDE Adapter
Bus 004 Device 002: ID 0409:0059 NEC Corp. HighSpeed Hub
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
any idea which driver shall I use for this cam?

---

### Post by ubernoob on 2005-11-30
Sorry, but i don't have a webcam my self, and can probably not help you. But you might want to try the cvs version of amsn. That has full support for webcams. Maybe you can get it to work there? [http://amsn.sf.net]("http://amsn.sf.net")

---

### Post by blakken on 2005-12-01
thanx for your answer but i did try already 1 month ago and didn't change anything

---

### Post by tseliot on 2005-12-01
I have used this guide for my Creative FX webcam: [HOWTO: Making ICM532 chipset based webcams work on breezy]("http://ubuntuforums.org/showthread.php?t=75284")

In that guide you will find a link to the list of all the webcams which are supported by the driver.

It works great for me.

---

### Post by blakken on 2005-12-01
yes I did try this guide unfortunately I didn't manage to compile the spca...ko ,if in case you managed you can always send the file to me!:cool:

---

### Post by dbeckham32 on 2005-12-02
I don't have a Creative webcam, but I do that a Logitech QuickCam 4000 Pro running under Breezy.

I'm using the PWC driver. Follow the instructions on these website for more information. Sorry I could not be of more help.

[http://www.saillard.org/linux/pwc/](http://www.saillard.org/linux/pwc/)

[http://www.linux-sxs.org/hardware/pwc.html](http://www.linux-sxs.org/hardware/pwc.html)

[http://www.lavrsen.dk/twiki/bin/view/PWC/WebHome](http://www.lavrsen.dk/twiki/bin/view/PWC/WebHome)

---

### Post by blakken on 2005-12-03
this stuff seams really  interesting but the module.conf in ubuntu doesn't exist !is there any way to configure in a different file than module.conf?

---

### Post by cylon359 on 2005-12-03
[QUOTE=blakken]this stuff seams really  interesting but the module.conf in ubuntu doesn't exist !is there any way to configure in a different file than module.conf?[/QUOTE]

I have a similar model to you:

Bus 003 Device 002: ID 041e:4036 Creative Technology, Ltd Webcam Live

And got it working using this guide:

[http://www.macewan.org/2005/08/07/ubuntu-creative-live-webcam/](http://www.macewan.org/2005/08/07/ubuntu-creative-live-webcam/)

I had to use the driver listed in the guide (and not a more recent one), since they cause my box to freeze...

Hope that helps.

---

### Post by blakken on 2005-12-04
I think it's really gonna help me ,thank you very much!
I already tried and here is the error I got;
slayer@ubuntu:~/debian package/spca5xx-20050701$ make clean
rm -r -f drivers/usb/*.o drivers/usb/.spcadecoder.o.cmd \
drivers/usb/.spca5xx.o.cmd  *.o *.ko *.mod.* .[a-z]* core *.i
slayer@ubuntu:~/debian package/spca5xx-20050701$ make
   Building SPCA5XX driver for 2.5/2.6 kernel.
   Remember: you must have read/write access to your kernel source tree.
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/slayer/debian package/spca5xx-20050701 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-10-686'
make[1]: *** No rule to make target `package/spca5xx-20050701'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-10-686'
make: *** [default] Error 2
slayer@ubuntu:~/debian package/spca5xx-20050701$ sudo make install
mkdir -p /lib/modules/`uname -r`/kernel/drivers/usb/media/
rm -f /lib/modules/`uname -r`/kernel/drivers/usb/media/spca50x.ko
rm -f /lib/modules/`uname -r`/kernel/drivers/usb/media/et61x.ko
install -c -m 0644 spca5xx.ko /lib/modules/`uname -r`/kernel/drivers/usb/media/
install: cannot stat `spca5xx.ko': No such file or directory

what's wrong with it do you have any idea?
:(

---

### Post by cylon359 on 2005-12-04
When you run "make", try "sudo make" as you need read/write access to the header headers.

---

### Post by blakken on 2005-12-04
same message!
slayer@ubuntu:~/debian package/spca5xx-20050701$ sudo make
Password:
   Building SPCA5XX driver for 2.5/2.6 kernel.
   Remember: you must have read/write access to your kernel source tree.
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/slayer/debian package/spca5xx-20050701 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-10-686'
make[1]: *** No rule to make target `package/spca5xx-20050701'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-10-686'
make: *** [default] Error 2
slayer@ubuntu:~/debian package/spca5xx-20050701$

---

### Post by tseliot on 2005-12-05
[QUOTE=blakken]same message!
slayer@ubuntu:~/debian package/spca5xx-20050701$ sudo make
Password:
   Building SPCA5XX driver for 2.5/2.6 kernel.
   Remember: you must have read/write access to your kernel source tree.
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/slayer/debian package/spca5xx-20050701 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.12-10-686'
make[1]: *** No rule to make target `package/spca5xx-20050701'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.12-10-686'
make: *** [default] Error 2
slayer@ubuntu:~/debian package/spca5xx-20050701$[/QUOTE]

Try with a real root account:
First off set your root password:
sudo passwd root
(and set the root password)

Then become root
```
su
```
and try to compile (without using sudo)

---

