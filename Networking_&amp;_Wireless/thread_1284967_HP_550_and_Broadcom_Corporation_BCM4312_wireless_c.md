---
title: "HP 550 and Broadcom Corporation BCM4312 wireless card not working with Kismet"
date: 2009-10-07
forum: Networking &amp; Wireless
---

### Post by Haribda on 2009-10-07
Hi there, I have a problem with my Kismet. It won't load. This is the output:

```
Launching kismet_server: //usr/bin/kismet_server
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.
Enabling channel splitting.
NOTICE: Disabling channel hopping, no enabled sources are able to change channel.
Source 0 (eth0): Enabling monitor mode for bcm43xx source interface eth0 channel 6...
FATAL: mode get ioctl failed 95:Operation not supported
Done.

```

The source in the config file are
```
source=bcm43xx,eth0,eth0
```

and here's the wireless card output

```
           *-network
                description: Wireless interface
                product: BCM4312 802.11b/g
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:10:00.0
                logical name: eth1
                version: 01
                serial: removed
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 
latency=0 module=wl multicast=yes wireless=IEEE 802.11

```

Is this because my card doesn't support monitor mode or it's because I have not upgraded it with bcm-42XX-fwcutter? I've tried taking it from the repo, but it won't work and it doesn't show in the synaptics manager.

Anybody has an idea of what the problem can be? I'd appreciate it.

---

### Post by t0mppa on 2009-10-07
The STA (module named wl) does not support monitor mode, neither does ndiswrapper. You have to use [b43]("http://linuxwireless.org/en/users/Drivers/b43") or [OpenFWWF]("http://www.ing.unibs.it/openfwwf/") as drivers, if you want to have monitor mode with a Broadcom chip.

---

### Post by Haribda on 2009-10-07
The thing is...

I've already done that. When i type:

```
user@haribda:~$ sudo apt-get install b43-fwcutter
Reading package lists... Done
Building dependency tree       
Reading state information... Done
b43-fwcutter is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

Now i tought I might be missing the libraries, so what i did is this:

```
su - 

yum install b43-fwcutter wget

wget http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2 
Now decompress, extract and copy firmware to /lib/firmware directory. 

tar xjf broadcom-wl-4.80.53.0.tar.bz2 

cd broadcom-wl-4.80.53.0/kmod 

b43-fwcutter -w /lib/firmware/ wl_apsta.o
```

When I type the last command, I get:

```
user@haribda:~$ cd broadcom-wl-4.80.53.0/kmod
user@haribda:~/broadcom-wl-4.80.53.0/kmod$ b43-fwcutter -w /lib/firmware/ wl_apsta.o
This file is recognised as:
  ID         :  FW11
  filename   :  wl_apsta.o
  version    :  351.126
  MD5        :  9207bc565c2fc9fa1591f6c7911d3fc0
Extracting b43/ucode4.fw
failed to open file: Permission denied
user@haribda:~/broadcom-wl-4.80.53.0/kmod$ 

