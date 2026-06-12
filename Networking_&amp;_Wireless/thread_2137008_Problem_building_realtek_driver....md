---
title: "Problem building realtek driver..."
date: 2013-04-19
forum: Networking &amp; Wireless
---

### Post by nethfel on 2013-04-19
Hi all,

I'm needing to build the realtek 8192 driver for the Edimax wifi dongle (the atheros driver for my built in wireless doesn't work all that great (I have to be very close to the AP compared to being in windows) ).  I downloaded the drivers from the realtek website (which is the recommended way to get them) and when I run the install script, it exits with:

```

make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/3.5.0-27-generic/build M=/home/nethfel/Desktop/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105  modulesmake[1]: Entering directory `/lib/modules/3.5.0-27-generic/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/3.5.0-27-generic/build'
make: *** [modules] Error 2
##################################################
Compile make driver error: 2
Please check error Mesg
##################################################



```

I'm really not sure how to fix this to get the module to compile so I can use it in my system.  This is an ubuntu 12.10 system fully updated.

---

### Post by chili555 on 2013-04-19
It appears that you lack the necessary prerequisites:```
sudo apt-get install linux-headers-generic build-essential
```Then try again.

---

### Post by nethfel on 2013-04-19
Hi,

Thanks for responding - I had the headers, but I was missing the build essential.  I downloaded them and tried again, but I got the same error as before :(

---

### Post by chili555 on 2013-04-19
Let's check:```
sudo dpkg -s linux-headers-`uname -r`
```Those backticks are on the left side of my US keyboard on the same key with ~.

If you find it's not installed, please do:```
sudo apt-get install linux-headers-`uname -r`
```Then try again.

---

### Post by nethfel on 2013-04-19
As I mentioned - I already had them installed - 

```
Package: linux-headers-3.5.0-27-generic
Status: install ok installed
Priority: optional
Section: devel
Installed-Size: 10995
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: amd64
Source: linux
Version: 3.5.0-27.46
Provides: linux-headers, linux-headers-3.0
Depends: linux-headers-3.5.0-27, libc6 (>= 2.14)
Description: Linux kernel headers for version 3.5.0 on 64 bit x86 SMP
 This package provides kernel header files for version 3.5.0 on
 64 bit x86 SMP.
 .
 This is for sites that want the latest kernel headers.  Please read
 /usr/share/doc/linux-headers-3.5.0-27/debian.README.gz for details.
```

---

### Post by chili555 on 2013-04-19
Let's see if the error message has changed:```
cd Desktop/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/
sudo su
./install.sh
exit
```

---

### Post by nethfel on 2013-04-19
it hasn't.

```

make ARCH=x86_64 CROSS_COMPILE= -C /lib/modules/3.5.0-27-generic/build M=/home/nethfel/Desktop/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/driver/rtl8188C_8192C_usb_linux_v3.4.4_4749.20121105  modules
make[1]: Entering directory `/lib/modules/3.5.0-27-generic/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/3.5.0-27-generic/build'
make: *** [modules] Error 2
##################################################
Compile make driver error: 2
Please check error Mesg
##################################################


```

