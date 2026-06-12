---
title: "Can't make install wireless driver, Meerkat 10.10"
date: 2010-11-30
forum: Networking &amp; Wireless
---

### Post by Bucky Ball on 2010-11-30
Hi all,

I am using Maverick 10.10 on a Toshiba Satellite Pro L510 which has this card, full output from lshw:

 ```
description: Wireless interface
                product: RTL8191SEvB Wireless LAN Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlan0
                version: 10
                serial: b4:82:fe:3c:ad:72
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes **driver=rtl819xSE **driverversion=0017.0507.2010 firmware=63 ip=192.168.0.107 latency=0 multicast=yes wireless=802.11bg
```Take note of the driver I have in bold. I was advised on my thread [here]("http://ubuntuforums.org/showthread.php?t=1616726") in post #4 to use [this]("http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true") driver from the Realtek site. In Realtek's  instructions it tells me to get into the appropriate directory (yes, all is untarred!) and run, as root:

```
make
make install

```... then reboot. My problem? 'make' seems to run fine, no errors, but when I run 'make install', I get:

```
binky@tosher:~/Downloads/RealtekDriver/rtl8192se_linux_2.6.0018.1025.2010$ sudo make install
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-22-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
make[1]: Entering directory `/home/binky/Downloads/RealtekDriver/rtl8192se_linux_2.6.0018.1025.2010/HAL/rtl8192'
make -C /lib/modules/2.6.35-22-generic/build M= CC=gcc modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.35-22-generic'
  CHK     include/linux/version.h
  CHK     include/generated/utsrelease.h
make[3]: *** **No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'.  Stop.**
make[2]: *** [prepare0] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/binky/Downloads/RealtekDriver/rtl8192se_linux_2.6.0018.1025.2010/HAL/rtl8192'
make: *** [install] Error 2
```So far, I've figured out that 'Error 2' basically means any of probably a zillion or two possible errors.
The line I have in bold is obviously the one. I have searched, dug, probed, but can not
work out what it means or where to start fixing it. 

Reason I'm bothering at all is that yes, the Realtek card worked 'out of the box' but is
pretty unreliable, a third and less the speed of the other machines in the house, and overall a
bit painful!

Any help?

---

### Post by uncaspi on 2010-11-30
make[2]: Entering directory `/usr/src/linux-headers-2.6.35-22-generic'
  CHK     include/linux/version.h
  CHK     include/generated/utsrelease.h

The problem is that version.h and utsrelease.h are missing in the directory above. These are header files for your kernel release.  You could try to install them by sudo apt-get install kernel-source-headers 
I'm not quite sure if this is typed correct. Check with google.

---

### Post by Bucky Ball on 2010-11-30
Thanks unicaspi. I suspected something like that. I did read somewhere though that if it could find:

/usr/src/linux-headers-2.6.35-22-generic

... then they should be installed. Maybe not. Will try your suggestion. :)

---

### Post by Bucky Ball on 2010-11-30
> **uncaspi said:**
>  You could try to install them by sudo apt-get install kernel-source-headers 
I'm not quite sure if this is typed correct. Check with google.

Like I say, pretty much answers that question; all headers installed:

```
binky@tosher:/$ sudo apt-get install linux-headers-$(uname -r)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.35-22-generic is already the newest version.
linux-headers-2.6.35-22-generic set to manually installed.
The following package was automatically installed and is no longer required:
  python-iniparse
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 16 not upgraded.

```Next suggestion ... anyone.

*** HAHA! Hold on. Just as I posted that, noticed there is updates awaiting and what do you know ... all new header files for the Maverick kernel. How bizarre at 2:20am when I am still trying to sort this out. Wouldn't be any other way though really. Thanks for your help. Lets see how this goes, then and upgrade, then try 'make install' again.

---

### Post by Bucky Ball on 2010-11-30
Nope, all turning into another Ubuntu Wireless Joke. The powers that be make it that difficult. New headers in, 'make' looked a little different, 'make install' exactly as was, Error 2 and same error. 

When the hell is it going to be a level playing field for the open-source community? I'm sick of battling crap to use the best OS around ...

Then again, I could be missing something really obvious, but think I've been pretty clear and no-one's filled me in on what I might be missing.

---

### Post by uncaspi on 2010-11-30
make -C /lib/modules/2.6.35-22-generic/build M= CC=gcc modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.35-22-generic'
  CHK     include/linux/version.h
  CHK     include/generated/utsrelease.h


Ok try to locate the files with locate version.h and locate utsrelease.h to see if they are somewhere in your system i.e in

lib/modules/2.6.35-22-generic/build/include

If you find them then copy them to  /usr/src/linux-headers-2.6.35-22-generic

---

### Post by Bucky Ball on 2010-11-30
Think this just about covers it:

```
binky@tosher:~$ locate utsrelease.h
/usr/src/linux-headers-2.6.35-22-generic/include/generated/utsrelease.h
```Already there.

Ahh! But I just updated to 2.6.35-23 and that is the kernel I am currently running. Strange didn't show up there. Plot thickens.

```
binky@tosher:~$ uname -r
2.6.35-23-generic

```

Think I'm missing something obvious here but we'll get there! ;)

---

### Post by uncaspi on 2010-11-30
You must run sudo updatedb
first to view newly installed files using locate.

---

### Post by chili555 on 2010-11-30
I just compiled it perfectly. Please assure you have build-essential installed. Next, try:```
sudo su
make install
exit
```

---

### Post by Bucky Ball on 2010-12-01
Installed build-essential. No errors. Reboot. 'lshw' gives me this:

```
description: Wireless interface
                product: RTL8191SEvB Wireless LAN Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlan0
                version: 10
                serial: b4:82:fe:3c:ad:72
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=rtl819xSE driverversion=0018.1025.2010 firmware=63 ip=192.168.0.107 latency=0 multicast=yes wireless=802.11bg
```No different, same driver, same inconsistency, 'cept now going between 88% and random percentages below that (although 56% seems to be common regardless of the tweak).

Thanks for the tips people. Getting closer.

---

### Post by Bucky Ball on 2010-12-01
> **uncaspi said:**
> You must run sudo updatedb
first to view newly installed files using locate.

? I found the file.

---

### Post by chili555 on 2010-12-01
It is the same driver but the newer version:> driver=rtl819xSE driverversion=[COLOR="Red"]0018.1025.2010[/COLOR]

---

### Post by Bucky Ball on 2010-12-01
Same same then. Sluggish speeds and on 59% ... hang on, 86% as we speak. Sheesh. Boring. But still trying. At least we got make install happening. Cheers.

---

