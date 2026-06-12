---
title: "DLink USB Wireless Dual Band (DWA-171)"
date: 2013-08-17
forum: Networking &amp; Wireless
---

### Post by bell1996 on 2013-08-17
Just an FYI to the community. 

I finally found a mini USB wireless dual band (2.4 & 5 GHz) that is working on my laptop running Ubuntu 12.04 (64-bit).
It wasn't to hard to setup. 

   Downloaded the drivers from this site [http://wikidevi.com/wiki/D-Link_DWA-180_rev_A1](http://wikidevi.com/wiki/D-Link_DWA-180_rev_A1)
   (I know it says DWA-180, but it works for the DWA-181 also)
   I did a make clean, make, and make install from the directory with the drivers. An then a modprobe 8812au

then did a re-boot and. That's it.

---

### Post by johnrevier on 2014-03-09
Hello,

I tried installing this driver on Ubuntu 12.04. [make clean] was ok,] But I get errors after using ¨make"

here is the output from that command.

```
root@Ubuntu-John:/home/john/Downloads/dwa171# make
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/3.11.0-18-generic/build M=/home/john/Downloads/dwa171  modules
make[1]: Entering directory `/usr/src/linux-headers-3.11.0-18-generic'
  CC [M]  /home/john/Downloads/dwa171/core/rtw_cmd.o
  CC [M]  /home/john/Downloads/dwa171/core/rtw_security.o
  CC [M]  /home/john/Downloads/dwa171/core/rtw_debug.o
  CC [M]  /home/john/Downloads/dwa171/core/rtw_io.o
  CC [M]  /home/john/Downloads/dwa171/core/rtw_ioctl_query.o
  CC [M]  /home/john/Downloads/dwa171/core/rtw_ioctl_set.o
  CC [M]  /home/john/Downloads/dwa171/core/rtw_ieee80211.o
  CC [M]  /home/john/Downloads/dwa171/core/rtw_mlme.o
  CC [M]  /home/john/Downloads/dwa171/core/rtw_mlme_ext.o
  CC [M]  /home/john/Downloads/dwa171/core/rtw_wlan_util.o
  CC [M]  /home/john/Downloads/dwa171/core/rtw_vht.o
  CC [M]  /home/john/Downloads/dwa171/core/rtw_pwrctrl.o
  CC [M]  /home/john/Downloads/dwa171/core/rtw_rf.o
  CC [M]  /home/john/Downloads/dwa171/core/rtw_recv.o
  CC [M]  /home/john/Downloads/dwa171/core/rtw_sta_mgt.o
  CC [M]  /home/john/Downloads/dwa171/core/rtw_ap.o
  CC [M]  /home/john/Downloads/dwa171/core/rtw_xmit.o
  CC [M]  /home/john/Downloads/dwa171/core/rtw_p2p.o
  CC [M]  /home/john/Downloads/dwa171/core/rtw_tdls.o
  CC [M]  /home/john/Downloads/dwa171/core/rtw_br_ext.o
  CC [M]  /home/john/Downloads/dwa171/core/rtw_iol.o
  CC [M]  /home/john/Downloads/dwa171/core/rtw_sreset.o
  CC [M]  /home/john/Downloads/dwa171/core/efuse/rtw_efuse.o
  CC [M]  /home/john/Downloads/dwa171/os_dep/osdep_service.o
  CC [M]  /home/john/Downloads/dwa171/os_dep/linux/os_intfs.o
