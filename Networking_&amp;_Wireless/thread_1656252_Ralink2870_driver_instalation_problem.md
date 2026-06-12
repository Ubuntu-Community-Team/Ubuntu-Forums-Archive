---
title: "Ralink2870 driver instalation problem"
date: 2010-12-30
forum: Networking &amp; Wireless
---

### Post by Mr. ViC on 2010-12-30
I'm really getting a damn big headache here.

I am running Ubuntu 10.14 Maverick.

Followed this tutorial:

```
[http://ubuntuforums.org/showthread.php?t=1342593](http://ubuntuforums.org/showthread.php?t=1342593)
```Followed for my 2870sta, everything went fine until this step:

```
cd ~/Desktop/*2870*
(If you're trying to compile a second time, please note: Run "make clean" before running "make" to remove your previous attempt.)
make
sudo make install
```When entering make, there's some errors at the end. Here's the log:

```
dave@ViTALiTY:~/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1$ make
make -C tools
make[1]: Entering directory `/home/dave/Desktop/2010_0709_RT2870_Linux_STA_v[2.4.0.1/tools]("http://2.4.0.1/tools")'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/dave/Desktop/2010_0709_RT2870_Linux_STA_v[2.4.0.1/tools]("http://2.4.0.1/tools")'
/home/dave/Desktop/2010_0709_RT2870_Linux_STA_v[2.4.0.1/tools/bin2h]("http://2.4.0.1/tools/bin2h")
cp -f os/linux/Makefile.6 /home/dave/Desktop/2010_0709_RT2870_Linux_STA_v[2.4.0.1/os/linux/Makefile]("http://2.4.0.1/os/linux/Makefile")
make -C /lib/modules/2.6.35-24-generic/build SUBDIRS=/home/dave/Desktop/2010_0709_RT2870_Linux_STA_v[2.4.0.1/os/linux]("http://2.4.0.1/os/linux") modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-24-generic'
  CC [M]  /home/dave/Desktop/2010_0709_RT2870_Linux_STA_v[2.4.0.1/os/linux/../../common/cmm_mac_usb.o]("http://2.4.0.1/os/linux/../../common/cmm_mac_usb.o")
