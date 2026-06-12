---
title: "Marvell 88e8056 network up/down"
date: 2011-04-05
forum: Networking &amp; Wireless
---

### Post by blankfile1 on 2011-04-05
Hello!

I'm currently experiencing some strange troubles installing ubuntu 10.04 /10.10 (tried both, same issue). My network connection appears to fail after some very small amount of packet is sent/received. Searched a bit around the forums here, and ended up installing the Marvell drivers (v10.87.3.3) with success. However, the issue remains.

Here's the relevant info:

i386 installation
Motherboard:DFI lanparty dk 790gx-m2rs
Network controller: Marvell 88e8056
kernel:2.6.32-30-generic
Network config: manual (and tested working config on other computer)

```
$ lspci -nnk |grep Ethernet
02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller [11ab:4364] (rev 12)
```



```
$ nm-tool 

NetworkManager Tool

State: connected

- Device: eth0  [Connexion filaire 1] ------------------------------------------
  Type:              Wired
  Driver:            sky2
  State:             connected
  Default:           yes
  HW Address:        00:01:29:A6:53:87

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.2.100
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1

    DNS:             8.8.4.4
    DNS:             8.8.8.8

```

Marvell driver installation log:

```
+++ Install mode: User
+++ Driver version: 10.87.3.3 (Feb-01-2011)
+++ Kernel version 2.6.32-30-generic
+++ smp_count=1
+++ cpu_number=2
+++ kernel_machine=i686
+++ Architecture: i386
+++ modpost available
+++ Unpack the sources
+++ ====================================
+++ tar xfv sk98lin.tar
2.6/
2.6/sky2.c
2.6/skethtool.c
2.6/skproc.c
2.6/Makefile
2.6/skge.c
2.6/h/
2.6/h/skdrv1st.h
2.6/h/skdrv2nd.h
2.6/skdim.c
common/
common/skaddr.c
common/fwos.c
common/skgeinit.c
common/skgehwt.c
common/skspi.c
common/sk98lin.htm
common/fwapp.c
common/sktimer.c
common/fwhci.c
common/fwptrn.c
common/flashfun.c
common/fwfunctions.c
common/skgemib.c
common/vpdcheck.c
common/skvpd.c
common/skpflash.c
common/sky2le.c
common/fwimage.c
common/fwoids.c
common/skgesirq.c
common/sk98lin.4
common/fwmain.c
common/sktwsi.c
common/skgepnmi.c
common/sklm80.c
common/skgespilole.c
common/skxmac2.c
common/sk98lin.txt
common/h/
common/h/sktimer.h
common/h/fwimage.h
common/h/sktypes.h
common/h/fwptrn.h
common/h/skdebug.h
common/h/skaddr.h
common/h/skversion.h
common/h/skgeasfapi.h
common/h/lm80.h
common/h/skvpd.h
common/h/skgetwsi.h
common/h/skgeinit.h
common/h/skgesirq.h
common/h/skpflash.h
common/h/skqueue.h
common/h/fwoids.h
common/h/skcsum.h
common/h/skgepnm2.h
common/h/skspi.h
common/h/fwapp.h
common/h/skpcidevid.h
common/h/fwos.h
common/h/mvyexhw.h
common/h/sktwsi.h
common/h/fwmain.h
common/h/xmac_ii.h
common/h/fwhci.h
common/h/skgehw.h
common/h/skgedrv.h
common/h/sky2le.h
common/h/skgepnmi.h
common/h/flash.h
common/h/fwcommon.h
common/h/skgehwt.h
common/h/skerror.h
common/skqueue.c
common/skgeasfapi.c
common/skcsum.c
misc/
misc/Kconfig
misc/Configure.help
+++ Compile the driver+++ ====================================make: entrant dans le répertoire « /usr/src/linux-headers-2.6.32-30-generic »make -C /lib/modules/2.6.32-30-generic/build \        KBUILD_SRC=/usr/src/linux-headers-2.6.32-30-generic \
        KBUILD_EXTMOD="/tmp/Sk98IFRREOZLkTUXBHaHNPahR/all" -f /usr/src/linux-headers-2.6.32-30-generic/Makefile \
test -e include/linux/autoconf.h -a -e include/config/auto.conf || (            \        echo;                                                           \        echo "  ERROR: Kernel configuration is invalid.";               \        echo "         include/linux/autoconf.h or include/config/auto.conf are missing.";      \        echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";  \        echo;                                                           \        

(Cutting this short, if needed i'll copypaste the full thing, but there's only the normal installation process going on. Following is the last couple lines of output)

ld -r -m elf_i386 -T /usr/src/linux-headers-2.6.32-30-generic/scripts/module-common.lds --build-id -o /tmp/Sk98IFRREOZLkTUXBHaHNPahR/all/sk98lin.ko /tmp/Sk98IFRREOZLkTUXBHaHNPahR/all/sk98lin.o /tmp/Sk98IFRREOZLkTUXBHaHNPahR/all/sk98lin.mod.o
make: quittant le répertoire « /usr/src/linux-headers-2.6.32-30-generic »
Check the driver
====================================




```



I'm most likely missing some important piece of information, but that should be a start. 

One thing that i noticed, is a very strange behavior from ping. I'm letting a ping google.com running in a terminal, and it does land hits every now and then. It reports 3% packet loss, with an average of 72.07 ms, whereas this laptop i am typing on gets about 25. It also takes forever to ctrl+c out of the ping, for some reason. A traceroute to google.com takes forever too, but eventually makes it.

Now, i'm unsure if the problem is really with the drivers. I did try and limit the scope of errors, namely by using static IP, google's DNS, 32bit install, LTS version. The one non-standard thing that i still have left is a French  installation. I highly doubt this has any effect on the network, but who knows?

At that point i am left a bit clueless as to what to do. I can't even find a log with errors in it to prove that there is an actual issue!  Any help will be greatly appreciated.

Thanks a whole huge lot!

---

### Post by blankfile1 on 2011-04-05
So i tried reverting to 10.10, tried it in english, attempted to install the latest net backports, no cigar. I honestly have no idea how to get this NIC working.

I will try an old centOS 5.x dvd i have lying around, see if that works.

Things i have ruled out:
-ipv6 interference
-ipv4 misconfiguration
-DNS



My current suspicions are:

-kernel trouble? I'm not certain how i would go around to pinpoint that.
-newest version of Marvell drivers, 10.87.3.3 don't play nice with the current kernel? Considering there are very few (but some) other threads about this issue, that seems highly unlikely.
-network-manager. Seems unlikely to me, but i suppose that could be it. Couldn't install an alternative manager from the repo (since well, no network :P )
-bad cd burns on both my 10.04 AND 10.10 ? I could md5check that.
-bad ethernet cable/router/port I am certain the wireless component works. the wired part COULD be an issue, somehow. I will try a straight connection to the cablemodem, bypassing the router entirely.

I'll update with more later.

---

### Post by blankfile1 on 2011-04-05
Darwin's beard! Used a different ethernet cable, network came up and stable instantly on my fresh 10.10 64bit install. I'll keep testing a little bit to be sure, but if that was it, i shall go hide away in a dark, shameful corner. It should have been so obvious. Occam's razor and all...

---

Yeah i left this mesage unposted for a bit, it was my network cable all along. May my public shaming serve as a lesson to always cover the very basics ;)

---