```

What I'm doing wrong?

---

### Post by SmarterThanMyPhone on 2009-10-07
try airodump its more beginner friendly in my experience.

---

### Post by Ayuthia on 2009-10-07
Most likely the 4312 card that you have contains the 14e4:4315 chipset (you can verify by doing lspci -nn in the Terminal).  If that is the case, the Jaunty supplied b43 module will not work for your card.  The changes were made for this chipset in 2.6.32 if I recall correctly.  

At this point, some have been able to download the source for the newer version and get it to work in Jaunty, but some are also having some problems.

---

### Post by Haribda on 2009-10-07
I've just tried to install it...and it has to be done with compiling and by reading the README I can't figure all out, I can't even start it after extracting it. ANd after the make and make install compile it gives me all bunch of errors...

```
make -C src all
make[1]: Entering directory `/home/andronik/aircrack-ng-1.0/src'
make -C osdep
make[2]: Entering directory `/home/andronik/aircrack-ng-1.0/src/osdep'
Building for Linux
make[3]: Entering directory `/home/andronik/aircrack-ng-1.0/src/osdep'
gcc -g -W -Wall -Werror -O3 -D_FILE_OFFSET_BITS=64 -D_REVISION=0  -fPIC -I..    -c -o osdep.o osdep.c
makegcc -g -W -Wall -Werror -O3 -D_FILE_OFFSET_BITS=64 -D_REVISION=0  -fPIC -I..    -c -o network.o network.c
gcc -g -W -Wall -Werror -O3 -D_FILE_OFFSET_BITS=64 -D_REVISION=0  -fPIC -I..    -c -o linux.o linux.c
gcc -g -W -Wall -Werror -O3 -D_FILE_OFFSET_BITS=64 -D_REVISION=0  -fPIC -I..    -c -o linux_tap.o linux_tap.c
gcc -g -W -Wall -Werror -O3 -D_FILE_OFFSET_BITS=64 -D_REVISION=0  -fPIC -I..    -c -o radiotap/radiotap-parser.o radiotap/radiotap-parser.c
gcc -g -W -Wall -Werror -O3 -D_FILE_OFFSET_BITS=64 -D_REVISION=0  -fPIC -I..    -c -o common.o common.c
ar cru libosdep.a  osdep.o network.o linux.o linux_tap.o radiotap/radiotap-parser.o common.o
ranlib libosdep.a 
touch .os.Linux
make[3]: Leaving directory `/home/andronik/aircrack-ng-1.0/src/osdep'
make[2]: Leaving directory `/home/andronik/aircrack-ng-1.0/src/osdep'
gcc -g -W -Wall -Werror -O3 -D_FILE_OFFSET_BITS=64 -D_REVISION=0  -Iinclude   -c -o aircrack-ng.o aircrack-ng.c
In file included from aircrack-ng.c:65:
crypto.h:12:26: error: openssl/hmac.h: No such file or directory
crypto.h:13:25: error: openssl/sha.h: No such file or directory
crypto.h:15:25: error: openssl/rc4.h: No such file or directory
crypto.h:16:25: error: openssl/aes.h: No such file or directory
cc1: warnings being treated as errors
In file included from aircrack-ng.c:69:
sha1-sse2.h: In function &#8216;calc_4pmk&#8217;:
sha1-sse2.h:140: error: implicit declaration of function &#8216;HMAC&#8217;
sha1-sse2.h:140: error: implicit declaration of function &#8216;EVP_sha1&#8217;
aircrack-ng.c: In function &#8216;crack_wpa_thread&#8217;:
aircrack-ng.c:3910: error: implicit declaration of function &#8216;EVP_md5&#8217;
make[1]: *** [aircrack-ng.o] Error 1
make[1]: Leaving directory `/home/andronik/aircrack-ng-1.0/src'
make: *** [all] Error 2
user@haribda:~/aircrack-ng-1.0$ make install
make -C src install
make[1]: Entering directory `/home/andronik/aircrack-ng-1.0/src'
make -C osdep
make[2]: Entering directory `/home/andronik/aircrack-ng-1.0/src/osdep'
Building for Linux
make[3]: Entering directory `/home/andronik/aircrack-ng-1.0/src/osdep'
make[3]: `.os.Linux' is up to date.
make[3]: Leaving directory `/home/andronik/aircrack-ng-1.0/src/osdep'
make[2]: Leaving directory `/home/andronik/aircrack-ng-1.0/src/osdep'
gcc -g -W -Wall -Werror -O3 -D_FILE_OFFSET_BITS=64 -D_REVISION=0  -Iinclude   -c -o aircrack-ng.o aircrack-ng.c
In file included from aircrack-ng.c:65:
crypto.h:12:26: error: openssl/hmac.h: No such file or directory
crypto.h:13:25: error: openssl/sha.h: No such file or directory
crypto.h:15:25: error: openssl/rc4.h: No such file or directory
crypto.h:16:25: error: openssl/aes.h: No such file or directory
cc1: warnings being treated as errors
In file included from aircrack-ng.c:69:
sha1-sse2.h: In function &#8216;calc_4pmk&#8217;:
sha1-sse2.h:140: error: implicit declaration of function &#8216;HMAC&#8217;
sha1-sse2.h:140: error: implicit declaration of function &#8216;EVP_sha1&#8217;
aircrack-ng.c: In function &#8216;crack_wpa_thread&#8217;:
aircrack-ng.c:3910: error: implicit declaration of function &#8216;EVP_md5&#8217;
make[1]: *** [aircrack-ng.o] Error 1
make[1]: Leaving directory `/home/andronik/aircrack-ng-1.0/src'
make: *** [install] Error 2

```

---

### Post by Haribda on 2009-10-07
> **Ayuthia said:**
> Most likely the 4312 card that you have contains the 14e4:4315 chipset (you can verify by doing lspci -nn in the Terminal).  If that is the case, the Jaunty supplied b43 module will not work for your card.  The changes were made for this chipset in 2.6.32 if I recall correctly.  

At this point, some have been able to download the source for the newer version and get it to work in Jaunty, but some are also having some problems.

Exacly! Here's the output: 

```
user@haribda:# lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile GME965/GLE960 Memory Controller Hub [8086:2a10] (rev 0c)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GME965/GLE960 Integrated Graphics Controller [8086:2a12] (rev 0c)
00:02.1 Display controller [0380]: Intel Corporation Mobile GME965/GLE960 Integrated Graphics Controller [8086:2a13] (rev 0c)
00:19.0 Ethernet controller [0200]: Intel Corporation 82562GT 10/100 Network Connection [8086:10c4] (rev 03)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 03)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 [8086:2847] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 03)
00:1f.2 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller [8086:2828] (rev 03)
10:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [1**4e4:4315**] (rev 01)


```

The question is, what do I do next?

---

### Post by Haribda on 2009-10-09
Somebody has an answer?

---

### Post by Ayuthia on 2009-10-09
If you want to use the b43 module, you will have to compile it.  Here is a link that might help:
[http://ubuntuforums.org/showthread.php?t=1266620](http://ubuntuforums.org/showthread.php?t=1266620)

However, only one person there appears to have it working.

---

### Post by chili555 on 2009-10-09
> **Ayuthia said:**
> If you want to use the b43 module, you will have to compile it.  Here is a link that might help:
[http://ubuntuforums.org/showthread.php?t=1266620](http://ubuntuforums.org/showthread.php?t=1266620)

However, only one person there appears to have it working.I believe b43 is native in Jaunty and beyond, perhaps even earlier. Why can one not simply rmmod wl and modprobe b43, after amending kismet.conf, of course.

You may be correct; I am just trying to understand.

---

### Post by Ayuthia on 2009-10-09
> **chili555 said:**
> I believe b43 is native in Jaunty and beyond, perhaps even earlier. Why can one not simply rmmod wl and modprobe b43, after amending kismet.conf, of course.

You may be correct; I am just trying to understand.

The b43 driver does not support the 4315 chipset until 2.6.32 so the only way to get it into Jaunty is to build from the newer source.

Otherwise, you are correct.  The b43 is available for the 4303, 4306, 4311, 4312 (14e4:4312 chipsets), and 4318 cards.

---

### Post by chili555 on 2009-10-09
Ahhh, gotcha. Thanks for the info. I and, I suspect, quite a few searchers, learned something today. Thanks!

---

