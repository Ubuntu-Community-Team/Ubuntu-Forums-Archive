---
title: "Using a USB winmodem with a Conexant driver in (K)Ubuntu 11.10 (Oneiric)"
date: 2012-01-02
forum: Networking &amp; Wireless
---

### Post by Ganton on 2012-01-02
With the information given by Diaco, Lamp20, Shizeon, Backu, Chiaseth and the writers of [http://help.ubuntu.com/community/DialupModemHowto/Conexant](http://help.ubuntu.com/community/DialupModemHowto/Conexant) I have used a USB winmodem with a Conexant driver in (K)Ubuntu 11.10 (Oneiric).

Anyway, if I had any big problem with a Conexant modem, I would remember what was written, not about winmodems but about true modems, in [https://help.ubuntu.com/community/DialupModemHowto/Conexant](https://help.ubuntu.com/community/DialupModemHowto/Conexant): *"Note that in general, you can buy a Lucent or Intel (smartlink, or other brand with intel chipset) modem for less than 19.99 US"*.

When I plugged a Conexant modem, I executed ```
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

I checked that I had no previous Conexant drivers installed. For example: I executed 
```
ls /usr/sbin/hsfconfig
```
and it said that that file did not exist; if it existed I would have thought that something was still installed.

I made sure that I had "gcc" and "make" ready, executing
```
sudo apt-get install gcc make
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

Then I had to change some files to adapt them to work with the 3.0.0 version of the Linux kernel. 
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
and then a text editor was launched. I searched for the string
```
#ifndef FOUND_UART_REGISTER_PORT
```
and below I found the string
```
static DECLARE_MUTEX(cnxt_port_sem);
```
I deleted that last string, and wrote there
```
static DEFINE_SEMAPHORE(cnxt_port_sem);
```

and I saved and closed that file. I executed
```

xdg-open modules/osdiag.c

```
and then a text editor was launched. I searched for the string
```
THIS_MODULE,
```
and below I found the string
```
.ioctl    = diag_ioctl,
```
I deleted that string, and wrote there
```
.compat_ioctl = diag_ioctl,
```
    
and I saved and closed that file. I executed
```

xdg-open modules/osnvm.c

```
and then a text editor was launched. I searched for the string
```
static LIST_HEAD(nvm_newinst_list);
```
and below I found the string
```
static DECLARE_MUTEX(nvmelem_writelist_sem);
```
I deleted that last string, and wrote there
```
static DEFINE_SEMAPHORE(nvmelem_writelist_sem);
```

and I saved and closed that file. 

*A note for the curious ones: the source of those changes in those files was [http://www.openmamba.org/showfile.html?file=/pub/openmamba/devel/patches/hsfmodem-7.80.02.06-kernel-2.6.37.patch](http://www.openmamba.org/showfile.html?file=/pub/openmamba/devel/patches/hsfmodem-7.80.02.06-kernel-2.6.37.patch)*

The user named Chiaseth helped telling those steps that I followed, this way:

1. I executed
```

xdg-open modules/osservices.c

```
and then a text editor was launched. I searched for the string
```
#include <linux/smp_lock.h>
```
and I deleted that string, and wrote there
```

#include <linux/mutex.h>
DEFINE_MUTEX(os_mutex);  // Define a mutex

```

In that file I searched for the strings
```
unlock_kernel()
```
replacing all of them with
```
mutex_unlock(&os_mutex)
```

Also, in that file I searched for the strings
```
lock_kernel()
```
replacing all of them with
```
mutex_lock(&os_mutex)
```

and I saved and closed that file.

2. I executed
```

xdg-open modules/osdcp.c

```

In that file I searched for the string
```
static spinlock_t dcp_lock = SPIN_LOCK_UNLOCKED;
```
replacing it with
```
static DEFINE_SPINLOCK(dcp_lock);
```

and I saved and closed that file.

3. I executed
```

xdg-open modules/osdiag.c

```

In that file I searched for the string
```
static spinlock_t diag_lock = SPIN_LOCK_UNLOCKED;
```
replacing it with
```
static DEFINE_SPINLOCK(diag_lock);
```

and I saved and closed that file.

4. I executed
```

xdg-open modules/osfloat.c

```

In that file I searched for the string
```
static spinlock_t fpstates_lock __attribute__((unused)) = SPIN_LOCK_UNLOCKED;
```
replacing it with
```
static DEFINE_SPINLOCK(fpstates_lock);
```

and I saved and closed that file.

5. I executed
```

xdg-open modules/osservices.c

```

In that file I searched for the string
```
static spinlock_t atomic_lock __attribute__((unused)) = SPIN_LOCK_UNLOCKED;
```
replacing it with
```
static DEFINE_SPINLOCK(atomic_lock);
```

and I saved and closed that file.

6. I executed
```

xdg-open modules/GPL/oscompat.h

```

In that file I searched for the string
```
static spinlock_t tqueue_lock __attribute__((unused)) = SPIN_LOCK_UNLOCKED;
```
replacing it with
```
static DEFINE_SPINLOCK(tqueue_lock);
```

and I saved and closed that file.


Finally...
If executed
```

sudo make install
sudo hsfconfig

```

It asked "Where is the linux source build directory that matches your running kernel?", then I simply pressed the return key to accept the default answer. I also accepted the default answer in other questions.

Finally the command reported that
```
The /dev/modem alias (symlink) points to ttySHSF0
```

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
which meant, among other things, that the USB modem was detected at /dev/ttySHSF0.

Note: as they said in [https://help.ubuntu.com/community/DialupModemHowto/Conexant](https://help.ubuntu.com/community/DialupModemHowto/Conexant): "*do not delete or move the source tree* [in our case: ~/conexant_modem] *from your system after these steps, it will be required to uninstall and patch the driver.*"

I launched kppp (for example) and configured a new "connection", specifying that the modem was at /dev/ttySHSF0. You could also use a program like efax-gtk to send faxes through the modem.


**Notes about maintenance:**
[INDENT]If a system upgrade changed the kernel version of my computer, and I could not connect to internet or I saw a general protection fault due to a hsf driver error:
[INDENT]
      I executed
      ```

      sudo hsfconfig --uninstall
      
``` 
      and rebooted the computer (just in case).

      If I had a 64-bit operating system I executed
      ```

      cd ~/conexant_modem/hsfmodem-7.80.02.06x86_64full
      
``` 

      else, if I had a 32-bit operating system I executed
      ```

      cd ~/conexant_modem/hsfmodem-7.80.02.06full
      
``` 

      I executed
      ```

      sudo make clean
      sudo make install
      sudo hsfconfig
      
``` 
      and I accepted the default answer in the questions.
   [/INDENT]   
[/INDENT]   


**Further information**
If you find any problem, or want to make any change to the method, please write it in this thread, so we can all have a proper final document.

---

### Post by altima on 2012-01-25
thank you! this tutorial helped me to install the driver, but the modem was not found during installation or reboot. and I suppose that the problem is that this modem, though based on Conexant chip, is Intel HDA. and when I type hsfconfig -i, it returns the following:

```
Note: HDA support not compiled in the driver

Note: kernel module snd-via82xx-modem overridden by hsfmc97via
Note: kernel module snd-intel8x0m overridden by hsfmc97ich hsfmc97sis
Note: kernel module snd-atiixp-modem overridden by hsfmc97ati

Warning: no device detected by hsf driver - HDA modems may require reboot

Note: **HDA support not compiled in the driver**

Note: kernel module snd-via82xx-modem overridden by hsfmc97via
Note: **kernel module snd-intel8x0m overridden by hsfmc97ich hsfmc97sis**
Note: kernel module snd-atiixp-modem overridden by hsfmc97ati
```
I am not so advanced in linux to tell why it is so. I believe I need to compile HDA support into the driver, but I don't know whether I am right and how to do it. could you please help me with it? thank you!

UPDATE
hm. I visited the site of Linuxant, and it is written there that I need to install the [alsa driver provided by them]("http://www.linuxant.com/alsa-driver/") prior to installing the driver for the HSF modem. and of course, their alsa driver is also for linux 2.6 and on my linux kernel 3.2.1 it returns the same fatal error as the modem driver: smp_lock.h is missing =( I wish I knew how to patch that one, too.

---

### Post by AllGamer on 2012-01-26
Thanks Ganton for the super clear and extensive guide, made the drivers patching a breeze

I wouldn't have been able to figure all that stuff out by myself.

However I'm facing a weird problem with the modem.

Here are few details:
- it was working fine in Ubuntu 10.10
- the **scanmodem** script detected this, which is correct
```

Predictive  diagnostics for card in bus 00:0d.0:
	Modem chipset  detected on
NAME="Communication controller: Rockwell International HSF 56k Data/Fax/Voice/Spkp "
CLASS=0780
PCIDEV=127a:2015
SUBSYS=127a:2015
IRQ=3
IDENT=hsfmodem
Driver=hsfmodem-drivers

 For candidate modem in:  00:0d.0
   0780 Communication controller: Rockwell International HSF 56k Data/Fax/Voice/Spkp 
      Primary device ID:  127a:2015
 Support type needed or chipset:	hsfmodem

```

- it was installed and "*working*" as /dev/ttySHSF0

However the problem is that after it picks up the line, it won't do anything, no normal modem or fax handshake

and it gets locked, or doesn't know how to reset back to normal state after it picks up the line... which will time out and the call drops, but the modem remains open as in on hook with a line that never disconnects

the goal is was to use it with efax-gtk, these are the errors i get from it (it runs fine until it tries to answer a fax)
```

efax-0.9a: 17:50:04 opened /dev/ttySHSF0
efax-0.9a: 17:50:05 using hsfmodem-7.68.00.09oem in class 1
efax-0.9a: 17:50:06 waiting for activity
efax-0.9a: Thu 26 Jan 2012 06:03:20 PM EST activity detected
efax-0.9a: 18:03:25 fax call answered
efax-0.9a: Thu 26 Jan 2012 06:03:38 PM EST Error: timed out after waiting
efax-0.9a: 18:03:43 Warning: timed out after waiting
efax-0.9a: 18:03:47 Error: timed out after command: +FTH=3
efax-0.9a: 18:03:52 Warning: timed out after command: H
efax-0.9a: 18:03:25 sent CSI - answering ID
efax-0.9a: 18:03:43 received CSI - answering ID
efax-0.9a: 18:03:58 sync: dropping DTR
efax-0.9a: 18:04:02 sync: sending escapes
efax-0.9a: 18:04:08 Error: sync: modem not responding
efax-0.9a: 18:04:08 finished - invalid modem response

```

the it keeps looping the error below
```

efax-0.9a: 12:34:40 sync: dropping DTR
efax-0.9a: 12:34:45 sync: sending escapes
efax-0.9a: 12:34:51 Error: sync: modem not responding
efax-0.9a: 12:34:51 finished - no response from modem

```

hsfconfig --info
```

Config for modem unit 0: /dev/ttySHSF0
	Device instance: 0-PCI-127a:2015-127a:2015
	HW revision    : Basic2 2.15 Standard DAA
	HW profile name: hsfpcibasic2
	Current region : USA (T.35 code: 00B5)

The /dev/modem alias (symlink) points to ttySHSF0

```



i have a hunch it's something to do with the drivers, but Ubuntu 11.10 is not very well supported driver wise.

if i can't fix this i'll probably have to roll back to 10.10

---

### Post by TheBuzzer on 2012-01-27
Hi, I followed the steps here and I still avec a error 2!

Here is my log error file:

hsfconfig
Conexant HSF softmodem driver, version 7.68.00.09x86_64oem

If you need assistance or more information, please go to:
        [http://www.linuxant.com/](http://www.linuxant.com/)

When reporting a problem for the first time, please send
us the file generated by "hsfconfig --dumpdiag".

No pre-built modules for: Ubuntu-11.10 linux-3.0.0-14-server x86_64-SMP

Trying to automatically build the driver modules...
(this requires a C compiler and proper kernel sources to be installed)

Where is the linux source build directory that matches your running kernel?
[/lib/modules/3.0.0-14-server/build]
```
Building modules for kernel 3.0.0-14-server, using source directory
/lib/modules/3.0.0-14-server/build. Please wait...

ERROR: Module build failed!
Please examine the log file "/etc/hsfmodem/log/buildlog-20120127132938.txt" to determine why.
root@DELL-SERVER-Marc:~# cat /etc/hsfmodem/log/buildlog-20120127132938.txt
driver version 7.68.00.09x86_64oem
(cd /lib/modules/3.0.0-14-server/build && make "CNXT_KERNELSRC=/lib/modules/3.0.0-14-server/build" "M=/usr/lib/hsfmodem/modules" "CC=gcc" clean)
make[1]: Entering directory `/usr/src/linux-headers-3.0.0-14-server'
make[1]: Leaving directory `/usr/src/linux-headers-3.0.0-14-server'
(cd /lib/modules/3.0.0-14-server/build && make "CNXT_KERNELSRC=/lib/modules/3.0.0-14-server/build" "M=/usr/lib/hsfmodem/modules/GPL/hda" "CC=gcc" "HDA_CFLAGS=-DFOUND_KZALLOC  -DFOUND_TLV   -DFOUND_IRQ_HANDLER_T -DFOUND_DELAYED_WORK  -DFOUND_NO_CTL_ELEM_RW" clean)
make[1]: Entering directory `/usr/src/linux-headers-3.0.0-14-server'
make[1]: Leaving directory `/usr/src/linux-headers-3.0.0-14-server'
rm -rf *.o GPL/*.o *.ko GPL/*.ko *.mod.c GPL/*.mod.c .*.cmd GPL/.*.cmd .tmp_versions .tmp_versions  /lib/modules/3.0.0-14-server/build/.tmp_versions/hsfosspec.mod  /lib/modules/3.0.0-14-server/build/.tmp_versions/hsfserial.mod  /lib/modules/3.0.0-14-server/build/.tmp_versions/hsfengine.mod  /lib/modules/3.0.0-14-server/build/.tmp_versions/hsfpcibasic2.mod  /lib/modules/3.0.0-14-server/build/.tmp_versions/hsfpcibasic3.mod  /lib/modules/3.0.0-14-server/build/.tmp_versions/hsfhda.mod  /lib/modules/3.0.0-14-server/build/.tmp_versions/hsfmc97ich.mod  /lib/modules/3.0.0-14-server/build/.tmp_versions/hsfmc97via.mod  /lib/modules/3.0.0-14-server/build/.tmp_versions/hsfmc97ali.mod  /lib/modules/3.0.0-14-server/build/.tmp_versions/hsfmc97ati.mod  /lib/modules/3.0.0-14-server/build/.tmp_versions/hsfmc97sis.mod  /lib/modules/3.0.0-14-server/build/.tmp_versions/hsfsoar.mod Modules.symvers GPL/hda/Modules.symvers Module.symvers GPL/hda/Module.symvers modules.order GPL/hda/modules.order Module.markers GPL/hda/Module.markers
(cd /lib/modules/3.0.0-14-server/build && make "CNXT_KERNELSRC=/lib/modules/3.0.0-14-server/build" "M=/usr/lib/hsfmodem/modules" "CC=gcc" modules)
make[1]: Entering directory `/usr/src/linux-headers-3.0.0-14-server'
  CC [M]  /usr/lib/hsfmodem/modules/mod_engine.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_hda.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_mc97ali.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_mc97ati.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_mc97ich.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_mc97sis.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_mc97via.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_osspec.o
  CC [M]  /usr/lib/hsfmodem/modules/osservices.o
/usr/lib/hsfmodem/modules/osservices.c: In function 'OsInit':
/usr/lib/hsfmodem/modules/osservices.c:1288:80: warning: format '%d' expects argument of type 'int', but argument 2 has type 'long unsigned int' [-Wformat]
/usr/lib/hsfmodem/modules/osservices.c:1288:80: warning: format '%d' expects argument of type 'int', but argument 3 has type 'long unsigned int' [-Wformat]
/usr/lib/hsfmodem/modules/osservices.c: In function 'cnxthsf_OsRawVPrintf':
/usr/lib/hsfmodem/modules/osservices.c:1321:1: warning: the frame size of 1040 bytes is larger than 1024 bytes [-Wframe-larger-than=]
/usr/lib/hsfmodem/modules/osservices.c: In function 'cnxthsf_OsErrorVPrintf':
/usr/lib/hsfmodem/modules/osservices.c:1370:1: warning: the frame size of 1040 bytes is larger than 1024 bytes [-Wframe-larger-than=]
/usr/lib/hsfmodem/modules/osservices.c: In function 'cnxthsf_OsDebugVPrintf':
/usr/lib/hsfmodem/modules/osservices.c:1397:1: warning: the frame size of 1040 bytes is larger than 1024 bytes [-Wframe-larger-than=]
  CC [M]  /usr/lib/hsfmodem/modules/osstdio.o
  CC [M]  /usr/lib/hsfmodem/modules/osnvm.o
/usr/lib/hsfmodem/modules/osnvm.c:408:8: warning: type defaults to 'int' in declaration of 'DECLARE_SEMAPHORE' [-Wimplicit-int]
/usr/lib/hsfmodem/modules/osnvm.c:408:1: warning: parameter names (without types) in function declaration [enabled by default]
/usr/lib/hsfmodem/modules/osnvm.c: In function 'cnxthsf_NVM_WriteFlushList':
/usr/lib/hsfmodem/modules/osnvm.c:551:11: error: 'nvmelem_writelist_sem' undeclared (first use in this function)
/usr/lib/hsfmodem/modules/osnvm.c:551:11: note: each undeclared identifier is reported only once for each function it appears in
/usr/lib/hsfmodem/modules/osnvm.c: In function 'NVM_WriteFile':
/usr/lib/hsfmodem/modules/osnvm.c:612:11: error: 'nvmelem_writelist_sem' undeclared (first use in this function)
/usr/lib/hsfmodem/modules/osnvm.c: In function 'NVM_ReadFile':
/usr/lib/hsfmodem/modules/osnvm.c:665:11: error: 'nvmelem_writelist_sem' undeclared (first use in this function)
/usr/lib/hsfmodem/modules/osnvm.c: In function 'cnxthsf_NVM_Open':
/usr/lib/hsfmodem/modules/osnvm.c:1077:8: error: 'nvmelem_writelist_sem' undeclared (first use in this function)
/usr/lib/hsfmodem/modules/osnvm.c: At top level:
/usr/lib/hsfmodem/modules/osnvm.c:408:8: warning: 'DECLARE_SEMAPHORE' declared 'static' but never defined [-Wunused-function]
make[2]: *** [/usr/lib/hsfmodem/modules/osnvm.o] Error 1
make[1]: *** [_module_/usr/lib/hsfmodem/modules] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.0.0-14-server'
make: *** [all] Error 2
```

---

### Post by Ganton on 2012-02-26
> **TheBuzzer said:**
> Hi, I followed the steps here and I still have a error 2!

[...]
/usr/lib/hsfmodem/modules/osnvm.c:551:11: error: 'nvmelem_writelist_sem' undeclared (first use in this function)
[...]

It looks like there was an error with that "osnvm.c" file. Can you send a message in this forum, with your "osnvm.c" attached?

---

### Post by vinuuen on 2012-02-27
I am getting the same error. Though I have programming experience I am not seeing why it is not working.  I will attach the file for you. If you need anything else, let me know too.

---

### Post by Ganton on 2012-02-28
> **vinuuen said:**
> I am getting the same error. Though I have programming experience I am not seeing why it is not working.  I will attach the file for you. If you need anything else, let me know too.
Vinuuen, I got your file "osnvm.c", but there, where you wrote
```
static DECLARE_SEMAPHORE(nvmelem_writelist_sem);
```
it should be
```
static DEFINE_SEMAPHORE(nvmelem_writelist_sem);
```
as it is stated in the steps written in this page.

Also, in your "osdiag.c" file, you wrote
```
static DEFINE_SPINLOCK(dcp_lock);
```
but it should be
```
static DEFINE_SPINLOCK(diag_lock);
```
as it is stated in the steps written in this page.

I attach my "serial_cnxt.c" file, since you wrote extra points in yours. If you wish, you could compare my file and yours.

I also attach my "osservices.c" file, since you wrote "mutex_lock" where it should be "mutex_unlock". If you wish, you could compare my file and yours.

At the end, you could try again the 
```
sudo make install
sudo hsfconfig
```
steps and tell us how it went :KS

---

### Post by TheBuzzer on 2012-02-28
> **Ganton said:**
> It looks like there was an error with that "osnvm.c" file. Can you send a message in this forum, with your "osnvm.c" attached?

I had the same problem of vinuuen and did same fix and it works now, thanks!

Marc

---

### Post by vinuuen on 2012-02-28
Thank you very much.
I should have known it wasn't DECLARE that it was DEFINE

---

### Post by Giancy on 2012-03-02
Hi, I am a new user with linux and I am seeking your help in solving a problem with the installation of a modem PCI 02:03.0 Communication controller: Conexant Systems, Inc. SoftV92 Speakerphone Modem with SoftRing SmartSP (rev 01) 
I have followed various guides on the web including this post to install the driver Conexant HSF SoftModem driver, version 7.80.02.06full (hsfmodem_7.80.02.06full_i386.deb) on a linux-i686 (i686)-6.2.38-13-generic-Ubuntu SMP-11.04, before I installed the ALSA driver but when hsfconfig I run it returns the following error message:
```
Conexant HSF softmodem driver, version 7.80.02.06full
  
If you need license keys, assistance or more information, please go to:
    http://www.linuxant.com/
  
When reporting a problem for the first time, please send
us the file generated by "hsfconfig --dumpdiag".
  
Note: HDA support not compiled in the driver
  
Note: kernel module snd-via82xx-modem overridden by hsfmc97via
Note: kernel module snd-intel8x0m overridden by hsfmc97ich hsfmc97sis
Note: kernel module snd-atiixp-modem overridden by hsfmc97ati
```wvdialconf is returned by executing the command the following message:
```
Editing `/etc/wvdial.conf'.

Scanning your serial ports for a modem.

Modem Port Scan<*1>: Scanning ttySHSF0 first, /dev/modem is a link to it.
Modem Port Scan<*1>: SHSF0 
ttyS0<*1>: ATQ0 V1 E1 -- failed with 2400 baud, next try: 9600 baud
ttyS0<*1>: ATQ0 V1 E1 -- failed with 9600 baud, next try: 115200 baud
ttyS0<*1>: ATQ0 V1 E1 -- and failed too at 115200, giving up.
Modem Port Scan<*1>: S1   S2   S3   S4   S5   S6   S7   
Modem Port Scan<*1>: S8   S9   S10  S11  S12  S13  S14  S15  
Modem Port Scan<*1>: S16  S17  S18  S19  S20  S21  S22  S23  
Modem Port Scan<*1>: S24  S25  S26  S27  S28  S29  S30  S31  
Modem Port Scan<*1>: SHSF1 SHSF2 SHSF3 SHSF4 SHSF5 SHSF6 SHSF7 


Sorry, no modem was detected!  Is it in use by another program?
Did you configure it properly with setserial?

Please read the FAQ at http://alumnit.ca/wiki/?WvDial
```you have any suggestions why the modem is not seen by the driver, the system will detect this and a part extracted from the file hsfdiag.txt
 ```
02:03.0 Communication controller: Conexant Systems, Inc. SoftRing SoftV92 Speakerphone Modem with SmartSP (rev 01)
 Subsystem: Conexant Systems, Inc. Device 205d
 Flags: medium devsel, IRQ 19
 Memory at ff9e0000 (32-bit, non-prefetchable) [size = 64K]
 I / O ports at b000 [size = 8]
 Capabilities: [40] Power Management version 2
 Kernel modules: hsfpcibasic2
``` thanks in advance

---

### Post by buntya on 2012-04-08
Hmmm...I followed all the steps Ganton mentioned but still I get this.


$ sudo hsfconfig

/usr/lib/hsfmodem/modules/imported/include/framewrk.h:244:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:265:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:286:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:304:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:322:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:343:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:366:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:388:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:406:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:425:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:447:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:469:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:490:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:508:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:526:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:548:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:570:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
...........

In file included from /usr/lib/hsfmodem/modules/mod_engine.c:10:0:
/usr/lib/hsfmodem/modules/imported/include/osservices.h:356:20: fatal error: string.h: No such file or directory
compilation terminated.
make[2]: *** [/usr/lib/hsfmodem/modules/mod_engine.o] Error 1
make[1]: *** [_module_/usr/lib/hsfmodem/modules] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.0.0-17-generic-pae'
make: *** [all] Error 2

---

### Post by buntya on 2012-04-15
Well forget about having modem working,I lost the audio on my laptop. Lots of uninstalling and installing - pulse audio,alsa-base etc. still no audio back. I guess I have to wait for official release on April 26.

---

### Post by afrodeity on 2012-04-28
If I run hfsconfig

```

/usr/lib/hsfmodem/modules/osservices.c: In function &#8216;cnxt_thread&#8217;:
/usr/lib/hsfmodem/modules/osservices.c:502:2: error: implicit declaration of function &#8216;mutex_unlock_&#8217; [-Werror=implicit-function-declaration]
cc1: some warnings being treated as errors

make[2]: *** [/usr/lib/hsfmodem/modules/osservices.o] Error 1
make[1]: *** [_module_/usr/lib/hsfmodem/modules] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.0.0-17-generic'
make: *** [all] Error 2

```

---

### Post by joops on 2012-05-03
Hallo.

i'm working on dell inspiron 6400 laptop with internal conexant modem on precise. i would like to use the modem for fax.

i tried the steps 

```
wget http://www.linuxant.com/drivers/hsf/full/archive/hsfmodem-7.80.02.04full/hsfmodem-7.80.02.04full.tar.gz 
wget http://linux.dell.com/files/ubuntu/hardy/modem-drivers/hsf/hsfmodem-7.68.00.09oem.tar.gz 

for i in *.tar.gz; do tar -xzf "$i"; done

rm -r hsfmodem-7.80.02.04full/modules/imported  

cp -R hsfmodem-7.68.00.09oem/modules/imported hsfmodem-7.80.02.04full/modules/cd hsfmodem-7.80.02.04full 
sudo make install 
```
untill here all worked fine. but the 
```
sudo hsfconfig 
```
gives
```
sudo hsfconfig
Conexant HSF softmodem driver, version 7.68.00.09oem

If you need assistance or more information, please go to:
	http://www.linuxant.com/

When reporting a problem for the first time, please send
us the file generated by "hsfconfig --dumpdiag".

No pre-built modules for: Ubuntu-12.04 linux-3.2.0-24-generic-pae i686-SMP

Trying to automatically build the driver modules...
(this requires a C compiler and proper kernel sources to be installed)

Where is the linux source build directory that matches your running kernel?

WARNING: missing file /lib/modules/3.2.0-24-generic-pae/build/include/linux/autoconf.h
The cause of this is usually a missing or unconfigured
kernel source tree (and sometimes an incorrect directory or symbolic link).

However, proper /boot/config-3.2.0-24-generic-pae was found.
Would you like to try using it (in a temporary kernel tree)? [yes] 

Unable to prepare temporary kernel tree

First, ensure that the proper kernel source and compiler packages
from your distribution vendor and/or the community are installed.

The Linux kernel can then be reconfigured by running "make menuconfig"
under the kernel source directory (usually /usr/src/linux).

Verify that the proper options for your system are selected.

Then compile and install your new kernel (for more information about
this procedure, see the README file under the kernel source directory),
reboot the system using the new kernel, and re-run "hsfconfig".

```

i'm not very practical on these things.

Somebody could help me

Thanks an best regards

---

### Post by buntya on 2012-05-04
> **buntya said:**
> Well forget about having modem working,I lost the audio on my laptop. Lots of uninstalling and installing - pulse audio,alsa-base etc. still no audio back. I guess I have to wait for official release on April 26.

Upgrade to 12.04 but still no audio. I have had no audio issues on my laptop until I started playing around with conexant. :(

---

### Post by buntya on 2012-05-04
> **buntya said:**
> Upgrade to 12.04 but still no audio. I have had no audio issues on my laptop until I started playing around with conexant. :(


Okay,audio is back after I removed alsa-hda-dkms(alsa-hda-dkms 0.201205021650~precise1) and rebooted. Weirdo.

---

### Post by juberticus on 2012-06-04
Got an error with Ubuntu 12.04 64bit. If someone could help me out with this one. Followed all the steps but I cannot do the hsfconfig because of this error.

Here is the Error:

driver version 7.68.00.09x86_64oem
(cd /lib/modules/3.2.0-24-generic/build && make "CNXT_KERNELSRC=/lib/modules/3.2.0-24-generic/build" "M=/usr/lib/hsfmodem/modules" "CC=gcc" clean)
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-24-generic'
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-24-generic'
(cd /lib/modules/3.2.0-24-generic/build && make "CNXT_KERNELSRC=/lib/modules/3.2.0-24-generic/build" "M=/usr/lib/hsfmodem/modules/GPL/hda" "CC=gcc" "HDA_CFLAGS=-DFOUND_KZALLOC  -DFOUND_TLV   -DFOUND_IRQ_HANDLER_T -DFOUND_DELAYED_WORK  -DFOUND_NO_CTL_ELEM_RW" clean)
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-24-generic'
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-24-generic'
rm -rf *.o GPL/*.o *.ko GPL/*.ko *.mod.c GPL/*.mod.c .*.cmd GPL/.*.cmd .tmp_versions .tmp_versions  /lib/modules/3.2.0-24-generic/build/.tmp_versions/hsfosspec.mod  /lib/modules/3.2.0-24-generic/build/.tmp_versions/hsfserial.mod  /lib/modules/3.2.0-24-generic/build/.tmp_versions/hsfengine.mod  /lib/modules/3.2.0-24-generic/build/.tmp_versions/hsfpcibasic2.mod  /lib/modules/3.2.0-24-generic/build/.tmp_versions/hsfpcibasic3.mod  /lib/modules/3.2.0-24-generic/build/.tmp_versions/hsfhda.mod  /lib/modules/3.2.0-24-generic/build/.tmp_versions/hsfmc97ich.mod  /lib/modules/3.2.0-24-generic/build/.tmp_versions/hsfmc97via.mod  /lib/modules/3.2.0-24-generic/build/.tmp_versions/hsfmc97ali.mod  /lib/modules/3.2.0-24-generic/build/.tmp_versions/hsfmc97ati.mod  /lib/modules/3.2.0-24-generic/build/.tmp_versions/hsfmc97sis.mod  /lib/modules/3.2.0-24-generic/build/.tmp_versions/hsfsoar.mod Modules.symvers GPL/hda/Modules.symvers Module.symvers GPL/hda/Module.symvers modules.order GPL/hda/modules.order Module.markers GPL/hda/Module.markers
(cd /lib/modules/3.2.0-24-generic/build && make "CNXT_KERNELSRC=/lib/modules/3.2.0-24-generic/build" "M=/usr/lib/hsfmodem/modules" "CC=gcc" modules)
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-24-generic'
  CC [M]  /usr/lib/hsfmodem/modules/mod_engine.o
In file included from <command-line>:0:0:
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:244:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:265:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:286:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:304:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:322:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:343:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:366:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:388:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:406:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:425:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:447:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:469:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:490:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:508:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:526:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:548:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:570:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:593:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:614:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:645:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:667:8: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:688:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:712:9: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:736:8: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
/usr/lib/hsfmodem/modules/imported/include/framewrk.h:757:8: error: token ""Framework: Linux SoftK56"" is not valid in preprocessor expressions
make[2]: *** [/usr/lib/hsfmodem/modules/mod_engine.o] Error 1
make[1]: *** [_module_/usr/lib/hsfmodem/modules] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-24-generic'
make: *** [all] Error 2

---

### Post by Ralph L on 2012-06-11
Has anybody got a winmodem (internal not USB) to work on Precise Pangolin 12.04.  I am looking for instructions for that system and the ones here seem to be failing with Precise.

Thanks
Ralph

---

### Post by mbuell on 2012-06-15
I went to the Dell site today to download - and the files were not available from Dell. Has Dell discontinued support for the Linux side of these modems?

On my Thinkpad T60 (used but new to me) the sound and everything is working. I think I will pass on all this work to get the internal modem working. I'm going to spring $25 to get a USB modem from Amazon.

---

### Post by simonrodan on 2012-06-19
Dell has removed the drived from the URL mentioned in this thread.

---

### Post by mbuell on 2012-06-26
Well - thank you to all the posters in this thread who found solutions and tried to find solutions. You did some fine work!

This is not a trivial work-around. My card, and others in this category, is embedded on my sound card in my laptop. Which means I have to get the ALSA driver involved as well. 

However:
1: It seems Dell is no longer supporting the driver that these methods rely on.
2: This is kernel specific, if I understand correctly, and every time my kernel upgrades, the "fix" will have to be redone. 
3: I am running 12.04, and a "fix" for 12.04 has not been posted yet.
4: Plug-in modems of the sort suggested as being available for 19.99 are not that cheap as of this posting. On Amazon.com and Tigerdirect I see two - and the price is 25-45. 

Another suggestion was made - to find an old external serial modem. While I have yet to try this, my experience so far indicates this might be the most promising avenue of exploration. Also, I can get one of these for free, using Freecycle, by locating another old geek like myself who has stuff in the basement or closet. I got rid of most of my old stuff like this, but plenty of people still have things hiding in some corner.

---

### Post by fox1t on 2012-06-28
I nave a new workaround if are you going to use [http://www.linuxant.com/drivers/dgc/downloads.php](http://www.linuxant.com/drivers/dgc/downloads.php) which are for a newer USB models. If you get SPIN_LOCK_UNLOCKED error while trying to compile, the problem is the different manner of 3.x kernels to handle that constant. The solution is easy and fast just search in mod_dgcusbdcp.c for 
```
static spinlock_t dgcusbdcp_lock = SPIN_LOCK_UNLOCKED; 
```and replace with ```
static DEFINE_SPINLOCK(dgcusbdcp_lock);
```
Now save this file and open osdcp.c find ```
static spinlock_t dcp_lock = SPIN_LOCK_UNLOCKED;
``` and replace with ```
static DEFINE_SPINLOCK(dcp_lock);
```
Save this file also, and then if you already tried to install drivers with no success type make uninstall and then make clean, to purge the system from the wrong installation. Now follow normal installation process described on the site and you will get working drivers. Your modem will be /dev/ttyACM0.
Hope this will help someone, and of course this method will work on 12.04 too, so mbuell you can try it...

---

### Post by fox1t on 2012-06-28
> **simonrodan said:**
> Dell has removed the drived from the URL mentioned in this thread.

Just find your product Id and vendor I'd using lsusb -v then go to [www.linuxant.com](www.linuxant.com) and search for the correct driver. When you find a working one we can try to fix you errors and problems, if any.

---

### Post by Trespasser on 2012-07-10
The same procedure outlined by Ganton works for Ubuntu 12.04, as well. This is on an internal, non-usb, Conexant dialup modem. I even made a deb file using debhelper for easy installation or removal. I'll still need to do the syslink thing...

sudo -s
cd /lib/modules/$(uname -r)/build/include/linux
ln -s ../generated/utsrelease.h
ln -s ../generated/autoconf.h
exit

on a kernel upgrade before installing the deb I assume. The modem showed up on /dev/SHSF0.

Just wanted to let you know.

Later...

---

### Post by zerocool9897 on 2012-08-09
Using a Google search, I found where the Dell drivers are located.
[http://linux.zsolttech.com/linmodem/hsfmodem/Dell/](http://linux.zsolttech.com/linmodem/hsfmodem/Dell/)
I have not tried these files but I did save them for future reference...

I had followed this procedure before successfully on Ubuntu 12.04, however, I can not seem to install this again still using Ubuntu 12.04 freshly installed and updated. I followed first 5 steps then used the files I had saved for re-installing. I attached the buildlog with the errors I get after the command sudo hsfconfig.  Thank you for any help on this and great post!

*I did figure out my problem...hope the link above helps :)

---

### Post by Ralph L on 2012-08-12
I was able to get my modem working on Ubuntu 12.04 Precise Pangolin using a Dell Latitude D610 by following Ganton's instructions at the beginning of this post.  When I ran scanModem I got:
CLASS=0703
NAME="Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW "
PCIDEV=8086:266d
SUBSYS=14f1:5423
IRQ=17
SOFT=8086:266d.MC97
CodecArchived=CXT
CodecDiagnosed=
slamrTest=
CodecClass=CXT
IDENT=hsfmodem
SLMODEMD_DEVICE=
OPTS=
Driver=hsfmodem-drivers

I looked at [http://www.linuxant.com/drivers/hsf/index.php](http://www.linuxant.com/drivers/hsf/index.php) but tell whether or not I needed to install the Conexant friendly alsa drivers, so I didn't install them.  So far my audio continues to work.

So far I have been able to dial numbers with wvdial and with Efax-gtk and send and receive faxes to/from my computer.  For testing I used web sites suggested here [http://pclosmag.com/html/Issues/201301/page09.html](http://pclosmag.com/html/Issues/201301/page09.html) 

I did have a couple of glitches and found solutions to them:

If anybody else decides to use Ganton's method, when it come to doing "sudo make install" and "sudo hsfconfig", change it to:
```
sudo -s
make install
hsfconfig
exit
```
Otherwise you get permission errors.  Apparently sudo doesn't always give you permission to all files.  I don't know why that is, but I have had the problem before and the use of "sudo -s" solves it.
Also, I had to add my fax users to the group "dialout" to let them use the modem.  AND I had to RESTART the computer to get these changes to take effect. (I installed Users and Groups (user-admin)).
Finally, to get wvdial to run I also had to set /etc/wvdial.conf to give read only access to Others.  This does not seem dangerous, but I was surprised that I had to do it.  Is this normal?
And thanks to Ganton for putting out such good instructions.
Maybe this post will be useful to somebody else who also lives in the past, still has a modem on their computer, and wants to use it to log into the Internet or send and receive faxes.

---

### Post by Ralph L on 2012-09-10
One last note for my previous post.  After installing the Conexant modem software, I used Synaptic to install efax and its gui (efax-gtk) and Wvdial and its gui (gnome-ppp).  These came up in  the Office menu and the  Internet menu, respectively.  efax-gtk sends a fax and gnome-ppp allows accessing dialup Internet.

---

### Post by dotish on 2012-09-22
Ganton's message is a real treasure. It worked for me with Ubuntu 12.04, after days of trials and shear frustration I followed the instructions for a 32 bit O.S. step by step and my dialup PCI softmodem, formerly undetectable, is now recognized and able to connect.  Thank you so much!!.

---

### Post by nlogax on 2012-12-18
This worked perfectly for me on 12.04. I previously had tested using a spare HCF modem and had generated a licence on Linuxant, only to find that when I moved the HCF modem to the target machine the licence was invalid! Linuxant hasn't returned my emails - probably hoping I'll pay $20 for another licence.

Thanks to you, the spare HSF modem is now working and receiving faxes! ;)

---

### Post by seltech on 2013-03-21
Hi all, hopefully someone can point me in the right direction. I'm on 12.04 64bit, followed the 64-bit instructions. When performing sudo hsfconfig i'm getting a error, here is the build log

```
driver version 7.68.00.09x86_64oem
(cd /lib/modules/3.5.0-26-generic/build && make "CNXT_KERNELSRC=/lib/modules/3.5.0-26-generic/build" "M=/usr/lib/hsfmodem/modules" "CC=gcc" clean)
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-26-generic'
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-26-generic'
(cd /lib/modules/3.5.0-26-generic/build && make "CNXT_KERNELSRC=/lib/modules/3.5.0-26-generic/build" "M=/usr/lib/hsfmodem/modules/GPL/hda" "CC=gcc" "HDA_CFLAGS=-DFOUND_KZALLOC  -DFOUND_TLV   -DFOUND_IRQ_HAN$
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-26-generic'
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-26-generic'
rm -rf *.o GPL/*.o *.ko GPL/*.ko *.mod.c GPL/*.mod.c .*.cmd GPL/.*.cmd .tmp_versions .tmp_versions  /lib/modules/3.5.0-26-generic/build/.tmp_versions/hsfosspec.mod  /lib/modules/3.5.0-26-generic/build/.tmp_$
(cd /lib/modules/3.5.0-26-generic/build && make "CNXT_KERNELSRC=/lib/modules/3.5.0-26-generic/build" "M=/usr/lib/hsfmodem/modules" "CC=gcc" modules)
make[1]: Entering directory `/usr/src/linux-headers-3.5.0-26-generic'
  CC [M]  /usr/lib/hsfmodem/modules/mod_engine.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_hda.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_mc97ali.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_mc97ati.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_mc97ich.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_mc97sis.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_mc97via.o
  CC [M]  /usr/lib/hsfmodem/modules/mod_osspec.o
  CC [M]  /usr/lib/hsfmodem/modules/osservices.o
/usr/lib/hsfmodem/modules/osservices.c: In function 'OsInit':
/usr/lib/hsfmodem/modules/osservices.c:1288:80: warning: format '%d' expects argument of type 'int', but argument 2 has type 'long unsigned int' [-Wformat]
/usr/lib/hsfmodem/modules/osservices.c:1288:80: warning: format '%d' expects argument of type 'int', but argument 3 has type 'long unsigned int' [-Wformat]
/usr/lib/hsfmodem/modules/osservices.c: In function 'cnxthsf_OsRawVPrintf':
/usr/lib/hsfmodem/modules/osservices.c:1321:1: warning: the frame size of 1040 bytes is larger than 1024 bytes [-Wframe-larger-than=]
/usr/lib/hsfmodem/modules/osservices.c: In function 'cnxthsf_OsErrorVPrintf':
/usr/lib/hsfmodem/modules/osservices.c:1370:1: warning: the frame size of 1040 bytes is larger than 1024 bytes [-Wframe-larger-than=]
/usr/lib/hsfmodem/modules/osservices.c: In function 'cnxthsf_OsDebugVPrintf':
/usr/lib/hsfmodem/modules/osservices.c:1397:1: warning: the frame size of 1040 bytes is larger than 1024 bytes [-Wframe-larger-than=]
  CC [M]  /usr/lib/hsfmodem/modules/osstdio.o
  CC [M]  /usr/lib/hsfmodem/modules/osnvm.o
  CC [M]  /usr/lib/hsfmodem/modules/osresour.o
/usr/lib/hsfmodem/modules/osresour.c: In function 'cnxthsf_OsHookInterrupt':
/usr/lib/hsfmodem/modules/osresour.c:131:13: warning: the address of '__this_module' will always evaluate as 'true' [-Waddress]
  CC [M]  /usr/lib/hsfmodem/modules/osstring.o
  CC [M]  /usr/lib/hsfmodem/modules/osmemory.o
/usr/lib/hsfmodem/modules/osmemory.c: In function 'cnxthsf_OsMemDMAAllocate':
/usr/lib/hsfmodem/modules/osmemory.c:101:1: warning: the frame size of 2064 bytes is larger than 1024 bytes [-Wframe-larger-than=]
  CC [M]  /usr/lib/hsfmodem/modules/osdiag.o
/usr/lib/hsfmodem/modules/osdiag.c: In function 'diag_read':
/usr/lib/hsfmodem/modules/osdiag.c:486:6: warning: passing argument 1 of 'touch_atime' from incompatible pointer type [enabled by default]
include/linux/fs.h:1874:13: note: expected 'struct path *' but argument is of type 'struct vfsmount *'
/usr/lib/hsfmodem/modules/osdiag.c:486:6: error: too many arguments to function 'touch_atime'
include/linux/fs.h:1874:13: note: declared here
/usr/lib/hsfmodem/modules/osdiag.c: At top level:
/usr/lib/hsfmodem/modules/osdiag.c:602:5: warning: initialization from incompatible pointer type [enabled by default]
/usr/lib/hsfmodem/modules/osdiag.c:602:5: warning: (near initialization for 'diag_fops.compat_ioctl') [enabled by default]
make[2]: *** [/usr/lib/hsfmodem/modules/osdiag.o] Error 1
make[1]: *** [_module_/usr/lib/hsfmodem/modules] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.5.0-26-generic'
make: *** [all] Error 2
```


I've double checked my edits in osdiag.c but cannot see any errors. Any suggestions?

---

### Post by Ganton on 2013-03-30
Hi!

This is me again. Nowadays I don't use any winmodem, but because some sites removed the original files, I will copy them here.

Notes about the "ubuntuforums.org" site: 
- It had limits in the size of the attachments, so I had to use several parts of files. 
- It forbade me to add more than five attachments, so I had to use more than one post. 
- It didn't allow me to attach the files that I split using the "split" command.

Those are the files only for 32 bits systems:
[ATTACH=CONFIG]240752[/ATTACH]
[ATTACH=CONFIG]240753[/ATTACH]
[ATTACH=CONFIG]240754[/ATTACH]
[ATTACH=CONFIG]240755[/ATTACH]

For example, you can move "hsfmodem-7.68.00.09oem.part_1.tar.bz2" and "hsfmodem-7.68.00.09oem.part_2.tar.bz2" to the same directory/folder and uncompress them using 
```
tar -xvf hsfmodem-7.68.00.09oem.part_1.tar.bz2
tar -xvf hsfmodem-7.68.00.09oem.part_2.tar.bz2
```
to obtain the original folder.

---

### Post by Ganton on 2013-03-30
Those are the files only for 64 bits systems:
[ATTACH=CONFIG]240757[/ATTACH]
[ATTACH=CONFIG]240756[/ATTACH]
[ATTACH=CONFIG]240761[/ATTACH]
[ATTACH=CONFIG]240760[/ATTACH]

---

### Post by Ganton on 2013-03-30
Those are the files common for all systems:
[ATTACH=CONFIG]240765[/ATTACH]
[ATTACH=CONFIG]240764[/ATTACH]
[ATTACH=CONFIG]240763[/ATTACH]
[ATTACH=CONFIG]240762[/ATTACH]

---

### Post by GrayJack on 2013-05-14
Anyway the solution doesn't work with the latest kernel for Ubuntu 12.04 - errors during compiling.
So one should forget about Conexant PCI/USB modems :(

---

### Post by chayzer on 2013-05-26
> **GrayJack said:**
> Anyway the solution doesn't work with the latest kernel for Ubuntu 12.04 - errors during compiling.
So one should forget about Conexant PCI/USB modems :(

I can confirm that it looks like theres a lot of issues to compile on 3.5.* kernels. I rolled back to 3.2.* and all seems fine.

---

### Post by ba0547 on 2014-01-25
Hello,

are there any news about to compile the driver on recent (3.10) kernels? i am still not able to compile any conexant driver modules on my 3.1x kernels. always get the message that file version.h is missing.

hope anyone has an idea.

best regards, harald.

---

### Post by george-hopkins on 2015-01-04
As downloading all the files is a bit tedious, I uploaded them to GitHub for easier retrieval:
[http://george-hopkins.github.io/hsfmodem](http://george-hopkins.github.io/hsfmodem)

---

### Post by Li_Wu on 2015-09-17
[https://github.com/george-hopkins/hsfmodem/issues/1](https://github.com/george-hopkins/hsfmodem/issues/1)

was anyone successful on a 4.x kernel ?

---

### Post by Sven_Goldt on 2015-10-02
Hi,

to make it easier i just downloaded the hsfmodem-7.80.02.06oem.tar.gz from [http://www.linuxant.com/drivers/hsf/oem/downloads.php](http://www.linuxant.com/drivers/hsf/oem/downloads.php).

Then i extracted the file, fixed all files to match a newer kernel (3.2.0 in my case) and instead of greying your hair i created a patch file to apply to the driver. I put all files in /usr/src which you should do aswell.

Then you can "patch -p0 < hsfmodem.patch" and follow the instructions afterwards which means "make install ; hsfconfig" and your HSF modem should work (/dev/modem it is).

I don't have a 4.x kernel in use so maybe it does not work with 4.x kernels but probably it needs just a few adjustments as it was needed from 2.x to 3.x.

---

### Post by arag0rn.smart on 2015-12-17
please could you do same patch for x64 system? thank you

---

