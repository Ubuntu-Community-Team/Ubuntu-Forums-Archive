---
title: "How to compile acx 100/111 driver in Karmic (FIXED)"
date: 2009-11-09
forum: Networking &amp; Wireless
---

### Post by sechole on 2009-11-09
I´m glad to announce that there is a patch to compile acx 100/111 driver in kernel 2.6.31 
Just follow this instructions:

mkdir acx
cd acx
wget [http://downloads.sourceforge.net/acx100/acx-20080210.tar.bz2](http://downloads.sourceforge.net/acx100/acx-20080210.tar.bz2)
tar xjvf acx-20080210.tar.bz2
wget [http://cc.oulu.fi/~rantalai/acx_karmic.patch](http://cc.oulu.fi/~rantalai/acx_karmic.patch)
patch -p0 < acx_karmic.patch
cd acx-20080210/
make -C /lib/modules/`uname -r`/build M=`pwd`

Load de kernel module
sudo insmod acx.ko

And that's all folks!

Could someone submit the patch to the Ubuntu kernel team?

---

### Post by dmizer on 2009-11-09
> **sechole said:**
> I´m glad to announce that there is a patch to compile acx 100/111 driver in kernel 2.6.31 
Just follow this instructions:

mkdir acx
cd acx
wget [http://downloads.sourceforge.net/acx100/acx-20080210.tar.bz2](http://downloads.sourceforge.net/acx100/acx-20080210.tar.bz2)
tar xjvf acx-20080210.tar.bz2
wget [http://cc.oulu.fi/~rantalai/acx_karmic.patch](http://cc.oulu.fi/~rantalai/acx_karmic.patch)
patch -p0 < acx_karmic.patch
cd acx-20080210/
make -C /lib/modules/`uname -r`/build M=`pwd`

Load de kernel module
sudo insmod acx.ko

And that's all folks!

Could someone submit the patch to the Ubuntu kernel team?

To get a patch applied, you'll need to open a bug report: [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs) Once the bug has been reported, then you can submit the patch and the devs will review it and apply it if possible.

---

### Post by notbad on 2009-11-20
does not work for me:(

tomas@tomas-desktop:~$ sudo modprobe -v acx
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
FATAL: Module acx not found.

tomas@tomas-desktop:~$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
airplus : driver installed
	device (104C:8400) present

tomas@tomas-desktop:~$ sudo modprobe ndiswrapper
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
FATAL: Module ndiswrapper not found.

in 9.04 everything worked with ndiswrapper

---

### Post by dmizer on 2009-11-20
> **notbad said:**
> does not work for me:(

tomas@tomas-desktop:~$ sudo modprobe -v acx
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
FATAL: Module acx not found.

tomas@tomas-desktop:~$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
airplus : driver installed
	device (104C:8400) present

tomas@tomas-desktop:~$ sudo modprobe ndiswrapper
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
FATAL: Module ndiswrapper not found.

in 9.04 everything worked with ndiswrapper

Everyone I've encountered indicates that ndiswrapper STILL works in Karmic. Try installing the ndisgtk package. After that, you may be able to get a successful response with:
```
sudo modprobe ndiswrapper
```

---

### Post by aapo4 on 2009-11-21
Notbad, there are two (very) different way to use acx driver. You first tried this:

```
modprobe acx

```
This is native driver. And problem is that driver is removed from Karmic (actually kernel 2.6.31, Karmic can be run on older kernel too).
(Therefor error message was: FATAL: Module acx not found.)

You can compile this module by yourself with instructions on first post by sechole.


Second way is use ndiswrapper which uses driver from windows.
apt-get install ndisgtk
modprobe ndiswrapper
find needed windows driver.


dmizer, what is right package to make bug report against? Kernel? Or maybe firmware?
name of bug: "acx kernel module removed"?

---

### Post by notbad on 2009-11-21
none of your suggestions works. ive done everything i could but ndisgtk does not see my pci card: error pops oppening: we do not see any hardware or smthg and Could not find a network configuration tool.

thats it im about to go back to 9.04 or to buy a new wireless adapter:D

---

### Post by aapo4 on 2009-11-21
> none of your suggestions works

You only told how one of these fails.
Did you get acx module compiled? What it said when you tried modprobe it? 
It is the same driver used before and maybe we can get it back to Ubuntu (or maybe it is dropped by upstream) if people report that it is still working.


Do you have other kernel installed? Is there rows in grub already? You can test these, older kernels (2.6.27 and 2.6.28 ) have acx, but they may miss some other needed features. E.g  2.6.27 has acx, but not support ext4.

---

### Post by notbad on 2009-11-21
tomas@tomas-desktop:~/acx/acx-20080210$ make -C /lib/modules/`uname -r`/build M=`pwd`
make: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
  CC [M]  /home/tomas/acx/acx-20080210/ioctl.o
  LD [M]  /home/tomas/acx/acx-20080210/acx.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: modpost: Found 3 section mismatch(es).
To see full details build your kernel with:
'make CONFIG_DEBUG_SECTION_MISMATCH=y'
  LD [M]  /home/tomas/acx/acx-20080210/acx.ko
make: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'

lspci -v:
02:0a.0 Network controller: Texas Instruments ACX 100 22Mbps Wireless Interface
	Subsystem: D-Link System Inc Device 3b01
	Flags: bus master, medium devsel, latency 32, IRQ 11
	I/O ports at c000 [size=32]
	Memory at ee010000 (32-bit, non-prefetchable) [size=4K]
	Memory at ee000000 (32-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>

tomas@tomas-desktop:~$ uname -a
Linux tomas-desktop 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux

tomas@tomas-desktop:~$ modprobe acx
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
FATAL: Module acx not found.

tomas@tomas-desktop:~$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
airplus : driver installed
	device (104C:8400) present

tomas@tomas-desktop:~$ dpkg -l|grep linux-image
ii  linux-image-2.6.31-14-generic                       2.6.31-14.48                               Linux kernel image for version 2.6.31 on x86
ii  linux-image-2.6.31-14-generic-pae                   2.6.31-14.48                               Linux kernel image for version 2.6.31 on x86
ii  linux-image-generic                                 2.6.31.14.27                               Generic Linux kernel image

so the driver is installed but the modules are not being loaded

---

### Post by aapo4 on 2009-11-21
Do not use 'modprobe acx', it is looking module under system directories. If this log text is not snapped you were only just compiled it (not installed)


Give full or relative path to acx.ko you are just produced.
```
sudo insmod acx.ko
```
And it should not say FATAL: Module acx not found.

And with this solution you do not need ndiswrapper at all.

First check iwconfig, is there any wlan (maybe not). Then clear log take module and check messages
```
sudo dmesg -c
sudo insmod acx.ko
dmesg
iwconfig
```

---

### Post by notbad on 2009-11-21
i gave up trying;) but thanks for the help;)

---

### Post by johnys on 2009-11-21
Sorry, bit of a Ubuntu neophyte here. What exactly does "Load de kernel module" entail?

---

### Post by johnys on 2009-11-21
Well, I lost patience and just got it working with ndiswrapper. Still would like to know what it means, though.

---

### Post by iseppo on 2009-11-23
> **johnys said:**
> Well, I lost patience and just got it working with ndiswrapper. Still would like to know what it means, though.

Loading akernel module is this 
sudo modprobe MODULENAME 
part. (Dont know if this was what you meant with your question though).

So ndiswrapper works well with acx-based cards? I was considering buying a new card but perhaps will try this first.

---

### Post by dmizer on 2009-11-23
> **iseppo said:**
> So ndiswrapper works well with acx-based cards? I was considering buying a new card but perhaps will try this first.

Yes.

Here is a howto for acx111 cards: [http://ubuntuforums.org/showthread.php?t=324148](http://ubuntuforums.org/showthread.php?t=324148)

Some people are reporting problems with trying to modprobe ndiswrapper in Karmic, but I'm not sure why. It's working perfectly for me in Karmic.

---

### Post by JungleBeast on 2009-11-24
Hello there,
The above walk through looks really good. 
Would it be possible to do another walk through but for people who don't have internet on the machine they're trying to get working with wireless?

In my case I have a dual boot, with a fresh karmic install which has no net until i get wireless working, and a happy version of jaunty with wireless working on another drive.

The problem i'm having is that the wget line for the karmic patch seems to do a fair bit more than just download a file. 



Thanks!

---

### Post by jvnn on 2009-12-06
OK, I'll bite.  I'm in the exact same boat, D-link card with acx 100 chipset.

Seems I had an error in the make - dunno what to do about that.
and the modprobe thing - I'm stuck atm.
Here's what I've done so far:

jvnn@jvnn-desktop:~$ mkdir acx
jvnn@jvnn-desktop:~$ cd acx
jvnn@jvnn-desktop:~/acx$ wget [http://downloads.sourceforge.net/acx100/acx-20080210.tar.bz2](http://downloads.sourceforge.net/acx100/acx-20080210.tar.bz2)

jvnn@jvnn-desktop:~/acx$ tar xjvf acx-20080210.tar.bz2
jvnn@jvnn-desktop:~/acx$ wget [http://cc.oulu.fi/~rantalai/acx_karmic.patch](http://cc.oulu.fi/~rantalai/acx_karmic.patch)
jvnn@jvnn-desktop:~/acx$ sudo apt-get install patch
jvnn@jvnn-desktop:~/acx$ patch -p0 < acx_karmic.patch

jvnn@jvnn-desktop:~/acx$ cd acx-20080210/
jvnn@jvnn-desktop:~/acx/acx-20080210$ make -C /lib/modules/`uname -r`/build M=`pwd`
make: Entering directory `/usr/src/linux-headers-2.6.31-16-generic'
  LD      /home/jvnn/acx/acx-20080210/built-in.o
  CC [M]  /home/jvnn/acx/acx-20080210/wlan.o
  CC [M]  /home/jvnn/acx/acx-20080210/conv.o
  CC [M]  /home/jvnn/acx/acx-20080210/ioctl.o
  CC [M]  /home/jvnn/acx/acx-20080210/common.o
  CC [M]  /home/jvnn/acx/acx-20080210/pci.o
  CC [M]  /home/jvnn/acx/acx-20080210/usb.o
  LD [M]  /home/jvnn/acx/acx-20080210/acx.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: modpost: Found 3 section mismatch(es).
To see full details build your kernel with:
'make CONFIG_DEBUG_SECTION_MISMATCH=y'
  CC      /home/jvnn/acx/acx-20080210/acx.mod.o
  LD [M]  /home/jvnn/acx/acx-20080210/acx.ko
make: Leaving directory `/usr/src/linux-headers-2.6.31-16-generic'

jvnn@jvnn-desktop:~/acx/acx-20080210$ modprobe acx
FATAL: Module acx not found.
jvnn@jvnn-desktop:~/acx/acx-20080210$ modprobe acx.ko
FATAL: Module acx.ko not found.

---

### Post by aapo4 on 2009-12-07
Last row should be ```
sudo insmod acx.ko
```

Without sudo it will say "insmod: error inserting 'acx.ko': -1 Operation not permitted". 

It if say "No such file or directory", there are something wrong with compiling.

acx.ko is file, you can check with 'ls' is there such a file or not.

---

### Post by chili555 on 2009-12-07
> vnn@jvnn-desktop:~/acx/acx-20080210$ modprobe acxI believe it is:```
sudo [COLOR="Red"]insmod[/COLOR] acx.ko
```Be sure you are in the correct directory first: *acx/acx-20080210*

---

### Post by jvnn on 2009-12-07
Thank you guys!
Now I'm stuck at the next step on the ladder.
I've read a few other posts re troubleshooting wireless and here are the results of some of those steps:

jvnn@jvnn-desktop:~/acx/acx-20080210$ sudo insmod acx.ko

jvnn@jvnn-desktop:~/acx/acx-20080210$ lsmod | grep 'acx'
acx                   142788  0 

jvnn@jvnn-desktop:~/acx/acx-20080210$ sudo lshw -c network
  *-network:1 UNCLAIMED
       description: Network controller
       product: ACX 100 22Mbps Wireless Interface
       vendor: Texas Instruments
       physical id: 9
       bus info: pci@0000:02:09.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=32
       resources: ioport:a400(size=32) memory:f6010000-f6010fff memory:f6000000-f600ffff

jvnn@jvnn-desktop:~/acx/acx-20080210$ dmesg |grep acx
[  366.815405] acx: this driver is still EXPERIMENTAL
[  366.815408] acx: reading README file and/or Craig's HOWTO is recommended, visit [http://acx100.sf.net](http://acx100.sf.net) in case of further questions/discussion
[  366.815413] acx: compiled to use 32bit I/O access. I/O timing issues might occur, such as non-working firmware upload. Report them
[  366.815416] acx: running on a little-endian CPU
[  366.815418] acx: PCI/VLYNQ module v0.3.37 initialized, waiting for cards to probe...
[  366.815481] acx_pci 0000:02:09.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[  366.815512] acx: found ACX100-based wireless network card at 0000:02:09.0, irq:21, phymem1:0xF6010000, phymem2:0xF6000000, mem1:0xf8082000, mem1_size:4096, mem2:0xf82e0000, mem2_size:65536
[  366.815561] acx: need to load firmware for acx100 chipset with radio ID 0d, please provide via firmware hotplug:
[  366.815563] acx: either one file only (<c>ombined firmware image file, radio-specific) or two files (radio-less base image file *plus* separate <r>adio-specific extension file)
[  366.815569] requesting firmware image 'tiacx100c0D'
[  366.815573] acx_pci 0000:02:09.0: firmware: requesting tiacx100c0D
[  366.843410] acx: firmware image 'tiacx100c0D' was not provided. Check your hotplug scripts
[  366.843420] requesting firmware image 'tiacx100'
[  366.843429] acx_pci 0000:02:09.0: firmware: requesting tiacx100
[  366.849779] acx: firmware image 'tiacx100' was not provided. Check your hotplug scripts
[  366.849786] acx: reset_dev() FAILED
[  366.849822] acx_pci 0000:02:09.0: PCI INT A disabled
[  366.864817] acx_pci: probe of 0000:02:09.0 failed with error -5
[  366.864942] usbcore: registered new interface driver acx_usb

---

### Post by jvnn on 2009-12-07
I'm burning a lot of time on this, anybody else able to help me out?

I just added info about this to [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/259182](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/259182)

It seems my problem and that bug are similar/identical.

Thanks everyone!

---

### Post by aapo4 on 2009-12-07
jvnn, driver is now loaded. Then you need firmware image. ("requesting firmware image 'tiacx100' ")

I read you have working Feisty. First try use firmware image from Feisty. /lib/firmware/acx contains subdirectories named by version number. Check is there anywhere exact 'tiacx100c0D' and then common 'tiacx100'. Copy to /lib/firmware of Karmic.


Then insmod driver and check what dmesg says (and iwconfig).

---

### Post by jvnn on 2009-12-07
Still no success, but fascinating...

And btw, thanks for helping me out with this!

In the feisty install I have:
jvnn@jvnn-desktop:/lib/firmware/2.6.20-17-generic/acx$ ls
0.1.0.11  0.4.11.9  1.0.9     1.2.1.34  1.9.8.b   default
0.4.11.4  1.0.7     1.2.0.30  1.7.0     2.3.1.31  readme.txt

In the Karmic install the acx directory is already sitting below firmware instead of in the kernel-specific directory.
I didn't copy it to there, that's what I saw when I looked there!?!


jvnn@jvnn-desktop:/lib/firmware/acx$ ls
0.1.0.11  0.4.11.9  1.0.9     1.2.1.34  1.9.8.b   default
0.4.11.4  1.0.7     1.2.0.30  1.7.0     2.3.1.31

-----------
-----------
none of the different directories contain a file named 'tiacx100c0D'
However there are files 'tiacx100' and 'tiacx100r0D' in the default and several other directories.


I tried insmod again and the results seem the same as before:
jvnn@jvnn-desktop:/lib/firmware/acx$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

jvnn@jvnn-desktop:~/acx/acx-20080210$ dmesg |grep acx
[  284.819872] acx: this driver is still EXPERIMENTAL
[  284.819884] acx: reading README file and/or Craig's HOWTO is recommended, visit [http://acx100.sf.net](http://acx100.sf.net) in case of further questions/discussion
[  284.819891] acx: compiled to use 32bit I/O access. I/O timing issues might occur, such as non-working firmware upload. Report them
[  284.819897] acx: running on a little-endian CPU
[  284.819899] acx: PCI/VLYNQ module v0.3.37 initialized, waiting for cards to probe...
[  284.819989] acx_pci 0000:02:09.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[  284.822881] acx: found ACX100-based wireless network card at 0000:02:09.0, irq:21, phymem1:0xF6010000, phymem2:0xF6000000, mem1:0xf8124000, mem1_size:4096, mem2:0xf8300000, mem2_size:65536
[  284.822956] acx: need to load firmware for acx100 chipset with radio ID 0d, please provide via firmware hotplug:
[  284.822960] acx: either one file only (<c>ombined firmware image file, radio-specific) or two files (radio-less base image file *plus* separate <r>adio-specific extension file)
[  284.822969] requesting firmware image 'tiacx100c0D'
[  284.822977] acx_pci 0000:02:09.0: firmware: requesting tiacx100c0D
[  284.851166] acx: firmware image 'tiacx100c0D' was not provided. Check your hotplug scripts
[  284.851177] requesting firmware image 'tiacx100'
[  284.851183] acx_pci 0000:02:09.0: firmware: requesting tiacx100
[  284.857702] acx: firmware image 'tiacx100' was not provided. Check your hotplug scripts
[  284.857709] acx: reset_dev() FAILED
[  284.857748] acx_pci 0000:02:09.0: PCI INT A disabled
[  284.872081] acx_pci: probe of 0000:02:09.0 failed with error -5
[  284.872185] usbcore: registered new interface driver acx_usb

---

### Post by aapo4 on 2009-12-08
Try 
```
sudo cp /lib/firmware/2.6.20-17-generic/acx/default/tiacx100 /lib/firmware/
```

And then sudo insmod acx.ko

For some reason driver (acx.ko) doesn't see firmware image (tiacx100).


There are firmware images, but maybe they are same than you have in /lib/firmware/2.6.20-17-generic/acx.
[http://acx100.erley.org/acx/fw/](http://acx100.erley.org/acx/fw/)

I do not know do you need both tiacx100c0D and tiacx100. (And where to get tiacx100c0D? Is it same than tiacx100**r**0D?)
This link is about that issue, but I do not understand what it says: [http://acx100.sourceforge.net/wiki/Firmware](http://acx100.sourceforge.net/wiki/Firmware)

This is from manual, but what it means?
c=combined
r=radio only

---

### Post by jvnn on 2009-12-08
ok, got that.

```
jvnn@jvnn-desktop:/media/496297a5-e668-459f-a8d4-b0ea51ccffb2/lib/firmware/2.6.20-17-generic/acx$ cd default
jvnn@jvnn-desktop:/media/496297a5-e668-459f-a8d4-b0ea51ccffb2/lib/firmware/2.6.20-17-generic/acx/default$ ls
tiacx100     tiacx100r11  tiacx100usb  tiacx111c17
tiacx100r0D  tiacx100r15  tiacx111c16  tiacx111c19
jvnn@jvnn-desktop:/media/496297a5-e668-459f-a8d4-b0ea51ccffb2/lib/firmware/2.6.20-17-generic/acx/default$ sudo cp tiacx100 /lib/firmware/[sudo] password for jvnn: 
jvnn@jvnn-desktop:/media/496297a5-e668-459f-a8d4-b0ea51ccffb2/lib/firmware/2.6.20-17-generic/acx/default$ 
```

Now we have an improvement!

```
jvnn@jvnn-desktop:~/acx/acx-20080210$ sudo insmod acx.ko

jvnn@jvnn-desktop:~/acx/acx-20080210$ dmesg | grep acx
[ 2020.672029] acx_set_status(1):SCANNING

jvnn@jvnn-desktop:~/acx/acx-20080210$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b+  ESSID:"STA55CE0E"  Nickname:"acx v0.3.37"
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:22 Mb/s   Tx-Power=18 dBm   Sensitivity=64/255  
          Retry min limit:7   RTS thr:off   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

jvnn@jvnn-desktop:~/acx/acx-20080210$ lshw -c network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: 82562EZ 10/100 Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 02
       serial: 00:11:09:8e:72:e5
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI firmware=N/A ip=192.168.2.8 latency=32 maxlatency=56 mingnt=8 multicast=yes
       resources: irq:20 memory:f6011000-f6011fff ioport:a000(size=64)
  *-network:1
       description: Wireless interface
       product: ACX 100 22Mbps Wireless Interface
       vendor: Texas Instruments
       physical id: 9
       bus info: pci@0000:02:09.0
       logical name: wlan0
       version: 00
       serial: 00:40:05:55:ce:0e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=acx_pci latency=32 multicast=yes wireless=IEEE 802.11b+
       resources: irq:21 ioport:a400(size=32) memory:f6010000-f6010fff memory:f6000000-f600ffff

```

Ok this looks much better.
I have edited my connection, but it won't connect now !?!

Thanks for all your help aapo4!

---

### Post by aapo4 on 2009-12-08
Clear dmesg with sudo dmesg -c

Then insmod and check is there something in dmesg.

Check ```
iwlist wlan0 scan
```

It should show wireless networks or dumb errors to dmesg.

If there are errors about radio, then maybe you could try what happens if you copy tiacx100r0D to /lib/firmware before insmod (you can sudo rmmod acx).

I'm not sure but maybe tiacx100c0D = tiacx100 + tiacx100r0D. And first it search tiacx100c0D. If it doesn't exist it search tiacx100 (I think it now finds this) and tiacx100r0D (maybe this is still wrong place).

---

### Post by jvnn on 2009-12-08
OK, got that, I did a restart also.
```
jvnn@jvnn-desktop:/lib/firmware$ sudo rmmod acx
ERROR: Module acx does not exist in /proc/modules

jvnn@jvnn-desktop:/lib/firmware$ sudo insmod /home/jvnn/acx/acx-20080210/acx.ko

jvnn@jvnn-desktop:/lib/firmware$ dmesg | grep acx

[ 1369.152024] acx_set_status(1):SCANNING
[ 1369.166152] acx: unknown EID 45 in mgmt frame at offset 76. IE: 2D 1A 1C 18 1A FF FF 00 00 00 00 00 00 00 00 00
[ 1369.166177] acx: unknown EID 61 in mgmt frame at offset 104. IE: 3D 16 0B 08 03 00 00 00 00 00 00 00 00 00 00 00
[ 1369.177024] acx_set_status(1):SCANNING
[ 1369.200029] acx_set_status(1):SCANNING
[ 1369.224048] acx_set_status(1):SCANNING
[ 1369.248024] acx_set_status(1):SCANNING
[ 1369.268575] acx: unknown EID 45 in mgmt frame at offset 76. IE: 2D 1A 1C 18 1A FF FF 00 00 00 00 00 00 00 00 00
[ 1369.268600] acx: unknown EID 61 in mgmt frame at offset 104. IE: 3D 16 0B 08 03 00 00 00 00 00 00 00 00 00 00 00
[ 1369.273031] acx_set_status(1):SCANNING
[ 1369.296025] acx_set_status(1):SCANNING
[ 1371.376036] acx_set_status(1):SCANNING
[ 1371.400028] acx_set_status(1):SCANNING
[ 1371.419275] acx: unknown EID 45 in mgmt frame at offset 76. IE: 2D 1A 1C 18 1A FF FF 00 00 00 00 00 00 00 00 00
[ 1371.419300] acx: unknown EID 61 in mgmt frame at offset 104. IE: 3D 16 0B 08 03 00 00 00 00 00 00 00 00 00 00 00
[ 1371.424031] acx_set_status(1):SCANNING
[ 1371.448029] acx_set_status(1):SCANNING
[ 1371.472025] acx_set_status(1):SCANNING
[ 1371.496027] acx_set_status(1):SCANNING
[ 1371.520025] acx_set_status(1):SCANNING
[ 1371.521688] acx: unknown EID 45 in mgmt frame at offset 76. IE: 2D 1A 1C 18 1A FF FF 00 00 00 00 00 00 00 00 00
[ 1371.521712] acx: unknown EID 61 in mgmt frame at offset 104. IE: 3D 16 0B 08 03 00 00 00 00 00 00 00 00 00 00 00
[ 1371.544040] acx_set_status(1):SCANNING
[ 1371.568022] acx_set_status(1):SCANNING

jvnn@jvnn-desktop:/lib/firmware$ iwlist wlan0 scan
wlan0     No scan results

```


On a side note, firefox is crashing often and a window popped up saying "the volume "var" has only 25.4 mb disk space remaining.
So I restarted and did this because they were all huge.
```
jvnn@jvnn-desktop:/var/log$ sudo rm syslog
jvnn@jvnn-desktop:/var/log$ sudo rm messages
jvnn@jvnn-desktop:/var/log$ sudo rm kern.log

```
I have to do that again, every time I do the insmod I get that disk space error.

---

### Post by jvnn on 2009-12-08
ok, secondary problem coming up,
This time the disk space error isn't due to items in /var/log.
Now I have large files in /var/cache/apt and /var/lib.

I guess creating a separate partition for /var was a mistake...

any suggestions?

---

### Post by chili555 on 2009-12-08
> jvnn@jvnn-desktop:/var/log$ sudo rm messagesBefore you do this, why not read *messages* and see what is filling it up so fast? Maybe it's an issue we can fix, rather than just shooting the messenger.```
sudo tail -n 25 /var/log/messages
```

---

### Post by jvnn on 2009-12-08
> **chili555 said:**
> Before you do this, why not read *messages* and see what is filling it up so fast? Maybe it's an issue we can fix, rather than just shooting the messenger.```
sudo tail -n 25 /var/log/messages
```

Cause I'm a noob and thought maybe the system would re-create the message file next time around.
Seems that's not the case and I would appreciate a hand putting thing back properly.

Maybe if I create the files again, the system will resume using them?

Thanks - Joel

---

### Post by chili555 on 2009-12-08
> maybe the system would re-create the message file next time around.As far as I know, it should. Please look at:```
ls /var/log
```Aren't all these message files you removed recreated?> I guess creating a separate partition for /var was a mistake...Probably not. I'd guess you just made it too small. Find out with:```
df -h
```My /var, for comparison, takes up 642 MB. I'd suggest at least 2 GB.

You can probably --- carefully --- resize it using qparted here: [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)

WARNING: The purpose of running qparted in a live CD format is that the partitions to be resized must be unmounted. Please read the directions carefully, twice, and back up any critical data before you proceed.

---

### Post by jvnn on 2009-12-08
Thanks Chili,

Apparently the system did not re-create them, cause I couldn't find them after a restart.
I made new ones and the system is using them...

I'll do that re-size bit. I initially made /var 1 GB so I'll bump it to 2GB.
I don't have much to lose on this drive yet - it's a new install I'm trying to get up and running.
Does the system ever do housecleaning on those files?  I imagine it must or they'd eventually take over the world.

My background is I learned on unix boxes back in '90 and was an avid learner, but then I didn't touch a command line until around '04 and was not interested in learning much, just wanted to get the box running/limping.
Now I'm committed to avoiding microsoft and learning when I must.
Does linux have filename completion like I had in the old days?
I'd love to get that running.  I only looked at .bashrc very briefly and I don't really remember much from .cshrc...

-Joel

---

### Post by chili555 on 2009-12-08
> Does the system ever do housecleaning on those files?Yes. When the file reaches a certain size, it is transferred to messages.1 and .1 is transferred to messages.2 and gzipped. This continues until messages.4.gz, after which they are removed. My oldest messages.4.gz goes back to November 8. Other log files follow a similar process.> Does linux have filename completion like I had in the old days?Yes, in several ways. If you type a partial name and press 'Tab,' it will fill in automagically. Also, the most dangerous of all, the dreaded asterisk. The command:```
sudo rm foo*
```will remove foo, foo2, foobar, fool, fools, etc., etc. Use the command with care and proofread carefully.

Welcome back to the party! Have fun and post back if we can help you.

---

### Post by kyber on 2009-12-08
> **jvnn said:**
> ok, secondary problem coming up,
This time the disk space error isn't due to items in /var/log.
Now I have large files in /var/cache/apt and /var/lib.

I guess creating a separate partition for /var was a mistake...

any suggestions?

[http://acx100.sourceforge.net/wiki/Main_Page#Troubleshooting](http://acx100.sourceforge.net/wiki/Main_Page#Troubleshooting)
(note the part on disabling debug messages)

---

### Post by jvnn on 2009-12-09
Kyber, after reading some of the pages at SF and looking at what I'm getting out of the machine...
[http://acx100.sourceforge.net/wiki/Firmware](http://acx100.sourceforge.net/wiki/Firmware) says,
> The driver will first try, where appropriate, to load a combined (main chip + radio module) firmware. Failing that, it will try to first load the main chip's firmware image and then the one for the radio module.

In the absence of a copy of tiacx100c0D (combined firmware), it seems as though the tiacx100 (main chip) is loading now and I'm not sure about the tiacx100r0D (radio module).

I am presently running out of available time to work on this. We can't run this computer off the network cable without inconveniencing my wife so I'm back in the basement running on my feisty install which uses the wireless card beautifully.

I have 3 wireless cards; this one, a motorola WPCI810G, and a MSI 6834.
This one always got the best signal, but I'll get whichever one going that will work with Karmic...
Definitely still need help.

---

### Post by aapo4 on 2009-12-10
I got my acx wireless card working with these steps. I made bug report to Launchpad and added my solution+patch.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/495077](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/495077)

Check do this work with your card (tell me what step didn't success and what is says). Make comments to bug report, maybe we got this driver back to upstream.

---

### Post by jvnn on 2009-12-10
Thanks Aapo, I'll get to it sometime in the next day or 2...

---

