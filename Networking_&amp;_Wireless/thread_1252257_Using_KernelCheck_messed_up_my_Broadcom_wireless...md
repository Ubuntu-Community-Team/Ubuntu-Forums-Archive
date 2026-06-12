---
title: "Using KernelCheck messed up my Broadcom wireless..."
date: 2009-08-28
forum: Networking &amp; Wireless
---

### Post by Grimhound on 2009-08-28
I am in no way a skilled user yet, and so I find myself in a bit of a bind. I just got done using KernelCheck to update the kernel of Ubuntu after the action was suggested to take care of another preexisting issue I was having with Ubuntu not recognizing the hardware of my C712nr notebook computer. Upon completion of the update, I restarted only to find that my wireless no longer worked. In fact it seems as though the propriety driver was either disabled or removed entirely, and the Hardware Drivers tool no longer lists it. The wireless on my notebook was using the Broadcom driver presented by Ubuntu in the Hardware Drivers window when I first installed the OS. Is there any way to recover this to reenable my wireless card, or am I going to have to reformat with a fresh install, thus negating what I did using KernelCheck?

---

### Post by Grimhound on 2009-08-28
Is there anyone out there who could help me? I have a notebook sitting here with no internet access, and I'm about ready to reformat it just to get back a driver it gave me then took away when I updated the kernel. If that's the case, I'm about to give up on all hopes for Linux again and go back to Windows 7.

I need to get the Broadcom restricted driver operational again after updating the Linux kernel. I used KernelCheck to update it, and upon restarting found that my Ubuntu-provided Broadcom wireless card proprietary driver was no longer functioning at all.

---

### Post by kevdog on 2009-08-28
Just boot back into the older kernel.  Because kernelcheck updates to the latest vanilla kernel, the restricted broadcom drivers were not included in the kernel.  Ubuntu modifies their kernels they release to include these drivers.  I would just boot back into the old kernel, or you are going to have to download the restricted driver package and install manually.

---

### Post by Grimhound on 2009-08-28
> **kevdog said:**
> Just boot back into the older kernel.  Because kernelcheck updates to the latest vanilla kernel, the restricted broadcom drivers were not included in the kernel.  Ubuntu modifies their kernels they release to include these drivers.  I would just boot back into the old kernel, or you are going to have to download the restricted driver package and install manually.

And how would I go about downloading the restricted driver package?

---

### Post by kevdog on 2009-08-28
You need to tell me the driver you were using -- was it the wl driver or something else?  I don't know anything about your card right now other than it was a Broadcom.  There are many drivers for broadcom cards depending on the broadcom chipset number -- bcm43xx, b43, wl, ndiswrapper, etc.

---

### Post by Grimhound on 2009-08-28
Alright. Just looked it up on the install disc. The one Ubuntu gave me was "Broadcom STA wireless driver".

---

### Post by kevdog on 2009-08-28
Ok -- here is where you get the driver from:
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

What kernel version are you using?

You can get this from
uname -r

---

### Post by Grimhound on 2009-08-28
> **kevdog said:**
> Ok -- here is where you get the driver from:
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

What kernel version are you using?

You can get this from
uname -r

2.6.30.5-candela

---

### Post by kevdog on 2009-08-28
Can you install any packages lets say through a wired connection?

If you can you install this:

sudo apt-get install bcmwl-kernel-source

---

### Post by Grimhound on 2009-08-28
> **kevdog said:**
> Can you install any packages lets say through a wired connection?

If you can you install this:

sudo apt-get install bcmwl-kernel-source

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package bcmwl-kernel-source

---

### Post by kevdog on 2009-08-28
Did you enable the restricted repository tree within Synaptic or with /etc/apt/sources.list?

---

### Post by Grimhound on 2009-08-28
> **kevdog said:**
> Did you enable the restricted repository tree within Synaptic or with /etc/apt/sources.list?
The multiverse? It's already enabled.

---

