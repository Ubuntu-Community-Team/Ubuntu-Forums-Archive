---
title: "Howto: Belkin N Wireless USB Adapter (F5D8053) Native Driver"
date: 2010-01-16
forum: Networking &amp; Wireless
---

### Post by M1GEO on 2010-01-16
**Introduction**
I searched around for some time trying to get an explanation on how to get the Belkin N Wireless USB Adapter (F5D8053) to work in Ubuntu 9.10 (karmic).  I had tried several times to get the native ralink driver working, but to no avail.  This afternoon I managed it, and so I thought I would share what I'd learned, as there seemed to a good few others with similar problems.

**Get the driver from Ralink**
Visit **[http://www.ralink.com.tw/support.php?s=2]("http://www.ralink.com.tw/support.php?s=2")** and download ***RT2870USB(RT2870/RT2770)***.  The version I used was *2.3.0.0*.  Extract the downloaded driver (*RT2870_LinuxSTA_V2.3.0.0.tar.tar.bz2*) and cd into the directory:
```

george@transistor:~$ tar xfj RT2870_LinuxSTA_V2.3.0.0.tar.tar.bz2 
george@transistor:~$ cd RT2870_LinuxSTA_V2.3.0.0/

```

**Configure the Driver**
Next we must configure the driver, as explained in *README_STA*:
```

george@transistor:~/RT2870_LinuxSTA_V2.3.0.0$ nano os/linux/config.mk

```

We must edit two options - Find these two options:
```

HAS_WPA_SUPPLICANT=n
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n

```

... and change them to
```

HAS_WPA_SUPPLICANT=y
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y

```

Use CTRL+X to exit, answering Y to save changes, and ENTER to use the original filename.

**Compile & Install the Driver**
Next I compiled the driver.  You will need to install build-essential and kernel headers.  Im pretty sure thats all you need, but I am unsure.  I had already installed them a long time ago.
```

george@transistor:~/RT2870_LinuxSTA_V2.3.0.0$ sudo apt-get install build-essential linux-headers-generic
george@transistor:~/RT2870_LinuxSTA_V2.3.0.0$ make

```

Once make finishes (if it errors, you will need to fix this first of course - it compiled first time for me) you need to install the drivers.  This must be done as root, and is done as follows:
```

george@transistor:~/RT2870_LinuxSTA_V2.3.0.0$ sudo make install
[sudo] password for george: <USER PASSWORD HERE>

```

**Blacklist the old drivers & force use of the new ones**
To force the use of the compiled driver, called rt2870sta, you need to blacklist the ones loaded Karmic as default.  To do this, enter the following command:
```

george@transistor:~$ sudo nano /etc/modprobe.d/blacklist-rtusb.conf

```

This opens the nano text editor as before.  Add the following to the file /etc/modprobe.d/blacklist-rtusb.conf
```

# Blacklist the default usb drivers for rslink card
blacklist rt2500usb
blacklist rt2800usb

```
Use CTRL+X to exit, answering Y to save changes, and ENTER to use the original filename.

**Reboot**
The simplest thing to do at this point is reboot.  If you know what you're doing, you can easily use modprobe to remove the default modules and to insert the newly compiled module into the kernel.  Something like the below:

```

modprobe -r rt2500usb rt2800usb
modprobe -i rt2870sta

```

**It works :)**
```

george@transistor:~$ lsmod | grep rt2870
Module                  Size  Used by
rt2870sta             624696  1 

```

---

### Post by viperjed1970 on 2010-01-16
Wow...I'm new to Linux and have been trying to get my Belkin usb wireless adapter to work with Linux Mint 8.  Finally found this thread.  All other threads I read required some knowledge of Linux that I haven't absorbed yet.  This one is in "English" and got me working in 5 minutes.  Thank you very much!

---

### Post by ljerabek on 2010-05-03
The driver is almost always there on the file system so there is no need to download it.

The really easy way around this is to ensure that the correct driver is loaded and installed. Run the following...

test@test:~$ sudo modprobe -l | grep rt28[67].*

**Your output should show these in the output**

kernel/drivers/staging/rt2860/rt2860sta.ko
kernel/drivers/staging/rt2870/rt2870sta.ko

If they are not in the output you should check to see if they are on your system.

