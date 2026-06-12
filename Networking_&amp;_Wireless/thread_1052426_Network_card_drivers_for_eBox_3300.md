---
title: "Network card drivers for eBox 3300"
date: 2009-01-27
forum: Networking &amp; Wireless
---

### Post by tdeli on 2009-01-27
First, I'm new to linux and Ubuntu, but impressed with Ubuntu so far.

I'm running Ubuntu 8.04 on a fanless pc (Ebox-3300) with 256mb RAM and a 4GB compact flash card.

The manufacturer of the pc says that the embedded NIC won't work without applying a driver patch to the kernel.

The CPU / NIC info is here: [http://www.vortex86dx.com/](http://www.vortex86dx.com/) under the LINUX section there is a link to download the .tar.gz file for the ethernet driver.

I've read that I have to 'patch' or 'make' the kernel... How do I do this?

Any help is appreciated. Thanks!

---

### Post by nixscripter on 2009-01-28
You don't have to build your own kernel; just a driver against it. Something like this will do:

1. Download the tar.gz file they have.
2. Using Synaptic package manager, install the **linux-headers** package.
3. Unpack the tarball, let's say into **/usr/src/r6040**
4. Open a terminal and run the make file: ```
cd /usr/src/r6040 && make && sudo make install
```
5. Load the new module if all that worked: ```
modprobe r6040
```

If you get errors in the build, I'll see what I can do.

---

### Post by tdeli on 2009-01-29
> **nixscripter said:**
> You don't have to build your own kernel; just a driver against it. Something like this will do:

1. Download the tar.gz file they have.
2. Using Synaptic package manager, install the **linux-headers** package.
3. Unpack the tarball, let's say into **/usr/src/r6040**
4. Open a terminal and run the make file: ```
cd /usr/src/r6040 && make && sudo make install
```
5. Load the new module if all that worked: ```
modprobe r6040
```

If you get errors in the build, I'll see what I can do.
NixScripter,

Thanks for the response. 

First off is there a particular 'linux-headers' package that I need to install?  The specific package I had was 'linux-headers-2.6.24-23-generic'.  I presume by the result, this is wrong?

Here is the output after the attempt to 'make':


make -C /lib/modules/2.6.24-23-generic/build M=/usr/src/r6040
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-23-generic'
  CC [M]  /usr/src/r6040/r6040.o
/usr/src/r6040/r6040.c: In function &#8216;mdio_write&#8217;:
/usr/src/r6040/r6040.c:236: warning: unused variable &#8216;np&#8217;
/usr/src/r6040/r6040.c: In function &#8216;r6040_init_one&#8217;:
/usr/src/r6040/r6040.c:278: error: implicit declaration of function &#8216;SET_MODULE_OWNER&#8217;
/usr/src/r6040/r6040.c: In function &#8216;r6040_open&#8217;:
/usr/src/r6040/r6040.c:381: error: &#8216;SA_SHIRQ&#8217; undeclared (first use in this function)
/usr/src/r6040/r6040.c:381: error: (Each undeclared identifier is reported only once
/usr/src/r6040/r6040.c:381: error: for each function it appears in.)
/usr/src/r6040/r6040.c:381: warning: passing argument 2 of &#8216;request_irq&#8217; from incompatible pointer type
/usr/src/r6040/r6040.c: In function &#8216;r6040_GetSet_MACaddress&#8217;:
/usr/src/r6040/r6040.c:1041: warning: unused variable &#8216;lp&#8217;
/usr/src/r6040/r6040.c: In function &#8216;r6040_init&#8217;:
/usr/src/r6040/r6040.c:1080: error: implicit declaration of function &#8216;pci_module_init&#8217;
make[2]: *** [/usr/src/r6040/r6040.o] Error 1
make[1]: *** [_module_/usr/src/r6040] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-23-generic'
make: *** [all] Error 2


I hope this helps.


Tom

---

### Post by nixscripter on 2009-01-29
First, the generic package turning into a specific version is normal.

Second, looks like they haven't updated it for 2.6.24. Open that terminal window again, cd into the directory, and run this rather complex command:

```
perl -pi.bak -e 's/SA_SHIRQ/IRQF_SHARED/;s/pci_module_init/pci_register_driver/;' r6040.c

```

That will replace the symbols in the kernel which were renamed, and are causing you errors.

Also, open r6040.c in a text editor (like gedit), go find the line that says SET_MODULE_OWNER, and put a "//" comment marker in front.

Then see if it compiles.

---

### Post by williwaw on 2009-02-25
Hi Tom,

How did you install Ubuntu to the CF card. Did you use a USB optical drive (and set BIOS to boot to that) or did you use a USB pen driv.e 

Never had any issues with the eBox-4300 but both my eBox-3300s keep failing when I boot from USB DVD drive (gets to Ubuntu splash screen, lets me select english, and then just crashes). 

Any tips on how you got 8.04 installed would much appreciated? Also, what do you think of the eBox-3300?

---

### Post by b4sakenxx on 2009-03-31
I realize the past post was 4 weeks ago, but here are a couple of things that will help you (ubuntu or debian). Start with a default BIOS.

For ubuntu, you really need to install to the CF using a regular PC. The livecd installer WILL NOT boot. Period. ;-)