/home/dave/Desktop/2010_0709_RT2870_Linux_STA_v[2.4.0.1/os/linux/../../common/cmm_mac_usb.c]("http://2.4.0.1/os/linux/../../common/cmm_mac_usb.c"): In function &#8216;RTMPAllocUsbBulkBufStruct&#8217;:
/home/dave/Desktop/2010_0709_RT2870_Linux_STA_v[2.4.0.1/os/linux/../../common/cmm_mac_usb.c:52]("http://2.4.0.1/os/linux/../../common/cmm_mac_usb.c:52"): error: implicit declaration of function &#8216;usb_buffer_alloc&#8217;
/home/dave/Desktop/2010_0709_RT2870_Linux_STA_v[2.4.0.1/os/linux/../../common/cmm_mac_usb.c:52]("http://2.4.0.1/os/linux/../../common/cmm_mac_usb.c:52"): warning: assignment makes pointer from integer without a cast
/home/dave/Desktop/2010_0709_RT2870_Linux_STA_v[2.4.0.1/os/linux/../../common/cmm_mac_usb.c]("http://2.4.0.1/os/linux/../../common/cmm_mac_usb.c"): In function &#8216;RTMPFreeUsbBulkBufStruct&#8217;:
/home/dave/Desktop/2010_0709_RT2870_Linux_STA_v[2.4.0.1/os/linux/../../common/cmm_mac_usb.c:78]("http://2.4.0.1/os/linux/../../common/cmm_mac_usb.c:78"): error: implicit declaration of function &#8216;usb_buffer_free&#8217;
/home/dave/Desktop/2010_0709_RT2870_Linux_STA_v[2.4.0.1/os/linux/../../common/cmm_mac_usb.c]("http://2.4.0.1/os/linux/../../common/cmm_mac_usb.c"): In function &#8216;RTMPFreeTxRxRingMemory&#8217;:
/home/dave/Desktop/2010_0709_RT2870_Linux_STA_v[2.4.0.1/os/linux/../../common/cmm_mac_usb.c:234]("http://2.4.0.1/os/linux/../../common/cmm_mac_usb.c:234"): warning: passing argument 3 of &#8216;RTMPFreeUsbBulkBufStruct&#8217; from incompatible pointer type
/home/dave/Desktop/2010_0709_RT2870_Linux_STA_v[2.4.0.1/os/linux/../../common/cmm_mac_usb.c:62]("http://2.4.0.1/os/linux/../../common/cmm_mac_usb.c:62"): note: expected &#8216;UCHAR **&#8217; but argument is of type &#8216;struct __TX_BUFFER **&#8217;
/home/dave/Desktop/2010_0709_RT2870_Linux_STA_v[2.4.0.1/os/linux/../../common/cmm_mac_usb.c:241]("http://2.4.0.1/os/linux/../../common/cmm_mac_usb.c:241"): warning: passing argument 3 of &#8216;RTMPFreeUsbBulkBufStruct&#8217; from incompatible pointer type
/home/dave/Desktop/2010_0709_RT2870_Linux_STA_v[2.4.0.1/os/linux/../../common/cmm_mac_usb.c:62]("http://2.4.0.1/os/linux/../../common/cmm_mac_usb.c:62"): note: expected &#8216;UCHAR **&#8217; but argument is of type &#8216;struct __TX_BUFFER **&#8217;
/home/dave/Desktop/2010_0709_RT2870_Linux_STA_v[2.4.0.1/os/linux/../../common/cmm_mac_usb.c:278]("http://2.4.0.1/os/linux/../../common/cmm_mac_usb.c:278"): warning: passing argument 3 of &#8216;RTMPFreeUsbBulkBufStruct&#8217; from incompatible pointer type
/home/dave/Desktop/2010_0709_RT2870_Linux_STA_v[2.4.0.1/os/linux/../../common/cmm_mac_usb.c:62]("http://2.4.0.1/os/linux/../../common/cmm_mac_usb.c:62"): note: expected &#8216;UCHAR **&#8217; but argument is of type &#8216;struct __HTTX_BUFFER **&#8217;
/home/dave/Desktop/2010_0709_RT2870_Linux_STA_v[2.4.0.1/os/linux/../../common/cmm_mac_usb.c]("http://2.4.0.1/os/linux/../../common/cmm_mac_usb.c"): In function &#8216;NICInitTransmit&#8217;:
/home/dave/Desktop/2010_0709_RT2870_Linux_STA_v[2.4.0.1/os/linux/../../common/cmm_mac_usb.c:507]("http://2.4.0.1/os/linux/../../common/cmm_mac_usb.c:507"): warning: passing argument 3 of &#8216;RTMPFreeUsbBulkBufStruct&#8217; from incompatible pointer type
/home/dave/Desktop/2010_0709_RT2870_Linux_STA_v[2.4.0.1/os/linux/../../common/cmm_mac_usb.c:62]("http://2.4.0.1/os/linux/../../common/cmm_mac_usb.c:62"): note: expected &#8216;UCHAR **&#8217; but argument is of type &#8216;struct __TX_BUFFER **&#8217;
/home/dave/Desktop/2010_0709_RT2870_Linux_STA_v[2.4.0.1/os/linux/../../common/cmm_mac_usb.c]("http://2.4.0.1/os/linux/../../common/cmm_mac_usb.c"): In function &#8216;RTMPAllocTxRxRingMemory&#8217;:
/home/dave/Desktop/2010_0709_RT2870_Linux_STA_v[2.4.0.1/os/linux/../../common/cmm_mac_usb.c:566]("http://2.4.0.1/os/linux/../../common/cmm_mac_usb.c:566"): warning: passing argument 3 of &#8216;RTMPAllocUsbBulkBufStruct&#8217; from incompatible pointer type
/home/dave/Desktop/2010_0709_RT2870_Linux_STA_v[2.4.0.1/os/linux/../../common/cmm_mac_usb.c:34]("http://2.4.0.1/os/linux/../../common/cmm_mac_usb.c:34"): note: expected &#8216;VOID **&#8217; but argument is of type &#8216;struct __HTTX_BUFFER **&#8217;
/home/dave/Desktop/2010_0709_RT2870_Linux_STA_v[2.4.0.1/os/linux/../../common/cmm_mac_usb.c:596]("http://2.4.0.1/os/linux/../../common/cmm_mac_usb.c:596"): warning: passing argument 3 of &#8216;RTMPAllocUsbBulkBufStruct&#8217; from incompatible pointer type
/home/dave/Desktop/2010_0709_RT2870_Linux_STA_v[2.4.0.1/os/linux/../../common/cmm_mac_usb.c:34]("http://2.4.0.1/os/linux/../../common/cmm_mac_usb.c:34"): note: expected &#8216;VOID **&#8217; but argument is of type &#8216;struct __TX_BUFFER **&#8217;
/home/dave/Desktop/2010_0709_RT2870_Linux_STA_v[2.4.0.1/os/linux/../../common/cmm_mac_usb.c:610]("http://2.4.0.1/os/linux/../../common/cmm_mac_usb.c:610"): warning: passing argument 3 of &#8216;RTMPAllocUsbBulkBufStruct&#8217; from incompatible pointer type
/home/dave/Desktop/2010_0709_RT2870_Linux_STA_v[2.4.0.1/os/linux/../../common/cmm_mac_usb.c:34]("http://2.4.0.1/os/linux/../../common/cmm_mac_usb.c:34"): note: expected &#8216;VOID **&#8217; but argument is of type &#8216;struct __TX_BUFFER **&#8217;
/home/dave/Desktop/2010_0709_RT2870_Linux_STA_v[2.4.0.1/os/linux/../../common/cmm_mac_usb.c:628]("http://2.4.0.1/os/linux/../../common/cmm_mac_usb.c:628"): warning: passing argument 3 of &#8216;RTMPAllocUsbBulkBufStruct&#8217; from incompatible pointer type
/home/dave/Desktop/2010_0709_RT2870_Linux_STA_v[2.4.0.1/os/linux/../../common/cmm_mac_usb.c:34]("http://2.4.0.1/os/linux/../../common/cmm_mac_usb.c:34"): note: expected &#8216;VOID **&#8217; but argument is of type &#8216;UCHAR **&#8217;
make[2]: *** [/home/dave/Desktop/2010_0709_RT2870_Linux_STA_v[2.4.0.1/os/linux/../../common/cmm_mac_usb.o]("http://2.4.0.1/os/linux/../../common/cmm_mac_usb.o")] Error 1
make[1]: *** [_module_/home/dave/Desktop/2010_0709_RT2870_Linux_STA_v[2.4.0.1/os/linux]("http://2.4.0.1/os/linux")] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-24-generic'
make: *** [LINUX] Error 2
```Then, when I try to run:

```
sudo make install
```This happens:

```
dave@ViTALiTY:~/Desktop/2010_0709_RT2870_Linux_STA_v2.4.0.1$ sudo make install
make -C /home/dave/Desktop/2010_0709_RT2870_Linux_STA_v[2.4.0.1/os/linux]("http://2.4.0.1/os/linux") -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/dave/Desktop/2010_0709_RT2870_Linux_STA_v[2.4.0.1/os/linux]("http://2.4.0.1/os/linux")'
rm -rf /etc/Wireless/RT2870STA
mkdir /etc/Wireless/RT2870STA
cp /home/dave/Desktop/2010_0709_RT2870_Linux_STA_v[2.4.0.1/RT2870STA.dat]("http://2.4.0.1/RT2870STA.dat") /etc/Wireless/RT2870STA/.
install -d /lib/modules/2.6.35-24-generic/kernel/drivers/net/wireless/
install -m 644 -c rt2870sta.ko /lib/modules/2.6.35-24-generic/kernel/drivers/net/wireless/
install: cannot stat `rt2870sta.ko': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/dave/Desktop/2010_0709_RT2870_Linux_STA_v[2.4.0.1/os/linux]("http://2.4.0.1/os/linux")'
make: *** [install] Error 2
```I have tried everything and I'm desperate with this. Tried to install Ubuntu again, tried to format my OS, clean everything and install again, nothing works,