test@test:~$ sudo find /* -name "rt28[67]*"

If those ko files are located on your system you should see somthing like the following:

/lib/firmware/rt2860.bin
/lib/firmware/rt2870.bin
/lib/modules/2.6.31-21-generic/kernel/drivers/staging/rt2860
/lib/modules/2.6.31-21-generic/kernel/drivers/staging/rt2860/rt2860sta.ko
/lib/modules/2.6.31-21-generic/kernel/drivers/staging/rt2870
/lib/modules/2.6.31-21-generic/kernel/drivers/staging/rt2870/rt2870sta.ko
/lib/modules/2.6.32-21-generic/kernel/drivers/staging/rt2860
/lib/modules/2.6.32-21-generic/kernel/drivers/staging/rt2860/rt2860sta.ko
/lib/modules/2.6.32-21-generic/kernel/drivers/staging/rt2870
/lib/modules/2.6.32-21-generic/kernel/drivers/staging/rt2870/rt2870sta.ko
/usr/src/linux-headers-2.6.32-21/drivers/staging/rt2860
/usr/src/linux-headers-2.6.32-21/drivers/staging/rt2870
/usr/src/linux-headers-2.6.32-21-generic/include/config/rt2860.h
/usr/src/linux-headers-2.6.32-21-generic/include/config/rt2870.h

Install the ko files under:
/lib/modules/2.6.32-21-generic/kernel/drivers/staging/rt2870/rt2870sta.ko
/lib/modules/2.6.32-21-generic/kernel/drivers/staging/rt2860/rt2860sta.ko

sudo insmod /lib/modules/2.6.32-21-generic/kernel/drivers/staging/rt2870/rt2870sta.ko

sudo insmod /lib/modules/2.6.32-21-generic/kernel/drivers/staging/rt2860/rt2860sta.ko

sudo depmod -a

You are almost done... just check what modules are currently loaded for your belkin.

test@test:~$ sudo lsmod | grep rt28*

If you have "rt2800usb" as a result you will need to black list that driver

sudo gedit /etc/modprobe.d/blacklist.conf

Goto the bottom of the file and add the following line and save the file:

blacklist rt2800usb

Now reboot and you should be all done.

---

### Post by Chong112193 on 2010-06-24
I am a total noob to Linux. I found this thread and read thru it after starting my own thread asking how to do exactly what you said to do. However, never having work with linux other then Downloading and installing it I had know idea what you were trying to tell me to do. So i referenced this thread in mine and got the help i needed. So if you read this thread and don't understand what to do. Go to [http://ubuntuforums.orgshowthread.php?t=1515837](http://ubuntuforums.orgshowthread.php?t=1515837) It is explained in the simplest form possible and it works Great!  Thank you so much for this information. I couldn't have connected with out this thread.

Chong

---

### Post by Lazarus13 on 2010-07-12
Ok, so I've been trying to get this stupid adapter working since I don't know when. I thought that with the release of Lucid that a lot of problems would clear up by themselves (this was the case with my laptop). So I've done everything in this thread.

I used this command [la@la-desktop:~$ sudo modprobe -l | grep rt28[67].*] and got the following:
kernel/drivers/staging/rt2860/rt2860sta.ko
kernel/drivers/net/wireless/rt2870sta.ko

So I thought that I might have something wrong, so I continued to use the following commands as instructed in the previous posts:

la@la-desktop:~$ sudo insmod /lib/modules/2.6.32-21-generic/kernel/drivers/staging/rt2870/rt2870sta.ko
la@la-desktop:~$ sudo insmod /lib/modules/2.6.32-21-generic/kernel/drivers/staging/rt2860/rt2860sta.ko
la@la-desktop:~$ sudo depmod -a
la@la-desktop:~$ sudo lsmod | grep rt28*
rt2860sta             481561  0 
rt2870sta             461811  0 

I rebooted, nothing. My adapter usually shows a blinking light when it's on and connected, but it doesn't even register that it's on in Ubuntu. I don't have any internet on the ubuntu side of my computer and I don't know what to do. I'm not sure if this is significant at all, but when I ran this command:
george@transistor:~/RT2870_LinuxSTA_V2.3.0.0$ sudo apt-get install build-essential linux-headers-generic
It said that there was no build-essentials file to install. I'm not sure if this is on account of me not having internet in ubuntu or what. If this is the problem, then can someone please give me a file so I can install build-essentials? I've tried so hard to get this to work and nothing seems to be working. I'm dead-set on getting Ubuntu to work. I really like the look and feel of the OS and I would love using it.

Any help would be greatly appreciated.

---

### Post by bcatt on 2010-07-15
worked perfect, thanks!

---

### Post by RAI1986 on 2011-04-27
I'm having trouble with this still. After inserting the make command I get:

> bobby@bobby-VGC-RB40:~/RT2870_Linux_STA_v2.4.0.1$ make
make -C tools
make[1]: Entering directory `/home/bobby/RT2870_Linux_STA_v2.4.0.1/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/bobby/RT2870_Linux_STA_v2.4.0.1/tools'
/home/bobby/RT2870_Linux_STA_v2.4.0.1/tools/bin2h
cp -f os/linux/Makefile.6 /home/bobby/RT2870_Linux_STA_v2.4.0.1/os/linux/Makefile
make -C /lib/modules/2.6.35-28-generic/build SUBDIRS=/home/bobby/RT2870_Linux_STA_v2.4.0.1/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-28-generic'
  CC [M]  /home/bobby/RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.o
/home/bobby/RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c: In function ‘RTMPAllocUsbBulkBufStruct’:
/home/bobby/RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:52: error: implicit declaration of function ‘usb_buffer_alloc’
/home/bobby/RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:52: warning: assignment makes pointer from integer without a cast
/home/bobby/RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c: In function ‘RTMPFreeUsbBulkBufStruct’:
/home/bobby/RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:78: error: implicit declaration of function ‘usb_buffer_free’
/home/bobby/RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c: In function ‘RTMPFreeTxRxRingMemory’:
/home/bobby/RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:234: warning: passing argument 3 of ‘RTMPFreeUsbBulkBufStruct’ from incompatible pointer type
/home/bobby/RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:62: note: expected ‘UCHAR **’ but argument is of type ‘struct __TX_BUFFER **’
/home/bobby/RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:241: warning: passing argument 3 of ‘RTMPFreeUsbBulkBufStruct’ from incompatible pointer type
/home/bobby/RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:62: note: expected ‘UCHAR **’ but argument is of type ‘struct __TX_BUFFER **’
/home/bobby/RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:278: warning: passing argument 3 of ‘RTMPFreeUsbBulkBufStruct’ from incompatible pointer type
/home/bobby/RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:62: note: expected ‘UCHAR **’ but argument is of type ‘struct __HTTX_BUFFER **’
/home/bobby/RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c: In function ‘NICInitTransmit’:
/home/bobby/RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:507: warning: passing argument 3 of ‘RTMPFreeUsbBulkBufStruct’ from incompatible pointer type
/home/bobby/RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:62: note: expected ‘UCHAR **’ but argument is of type ‘struct __TX_BUFFER **’
/home/bobby/RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c: In function ‘RTMPAllocTxRxRingMemory’:
/home/bobby/RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:566: warning: passing argument 3 of ‘RTMPAllocUsbBulkBufStruct’ from incompatible pointer type
/home/bobby/RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:34: note: expected ‘VOID **’ but argument is of type ‘struct __HTTX_BUFFER **’
/home/bobby/RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:596: warning: passing argument 3 of ‘RTMPAllocUsbBulkBufStruct’ from incompatible pointer type
/home/bobby/RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:34: note: expected ‘VOID **’ but argument is of type ‘struct __TX_BUFFER **’
/home/bobby/RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:610: warning: passing argument 3 of ‘RTMPAllocUsbBulkBufStruct’ from incompatible pointer type
/home/bobby/RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:34: note: expected ‘VOID **’ but argument is of type ‘struct __TX_BUFFER **’
/home/bobby/RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:628: warning: passing argument 3 of ‘RTMPAllocUsbBulkBufStruct’ from incompatible pointer type
/home/bobby/RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.c:34: note: expected ‘VOID **’ but argument is of type ‘UCHAR **’
make[2]: *** [/home/bobby/RT2870_Linux_STA_v2.4.0.1/os/linux/../../common/cmm_mac_usb.o] Error 1
make[1]: *** [_module_/home/bobby/RT2870_Linux_STA_v2.4.0.1/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-28-generic'
make: *** [LINUX] Error 2

Should I move onto install or fix the errors? I'm new to Ubuntu, please help.

---

### Post by jungle man on 2011-09-29
:o 

It worked out kind of smoothly... but what happened to my original built in wanl0 ? if I check on ifconfig I only get eth0 (ethernet) and lo (local loopback)
before I could see also wanl0 (as internal wirelessG) and wanl1 (as USB wirlessN)
Now I only see wanl0 as USB wirlessN but I've lost the internal one.

In any case it works for me as my internet access is working on 802.11N but my Intranet is still in 802.11G and I can't access it anymore.

Can you tell me how to reverse what we did so far?

Regards

---

