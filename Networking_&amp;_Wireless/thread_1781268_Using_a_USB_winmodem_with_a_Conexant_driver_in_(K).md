---
title: "Using a USB winmodem with a Conexant driver in (K)Ubuntu 11.04 (Natty)"
date: 2011-06-13
forum: Networking &amp; Wireless
---

### Post by Ganton on 2011-06-13
With the information given by Diaco, Lamp20, Shizeon, Backu and the writers of [http://help.ubuntu.com/community/DialupModemHowto/Conexant](http://help.ubuntu.com/community/DialupModemHowto/Conexant) I have used a USB winmodem with a conexant driver in (K)Ubuntu 11.04 (Natty).

When I plugged that modem, I executed ```
lsusb
``` and it said:
> [...]
Bus 006 Device 002: ID 0572:1300 Conexant Systems (Rockwell), Inc. SoftK56 Data Fax Voice CARP
[...]
so I knew that the HSF modem was recognized by the system.

As I had a previous internet connection, I upgraded the system 
```
sudo apt-get update && sudo apt-get dist-upgrade
```

I checked that I had no previous Conexant drivers installed. For example: I executed "ls /usr/sbin/hsfconfig", and it said that that file did not exist; if it existed I would have thought that something was still installed.

I made sure that I had gcc prepared, executing
```
sudo apt-get install gcc
```

Then I executed those steps told there:
```
sudo -s
cd /lib/modules/$(uname -r)/build/include/linux
ln -s ../generated/utsrelease.h
ln -s ../generated/autoconf.h
exit

```

I prepared the files for the driver compilation, executing
```
mkdir ~/conexant_modem
cd ~/conexant_modem

```
and if I had a 64-bit operating system I executed
```

wget http://linux.dell.com/files/ubuntu/hardy/modem-drivers/hsf/hsfmodem-7.68.00.09x86_64oem.tar.gz
tar xzf hsfmodem-7.68.00.09x86_64oem.tar.gz
wget http://www.bargweb.net/images/2009/november/hsfmodem-7.80.02.05-DiacoEdition.zip
unzip hsfmodem-7.80.02.05-DiacoEdition.zip
cp -a hsfmodem-7.80.02.05-DiacoEdition/modules/imported/include/framewrk.h hsfmodem-7.68.00.09x86_64oem/modules/imported/include/framewrk.h
cp -a hsfmodem-7.80.02.05-DiacoEdition/modules/imported/include/osservices.h hsfmodem-7.68.00.09x86_64oem/modules/imported/include/osservices.h

```
else, if I had a 32-bit operating system I executed
```

wget http://linux.dell.com/files/ubuntu/hardy/modem-drivers/hsf/hsfmodem-7.68.00.09oem.tar.gz
tar xzf hsfmodem-7.68.00.09oem.tar.gz
wget http://www.bargweb.net/images/2009/november/hsfmodem-7.80.02.05-DiacoEdition.zip
unzip hsfmodem-7.80.02.05-DiacoEdition.zip
cp -a hsfmodem-7.80.02.05-DiacoEdition/modules/imported/include/framewrk.h hsfmodem-7.68.00.09oem/modules/imported/include/framewrk.h
cp -a hsfmodem-7.80.02.05-DiacoEdition/modules/imported/include/osservices.h hsfmodem-7.68.00.09oem/modules/imported/include/osservices.h

```
*A note for the curious ones: those "framewrk.h" and "osservices.h" files were the different ones between the directories "hsfmodem-7.68.00.09oem/modules/imported" and "hsfmodem-7.80.02.05-DiacoEdition/modules/imported"*.

If I had a 64-bit operating system I executed
```

wget http://www.linuxant.com/drivers/hsf/full/archive/hsfmodem-7.80.02.06x86_64full/hsfmodem-7.80.02.06x86_64full.tar.gz

```
else, if I had a 32-bit operating system I executed
```

wget http://www.linuxant.com/drivers/hsf/full/archive/hsfmodem-7.80.02.06full/hsfmodem-7.80.02.06full.tar.gz

```

*A note for the curious ones: that file was the newest one in [http://www.linuxant.com/drivers/hsf/full/downloads.php](http://www.linuxant.com/drivers/hsf/full/downloads.php) *

And then, if I had a 64-bit operating system I executed
```

tar xzf hsfmodem-7.80.02.06x86_64full.tar.gz
rm -r hsfmodem-7.80.02.06x86_64full/modules/imported
cp -R hsfmodem-7.68.00.09x86_64oem/modules/imported hsfmodem-7.80.02.06x86_64full/modules/
cp -R hsfmodem-7.68.00.09x86_64oem/modules/imported hsfmodem-7.80.02.06x86_64full/modules/

```
else, if I had a 32-bit operating system I executed
```

tar xzf hsfmodem-7.80.02.06full.tar.gz
rm -r hsfmodem-7.80.02.06full/modules/imported
cp -R hsfmodem-7.68.00.09oem/modules/imported hsfmodem-7.80.02.06full/modules/
cp -R hsfmodem-7.68.00.09oem/modules/imported hsfmodem-7.80.02.06full/modules/

```

The next step was to clean the present directory.

If I had a 64-bit operating system I executed
```

rm -rf hsfmodem-7.68.00.09x86_64oem
rm -rf hsfmodem-7.80.02.05-DiacoEdition
rm hsfmodem-7.68.00.09x86_64oem.tar.gz
rm hsfmodem-7.80.02.05-DiacoEdition.zip
rm hsfmodem-7.80.02.06x86_64full.tar.gz

```
else, if I had a 32-bit operating system I executed
```

rm -rf hsfmodem-7.68.00.09oem
rm -rf hsfmodem-7.80.02.05-DiacoEdition
rm hsfmodem-7.68.00.09oem.tar.gz
rm hsfmodem-7.80.02.05-DiacoEdition.zip
rm hsfmodem-7.80.02.06full.tar.gz

```

Then I had to change some files to adapt them to work with the 2.6.38 kernel. 
If I had a 64-bit operating system I executed
```

cd hsfmodem-7.80.02.06x86_64full
xdg-open modules/GPL/serial_cnxt.c

```
else, if I had a 32-bit operating system I executed
```

cd hsfmodem-7.80.02.06full
xdg-open modules/GPL/serial_cnxt.c

```
and then a text editor was executed. I searched for the string
```
#ifndef FOUND_UART_REGISTER_PORT
```
Below I found the string
```
static DECLARE_MUTEX(cnxt_port_sem);
```
and I deleted that string, and wrote there
```
static DEFINE_SEMAPHORE(cnxt_port_sem);
```

I executed
```

xdg-open modules/osdiag.c

```
and then a text editor was executed. I searched for the string
```
.owner	= THIS_MODULE,
```
Below I found the string
```
.ioctl	= diag_ioctl,
```
and I deleted that string, and wrote there
```
.compat_ioctl = diag_ioctl,
```
    
I executed
```

xdg-open modules/osnvm.c

```
and then a text editor was executed. I searched for the string
```
static LIST_HEAD(nvm_newinst_list);
```
Below I found the string
```
static DECLARE_MUTEX(nvmelem_writelist_sem);
```
and I deleted that string, and wrote there
```
static DEFINE_SEMAPHORE(nvmelem_writelist_sem);
```

*A note for the curious ones: the source of those changes in those files was [http://www.openmamba.org/showfile.html?file=/pub/openmamba/devel/patches/hsfmodem-7.80.02.06-kernel-2.6.37.patch](http://www.openmamba.org/showfile.html?file=/pub/openmamba/devel/patches/hsfmodem-7.80.02.06-kernel-2.6.37.patch)*

And finally...
If I had a 64-bit operating system I executed
```

cd hsfmodem-7.80.02.06x86_64full
sudo make install
sudo hsfconfig

```
else, if I had a 32-bit operating system I executed
```

cd hsfmodem-7.80.02.06full
sudo make install
sudo hsfconfig

```

It asked "Where is the linux source build directory that matches your running kernel?", then I simply pressed the return key to accept the default answer. I also accepted the default answer in other questions.

I executed
```

dmesg

```
and at the end I saw
```

    [59190.782005] hsfengine: module license 'see LICENSE file distributed with driver' taints kernel.
    [59190.782011] Disabling lock debugging due to kernel taint
    [59192.564398] ttySHSF0 at MMIO 0x0 (irq = 0) is a Conexant HSF softmodem (USB-0572:1300)
    [59192.600274] usbcore: registered new interface driver hsfusbcd2
    [59194.416241] usbcore: deregistering interface driver hsfusbcd2
    [59194.600064] usb 6-1: reset full speed USB device using uhci_hcd and address 2
    [59194.811746] cnxthsf_DcpDestroy: units still active, waiting..
    [59194.811764] cnxthsf_DcpDestroy: units still active, waiting..
    [59194.811778] cnxthsf_DcpDestroy: units still active, waiting..
    [59196.967466] ttySHSF0 at MMIO 0x0 (irq = 0) is a Conexant HSF softmodem (USB-0572:1300)
    [59196.994150] usbcore: registered new interface driver hsfusbcd2

``` 
which meant, among other things, that the USB modem was detected at /dev/ttySHSF0, so I could use kppp (for example) and configure it specifying that the modem was at /dev/ttySHSF0.

Note: as they said in [https://help.ubuntu.com/community/DialupModemHowto/Conexant](https://help.ubuntu.com/community/DialupModemHowto/Conexant): "*do not delete or move the source tree* [in our case: ~/conexant_modem] *from your system after these steps, it will be required to uninstall and patch the driver.*"

Note: if you find any problem, or want to make any change to the method, please write it in this thread, so we can have a proper final document.

---

### Post by Starks on 2011-07-17
```
driver version 7.68.00.09oem
(cd /lib/modules/3.0.0-5-generic/build && make "CNXT_KERNELSRC=/lib/modules/3.0.0-5-generic/build" "M=/usr/lib/hsfmodem/modules" "CC=gcc" clean)
make[1]: Entering directory `/usr/src/linux-headers-3.0.0-5-generic'
make[1]: Leaving directory `/usr/src/linux-headers-3.0.0-5-generic'
(cd /lib/modules/3.0.0-5-generic/build && make "CNXT_KERNELSRC=/lib/modules/3.0.0-5-generic/build" "M=/usr/lib/hsfmodem/modules/GPL/hda" "CC=gcc" "HDA_CFLAGS=-DFOUND_KZALLOC  -DFOUND_TLV   -DFOUND_IRQ_HANDLER_T -DFOUND_DELAYED_WORK  -DFOUND_NO_CTL_ELEM_RW" clean)
make[1]: Entering directory `/usr/src/linux-headers-3.0.0-5-generic'
make[1]: Leaving directory `/usr/src/linux-headers-3.0.0-5-generic'
rm -rf *.o GPL/*.o *.ko GPL/*.ko *.mod.c GPL/*.mod.c .*.cmd GPL/.*.cmd .tmp_versions .tmp_versions  /lib/modules/3.0.0-5-generic/build/.tmp_versions/hsfosspec.mod  /lib/modules/3.0.0-5-generic/build/.tmp_versions/hsfserial.mod  /lib/modules/3.0.0-5-generic/build/.tmp_versions/hsfengine.mod  /lib/modules/3.0.0-5-generic/build/.tmp_versions/hsfpcibasic2.mod  /lib/modules/3.0.0-5-generic/build/.tmp_versions/hsfpcibasic3.mod  /lib/modules/3.0.0-5-generic/build/.tmp_versions/hsfmc97ich.mod  /lib/modules/3.0.0-5-generic/build/.tmp_versions/hsfmc97via.mod  /lib/modules/3.0.0-5-generic/build/.tmp_versions/hsfmc97ali.mod  /lib/modules/3.0.0-5-generic/build/.tmp_versions/hsfmc97ati.mod  /lib/modules/3.0.0-5-generic/build/.tmp_versions/hsfmc97sis.mod  /lib/modules/3.0.0-5-generic/build/.tmp_versions/hsfsoar.mod Modules.symvers GPL/hda/Modules.symvers Module.symvers GPL/hda/Module.symvers modules.order GPL/hda/modules.order Module.markers GPL/hda/Module.markers
(cd /lib/modules/3.0.0-5-generic/build && make "CNXT_KERNELSRC=/lib/modules/3.0.0-5-generic/build" "M=/usr/lib/hsfmodem/modules" "CC=gcc" modules)
make[1]: Entering directory `/usr/src/linux-headers-3.0.0-5-generic'
  CC [M]  /usr/lib/hsfmodem/modules/mod_engine.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_hda.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_mc97ali.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_mc97ati.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_mc97ich.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_mc97sis.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_mc97via.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_osspec.o
  CC [M]  /usr/lib/hsfmodem/modules/osservices.o
In file included from /usr/lib/hsfmodem/modules/osservices.c:20:0:
/usr/lib/hsfmodem/modules/GPL/oscompat.h:201:57: error: 'SPIN_LOCK_UNLOCKED' undeclared here (not in a function)
/usr/lib/hsfmodem/modules/osservices.c:51:28: fatal error: linux/smp_lock.h: No such file or directory
compilation terminated.
make[2]: *** [/usr/lib/hsfmodem/modules/osservices.o] Error 1
make[1]: *** [_module_/usr/lib/hsfmodem/modules] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.0.0-5-generic'
make: *** [all] Error 2
```

I'm going to see if following the updated Arch PKGBUILD helps.

---

### Post by Ganton on 2011-07-17
> **Starks said:**
> ```
[...]
make[1]: Leaving directory `/usr/src/linux-headers-3.0.0-5-generic'
make: *** [all] Error 2
```

I'm going to see if following the updated Arch PKGBUILD helps.
This thread is about "Using a USB winmodem with a Conexant driver in (K)Ubuntu 11.04 (Natty)". Using the version 3.0.0 of the Linux kernel is not what expected :-)

---

### Post by chiaseth on 2011-12-30
> **Ganton said:**
> This thread is about "Using a USB winmodem with a Conexant driver in (K)Ubuntu 11.04 (Natty)". Using the version 3.0.0 of the Linux kernel is not what expected :-)

Well, I had a fax to send out, and only 3.0.0 kernel machines to work with, so I slugged through making this work for the 3.0.0 Linux kernel, for use on Ubuntu 11.10. Here's what I had to do, beyond what was originally specified above:

1. In modules/osservices.c, use the new mutex.h header, define a mutex, and replace all instances of lock_kernel() and unlock_kernel():

```
- #include <linux/smp_lock.h>
+ #include <linux/mutex.h>
+ DEFINE_MUTEX(os_mutex);

- lock_kernel();
+ mutex_lock(&os_mutex);

- unlock_kernel();
+ mutex_unlock(&os_mutex);
```

2. In multiple files (in modules and modules/GPL), replace SPIN_LOCK_UNLOCKED declarations:

```
- static spinlock_t dcp_lock = SPIN_LOCK_UNLOCKED;
+ static DEFINE_SPINLOCK(dcp_lock);
```

or

```
- static spinlock_t atomic_lock __attribute__((unused)) = SPIN_LOCK_UNLOCKED;
+ static DEFINE_SPINLOCK(atomic_lock);
```

The files I found that in were:
[LIST]
[*]modules/osdcp.c
[*]modules/osdiag.c
[*]modules/osfloat.c
[*]modules/osservices.c
[*]modules/GPL/oscompat.h
[/LIST]

...and then run 'sudo hsfconfig' again, and it builds! I tested it thereafter with efax-gtk, in which I used "ttySHSF0" as the Serial Device, as was specified by hsfconfig. Your device may have a different name.

Hope this helps! 
--Seth

---

### Post by Ganton on 2012-01-02
> **chiaseth said:**
> Hope this helps! 
--Seth
Yes! Your writings helped me to make the driver compile and execute in the new 11.10 version ("Oneiric"). I'll try the driver more times. If it works OK, I'll create a new page, particular for the 11.10 version ("Oneiric").

Thanks!

---

### Post by Ganton on 2012-01-02
Done! The new page, with the steps for (K)Ubuntu 11.10 (Oneiric Ocelot), is [http://ubuntuforums.org/showthread.php?t=1903439](http://ubuntuforums.org/showthread.php?t=1903439)

---