### Post by kevdog on 2009-08-28
Which ubuntu release?

---

### Post by Grimhound on 2009-08-28
> **kevdog said:**
> Which ubuntu release?

9.04 Jaunty Jackalope

---

### Post by kevdog on 2009-08-28
Sorry about that package -- its only in Karmic -- can you just download the tarball from the link I gave you and follow the instructions in the readme.txt file?

---

### Post by Grimhound on 2009-08-28
> **kevdog said:**
> Sorry about that package -- its only in Karmic -- can you just download the tarball from the link I gave you and follow the instructions in the readme.txt file?

What does it mean by:
> 
On the target machine, setup the source/hybrid/build directory


What do I do there? I'm not really as skilled with the Terminal as I wish I was right now. @_@

Thanks for all your help so far, by the way.

---

### Post by kevdog on 2009-08-28
It just means setup a directory.

So it would be something like

mkdir -p ~/src/hybrid_wl

Put your tar.gz file within the ~/src/hybrid_wl directory and then proceed to extract the tar.gz file.

---

### Post by Grimhound on 2009-08-28
> **kevdog said:**
> It just means setup a directory.

So it would be something like

mkdir -p ~/src/hybrid_wl

Put your tar.gz file within the ~/src/hybrid_wl directory and then proceed to extract the tar.gz file.

Okay, so I am up to using the makefile, and I've deciphered what the directions are trying to tell me to a point, but now I'm stumped.


Currently, I have the line as make -C /lib/modules/2.6.30.5-candela/build M=`pwd`

So I substitute pwd with my admin password?
What do I do from here? ._.;

> You use the standard Linux 2.6 kernel build system as follows to make a Linux loadable
kernel module (LKM):

On the target machine, and cd'ed to the directory that contains the Makefile (fragment)

4.  Cleanup (optional):                  make -C /lib/modules/<2.6.xx.xx>/build M=`pwd` clean
5.  Build the LKM, i.e. wl.ko:           make -C /lib/modules/<2.6.xx.xx>/build M=`pwd`


---

### Post by kevdog on 2009-08-29
Just run this command in the Makefile directory:

make -C /lib/modules/`uname -r`/build M=`pwd`

pwd=present working directory -- no admin password needed.

---

### Post by Grimhound on 2009-08-29
> **kevdog said:**
> Just run this command in the Makefile directory:

make -C /lib/modules/`uname -r`/build M=`pwd`

pwd=present working directory -- no admin password needed.