/home/john/Downloads/dwa171/os_dep/linux/os_intfs.c: In function ‘rtw_proc_init_one’:
/home/john/Downloads/dwa171/os_dep/linux/os_intfs.c:352:3: error: implicit declaration of function ‘create_proc_entry’ [-Werror=implicit-function-declaration]
/home/john/Downloads/dwa171/os_dep/linux/os_intfs.c:352:11: warning: assignment makes pointer from integer without a cast [enabled by default]
/home/john/Downloads/dwa171/os_dep/linux/os_intfs.c:359:3: error: implicit declaration of function ‘create_proc_read_entry’ [-Werror=implicit-function-declaration]
/home/john/Downloads/dwa171/os_dep/linux/os_intfs.c:359:9: warning: assignment makes pointer from integer without a cast [enabled by default]
/home/john/Downloads/dwa171/os_dep/linux/os_intfs.c:370:21: warning: assignment makes pointer from integer without a cast [enabled by default]
/home/john/Downloads/dwa171/os_dep/linux/os_intfs.c:401:8: warning: assignment makes pointer from integer without a cast [enabled by default]
/home/john/Downloads/dwa171/os_dep/linux/os_intfs.c:407:7: error: dereferencing pointer to incomplete type
/home/john/Downloads/dwa171/os_dep/linux/os_intfs.c:409:8: warning: assignment makes pointer from integer without a cast [enabled by default]
/home/john/Downloads/dwa171/os_dep/linux/os_intfs.c:415:7: error: dereferencing pointer to incomplete type
/home/john/Downloads/dwa171/os_dep/linux/os_intfs.c:418:8: warning: assignment makes pointer from integer without a cast [enabled by default]
/home/john/Downloads/dwa171/os_dep/linux/os_intfs.c:426:8: warning: assignment makes pointer from integer without a cast [enabled by default]
/home/john/Downloads/dwa171/os_dep/linux/os_intfs.c:434:8: warning: assignment makes pointer from integer without a cast [enabled by default]
/home/john/Downloads/dwa171/os_dep/linux/os_intfs.c:442:8: warning: assignment makes pointer from integer without a cast [enabled by default]
/home/john/Downloads/dwa171/os_dep/linux/os_intfs.c:449:8: warning: assignment makes pointer from integer without a cast [enabled by default]
/home/john/Downloads/dwa171/os_dep/linux/os_intfs.c:456:8: warning: assignment makes pointer from integer without a cast [enabled by default]
/home/john/Downloads/dwa171/os_dep/linux/os_intfs.c:463:8: warning: assignment makes pointer from integer without a cast [enabled by default]
/home/john/Downloads/dwa171/os_dep/linux/os_intfs.c:470:8: warning: assignment makes pointer from integer without a cast [enabled by default]
/home/john/Downloads/dwa171/os_dep/linux/os_intfs.c:477:8: warning: assignment makes pointer from integer without a cast [enabled by default]
/home/john/Downloads/dwa171/os_dep/linux/os_intfs.c:484:8: warning: assignment makes pointer from integer without a cast [enabled by default]
/home/john/Downloads/dwa171/os_dep/linux/os_intfs.c:491:8: warning: assignment makes pointer from integer without a cast [enabled by default]
/home/john/Downloads/dwa171/os_dep/linux/os_intfs.c:498:8: warning: assignment makes pointer from integer without a cast [enabled by default]
/home/john/Downloads/dwa171/os_dep/linux/os_intfs.c:505:8: warning: assignment makes pointer from integer without a cast [enabled by default]
/home/john/Downloads/dwa171/os_dep/linux/os_intfs.c:512:8: warning: assignment makes pointer from integer without a cast [enabled by default]
/home/john/Downloads/dwa171/os_dep/linux/os_intfs.c:519:8: warning: assignment makes pointer from integer without a cast [enabled by default]
/home/john/Downloads/dwa171/os_dep/linux/os_intfs.c:526:8: warning: assignment makes pointer from integer without a cast [enabled by default]
/home/john/Downloads/dwa171/os_dep/linux/os_intfs.c:533:8: warning: assignment makes pointer from integer without a cast [enabled by default]
/home/john/Downloads/dwa171/os_dep/linux/os_intfs.c:542:9: warning: assignment makes pointer from integer without a cast [enabled by default]
/home/john/Downloads/dwa171/os_dep/linux/os_intfs.c:549:9: warning: assignment makes pointer from integer without a cast [enabled by default]
/home/john/Downloads/dwa171/os_dep/linux/os_intfs.c:559:8: warning: assignment makes pointer from integer without a cast [enabled by default]
/home/john/Downloads/dwa171/os_dep/linux/os_intfs.c:577:8: warning: assignment makes pointer from integer without a cast [enabled by default]
/home/john/Downloads/dwa171/os_dep/linux/os_intfs.c:585:8: warning: assignment makes pointer from integer without a cast [enabled by default]
/home/john/Downloads/dwa171/os_dep/linux/os_intfs.c:591:7: error: dereferencing pointer to incomplete type
/home/john/Downloads/dwa171/os_dep/linux/os_intfs.c:593:8: warning: assignment makes pointer from integer without a cast [enabled by default]
/home/john/Downloads/dwa171/os_dep/linux/os_intfs.c:599:7: error: dereferencing pointer to incomplete type
/home/john/Downloads/dwa171/os_dep/linux/os_intfs.c:601:8: warning: assignment makes pointer from integer without a cast [enabled by default]
/home/john/Downloads/dwa171/os_dep/linux/os_intfs.c:607:7: error: dereferencing pointer to incomplete type
/home/john/Downloads/dwa171/os_dep/linux/os_intfs.c:609:8: warning: assignment makes pointer from integer without a cast [enabled by default]
/home/john/Downloads/dwa171/os_dep/linux/os_intfs.c:615:7: error: dereferencing pointer to incomplete type
/home/john/Downloads/dwa171/os_dep/linux/os_intfs.c:617:8: warning: assignment makes pointer from integer without a cast [enabled by default]
/home/john/Downloads/dwa171/os_dep/linux/os_intfs.c:623:7: error: dereferencing pointer to incomplete type
/home/john/Downloads/dwa171/os_dep/linux/os_intfs.c:626:8: warning: assignment makes pointer from integer without a cast [enabled by default]
/home/john/Downloads/dwa171/os_dep/linux/os_intfs.c:629:8: warning: assignment makes pointer from integer without a cast [enabled by default]
/home/john/Downloads/dwa171/os_dep/linux/os_intfs.c:635:7: error: dereferencing pointer to incomplete type
/home/john/Downloads/dwa171/os_dep/linux/os_intfs.c:647:8: warning: assignment makes pointer from integer without a cast [enabled by default]
/home/john/Downloads/dwa171/os_dep/linux/os_intfs.c:653:7: error: dereferencing pointer to incomplete type
cc1: some warnings being treated as errors
make[2]: *** [/home/john/Downloads/dwa171/os_dep/linux/os_intfs.o] Error 1
make[1]: *** [_module_/home/john/Downloads/dwa171] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.11.0-18-generic'
make: *** [modules] Error 2