Can anyone please help me out here?

---

### Post by PatchesTheCaveman on 2010-12-30
You actually don't need to build the Ralink drivers.  They are included with the wireless-compat wifi drivers backported from newer versions of the Linux kernel.  To install them, run these commands from a terminal:
```
sudo apt-get update
sudo apt-get install linux-backports-modules-wireless-maverick-generic
```

---

### Post by Mr. ViC on 2010-12-30
Hi. Done that now.

But why isn't it still recognized?

[img]http://img.myph.us/rq3.png[/img]

Shouldn't it be ra0 or something?

---

### Post by PatchesTheCaveman on 2010-12-30
Run the following command:
```
sudo modprobe rt2800usb
```

See if it works now.

> Shouldn't it be ra0 or something?

No.  This driver is included with the Linux kernel, so it follows the kernel's standard procedure of naming wireless interfaces wlanX.

---

### Post by Mr. ViC on 2010-12-30
Thanks, understood now.

Still unknown...

I have removed this:

```
blacklist rt2x00usb
blacklist rt2x00lib
blacklist rt2800usb
```

From here:

```
gksudo gedit /etc/modprobe.d/blacklist.conf
```

Tried again, it is still unknown :(

---

### Post by PatchesTheCaveman on 2010-12-30
Did you give
```
sudo modprobe rt2800usb
```
another try after you removed those items from the blacklist?

If that doesn't work, run this command:
```
uname -r
```
and paste the line it returns in a message here.  You might have a faulty update that is causing problems with USB devices.

---

### Post by Mr. ViC on 2010-12-30
Yes mate, I have tried again after removing it from the blacklist.

Here it is what returned:

```
2.6.35-24-generic
```

Thank you again for being helping me. :)

---

### Post by PatchesTheCaveman on 2010-12-30
You do have the faulty update.  You will need to reboot your computer.

If you do not dual-boot with Windows or another operating system, you'll need to hold the SHIFT key **before** Ubuntu starts.  This will bring up the GRUB menu.  (If you dual-boot, you always get the GRUB menu.)

From that menu, press the down arrow to choose the Ubuntu entry that lists the 2.6.35-23-generic kernel and press Enter.  (If you don't have that one, pick any one but the 2.6.35-24-generic one.)  Your system should then boot normally.  If you're lucky, your USB wireless dongle will now work properly.

To remove the faulty kernel so you don't have to select it every time you start the computer, run the following commands:
```
sudo apt-get remove linux-image-2.6.35-24-generic
sudo apt-get --reinstall install linux-image-2.6.35-23-generic
```

That will also install the most recent version of the kernel that works properly.  (I'm having people do that to make double sure they'll have a working system when they reboot.)

---

### Post by Mr. ViC on 2010-12-30
Got it!

Everything works great now!

Thank you very much again. :P

---