I was really hopefully when you had pointed out the build-essential...  I wonder if I could be missing something else still... no idea what though. :(

ps - it may look a little different, but it's not, there somehow was a missing carriage return on my original post

---

### Post by ahallubuntu on 2013-04-19
~

---

### Post by nethfel on 2013-04-19
> **ahallubuntu said:**
> Simple question: can you verify exactly which 8192 chipset you have? What's the output of "lsusb" ?

There are several different Realtek chipsets with very similar names but completely different driver downloads...

I do not have the system in front of me, but I had already verified that it is the RTL8192cu (I confirmed it on my system as well as other documents online with regard to it and is also the style of the driver from Edimax's own website for this wifi dongle which is an earlier version of what is on the realtek website) - which regardless of which version I need, there is something wrong overall that it won't let me compile the module on my system which is of concern for me if I end up getting other hardware that requires a module to be compiled if it might run into a similar issue...  I should note, both the realtek and the edimax driver package gives the same results, it doesn't matter if I do the install.sh script or use make ; make install within the driver folder.

---

### Post by ahallubuntu on 2013-04-19
~

---

### Post by chili555 on 2013-04-19
Frankly, I don't know and evidently Google doesn't know what's wrong. I suspect it may be that the package is either too old to compile on 3.5.0-xx or it isn't written or at least isn't *well*-written for 64-bit:> make ARCH=[COLOR="#FF0000"]x86_64[/COLOR] CROSS_COMPILE= I went to the trouble to try to compile it for 3.5.0-27 64-bit on my own system. Despite my experience, it refused.

I suggest, instead, the Ubuntu-ized version:```
sudo apt-get install linux-backports-modules-cw-3.6-quantal-generic
```Then reboot.

---

### Post by nethfel on 2013-04-19
Hi ahallubuntu,

It's a 12.10 system, fully updated/patched with full kernel source/headers/etc.  When I installed I didn't have internet access at the time, but I can't imagine that would cause this problem now.

---

### Post by nethfel on 2013-04-20
> **chili555 said:**
> Frankly, I don't know and evidently Google doesn't know what's wrong. I suspect it may be that the package is either too old to compile on 3.5.0-xx or it isn't written or at least isn't *well*-written for 64-bit:I went to the trouble to try to compile it for 3.5.0-27 64-bit on my own system. Despite my experience, it refused.

I suggest, instead, the Ubuntu-ized version:```
sudo apt-get install linux-backports-modules-cw-3.6-quantal-generic
```Then reboot.


Well, at least I know I'm not loosing my mind and that it's not just me it's not working for :)

Once I have access to the laptop again, I'll give the backports a try.  Will the backports modules replace all of my modules or is there a way to be selective?  I've honestly never used backports before....

---

### Post by stingray71 on 2013-04-20
Having the exact same issue.  absolute pain trying to install usb wireless drivers.

---

### Post by cardu on 2013-04-20
> **stingray71 said:**
> Having the exact same issue.  absolute pain trying to install usb wireless drivers.

I have exactly the same problem. Trying to build Ralink RT5572 driver for my x64 12.10 Ubuntu. 
I have no internet now, and my Ubuntu is merely useless.

---

### Post by chili555 on 2013-04-20
> **cardu said:**
> I have exactly the same problem. Trying to build Ralink RT5572 driver for my x64 12.10 Ubuntu. 
I have no internet now, and my Ubuntu is merely useless.I suggest you start a new thread and reference RT5572 in the title. Tell us what you have tried so far and any error messages.

---

### Post by cardu on 2013-04-20
Hi,

My Ubuntu just updated itself, some linux image stuff. I guess that's important for this problem. Now I can build and install the rt2870sta driver. But I still have no device. When I run iconfig, I don't see it. I tried sudo modprobe rt2870sta, but it says "module not found". What could be the problem now? It seems to be installed properly in /etc/Wireless/RT2870STA directory. 

Thanks

---

### Post by chili555 on 2013-04-20
> **nethfel said:**
>  Will the backports modules replace all of my modules or is there a way to be selective?  The 'cw'stands for compat-wireless. It will update all your wireless drivers, if an update is available. Do you have some other wireless drivers you want undisturbed?

---

### Post by cardu on 2013-04-20
> **chili555 said:**
> I suggest you start a new thread and reference RT5572 in the title. Tell us what you have tried so far and any error messages.

No need for a new thread as I got exactly the same error message as this guy here. 
Anyway, it seems to be fixed by updates.

---

### Post by chili555 on 2013-04-20
> it seems to be fixed by updates. Awesome! Glad it's working.

---

### Post by cardu on 2013-04-20
> **chili555 said:**
> Awesome! Glad it's working.

The build problem seems fixed by newest updates. However, the install problem is not. I've started a new thread for my problem so that I don't pollute this guy's thread.

---

### Post by nethfel on 2013-04-22
Well, here's an update:
I installed the backport modules - my RTL wifi dongle still acts like it did.  My onboard wireless still has terrible reception, my USB ethernet stopped working.  Luckily, my belkin wifi dongle still works and my onboard ethernet still works.  Not sure what to do next...

---

### Post by kronozord on 2013-05-08
I've the exact same problem.
Did someone managed to compile the drivers?

---

### Post by nethfel on 2013-05-08
> **kronozord said:**
> I've the exact same problem.
Did someone managed to compile the drivers?

I ended up just deciding to replace the wifi adapter in my laptop with another one as I was never able to get the driver to compile.

---

### Post by kronozord on 2013-05-09
Solved :)
Thanks to the kind soul who made the package

[http://ubuntuforums.org/showthread.php?t=2092934&highlight=8188](http://ubuntuforums.org/showthread.php?t=2092934&highlight=8188)

---

