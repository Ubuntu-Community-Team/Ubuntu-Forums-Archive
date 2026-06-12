---
title: "PCMICIA Wireless card Airlive WL8000PCM"
date: 2010-01-29
forum: Networking &amp; Wireless
---

### Post by Grone1985 on 2010-01-29
Hi,
I have tried to install this card with the Linux driver on their website (Linuxant) but I haven't been able to install it. It says that it can't find the linux kernel source. Where can I find this? Has anyone been able to install it?
Thanks in advance!

---

### Post by pdc on 2010-01-29
does issuing the command

> sudo apt-get install build-essential

which should install the build-essential package help if you attempt again to install the driver package?

if you type the command

> lspci give .. it will help identify more details about your wireless

---

### Post by chili555 on 2010-01-29
Can you hook up an ethernet connection and do:```
sudo apt-get install linux-headers-`uname -r` build-essential
```Then try sudo make install again.

---

### Post by Grone1985 on 2010-02-01
Thanks for the replies!

lspci gives this:

```
06:00.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface
```

Trying all the other commands has no effect on my problem, I have everything installed and updated already... I keep on getting this message:

```
Configurando driverloader (2.26tiabocom) ...
Linuxant DriverLoader for Wireless LAN devices, version 2.26tiabocom

No pre-built modules for: Debian-squeeze/sid linux-2.6.31-17-generic i686-SMP

Trying to automatically build the driver modules...
(this requires a C compiler and proper kernel sources to be installed)

Where is the linux source build directory that matches your running kernel?
[/lib/modules/2.6.31-17-generic/build]     

WARNING: the kernel version () defined in
/lib/modules/2.6.31-17-generic/build/include/linux/version.h
does not match the currently running kernel (2.6.31-17-generic)
The cause of this problem is an incorrect kernel source path.
Please check that /lib/modules/2.6.31-17-generic/build points to the right tree.
The cause of this is usually a missing or unconfigured
kernel source tree (and sometimes an incorrect directory or symbolic link).

However, proper /boot/config-2.6.31-17-generic was found.
Would you like to try using it (in a temporary kernel tree)? [yes] n

ERROR: The kernel at '/lib/modules/2.6.31-17-generic/build' was compiled without the following
options enabled: CONFIG_NET_RADIO CONFIG_NET_WIRELESS
These options are needed for DriverLoader. Please enable these kernel
options, re-compile the kernel and try again.
dpkg: error al procesar driverloader (--configure):
 el subproceso script post-installation instalado devolvió el código de salida de error 1
Se encontraron errores al procesar:
 driverloader
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by chili555 on 2010-02-02
Does it build properly, that is, with no errors, if you change to:> Would you like to try using it (in a temporary kernel tree)? [yes] [COLOR="Red"]y[/COLOR]

---

### Post by Grone1985 on 2010-02-02
It makes no difference. It says it cannot use it. Also on the first question:

```

Where is the linux source build directory that matches your running kernel?
[/lib/modules/2.6.31-17-generic/build] 
```

You can point it to wherever you want by writing the path. I tried with different paths and it always says they don't match the current kernel.

---

### Post by chili555 on 2010-02-02
This is a problematic chipset.> Texas Instruments ACX 111 54Mbps Wireless InterfaceThis will give you a sense of the difficulty:  [http://ubuntuforums.org/showthread.php?t=1321303&highlight=acx111](http://ubuntuforums.org/showthread.php?t=1321303&highlight=acx111)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/495077](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/495077)

I have looked at the Linuxant site and, if I am reading correctly, it is a way to use the Windows driver. There is a way to do the same here in Ubuntu, called ndiswrapper. [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

If you have the Windows drivers, either by download or on the CD, I'd suggest you try ndiswrapper first.

---

### Post by Grone1985 on 2010-02-03
On the Airlive website it says that this Linuxant thing is the Linux driver. What I understood is that this is another alternative to ndiswrapper but still I'll give it a shot to see what I get. I'll post back with any progress. Thanks!

---

