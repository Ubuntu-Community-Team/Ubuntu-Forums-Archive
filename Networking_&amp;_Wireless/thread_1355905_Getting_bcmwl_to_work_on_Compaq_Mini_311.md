---
title: "Getting bcmwl to work on Compaq Mini 311"
date: 2009-12-15
forum: Networking &amp; Wireless
---

### Post by Torandi on 2009-12-15
**NOTICE:** This solution still apply if you really want to run 2.6.32, otherwise: 
 
[LIST]
[*]In Grub: edit the option your booting to nosplash
[*]When you have booted, install the STA driver.
[*]Done
[/LIST]
 [B]
The problem:
[/B]
After hours of work installing Karmic on my new Compaq Mini 311 (the computer frooze at boot, which i solved by blacklisting b43, ssb and b43-pci-bridge and then installing linux-image-2.6.32) I found that my wireless card didn't work. When i tried to install the bcmwl-kernel-source apt-get said something like "dkms build for kernel" etc.

So i needed the kernel-headers for 2.6.32. To install them i added [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) to software sources (se.archives since I'm in sweden) and install the headers
```
 $ sudo apt-get install linux-headers-`uname -r`
```After this I ran
```
$ sudo dkms build -m bcmwl -v 5.10.91.9+bdcom
``` which didn't work. In the make.log i could read that the error was "implicit declaration of schedule()" 
[FONT=Arial Black]
The solution:[/FONT]

[LIST]
[*]Add [http://se.archive.ubuntu.com/ubuntu](http://se.archive.ubuntu.com/ubuntu) to software source
[*]Install the headers: ```
 $ sudo apt-get install linux-headers-`uname -r`
```
[*]Now you need to patch the bcmwl sources. Download [ATTACH]140028[/ATTACH].
[*]Unpack the file in /usr/src/bcmwl-5.10.91.9+bdcom
[*]Patch dkms.conf: In /usr/src/bcmwl-5.10.91.9+bdcom, run ```
 $ sudo patch -p1 -i dkms.conf.patch
```
[*]Now the bcmwl source should build. ```
$ sudo dkms build -m bcmwl -v 5.10.91.9+bdcom
```
[*]If the build succeded, install the module:```
$ sudo dkms install -m bcmwl -v 5.10.91.9+bdcom
```
[*]Reboot and pray.
[/LIST]
I hope I helped someone, if you run into any problems, post them here and I will try to help you.

---

### Post by RabidRick on 2010-03-19
THANK YOU!

I was working on trying to get my wifi up on my HP Pavillion DV6-2155DX laptop I just bought last night.  I had to upgrade the kernel to get graphics support running (it would not even display anything on the install unless I went into safe graphics mode) and I'm on 2.6.33 now.

At first it was complaining about a file not found and I had to update the path in include/linuxver.h:

```
#include <linux/autoconf.h>
```to

```
#include <generated/autoconf.h>
```and then adding this line to wl_linux.c:

```
#include <linux/sched.h>
```fixed the declaration error of schedule() error


I guess it got moved to its own file?

Thanks again, figured I'd post this in case it helps anyone with 2.6.33

---

### Post by tkaiser on 2010-05-01
Thanks, RabidRick! This really helped me to get wireless in 2.6.33 working!

---

