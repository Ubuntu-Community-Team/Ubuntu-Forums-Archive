---
title: "Installing appropriate driver for D-Link Dwa-140 RevB"
date: 2011-10-09
forum: Networking &amp; Wireless
---

### Post by Burky on 2011-10-09
I attempted to install the appropriate driver for my card by trying the following tutorial on installing the rt2870 driver,[ here]("http://ubuntuforums.org/showthread.php?t=960642").


lusb

```
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 07d1:3c0a D-Link System DWA-140 RangeBooster N Adapter(rev.B2) [Ralink RT2870]
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 009: ID 045e:0745 Microsoft Corp. 
Bus 001 Device 008: ID 046d:0809 Logitech, Inc. Webcam Pro 9000
Bus 001 Device 007: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 005: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 004: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 003: ID 0c0b:b159 Dura Micro, Inc. (Acomdata) 
Bus 001 Device 002: ID 18e3:9102 Fitipower Integrated Technology Inc Multi Card Reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

dmesg | grep rt2

```
[   11.600165] Registered led device: rt2800usb-phy1::radio
[   11.600181] Registered led device: rt2800usb-phy1::assoc
[   11.600200] Registered led device: rt2800usb-phy1::quality
[   11.600475] usbcore: registered new interface driver rt2800usb
[   12.065011] phy1 -> rt2x00lib_request_firmware: Error - Current firmware does not support detected chipset.
[  699.676554] usbcore: registered new interface driver rt2870

```

lsmod | grep rt2

```
rt2870sta             549339  0 
rt2800usb              17907  0 
rt2800lib              43824  1 rt2800usb
crc_ccitt              12595  1 rt2800lib
rt2x00usb              19693  1 rt2800usb
rt2x00lib              39075  3 rt2800usb,rt2800lib,rt2x00usb
mac80211              257001  4 rt2800lib,rt2x00usb,rt2x00lib,rtl8187
cfg80211              156212  3 rt2x00lib,rtl8187,mac80211