```

Yes I renamed the foldername, but I tried the original foldername and it did not work either.

How to solve this?

John

---

### Post by chili555 on 2014-03-09
Do you mind if we just verify your device?```
lsusb
```

---

### Post by johnrevier on 2014-03-09
Hello chili555

No I do not mind:D

This is what  I have got
```

john@Ubuntu-John:~$ lsusb
Bus 001 Device 002: ID 04f2:b071 Chicony Electronics Co., Ltd 2.0M UVC Webcam / CNF7129
Bus 002 Device 010: ID 2001:3314 D-Link Corp. 
Bus 006 Device 002: ID 046d:c526 Logitech, Inc. Nano Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
john@Ubuntu-John:~$
```

---

### Post by chili555 on 2014-03-09
With a working temporary ethernet connection:```
sudo apt-get install git
git clone https://github.com/abperiasamy/rtl8812AU_8821AU_linux.git
cd rtl8812AU_8821AU_linux
make
sudo make install
sudo modprobe 8812au
```It 'makes' with a couple of possibly harmless warnings but no errors on my 3.11.0-18 system.

---

### Post by johnrevier on 2014-03-09
Thanks Chili 

It works great:P

Problem Solved

---

### Post by chili555 on 2014-03-09
> **johnrevier said:**
> Thanks Chili 

It works great:P

Problem SolvedWe're not quite done yet. When a later kernel version is installed by Update Manager, after reboot, you must recompile the driver:```
cd rtl8812AU_8821AU_linux
make clean
make
sudo make install
sudo modprobe 8812au
```Please retain the file and these instructions for that time.

---

### Post by johnrevier on 2014-03-09
Great info.

Just what a ¨newbee" needs.
I have saved the info and instructions.

I am comming over from the windowsside. 
I managed to install ubuntu, transfer mail and calendar within hours. Just using info right here.
I do have some questions left, but that is for sometime later.

Thanks again.

John

---

### Post by van-pelt-thomas on 2014-03-19
Superb!

Finally a dual band wifi adapter that fully (and easily) works.

Having found out Lenovo uses bios white listing for pci devices :( I was forced to look for an usb-adapter.
Having tried several, all unable to connect to a 5 GHz network due to driver isues (or better a lack of a proper driver) I almost gave in...


Many thanks again,

Thomas

---

### Post by johnrevier on 2014-04-29
Heads up folks

I just installed some updates, so the DWA driver went down.
I tried running "make clean", but it generated an error.:confused:
so I added "sudo su" (it looked like a permissions problem)
Life is good now):P

```
cd rtl8812AU_8821AU_linux
[COLOR=#ff0000]sudo su[/COLOR]
make clean
make
sudo make install
sudo modprobe 8812au
```

---

### Post by L_Bradley on 2014-06-30
I just read this review in the store, bought it, followed the directions (using the link to the drivers with patches for newer kernels from Github) and it does work totally in 12.04, including with WPA, which other USB wifi adapters I've bought for Ubuntu don't support. I wanted to make that last thing about clear, that was my only question in the store this thread didn't make clear.

---

### Post by bell1996 on 2014-07-01
L_Bradley, did you have a question or just making a statement?
I just installed this same wifi USB adapter in my laptop (using the same instructions ...again) and it worked. It is dual band and supports WPA.

---

### Post by silverstarfy on 2015-04-06
I don't know if this thread is still on anybody's radar, but I have done these instructions and "firmware=N/A" and "wireless unassociated" show up for me. It recognizes my drivers,but I can't get it to work!

---

### Post by chili555 on 2015-04-06
> **silverstarfy said:**
> I don't know if this thread is still on anybody's radar, but I have done these instructions and "firmware=N/A" and "wireless unassociated" show up for me. It recognizes my drivers,but I can't get it to work!It's still on my radar. Can you please provide full details?

---

### Post by mike_b.2 on 2015-04-21
I am also having issues... but I'm using Peppermint OS but seeing as it uses the same apt-get protocol right?

---

### Post by chili555 on 2015-04-21
> **mike_b.2 said:**
> I am also having issues... but I'm using Peppermint OS but seeing as it uses the same apt-get protocol right?I know nothing about Peppermint. If you care to share your details, I'll take a look. Have you tried the process above? Anything go wrong?

---

### Post by mike_b.2 on 2015-04-21
I've done the process before thanks to your instructions (Thank you so very much by the way, best description ever.) i may have found my issue. it's saying " stack protector enabled but no compiler support"

---

### Post by mike_b.2 on 2015-04-21
so yea.... making sure you have the correct compilers helps. oddly enough :lolflag:

---

### Post by chili555 on 2015-04-21
> **mike_b.2 said:**
>  it's saying " stack protector enabled but no compiler support"Where, exactly? In the terminal as you recompile for a newer kernel version? Which kernel?```
uname -r
```

---

### Post by mike_b.2 on 2015-04-21
3.13.0-29-generic

---

### Post by chili555 on 2015-04-21
>  it's saying " stack protector enabled but no compiler support"
[QUOTE]Where, exactly? In the terminal as you recompile for a newer kernel version? Which kernel?[/QUOTE]Details, please. We need details.

---

### Post by mike_b.2 on 2015-04-21
Ok. Chili. I'm sorry for wasting your time  "sudo su" then tried again, and.... yea flawless. my bad still new to linux.

---

### Post by chili555 on 2015-04-21
> **mike_b.2 said:**
> Ok. Chili. I'm sorry for wasting your time  "sudo su" then tried again, and.... yea flawless. my bad still new to linux.Glad it's working now.

---

### Post by Collin_Jones on 2015-05-16
I'm only three days into my linux experiment and I am having a bit of trouble with the same wireless adapter (tried running driver setup from cd and the suggested zip with wine but the install wizard cannot find the adapter) After looking around and trying a few other solutions with no luck I think this is my best option. Unfortunately I am completely out of my depth when it comes to using make commands could someone elaborate a bit on how this particular build would function in the terminal. (I'm stuck sitting on the floor in my living room so I can hook up to an ethernet cable and it makes for a terrible learning environment otherwise id bury myself in the research)

I downloaded and extracted the file folder specified to /home/*user*/Dlink/DWA-180A1_v1.00B05/Setup

---

### Post by chili555 on 2015-05-16
May we confirm the details of the device before we proceed?```
lsusb
uname -r
```Thanks.

---

### Post by Collin_Jones on 2015-05-16
Sure thing thanks for the quick response.


collin@Jane:~$ lsusb
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 011 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 010 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 002: ID 2001:3314 D-Link Corp. 
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 0461:4d0f Primax Electronics, Ltd HP Optical Mouse
Bus 004 Device 002: ID 0461:4d98 Primax Electronics, Ltd 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
collin@Jane:~$ uname -r
3.16.0-37-generic
collin@Jane:~$

---

### Post by chili555 on 2015-05-16
> Device 002: ID 2001:3314 D-Link Corp. Your device indeed uses the driver 8812au. Here is a method to install it. [http://askubuntu.com/questions/623048/help-with-belkin-dual-band-wireless-adapter-ac867/623126#623126](http://askubuntu.com/questions/623048/help-with-belkin-dual-band-wireless-adapter-ac867/623126#623126)

If you haven't already, you need to install some prerequisites:```
sudo apt-get install build-essential linux-headers-generic git
```You should be off the ethernet in about three minutes, but if you get stuck, post back.

---

### Post by Collin_Jones on 2015-05-16
> **chili555 said:**
> Your device indeed uses the driver 8812au. Here is a method to install it. [http://askubuntu.com/questions/623048/help-with-belkin-dual-band-wireless-adapter-ac867/623126#623126](http://askubuntu.com/questions/623048/help-with-belkin-dual-band-wireless-adapter-ac867/623126#623126)

If you haven't already, you need to install some prerequisites:```
sudo apt-get install build-essential linux-headers-generic git
```You should be off the ethernet in about three minutes, but if you get stuck, post back.


Working perfectly :)   Thanks for the help.

Would mind explaining how you knew which driver to use.

---

### Post by chili555 on 2015-05-16
Glad it's working. Please make note of my comment:> It should work until a later kernel is installed, then recompile as above and rebootYou should retain the files for that time.

I am glad to tell you and the searchers how I knew what driver to use. First, the usb.id or, in the case of PCI devices, the pci.id is everything. Using your device as an example, we see:> Bus 008 Device 002: ID [COLOR="#FF0000"]2001:3314[/COLOR] D-Link Corp. I then search Google for the usb.id of 2001:3314 and I get a very helpful site: [https://wikidevi.com/wiki/D-Link_DWA-171_rev_A1](https://wikidevi.com/wiki/D-Link_DWA-171_rev_A1)> Probable Linux driver
Realtek's vendor driver ([COLOR="#FF0000"]8812au[/COLOR])I happen to have the driver on my system and so I check its modaliases:```
$ modinfo Downloads/rtl8812AU_8821AU_linux/8812au.ko
filename:       /home/chili/Downloads/rtl8812AU_8821AU_linux/8812au.ko
version:        v4.2.2_7502.20130517
author:         Realtek Semiconductor Corp.
description:    Realtek Wireless Lan Driver
license:        GPL
srcversion:     9CFFF8AC9C858EAD8E62C17
alias:          usb:v2001p3318d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p0242d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E66p0023d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v[COLOR="#FF0000"]2001[/COLOR]p[COLOR="#FF0000"]3314[/COLOR]d*dc*dsc*dp*ic*isc*ip*in*
<snip>
```As I happened to have helped another person on askubuntu.com a few days ago, I knew the most likely driver package to compile. I recommended it to you and, as you saw, it works.

Pretty simple, eh?

---

### Post by Collin_Jones on 2015-05-17
Thanks for all the help. Feels like I am at least a step or two closer

---

### Post by einsiol on 2015-08-24
> **chili555 said:**
> We're not quite done yet. When a later kernel version is installed by Update Manager, after reboot, you must recompile the driver:```
cd rtl8812AU_8821AU_linux
make clean
make
sudo make install
sudo modprobe 8812au
```Please retain the file and these instructions for that time.

I've been able to use these instructions to rebuild the driver after kernel updates (with maybe sometimes few minor issues that I managed to resolve). But after updating the system yesterday I'm having a issue when installing the driver, one I don't understand. 

The error start when I try to enable the driver with modprobe 

" modprob: ERROR: could not insert '8812au': Exec format error "

I'm not sure what this means or how to get around it to get my wlan working again. Any ideas? I'm running Ubuntu 15.04 (Gnome version)

---

### Post by Hadaka on 2015-08-24
Hi, try this..
```
sudo apt-get --reinstall install linux-image-$(uname -r)                 
```
then run your code,..
```
cd rtl8812AU_8821AU_linux
make clean
make
sudo make install
sudo modprobe 8812au
```
if it doesnt work,please post a new thread. posting on a solved old thread
doesnt allow your problem to be marked solved.
thanks.

---

### Post by einsiol on 2015-08-25
Thank you for you answer[**[COLOR=#000000] Hadaka[/COLOR]**]("http://ubuntuforums.org/member.php?u=1599436"), I hoped this could be a easy fix so I wanted to keep the answer on this thread. Your suggestion how ever did not work so I started a new thread [here]("http://ubuntuforums.org/showthread.php?t=2292112&p=13344716")

---

### Post by sonik2 on 2015-10-08
> **chili555 said:**
> With a working temporary ethernet connection:```
sudo apt-get install git
git clone https://github.com/abperiasamy/rtl8812AU_8821AU_linux.git
cd rtl8812AU_8821AU_linux
make
sudo make install
sudo modprobe 8812au
```It 'makes' with a couple of possibly harmless warnings but no errors on my 3.11.0-18 system.

Hi, I gave this a crack on my Raspberry pi 2 running Ubuntu MATE 1.8.2 but came up with an error running make 

```

sonik@Ubuntu-pi:~/rtl8812AU_8821AU_linux$ make
make ARCH=armv7l CROSS_COMPILE= -C /lib/modules/3.18.0-25-rpi2/build M=/home/sonik/rtl8812AU_8821AU_linux  modules
make[1]: *** /lib/modules/3.18.0-25-rpi2/build: No such file or directory.  Stop.
Makefile:1049: recipe for target 'modules' failed
make: *** [modules] Error 2

```

Any ideas or am I stuck because pi?

---

### Post by chili555 on 2015-10-09
> /lib/modules/3.18.0-25-rpi2/build: No such file or directory.  Stop.This usually means that the linux-headers are not installed. Can you get headers matching your installed kernel; in this case, 3.18.0-25-rpi2?

I am not an RPi guy, so I can't offer many other suggestions.

---

### Post by jose_carlos3 on 2016-02-14
Thanks!!!

---

### Post by mellocello2003 on 2016-03-28
Hi - I'm having issues with this driver, but on a 4.2.0-34 kernel (ubuntu 14.04).  The errors aren't exactly useful.

Any help would be much appreciated!

lepoop# lsusb
Bus 004 Device 004: ID 2001:3314 D-Link Corp. 
Bus 004 Device 003: ID 046d:c318 Logitech, Inc. Illuminated Keyboard
Bus 004 Device 002: ID 8087:8000 Intel Corp. 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 8087:8008 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
lepoop# uname -r
4.2.0-34-generic
lepoop# dkms build -m rtl8812AU_8821AU_linux -v 1.0               

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
'make'....
ERROR (dkms apport): binary package for rtl8812AU_8821AU_linux: 1.0 not found
Error!  Build of 8812au.ko failed for: 4.2.0-34-generic (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/rtl8812AU_8821AU_linux/1.0/build/ for more information.
lepoop# cat /var/lib/dkms/rtl8812AU_8821AU_linux/1.0/build/make.log 
DKMS make.log for rtl8812AU_8821AU_linux-1.0 for kernel 4.2.0-34-generic (x86_64)
Mon Mar 28 10:06:21 EDT 2016
make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/4.2.0-34-generic/build M=/var/lib/dkms/rtl8812AU_8821AU_linux/1.0/build  modules
make[1]: Entering directory `/usr/src/linux-headers-4.2.0-34-generic'
  Building modules, stage 2.
  MODPOST 0 modules
make[1]: Leaving directory `/usr/src/linux-headers-4.2.0-34-generic'

---

### Post by mellocello2003 on 2016-03-28
Forgot to mention that I'm running 64-bit ubuntu 14.04.  Thanks...

---

### Post by chili555 on 2016-03-28
I just tried, and then wrote, this process on my 4.2.0-xx kernel a few days ago: [http://askubuntu.com/questions/750267/just-installed-ubuntu-how-do-i-install-internet-drivers/750433#750433](http://askubuntu.com/questions/750267/just-installed-ubuntu-how-do-i-install-internet-drivers/750433#750433)

Please try it and let me know if you encounter any errors.

---

### Post by jeremy31 on 2016-04-01
They somehow broke the makefile, this one still works [https://github.com/gnab/rtl8812au](https://github.com/gnab/rtl8812au)

---

### Post by vincezd on 2017-01-13
Thank you, it also worked for me. Notice that I entered:                " sudo modprobe rtl8812au # instead of just 8812au. I found it with TAB completion.      "  Also, for those that don't have the internet and fail to install the git package, you can download the driver up to date sources in a zip format from github ([https://github.com/abperiasamy/rtl8812AU_8821AU_linux](https://github.com/abperiasamy/rtl8812AU_8821AU_linux) and the green button "clone or download").

---