After install, you'll need to apply a new kernel (either a patched one or a new one compiled from source) to the CF, then you can boot it on the eBox.

I recommend Debian or Fedora, cuz they are LOADS easier to install.

Extra notes:

1. Turn USB2 mode to Full Speed. Hi Speed will not work because EHCI is broken.  This will fix your USB CD boot errors.

2. IDE Operate Mode. Play with it.  If Legacy doesn't work, use Native. Example: For Debian 4 installation, you need to install in Legacy Mode. Once you update the Kernel, you will probably need to switch to Native.  Fedora 10 only uses Native mode.

3a. Ethernet:  Use a new kernel/new driver (you can pull it out of new kernel sources).  Compile a new kernel on a different system, then install it.  The driver source from the manufacturer is old and is prone to problems.

3b. If you are installing Debian, and you've used the kernel provided by the manufacturer, you will run into issues, because the r6040 driver included in that kernel fights with the ide driver (it821x) for IRQ 14 (secondary master).  To fix this, either set IRQ14 to reserved, turn off any devices you don't use such as serial/parallel ports or one of the usb ports, or compile a new kernel with Generic IDE Support disabled.

3c. Generally speaking, the latest kernel should fix any issues you have.

Good luck.

---

### Post by senitenmert on 2009-04-08
Hello b4Sakenxx,

Sorry by advance for my english.

