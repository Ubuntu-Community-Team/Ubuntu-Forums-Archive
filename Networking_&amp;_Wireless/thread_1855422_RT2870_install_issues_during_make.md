---
title: "RT2870 install issues during make"
date: 2011-10-06
forum: Networking &amp; Wireless
---

### Post by kelwynsa8 on 2011-10-06
Hi,

I have an ASUS N13 USB card. I have it working using the native kernel one, however this doesn't work completely. For some reason its only connecting via G (not N). So my max attainable is 54Mb/s.

So I read this post [http://ubuntuforums.org/showthread.php?p=8346399#post8346399](http://ubuntuforums.org/showthread.php?p=8346399#post8346399) and it suggests I edit the .dat file. However, as I have native, I cannot edit the .dat file (unless I'm mistaken?). So I decided to install the drivers off Ralink's site - *2010_0709_RT2870_Linux_STA_v2.4.0.1* 

Now, I edited the config.mk as per [http://ubuntuforums.org/showthread.php?t=1743530](http://ubuntuforums.org/showthread.php?t=1743530) - [http://pastebin.com/RYX2FfD4](http://pastebin.com/RYX2FfD4)

When I execute *make*:

```

/home/kel/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:610:12: warning: passing argument 3 of &#8216;RTMPAllocUsbBulkBufStruct&#8217; from incompatible pointer type
/home/kel/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:34:20: note: expected &#8216;VOID **&#8217; but argument is of type &#8216;struct __TX_BUFFER **&#8217;
/home/kel/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:628:13: warning: passing argument 3 of &#8216;RTMPAllocUsbBulkBufStruct&#8217; from incompatible pointer type
/home/kel/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:34:20: note: expected &#8216;VOID **&#8217; but argument is of type &#8216;UCHAR **&#8217;
make[2]: *** [/home/kel/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.o] Error 1
make[1]: *** [_module_/home/kel/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-8-generic'
make: *** [LINUX] Error 2

```

When I execute *sudo make install*:
```

make -C /home/kel/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/kel/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux'
rm -rf /etc/Wireless/RT2870STA
mkdir /etc/Wireless/RT2870STA
cp /home/kel/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/RT2870STA.dat /etc/Wireless/RT2870STA/.
install -d /lib/modules/2.6.38-8-generic/kernel/drivers/staging/rt2870/
install -m 644 -c rt2870sta.ko /lib/modules/2.6.38-8-generic/kernel/drivers/staging/rt2870/
install: cannot stat `rt2870sta.ko': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/kel/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux'
make: *** [install] Error 2


```

***** Now, this would suggest rt2870sta.ko isn't there. Well, it is.

```

root@kel-desktop:/lib/modules/2.6.38-8-generic/kernel/drivers/staging/rt2870# ls -l
total 492
-rwxrwxrwx 1 root root 502912 2011-04-11 18:47 rt2870sta.ko


```

***** Ok, so it's there, maybe it cant read it? Well I have ran it as root (make && make install). Same error.

***** Maybe the packages for kernel headers aren't installed, or other packages?

Well they are too...

```

root@kel-desktop:~# apt-get install linux-headers-2.6.38-8-generic linux-headers-2.6.38-8 build-essential 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.38-8 is already the newest version.
linux-headers-2.6.38-8-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 23 not upgraded.

```
[B]
So, I'm a bit stumped. It should be working but it isn't, why? [/B]

I've also tried this, with the same results [http://www.cyberciti.biz/tips/linux-install-rt2870-chipset-based-usb-wireless-adapter.html](http://www.cyberciti.biz/tips/linux-install-rt2870-chipset-based-usb-wireless-adapter.html)

Thanks

---

### Post by kelwynsa8 on 2011-10-06
Ok, solved after doing a bit of research.

DO NOT change the contents of Makefile, make sure this bit is left at:

```

ifeq ($(PLATFORM),PC)
# Linux 2.6
LINUX_SRC = /lib/modules/$(shell uname -r)/build
# Linux 2.4 Change to your local setting
#LINUX_SRC = /usr/src/linux-2.4
LINUX_SRC_MODULE = /lib/modules/$(shell uname -r)/kernel/drivers/net/wireless/
CROSS_COMPILE = 
endif

```

Now, the awesome code:
```

make clean
find . -name \*.[ch] -exec grep usb_buffer_alloc "{}" ";" -exec sed -i 's/usb_buffer_alloc/usb_alloc_coherent/g' "{}" ";"
find . -name \*.[ch] -exec grep usb_buffer_free "{}" ";" -exec sed -i 's/usb_buffer_free/usb_free_coherent/g' "{}" ";"
make 
sudo make install

```

Give it a reboot. If it doesn't work you may need to install the mod, make sure you're in the driver make directory, then type:

```

cd os/linux/
insmod rt2870sta.ko

```

---

### Post by Gnobody on 2013-04-09
> **kelwynsa8 said:**
> Ok, solved after doing a bit of research.

DO NOT change the contents of Makefile, make sure this bit is left at:

```

ifeq ($(PLATFORM),PC)
# Linux 2.6
LINUX_SRC = /lib/modules/$(shell uname -r)/build
# Linux 2.4 Change to your local setting
#LINUX_SRC = /usr/src/linux-2.4
LINUX_SRC_MODULE = /lib/modules/$(shell uname -r)/kernel/drivers/net/wireless/
CROSS_COMPILE = 
endif

```

Now, the awesome code:
```

make clean
find . -name \*.[ch] -exec grep usb_buffer_alloc "{}" ";" -exec sed -i 's/usb_buffer_alloc/usb_alloc_coherent/g' "{}" ";"
find . -name \*.[ch] -exec grep usb_buffer_free "{}" ";" -exec sed -i 's/usb_buffer_free/usb_free_coherent/g' "{}" ";"
make 
sudo make install

```

Give it a reboot. If it doesn't work you may need to install the mod, make sure you're in the driver make directory, then type:

```

cd os/linux/
insmod rt2870sta.ko

```

I'm able to compile and make install the drivers without any error but when I reboot no wifi, I get the following error when I try your last step:

sudo insmod  rt2870sta.ko 
insmod: error inserting 'rt2870sta.ko': -1 Device or resource busy

---

### Post by Iowan on 2013-04-09
Closed 18 month-old thread. From Code of Conduct:
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