```


In response to this [URL="http://ubuntuforums.org/showpost.php?p=11325491&postcount=356"]reply
[/URL]

Please help <3

---

### Post by chili555 on 2011-10-09
Please do:```
sudo su
echo "blacklist rt2800usb" >> /etc/modprobe.d/blacklist.conf
exit
```Reboot and tell us how it's working.

---

### Post by praseodym on 2011-10-09
Hi,

which Ubuntu version do you use? From 10.4.3 and on this chipset is no longer supported with the rt2870sta (if it doesnt work) but with rt2800usb:

```
phy1 -> rt2x00lib_request_firmware: Error - Current firmware does not support detected chipset
```
This firmware can be installed from "linux-firmware" from the Natty version and on:

[http://de.archive.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.52_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.52_all.deb)

Installation by double clicking. In this case change the blacklist entry from rt2800usb to rt2870sta

---

### Post by chili555 on 2011-10-09
> From 10.4.3 and on this chipset is no longer supported with the rt2870sta:confused:```
$ modinfo rt2870sta 
filename:       /lib/modules/2.6.38-11-generic/kernel/drivers/staging/rt2870/rt2870sta.ko
version:        2.1.0.0
license:        GPL
description:    RT2870/RT3070 Wireless Lan Linux Driver
author:         Paul Lin <paul_lin@ralinktech.com>
firmware:       rt3071.bin
firmware:       rt3070.bin
firmware:       rt2870.bin
srcversion:     93C0C58E1A016FE5BD4DC9F
alias:          usb:v0411p015Dd*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2019pED14d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v2001p3C0Ad*dc*dsc*dp*ic*isc*ip*
alias:          usb:v[COLOR="Red"]07D1[/COLOR]p[COLOR="Red"]3C0A[/COLOR]d*dc*dsc*dp*ic*isc*ip*
<snip>
```Please help us understand.

---

### Post by praseodym on 2011-10-09
Oh, sorry. I was also confused by this Wiki article:

[http://wiki.ubuntuusers.de/WLAN/Karten/D-Link?highlight=07d1%3A3c0a](http://wiki.ubuntuusers.de/WLAN/Karten/D-Link?highlight=07d1%3A3c0a)

Alternatively it reads that the rt2800usb with new firmware files can be used. The article also links to this installation procedure:

[http://forum.ubuntuusers.de/topic/d-link-dwa-140-wir-nicht-erkannt/3/#post-2388926](http://forum.ubuntuusers.de/topic/d-link-dwa-140-wir-nicht-erkannt/3/#post-2388926)

So there are 3 possible ways. Maybe the rt2870sta just needs new firmware files?!

[COLOR="Red"]Edit:[/COLOR] Link to bug report:

[https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/762987](https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/762987)

---

### Post by chili555 on 2011-10-09
The reports of successful rt2800usb connections are few and far between. I think the landscape is about to change with Ubuntu 11.10 with kernel 3.0. I hear that rt2870sta will be retired.

In most cases, rt2870sta and rt2800usb conflict and one needs to be blacklisted. I've had the best luck with rt2870sta remaining and rt2800usb banished. We'll know when Burky returns.

---

### Post by Burky on 2011-10-09
I'm using the newest 32bit version of xubuntu.

```
sudo su
echo "blacklist rt2800usb" >> /etc/modprobe.d/blacklist.conf
exit
``` and a restart didnt do the trick :( I had the wireless comfigured correctly before on ubuntu, idk why it doesnt work now

 However I did use this driver from the D-link website.. I still get the same problems

driver i used before: ```
ftp://ftp.dlink.com/Wireless/dwa140_revB/Drivers/dwa140_revB_linux_drivers_2130.zip
```

---

### Post by chili555 on 2011-10-10
Let's see if there are kernel messages about this:```
dmesg | grep -i rt2
```

---

### Post by Burky on 2011-10-10
> **chili555 said:**
> Let's see if there are kernel messages about this:```
dmesg | grep -i rt2
```

Nothing came up in  the terminal when i did that :P

---

### Post by chili555 on 2011-10-10
When you used the drivers from Ralink and when you built the driver from Dlink, did the build go without error? What were you trying to accomplish? N speeds? A slow or not working connection? The latter is usually because of the driver conflict with rt2800usb.

Can you please try the build again?```
cd Downloads/driver/file
```...Or wherever the file is located.```
sudo su
make clean
make
make install
modprobe rt2870sta
exit
```Note any errors and post the results here.

---

### Post by Burky on 2011-10-10
When I run the 'make command' I get this error message

```
make[2]: *** [/home/david/Downloads/dwa140_revB_linux_drivers_2130/2010_0413_RT3070_Linux_STA_v2.1.3.0/os/linux/../../common/rtmp_init.o] Error 1
make[1]: *** [_module_/home/david/Downloads/dwa140_revB_linux_drivers_2130/2010_0413_RT3070_Linux_STA_v2.1.3.0/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-11-generic-pae'
make: *** [LINUX] Error 2
root@david-linux:/home/david
```

---

### Post by Burky on 2011-10-10
[QUOTE=Burky;11329557]When I run the 'make command' I get this error message

```
root@david-linux:/home/david/Downloads/dwa140_revB_linux_drivers_2130/2010_0413_RT3070_Linux_STA_v2.1.3.0# make
make -C tools
make[1]: Entering directory `/home/david/Downloads/dwa140_revB_linux_drivers_2130/2010_0413_RT3070_Linux_STA_v2.1.3.0/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/david/Downloads/dwa140_revB_linux_drivers_2130/2010_0413_RT3070_Linux_STA_v2.1.3.0/tools'
/home/david/Downloads/dwa140_revB_linux_drivers_2130/2010_0413_RT3070_Linux_STA_v2.1.3.0/tools/bin2h
cp -f os/linux/Makefile.6 /home/david/Downloads/dwa140_revB_linux_drivers_2130/2010_0413_RT3070_Linux_STA_v2.1.3.0/os/linux/Makefile
make  -C  /lib/modules/2.6.38-11-generic-pae/build SUBDIRS=/home/david/Downloads/dwa140_revB_linux_drivers_2130/2010_0413_RT3070_Linux_STA_v2.1.3.0/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.38-11-generic-pae'
  CC [M]  /home/david/Downloads/dwa140_revB_linux_drivers_2130/2010_0413_RT3070_Linux_STA_v2.1.3.0/os/linux/../../common/crypt_md5.o
  CC [M]  /home/david/Downloads/dwa140_revB_linux_drivers_2130/2010_0413_RT3070_Linux_STA_v2.1.3.0/os/linux/../../common/crypt_sha2.o
  CC [M]  /home/david/Downloads/dwa140_revB_linux_drivers_2130/2010_0413_RT3070_Linux_STA_v2.1.3.0/os/linux/../../common/crypt_hmac.o
  CC [M]  /home/david/Downloads/dwa140_revB_linux_drivers_2130/2010_0413_RT3070_Linux_STA_v2.1.3.0/os/linux/../../common/mlme.o
/home/david/Downloads/dwa140_revB_linux_drivers_2130/2010_0413_RT3070_Linux_STA_v2.1.3.0/os/linux/../../common/mlme.c: In function &#65533;&#65533;&#65533;BssTableSetEntry&#65533;&#65533;&#65533;:
/home/david/Downloads/dwa140_revB_linux_drivers_2130/2010_0413_RT3070_Linux_STA_v2.1.3.0/os/linux/../../common/mlme.c:4004:39: warning: operation on &#65533;&#65533;&#65533;Tab->BssOverlapNr&#65533;&#65533;&#65533; may be undefined
/home/david/Downloads/dwa140_revB_linux_drivers_2130/2010_0413_RT3070_Linux_STA_v2.1.3.0/os/linux/../../common/mlme.c: In function &#65533;&#65533;&#65533;BssTableSortByRssi&#65533;&#65533;&#65533;:
/home/david/Downloads/dwa140_revB_linux_drivers_2130/2010_0413_RT3070_Linux_STA_v2.1.3.0/os/linux/../../common/mlme.c:4408:1: warning: the frame size of 1576 bytes is larger than 1024 bytes
  CC [M]  /home/david/Downloads/dwa140_revB_linux_drivers_2130/2010_0413_RT3070_Linux_STA_v2.1.3.0/os/linux/../../common/cmm_wep.o
  CC [M]  /home/david/Downloads/dwa140_revB_linux_drivers_2130/2010_0413_RT3070_Linux_STA_v2.1.3.0/os/linux/../../common/action.o
  CC [M]  /home/david/Downloads/dwa140_revB_linux_drivers_2130/2010_0413_RT3070_Linux_STA_v2.1.3.0/os/linux/../../common/cmm_data.o
  CC [M]  /home/david/Downloads/dwa140_revB_linux_drivers_2130/2010_0413_RT3070_Linux_STA_v2.1.3.0/os/linux/../../common/rtmp_init.o
/home/david/Downloads/dwa140_revB_linux_drivers_2130/2010_0413_RT3070_Linux_STA_v2.1.3.0/os/linux/../../common/rtmp_init.c: In function &#65533;&#65533;&#65533;RtmpRaDevCtrlInit&#65533;&#65533;&#65533;:
/home/david/Downloads/dwa140_revB_linux_drivers_2130/2010_0413_RT3070_Linux_STA_v2.1.3.0/os/linux/../../common/rtmp_init.c:3710:2: error: implicit declaration of function &#65533;&#65533;&#65533;init_MUTEX&#65533;&#65533;&#65533;
/home/david/Downloads/dwa140_revB_linux_drivers_2130/2010_0413_RT3070_Linux_STA_v2.1.3.0/os/linux/../../common/rtmp_init.c:3711:2: warning: passing argument 2 of &#65533;&#65533;&#65533;os_alloc_mem&#65533;&#65533;&#65533; from incompatible pointer type
/home/david/Downloads/dwa140_revB_linux_drivers_2130/2010_0413_RT3070_Linux_STA_v2.1.3.0/include/rtmp.h:5707:13: note: expected &#65533;&#65533;&#65533;UCHAR **&#65533;&#65533;&#65533; but argument is of type &#65533;&#65533;&#65533;UCHAR *&#65533;&#65533;&#65533;
make[2]: *** [/home/david/Downloads/dwa140_revB_linux_drivers_2130/2010_0413_RT3070_Linux_STA_v2.1.3.0/os/linux/../../common/rtmp_init.o] Error 1
make[1]: *** [_module_/home/david/Downloads/dwa140_revB_linux_drivers_2130/2010_0413_RT3070_Linux_STA_v2.1.3.0/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.38-11-generic-pae'
make: *** [LINUX] Error 2

```

---

### Post by praseodym on 2011-10-11
Maybe this driver is too old. Try that one from my link.

---

### Post by Burky on 2011-10-12
> **praseodym said:**
> Maybe this driver is too old. Try that one from my link.

Nope nothing.. :((

I even tried sudo modprobe rt2870sta

---

### Post by praseodym on 2011-10-12
Are the needed tools for compiling installed?

```
sudo apt-get install --reinstall linux-headers-generic-pae build-essential dkms
```

---

### Post by Burky on 2011-10-12
I installed that packages, and tried recompiling.. same problem

thanks, though

Any other ideas?

---

### Post by praseodym on 2011-10-13
Can you show the outputs of "make"?

---

### Post by BlackDynamite on 2012-09-04
Bump

It's been a year since this thread went dead. Yet there was no solution on how to make this best selling (therefore used a lot) WiFi dongle...

Please, Please Ubuntu people, can we get some working drivers for the system?

---

### Post by chili555 on 2012-09-05
> **BlackDynamite said:**
> Bump

It's been a year since this thread went dead. Yet there was no solution on how to make this best selling (therefore used a lot) WiFi dongle...

Please, Please Ubuntu people, can we get some working drivers for the system?The thread went dead because the OP stopped posting. I'm pretty confident I can get it going if you'd like to try. Please post:```
lsusb
```

---

### Post by stelios313 on 2012-10-31
I dont know if i should post this here but i am having the same problem trying to install the drivers for D-link Dwa-140

Working on Ubuntu 10.04.4 (prerequisite for my university homework, not my choice)  

and the lsusb command gives me 
```

Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 004: ID 046d:c52b Logitech, Inc. 
Bus 002 Device 003: ID 046d:c316 Logitech, Inc. HID-Compliant Keyboard
Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 2001:3c15 D-Link Corp. [hex] 
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

how should i proceed?

---

### Post by chili555 on 2012-10-31
Please see here: [http://ubuntuforums.org/showthread.php?t=2068254](http://ubuntuforums.org/showthread.php?t=2068254)

You will need to download and compile the rt5372 driver. Please let me know if you need guidance. I have trouble gauging the experience level of posters.

---

### Post by stelios313 on 2012-10-31
i downloaded  the driver from [http://www.ralinktech.com/en/04_support/support.php?sn=501](http://www.ralinktech.com/en/04_support/support.php?sn=501)

now i untar it using this command in the terminal:

**tar 2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2.5.0.3_DPO.tar.bz2**    ?

Just getting started with ubuntu a have a fairly good grasp on the basics though
Appreciate your time and help:)

---

### Post by chili555 on 2012-10-31
Be certain you have installed linux-headers-generic and build-essential.> now i untar it using this command in the terminal:

tar 2011_0719_RT3070_RT3370_RT5370_RT5372_Linux_STA_V2 .5.0.3_DPO.tar.bz2 ?
If you see the package on your desktop, you can simply right-click it and select Extract Here.

I'm trying to help you not very much because I suspect part of the university homework experience is learning by doing and not learning to copy and paste from Chili.

---

### Post by stelios313 on 2012-10-31
> **chili555 said:**
> Be certain you have installed linux-headers-generic and build-essential.

Already installed both of them. i extracted the tar and now i have the folder with all the contents in it. Can you please guide me through the compile process?

---

### Post by chili555 on 2012-10-31
> Can you please guide me through the compile process?See my comment above? Have you consulted the README?

---

### Post by stelios313 on 2012-10-31
Actually the usb wireless installation has nothing to do with the assignment. I just need it because i am making a network monitor app in java , and i need a wireless interface(already made the ethernet monitoring) to check the functionality. The usb configuration is just a bump in the road;p I just suspected that on ubuntu 12.04 this sort of problem wouldn't have happened, i dont know if thats the case

---

### Post by chili555 on 2012-10-31
>  I just suspected that on ubuntu 12.04 this sort of problem wouldn't have happened, i dont know if thats the caseThat would be wonderful, however, manufacturers make new devices, re-write faulty drivers, adapt to dual-band N, et al faster than we can keep up. I will never run out of questions to answer until the coroner shows up.>  making a network monitor appDoes it require that the device go into monitor mode like Kismet? Not all wireless devices do monitor mode.

Give it a try. I'll be back soon.

---

### Post by stelios313 on 2012-10-31
> **chili555 said:**
> Does it require that the device go into monitor mode like Kismet? 

I dont think so. I just need it to show up on my wireless list so i can get some characteristics with iwconfig, iwlist etc.

Will try going through the readme. Looks like i m gonna need coffee

---

### Post by chili555 on 2012-10-31
Any progress to report? Success?

---

### Post by stelios313 on 2012-10-31
afraid not:/ i cant seem to figure out the configuration of the files that the readme suggests i do. some names don't correspond to the files i have downloaded and the whole thing seems too much for a guy who's been plug and playing for a long time on windows:/

---

### Post by chili555 on 2012-10-31
Here is a snip from the file I have. It may or may not agree with yours exactly. I've added notations:> 2> In Makefile
	 set the "MODE = STA" in Makefile and chose the TARGET to Linux by set "TARGET = LINUX"
	 define the linux kernel source include file path LINUX_SRC
	 modify to meet your need.
[COLOR="Red"]++Probably already done, you can safely ignore++
[/COLOR]
3> In os/linux/config.mk 
	define the GCC and LD of the target machine
	define the compiler flags CFLAGS
	modify to meet your need.
[COLOR="Red"]++Probably already done, you can safely ignore++
[/COLOR]
	** Build for being controlled by NetworkManager or wpa_supplicant wext functions
	   Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'.
[COLOR="Red"]++Probably not done and needed. Please see below.++[/COLOR]
	   => #>cd wpa_supplicant-x.x
	   => #>./wpa_supplicant -Dwext -ira0 -c wpa_supplicant.conf -d
	** Build for being controlled by WpaSupplicant with Ralink Driver
	   Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n'.
	   => #>cd wpa_supplicant-0.5.7
	   => #>./wpa_supplicant -Dralink -ira0 -c wpa_supplicant.conf -d
[COLOR="Red"]++You can skip all this.++[/COLOR]Please open os/linux/config.mk with any text editor and change as shown. All before and after is unchanged:> # Support AP-Client function
HAS_APCLI=n

# Support Wpa_Supplicant
HAS_WPA_SUPPLICANT=[COLOR="Red"]y[/COLOR]


# Support Native WpaSupplicant for Network Maganger
HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=[COLOR="Red"]y
[/COLOR]
#Support Net interface block while Tx-Sw queue full
HAS_BLOCK_NET_IF=n
Proofread carefully, save and close the text editor.

In the next post, we compile.

---

### Post by chili555 on 2012-10-31
Assuming the file you extracted is on your desktop, open a terminal and do:```
cd Desktop/2011
```Press Tab and the rest will fill in automagically. Pretty cool, eh? Press Enter. Now do:```
sudo su
make
make install
modprobe rt5370sta
exit
```Is your wireless working now?

Mrs. Chili has informed me I am taking her out to lunch, so please succeed quickly!

---

### Post by stelios313 on 2012-10-31
changed the os/linux/config.mk as shown, proofread twice.

---

### Post by stelios313 on 2012-10-31
it works!!!! :O it works!!!!! :O thank you so so much appreciate it! have fun and enjoy your meal!!:)

---

### Post by chili555 on 2012-10-31
Awesome! Glad it's working. When Update Manager installs a newer kernel, known in Ubuntu as linux-image, you'll need to rebuild the module for the newer kernel:```
sudo su
[COLOR="Red"]make clean[/COLOR]
make
make install
modprobe rt5370sta
exit
```Please retain these instructions and the folder you extracted so you'll know what to do when the time comes.

Have fun!

---