I tried to install Debian 5 on an eBox 3300. 
Everything goes right. The only problem is that I can't get a resolution of 1680x1050. I did experiment with the latest drivers XGI, SIS or VESA. None of them works in 1680x150. By adding a Modeline in xorg.conf, nothing happens. The resolution is still in 1600x1200. The command "dpkg-reconfigure xserver-xorg" does not work on debian 5. It can only configure the keyboard and mouse. My screen is a NEC LCD22WV.
How can I do to get the resolution of 1680x1050 (with Win XP it's work !).
I'm trying on Xubuntu ... same problems. 

Thank you for your responses.

---

### Post by rigola on 2009-06-11
Hi,
I'm trying to install Ubuntu 8.04 on the same device Ebox 3300.
I tried both with a real IDE hard disk (2.5") and a compact flash installed
in the ide port, but the installer of Ubuntu does not find any disk.
Where your CF is connected?
How you did the install?
Thank any help any help!
 
Rigola

---

### Post by tra4d on 2009-06-30
Did the OP get this to work?  I am also trying to compile the drivers against the kernel as suggested by user 'nixscripter'.

But, the r6040 source comes with its own makefile - kernel specific (there is an Makefile-2.4 and Makefile-2.6).  So, according to the README file, I type:

```
# make -f Makefile-2.6 KDIR=/usr/src/<header-src-dir>
```

Which goes fine (I think).  No errors only warnings.  But, when I type try:

```
# make install
```

I get the error:
make: *** No rule to make target 'install'. Stop

Any ideas?  There is no configure file in this dir.

---

### Post by tra4d on 2009-06-30
Running dmesg gives the following:

```

r6040: Unknown symbol generic_mii_ioctl

```

---

### Post by jmcnally on 2009-09-18
> **tdeli said:**
> First, I'm new to linux and Ubuntu, but impressed with Ubuntu so far.

I'm running Ubuntu 8.04 on a fanless pc (Ebox-3300) with 256mb RAM and a 4GB compact flash card.

The manufacturer of the pc says that the embedded NIC won't work without applying a driver patch to the kernel.

The CPU / NIC info is here: [http://www.vortex86dx.com/](http://www.vortex86dx.com/) under the LINUX section there is a link to download the .tar.gz file for the ethernet driver.

I've read that I have to 'patch' or 'make' the kernel... How do I do this?

Any help is appreciated. Thanks!
tdeli, you mention you got Ubuntu running on eBox.  Can you tell me how or where you got the info on how to do this?  I've been working on it and can't get past the panic at the start after seeing a message about the CPU being unknown.  Entering pnpbios=off did nothing...

Any help appreciated!

-John

---

### Post by tra4d on 2009-09-19
Try this (Ubuntu is based on Debian):
[http://forums.debian.net/viewtopic.php?f=16&t=40831](http://forums.debian.net/viewtopic.php?f=16&t=40831)

---

### Post by Malikiqbal on 2010-08-04
HI,
while compiling the r6040 i get the following errors:
make -C /lib/modules/2.6.32-24-generic/build M=/home/malik/Downloads/r6040
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-24-generic'
  CC [M]  /home/malik/Downloads/r6040/r6040.o
/home/malik/Downloads/r6040/r6040.c: In function ‘mdio_read’:
/home/malik/Downloads/r6040/r6040.c:228: error: ‘struct net_device’ has no member named ‘priv’
/home/malik/Downloads/r6040/r6040.c: In function ‘mdio_write’:
/home/malik/Downloads/r6040/r6040.c:236: error: ‘struct net_device’ has no member named ‘priv’
/home/malik/Downloads/r6040/r6040.c:237: error: ‘struct net_device’ has no member named ‘priv’
/home/malik/Downloads/r6040/r6040.c:236: warning: unused variable ‘np’
/home/malik/Downloads/r6040/r6040.c: In function ‘r6040_init_one’:
/home/malik/Downloads/r6040/r6040.c:287: error: ‘struct net_device’ has no member named ‘priv’
/home/malik/Downloads/r6040/r6040.c:318: error: ‘struct net_device’ has no member named ‘open’
/home/malik/Downloads/r6040/r6040.c:319: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
/home/malik/Downloads/r6040/r6040.c:320: error: ‘struct net_device’ has no member named ‘stop’
/home/malik/Downloads/r6040/r6040.c:321: error: ‘struct net_device’ has no member named ‘get_stats’
/home/malik/Downloads/r6040/r6040.c:322: error: ‘struct net_device’ has no member named ‘set_multicast_list’
/home/malik/Downloads/r6040/r6040.c:323: error: ‘struct net_device’ has no member named ‘do_ioctl’
/home/malik/Downloads/r6040/r6040.c:325: error: ‘struct net_device’ has no member named ‘tx_timeout’
/home/malik/Downloads/r6040/r6040.c: In function ‘r6040_open’:
/home/malik/Downloads/r6040/r6040.c:373: error: ‘struct net_device’ has no member named ‘priv’
/home/malik/Downloads/r6040/r6040.c:381: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
include/linux/interrupt.h:117: note: expected ‘irq_handler_t’ but argument is of type ‘enum irqreturn_t (*)(int,  void *, struct pt_regs *)’
/home/malik/Downloads/r6040/r6040.c: In function ‘r6040_tx_timeout’:
/home/malik/Downloads/r6040/r6040.c:409: error: ‘struct net_device’ has no member named ‘priv’
/home/malik/Downloads/r6040/r6040.c: In function ‘r6040_start_xmit’:
/home/malik/Downloads/r6040/r6040.c:430: error: ‘struct net_device’ has no member named ‘priv’
/home/malik/Downloads/r6040/r6040.c: In function ‘r6040_interrupt’:
/home/malik/Downloads/r6040/r6040.c:504: error: ‘struct net_device’ has no member named ‘priv’
/home/malik/Downloads/r6040/r6040.c: In function ‘r6040_get_stats’:
/home/malik/Downloads/r6040/r6040.c:601: error: ‘struct net_device’ has no member named ‘priv’
/home/malik/Downloads/r6040/r6040.c: In function ‘set_multicast_list’:
/home/malik/Downloads/r6040/r6040.c:613: error: ‘struct net_device’ has no member named ‘priv’
/home/malik/Downloads/r6040/r6040.c: In function ‘netdev_get_drvinfo’:
/home/malik/Downloads/r6040/r6040.c:668: error: ‘struct net_device’ has no member named ‘priv’
/home/malik/Downloads/r6040/r6040.c: In function ‘r6040_close’:
/home/malik/Downloads/r6040/r6040.c:682: error: ‘struct net_device’ has no member named ‘priv’
/home/malik/Downloads/r6040/r6040.c: In function ‘netdev_ioctl’:
/home/malik/Downloads/r6040/r6040.c:705: error: ‘struct net_device’ has no member named ‘priv’
/home/malik/Downloads/r6040/r6040.c: In function ‘r6040_down’:
/home/malik/Downloads/r6040/r6040.c:724: error: ‘struct net_device’ has no member named ‘priv’
/home/malik/Downloads/r6040/r6040.c: In function ‘r6040_up’:
/home/malik/Downloads/r6040/r6040.c:830: error: ‘struct net_device’ has no member named ‘priv’
/home/malik/Downloads/r6040/r6040.c: In function ‘r6040_timer’:
/home/malik/Downloads/r6040/r6040.c:937: error: ‘struct net_device’ has no member named ‘priv’
/home/malik/Downloads/r6040/r6040.c: In function ‘phy_mode_chk’:
/home/malik/Downloads/r6040/r6040.c:985: error: ‘struct net_device’ has no member named ‘priv’
/home/malik/Downloads/r6040/r6040.c: In function ‘r6040_GetSet_MACaddress’:
/home/malik/Downloads/r6040/r6040.c:1041: error: ‘struct net_device’ has no member named ‘priv’
/home/malik/Downloads/r6040/r6040.c:1041: warning: unused variable ‘lp’
/home/malik/Downloads/r6040/r6040.c:1056: warning: no return statement in function returning non-void
make[2]: *** [/home/malik/Downloads/r6040/r6040.o] Error 1
make[1]: *** [_module_/home/malik/Downloads/r6040] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-24-generic'
make: *** [all] Error 2




Does any one have an idea, what to do. i actually want to install the NIC driver for ebox 3300, the driver which i found at [http://www.compactpc.com.tw/download_drv.htm](http://www.compactpc.com.tw/download_drv.htm) i need to install, but somehow it is not compiling and i am getting above mentioned errors.


i have tried the way which [nixscripter]("http://ubuntuforums.org/member.php?u=509499") mentioned but no success. Does any one have an idea what to do.???
Thanks in advance.

---

### Post by tra4d on 2010-08-04
Did you read the ReadMe file that comes w/ the driver?  It may have changed but the last time I did this, the make command specified in the ReadMe file was not what you have posted.  Did you check out the link posted just before your post?

---

### Post by Malikiqbal on 2010-08-04
HI tra4d,
Here are the contens fo readme file: 

README
------

This is a RDC R6040 PCI FastEthernet Driver for Linux 2.4(2.4.22 and above) and 2.6.

The driver contains two makefiles, Makefile-2.4 and Makefile-2.6, for the kernel
2.4 and 2.6 respectively. In other words, when you compile the module with the
source trees of Linux kernel 2.4, you should use Makefile-2.4 as the make-
file, and vice versa.

For kernel 2.4
# make -f Makeifle-2.4 KDIR=/usr/src/linux-2.4

For kernel 2.6
# make -f Makeifle-2.6 KDIR=/usr/src/linux-2.6


i have tried the the link [http://forums.debian.net/viewtopic.php?f=16&t=40831](http://forums.debian.net/viewtopic.php?f=16&t=40831) , but the same errors i am getting when compiling using command: make -f Makefile-2.6 KDIR=/usr/src/linux-headers-`uname -r`.

any idea what to do .......??
Thanks,

---

### Post by tra4d on 2010-08-04
Do you have all the necessary modules loaded (like mii)?

---

### Post by Malikiqbal on 2010-08-04
HI tra4d,
yes i loaded th module(mii.ko), actually i am following the link which was provided in your post.
but i stop at compilation stage, because of these errors.
have you compiled it recently???
thanks.

---

### Post by tra4d on 2010-08-04
No  I haven't, sorry.  What version of Ubuntu are you using?  Kernel version?

---

### Post by Malikiqbal on 2010-08-04
Hi,

i am using Linux version 2.6.32-21-generic.

i am also new to linux and do not know alot about it....i am using whatever is described in forums about this problem.

Thanks.

---

### Post by tra4d on 2010-08-04
What version of ubuntu?

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by Malikiqbal on 2010-08-04
hi,

i am using Ubuntu 10.04 LTS- the Lucid Lynx - released in April 2010.

regards,

---

### Post by tra4d on 2010-08-04
You will probably need to try an older version w/ an older kernel.  I know Debian 4.0 works, so maybe 8.04 or even 7.10 ubuntu.  I know they are obsolete, but it may be the easiest way.  

If security is a major concern, you will have to keep working on one of the supported versions.

---

### Post by Malikiqbal on 2010-08-04
Ok let me try this 7.10 release and see if it works.
i will be back after installing and testing it.

---

### Post by Ohm's Lawyer on 2010-11-29
Hi all,
So, I managed to get everything working neatly (after creating a few new bald spots) using 9.04, but I'd really like to get it running on 10.04, being LTS. For whatever reason, I just can't manage to get the OS to see eth0. It doesn't even see the hardware. I've tried making the drivers and updating the kernel, with not luck at all. Does anyone have any experience with this?

---

### Post by uncaspi on 2010-11-29
If you run VMware you could have problems to see your hardware.

---

### Post by OSXCommunist on 2010-12-09
> **Ohm's Lawyer said:**
> Hi all,
So, I managed to get everything working neatly (after creating a few new bald spots) using 9.04, but I'd really like to get it running on 10.04, being LTS. For whatever reason, I just can't manage to get the OS to see eth0. It doesn't even see the hardware. I've tried making the drivers and updating the kernel, with not luck at all. Does anyone have any experience with this?

I managed to get the R6040 working on my system by installing on a regular PC to the flash module, then downloading the 2.6.32 kernel sources from [http://kernel.org](http://kernel.org), I used the makefile (Makefile-2.6) provided with the downloaded  r6040.tar.gz and replaced r6040.c with the r6040.c file contained in the kernel sources (drivers/net/r6040.c)

This was able to produce a r6040.ko for 10.04 Lucid Lynx LTS. I've attached the source file and built kernel module for your usage.

Edit:
I've attached my entire build directory, which was build against the 2.6.32-24-generic linux-headers package (build for the livecd).

Build it with:
> 
mkdir /usr/src/r6040
tar cjvf Build.tar.bz2 -C /usr/src/r6040
cd /usr/src/r6040
make -f Makefile-2.6 KDIR=/usr/src/linux-headers-2.6.32-24-generic


---

### Post by waterboy550 on 2011-03-03
I know this is old, but thanks a lot. I used your posted files and boom! Got my ethernet card up and running. Thanks a TON!

---

### Post by Rubenulis on 2011-12-03
For Ubuntu 10.04 the media independent interface module (mii.ko) needs to be installed before r6040.ko

---

### Post by igorium on 2012-02-11
Ubuntu Server 10 detects network during setup fine.
I have eBox 3310-L2 (two LANs, Vortex86DX), successfully installed it on Micro-SD (couldn't on CF).
Only problem was that for some reason installer put GRUB on flashdrive with distro.
Booted from flash, launched grub-install, got working router-box

---