The results from that:
> matthew@matthew-laptop:~/src/hybrid_wl$ make -C /lib/modules/`uname -r`/build M=`pwd`
make: Entering directory `/usr/src/linux-headers-2.6.30.5-candela'
  CC [M]  /home/matthew/src/hybrid_wl/src/wl/sys/wl_linux.o
/home/matthew/src/hybrid_wl/src/wl/sys/wl_linux.c:57:27: error: net/ieee80211.h: No such file or directory
/home/matthew/src/hybrid_wl/src/wl/sys/wl_linux.c: In function &#8216;wl_attach&#8217;:
/home/matthew/src/hybrid_wl/src/wl/sys/wl_linux.c:362: error: implicit declaration of function &#8216;ieee80211_get_crypto_ops&#8217;
/home/matthew/src/hybrid_wl/src/wl/sys/wl_linux.c:362: warning: assignment makes pointer from integer without a cast
/home/matthew/src/hybrid_wl/src/wl/sys/wl_linux.c:365: warning: assignment makes pointer from integer without a cast
/home/matthew/src/hybrid_wl/src/wl/sys/wl_linux.c: In function &#8216;wl_free&#8217;:
/home/matthew/src/hybrid_wl/src/wl/sys/wl_linux.c:634: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/home/matthew/src/hybrid_wl/src/wl/sys/wl_linux.c:669: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/home/matthew/src/hybrid_wl/src/wl/sys/wl_linux.c:685: error: dereferencing pointer to incomplete type
/home/matthew/src/hybrid_wl/src/wl/sys/wl_linux.c:689: error: dereferencing pointer to incomplete type
/home/matthew/src/hybrid_wl/src/wl/sys/wl_linux.c: In function &#8216;wl_open&#8217;:
/home/matthew/src/hybrid_wl/src/wl/sys/wl_linux.c:714: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/home/matthew/src/hybrid_wl/src/wl/sys/wl_linux.c: In function &#8216;wl_close&#8217;:
/home/matthew/src/hybrid_wl/src/wl/sys/wl_linux.c:742: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/home/matthew/src/hybrid_wl/src/wl/sys/wl_linux.c: In function &#8216;wl_start&#8217;:
/home/matthew/src/hybrid_wl/src/wl/sys/wl_linux.c:765: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/home/matthew/src/hybrid_wl/src/wl/sys/wl_linux.c: In function &#8216;wl_alloc_if&#8217;:
/home/matthew/src/hybrid_wl/src/wl/sys/wl_linux.c:850: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/home/matthew/src/hybrid_wl/src/wl/sys/wl_linux.c: In function &#8216;wl_get_driver_info&#8217;:
/home/matthew/src/hybrid_wl/src/wl/sys/wl_linux.c:1030: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/home/matthew/src/hybrid_wl/src/wl/sys/wl_linux.c: In function &#8216;wl_ioctl&#8217;:
/home/matthew/src/hybrid_wl/src/wl/sys/wl_linux.c:1118: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/home/matthew/src/hybrid_wl/src/wl/sys/wl_linux.c:1119: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/home/matthew/src/hybrid_wl/src/wl/sys/wl_linux.c: In function &#8216;wl_get_stats&#8217;:
/home/matthew/src/hybrid_wl/src/wl/sys/wl_linux.c:1204: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/home/matthew/src/hybrid_wl/src/wl/sys/wl_linux.c: In function &#8216;wl_get_wireless_stats&#8217;:
/home/matthew/src/hybrid_wl/src/wl/sys/wl_linux.c:1236: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/home/matthew/src/hybrid_wl/src/wl/sys/wl_linux.c:1237: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/home/matthew/src/hybrid_wl/src/wl/sys/wl_linux.c: In function &#8216;wl_set_mac_address&#8217;:
/home/matthew/src/hybrid_wl/src/wl/sys/wl_linux.c:1304: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/home/matthew/src/hybrid_wl/src/wl/sys/wl_linux.c:1312: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/home/matthew/src/hybrid_wl/src/wl/sys/wl_linux.c: In function &#8216;_wl_set_multicast_list&#8217;:
/home/matthew/src/hybrid_wl/src/wl/sys/wl_linux.c:1335: error: &#8216;struct net_device&#8217; has no member named &#8216;priv&#8217;
/home/matthew/src/hybrid_wl/src/wl/sys/wl_linux.c: In function &#8216;wl_tkip_miccheck&#8217;:
/home/matthew/src/hybrid_wl/src/wl/sys/wl_linux.c:1726: error: dereferencing pointer to incomplete type
/home/matthew/src/hybrid_wl/src/wl/sys/wl_linux.c:1729: error: dereferencing pointer to incomplete type
/home/matthew/src/hybrid_wl/src/wl/sys/wl_linux.c: In function &#8216;wl_tkip_micadd&#8217;:
/home/matthew/src/hybrid_wl/src/wl/sys/wl_linux.c:1748: error: dereferencing pointer to incomplete type
/home/matthew/src/hybrid_wl/src/wl/sys/wl_linux.c: In function &#8216;wl_tkip_encrypt&#8217;:
/home/matthew/src/hybrid_wl/src/wl/sys/wl_linux.c:1768: error: dereferencing pointer to incomplete type
/home/matthew/src/hybrid_wl/src/wl/sys/wl_linux.c: In function &#8216;wl_tkip_decrypt&#8217;:
/home/matthew/src/hybrid_wl/src/wl/sys/wl_linux.c:1790: error: dereferencing pointer to incomplete type
/home/matthew/src/hybrid_wl/src/wl/sys/wl_linux.c:1792: error: dereferencing pointer to incomplete type
/home/matthew/src/hybrid_wl/src/wl/sys/wl_linux.c: In function &#8216;wl_tkip_keyset&#8217;:
/home/matthew/src/hybrid_wl/src/wl/sys/wl_linux.c:1834: error: dereferencing pointer to incomplete type
/home/matthew/src/hybrid_wl/src/wl/sys/wl_linux.c:1844: error: dereferencing pointer to incomplete type
/home/matthew/src/hybrid_wl/src/wl/sys/wl_linux.c:1851: error: dereferencing pointer to incomplete type
/home/matthew/src/hybrid_wl/src/wl/sys/wl_linux.c:1861: error: dereferencing pointer to incomplete type
/home/matthew/src/hybrid_wl/src/wl/sys/wl_linux.c:1871: error: dereferencing pointer to incomplete type
/home/matthew/src/hybrid_wl/src/wl/sys/wl_linux.c:1878: error: dereferencing pointer to incomplete type
/home/matthew/src/hybrid_wl/src/wl/sys/wl_linux.c: In function &#8216;wl_tkip_printstats&#8217;:
/home/matthew/src/hybrid_wl/src/wl/sys/wl_linux.c:1897: error: dereferencing pointer to incomplete type
/home/matthew/src/hybrid_wl/src/wl/sys/wl_linux.c:1899: error: dereferencing pointer to incomplete type
make[1]: *** [/home/matthew/src/hybrid_wl/src/wl/sys/wl_linux.o] Error 1
make: *** [_module_/home/matthew/src/hybrid_wl] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.30.5-candela'
matthew@matthew-laptop:~/src/hybrid_wl$ 


This is getting really hopeless.

---

### Post by kevdog on 2009-08-29
Did you install the linux headers package?

sudo aptitude install linux-headers-`uname -r`

I'm definitely not trying to brag, but I downloaded the source, unzipped, and compiled the wl.ko module in like 3 minutes. Likely you are just missing some dependencies -- if you have never compiled things before -- the first time is always the roughest.

---

### Post by Grimhound on 2009-08-29
> **kevdog said:**
> Did you install the linux headers package?

sudo aptitude install linux-headers-`uname -r`

I just did, and the same results.

See, I don't know Linux at all. So I don't really have the foreknowledge to do anything.

---

### Post by perdido on 2009-08-29
I'm right there with you on the learning curve my friend! and it seems we are in the same boat as far as the broadcom drivers go. i will definitely be keeping an eye out for this!:popcorn:

---

### Post by kevdog on 2009-08-29
Do you still need help?

---

### Post by perdido on 2009-09-10
yes please! still can't get the darn broadcom drivers to work. i got a tx1000z with a broadcom bcm4328 chipset. no luck getting it to work yet.

---

### Post by stevenpusser on 2009-09-18
> **perdido said:**
> yes please! still can't get the darn broadcom drivers to work. i got a tx1000z with a broadcom bcm4328 chipset. no luck getting it to work yet.


You know, you should be able to install the Karmic deb package of the bcmwl-kernel-source, plus bcmwl-modaliases from the Karmic repository.  Since it uses dkms, doing that will automatically build and install the "wl.ko" driver module into your kernel's
/lib/modules/"version"/updates folder.

By the way, I have manually hacked the kernelcheck program to build a 2.6.31 kernel, by having it check a local file instead of the missing html files at kernel.org.  You have to choose "older patch" instead of "normal performance".

Of course, it's a good idea to be wary of random debs, but I did do some work with Master_Kernel to debug and package up the 1.2.5 version...and I include the source, if you want to build your own deb to be safe.

---

