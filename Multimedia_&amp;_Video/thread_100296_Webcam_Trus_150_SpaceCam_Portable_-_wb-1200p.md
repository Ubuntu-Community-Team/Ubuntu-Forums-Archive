---
title: "Webcam Trus 150 SpaceCam Portable - wb-1200p"
date: 2005-12-07
forum: Multimedia &amp; Video
---

### Post by Taku on 2005-12-07
Hello there, 

Excuse me if my topic isn't in the right place, but I really didn't know where to post it on the forums ... 

So here's my interogation : is there any hope to get my little cam ( [http://www.trust.com/products/product.aspx?artnr=13405](http://www.trust.com/products/product.aspx?artnr=13405) ) working on ubuntu, and more generally, on linux.

I've already tried to get some informations on google and others, but didn't get any answers to my questions ...

Just hope you'll be able to help me :).

Thanks for your help

---

### Post by jotape99 on 2005-12-07
I've just bought 2 of this webcams. One of them was out of order (don't work under windows), first try to see if the webcam is present on usb:
> lsusb
you must have one line similar to  
> Bus 002 Device 002: ID 093a:2468 Pixart Imaging, Inc.
Bus and Device can be different.


To get it working on ubuntu breezy, I almost follow this how to from arnieboy:
[http://ubuntuforums.org/showthread.php?t=75284](http://ubuntuforums.org/showthread.php?t=75284)

but using the last driver version:
[http://mxhaard.free.fr/spca50x/Download/spca5xx-20051105.tar.gz](http://mxhaard.free.fr/spca50x/Download/spca5xx-20051105.tar.gz)

In this how to, if you don' want to set a password for root, you can link gcc to gcc-3.4
replace the lines
> u
CC=gcc-3.4
export CC
exit
CC=gcc-3.4
export CC
by this

> sudo rm /usr/bin/gcc
sudo ln -s /usr/bin/gcc-3.4 /usr/bin/gcc

Note: If you want to compile your personnal apps with gcc 4, you must restore the link after the driver installation.

And follow:
> wget [http://mxhaard.free.fr/spca50x/Download/spca5xx-20051105.tar.gz](http://mxhaard.free.fr/spca50x/Download/spca5xx-20051105.tar.gz)
tar xvfz spca5xx-20051105.tar.gz
cd spca5xx-20051105
make
If the module is already loaded (try lsmod) remove it:
> sudo modprobe -r spca5xx
install and load module:
> sudo rm -rf /lib/modules/`uname -r`/kernel/drivers/usb/media/spca5xx*
sudo make install
sudo modprobe spca5xx

To load the module at each start of the computer you can add the line 'spca5xx' at the end of file /etc/modules

now you can try the camera with gqcam for example ( if you only have this webcam as video device (no tvcad,..) try this)
> gqcam -v /dev/video0

---

### Post by Titonel on 2006-01-07
Hello Folks,

I also have this webcam (Trust 150 SpaceCam) but no success in installing the spca5xx driver.

I followed the steps entirely but as soon as I enter *make* I get an error:
root@picasso:/usr/src/spca5xx-20060101# make
   Building SPCA5XX driver for 2.5/2.6 kernel.
   Remember: you must have read/write access to your kernel source tree.
make -C /lib/modules/`uname -r`/build SUBDIRS=/usr/src/spca5xx-20060101 CC=gcc-3.4 modules
make: *** /lib/modules/2.6.12-10-k7/build: Arquivo ou diretório não encontrado.  Pare.
make: ** [default] Erro 2

This line, *make: *** /lib/modules/2.6.12-10-k7/build: Arquivo ou diretório não encontrado.  Pare.* says that the file or directory was not found and stops. Of course I cannot proceed with the instalation with this error.

Since I am new to the Linux/Ubuntu world, I'd appreciate any help.

---

### Post by Titonel on 2006-01-07
I managed to find what was going on: a corruption during the installation of the headers was causing the problem. I re-installed them and now the camera works great :D

---

