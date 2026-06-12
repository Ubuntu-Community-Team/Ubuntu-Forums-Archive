---
title: "Can't install driver sk98lin for NIC (Marvell 88E8001)"
date: 2009-01-31
forum: Networking &amp; Wireless
---

### Post by JJRabbit on 2009-01-31
The WOL function of my NIC doesn't work in Ubuntu, for this reason I want to install the driver from Marvell. Unfortunately I can't figure out how to do this.
According to Ubuntu this NIC is in the PC:
```
jjr@jjr-desktop:~$ lspci | grep -i -e ethernet -e network
02:15.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
```

At [http://www.marvell.com/](http://www.marvell.com/) I downloaded this driver:

[I]Driver name: Linux Driver Install Package
Platform: Linux Kernel 2.4.20 and Higher
Date: 11/3/08
Version: 10.70.2.3[/I]


When I try to run the installscript there's an error:

```

jjr@jjr-desktop:~$ cd Desktop
jjr@jjr-desktop:~/Desktop$ cd DriverInstall
jjr@jjr-desktop:~/Desktop/DriverInstall$ ./install.sh
./functions: 44: Syntax error: "(" unexpected
jjr@jjr-desktop:~/Desktop/DriverInstall$

```

---

### Post by JJRabbit on 2009-02-07
On these forums I found that the script install.sh contains an error.
The first line [COLOR="DarkGreen"]#!/bin/sh[/COLOR] has to be changed into: [COLOR="DarkGreen"]#!/bin/bash[/COLOR].

I can now run the installation-script:
```
root@jjr-desktop:/home/jjr/Bureaublad/DriverInstall# ./install.sh
```

Created a symbolic link to the kernel-source:
```
jjr@jjr-desktop:/usr/src$ sudo -i
root@jjr-desktop:~# cd /usr/src
root@jjr-desktop:/usr/src# ln -s linux-headers-2.6.27-11 linux
```

Installation script succesfully completed! (a kernel patch has been created)

The readme-file said to type this in order to apply the generated patch into the kernel:
```
cat /home/jjr/Desktop/DriverInstall/sk98lin_v10.70.2.3_2.6.27_patch | patch -p1
```

Installed some stuff:
```
apt-get install kernel-package libncurses5-dev fakeroot wget bzip2
```

Now I have to reconfigure the kernel. So I typed this:
```

root@jjr-desktop:/usr/src/linux# make menuconfig
scripts/kconfig/mconf arch/x86/Kconfig
file drivers/net/arcnet/Kconfig already scanned?
make[1]: *** [menuconfig] Error 1
make: *** [menuconfig] Error 2

```

How can I get past this last error?

---

### Post by ydurant on 2009-03-10
The patch generate a corrupt file Kconfig present in drivers/net

To bypass this, grab a copy of the original Kconfig in the archive of source code of kernel and insert the following line coming from the sk98lin/misc/Kconfig

```
config SK98LIN
	tristate "Marvell Yukon Chipset / SysKonnect SK-98xx Support"
	depends on PCI
	---help---
	  Say Y here if you have a Marvell Yukon or SysKonnect SK-98xx/SK-95xx
	  compliant Gigabit Ethernet Adapter.
	  
	  The adapters support Jumbo Frames.
	  The dual link adapters support link-failover and dual port features.
	  Both Marvell Yukon and SysKonnect SK-98xx/SK-95xx adapters support 
	  the scatter-gather functionality with sendfile(). Please refer to 
	  Documentation/networking/sk98lin.txt for more information about
	  optional driver parameters.
	  Questions concerning this driver may be addressed to:
	      linux@syskonnect.de
	  
	  If you want to compile this driver as a module ( = code which can be
	  inserted in and removed from the running kernel whenever you want),
	  say M here and read Documentation/modules.txt. This is recommended.
	  The module will be called sk98lin. This is recommended.

config SK98LIN_NAPI
	bool "Use Rx polling (NAPI)"
	depends on SK98LIN
	help
	  NAPI is a new driver API designed to reduce CPU and interrupt load
	  when the driver is receiving lots of packets from the card.

```  

You could insert these lines before the declaration 
```
config SKGE
	tristate "New SysKonnect GigaEthernet support"
	depends on PCI
	select CRC32
	---help---


```

in the original Kconfig file (beware of the separating blanks lines) 

Put the modified Kconfig in place of patched one in /usr/src/linux/drivers/net

The error should disapear.

---

### Post by ydurant on 2009-03-11
One more things to do is to patch the Makefile in /usr/src/linux/drivers/net

```
obj-$(CONFIG_TC35815) += tc35815.o
obj-$(CONFIG_SKGE) += skge.o
obj-$(CONFIG_SKY2) += sky2.o
obj-$(CONFIG_SKFP) += skfp/
obj-$(CONFIG_VIA_RHINE) += via-rhine.o
obj-$(CONFIG_VIA_VELOCITY) += via-velocity.o
obj-$(CONFIG_ADAPTEC_STARFIRE) += starfire.o
obj-$(CONFIG_RIONET) += rionet.o
obj-$(CONFIG_SH_ETH) += sh_eth.o
**obj-$(CONFIG_SK98LIN) += sk98lin/**

#
# end link order section
#
```

---

### Post by jmcarter on 2009-04-16
Hi,

I'm very interested in switching from the skge driver to the sk98lin in the hope that i am able to WOL from a suspended state.

Did you manage to install the driver eventually, and if so would it be possible for you to describe all of the steps required to install it?

I attempted to run the install script in the installation mode, however it asked me to compile the kernel as modpost was missing, and I'm a little wary of doing so.  I see the [Ubuntu guide to compiling the kernel]("https://help.ubuntu.com/community/Kernel/Compile") mentions copying the existing kernel config file before compiling, along with some other steps not mentioned in the install scripts message.

Thanks for you help,
Jacob

---

### Post by vmendezb on 2009-08-06
I have the same problem can you please help me.What do you mean by:
"grab a copy of the original Kconfig in the archive of source code of kernel..."

How and where do we find this file.

Thank you

---

### Post by foresto on 2011-10-23
I just finished packaging the latest sk98lin driver (from August 2011) for Ubuntu Natty.  You can find my announcement post here:

[http://ubuntuforums.org/showthread.php?p=11382042#post11382042](http://ubuntuforums.org/showthread.php?p=11382042#post11382042)

---

