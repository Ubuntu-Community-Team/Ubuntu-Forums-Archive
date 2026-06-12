---
title: "Atheros Driver Supported But No Wireless"
date: 2009-02-22
forum: Networking &amp; Wireless
---

### Post by darksideforge on 2009-02-22
Hello All. It's been a while since I've posted. I have a Toshiba Satellite L45-S4687 with the onboard wireless and I can't get the wireless to work. I've tried madwifi, Madberry, apt-get install, and every other thing I can think of. I finally did a fresh install this morning, switching from the standard Gnome DTE to Xubuntu for a change of pace. I installed all of the updates via Synaptic Package Manager, and now I want to start afresh with this wireless issue. If you want me to try specific CLI commands, just let me know.  Here is what I have so far:
```

darkside@darkside:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

darkside@darkside:~$ iwlist
Usage: iwlist [interface] scanning [essid NNN] [last]
              [interface] frequency 
              [interface] channel 
              [interface] bitrate 
              [interface] rate 
              [interface] encryption 
              [interface] keys 
              [interface] power 
              [interface] txpower 
              [interface] retry 
              [interface] ap 
              [interface] accesspoints 
              [interface] peers 
              [interface] event 
              [interface] auth 
              [interface] wpakeys 
              [interface] genie 
              [interface] modulation 
darkside@darkside:~$ iwspy
lo        Interface doesn't support wireless statistic collection

eth0      Interface doesn't support wireless statistic collection

pan0      Interface doesn't support wireless statistic collection

darkside@darkside:~$ iwpriv
lo        no private ioctls.

eth0      no private ioctls.

pan0      no private ioctls.

darkside@darkside:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
**02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)**
05:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
05:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
darkside@darkside:~$ 


```

---

### Post by superprash2003 on 2009-02-22
post output of **lshw -C network**

---

### Post by darksideforge on 2009-02-22
> **superprash2003 said:**
> post output of **lshw -C network**


```

lshw -C network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:05:07.0
       logical name: eth0
       version: 10
       serial: 00:1a:92:a9:bf:35
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.0.100 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 2e:ff:1d:65:71:5e
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
darkside@darkside:~$ 
```

---

### Post by Reiger on 2009-02-22
I know this one! It is actually supported through aht5k. 

Try the packages listed for Ubuntu at compat.wireless.org first, if that fails try building the driver from a source package from compat.wireless.org -- be sure to have:
```

sudo aptitude install linux-headers-$(uname -r) build-essential dkms

```
installed before attempting to build the drivers yourself (don't worry, at compat.wireless.org there are step-by-step installation instructions).

Couple of tutorial links from a quick google:
[http://unsharptech.com/2008/10/31/atheros-wireless-in-ubuntu-810-intrepid-ibex/](http://unsharptech.com/2008/10/31/atheros-wireless-in-ubuntu-810-intrepid-ibex/)
[http://www.ubuntugeek.com/how-to-get-atheros-ar5007eg-or-ar242x-wireless-cards-may-be-other-models-working-in-ubuntu-810-intrepid-ibex.html](http://www.ubuntugeek.com/how-to-get-atheros-ar5007eg-or-ar242x-wireless-cards-may-be-other-models-working-in-ubuntu-810-intrepid-ibex.html)

---

### Post by darksideforge on 2009-02-22
> **Reiger said:**
> I know this one! It is actually supported through aht5k. 

Try the packages listed for Ubuntu at compat.wireless.org first, if that fails try building the driver from a source package from compat.wireless.org -- be sure to have:
```

sudo aptitude install linux-headers-$(uname -r) build-essential dkms

```
installed before attempting to build the drivers yourself (don't worry, at compat.wireless.org there are step-by-step installation instructions).

Couple of tutorial links from a quick google:
[http://unsharptech.com/2008/10/31/atheros-wireless-in-ubuntu-810-intrepid-ibex/](http://unsharptech.com/2008/10/31/atheros-wireless-in-ubuntu-810-intrepid-ibex/)
[http://www.ubuntugeek.com/how-to-get-atheros-ar5007eg-or-ar242x-wireless-cards-may-be-other-models-working-in-ubuntu-810-intrepid-ibex.html](http://www.ubuntugeek.com/how-to-get-atheros-ar5007eg-or-ar242x-wireless-cards-may-be-other-models-working-in-ubuntu-810-intrepid-ibex.html)

the only thing i get from compat.wireless.org is a bunch of ads to download some sort of windows-only software to keep my drivers updated for me.  i don't get any sort of step-by-step instructions...only a search window and then it brings up a bunch of links to the left that are nothing but advertisements.

---

### Post by darksideforge on 2009-02-22
New Development/Attempt:

I downloaded the Atheros drivers from Sourceforge to my Desktop. I created a new folder and moved the download into it. I unzipped it into it's own folder in the new folder. All of this was done in GUI.

I opened a terminal and performed:

```
sudo su
```

to become root.

I performed several changes of directory (cd) to navigate to my new folder, so that I ended up with this:

```
root@darkside:/home/darkside/Desktop# cd madwifi-0.9.4
```

Then, based on instructions in the INSTALL file (txt) in the madwifi folder:

> Building the driver
-------------------

The driver is built using the Linux kernel build mechanism.  This means
you must have some part of the kernel source distribution installed on
the machine where you want to build the driver.  In particular, the
kernel include files, makefiles, build scripts and configuration must be
available.

This will be present if you built your kernel from source.  Otherwise
you may need to install an additional kernel development package from
your distribution that would match your kernel.  For example, the
development package for the default kernel is called linux-headers on
Debian and kernel-devel on Fedora Core.  Installing a package with full
kernel sources should not be generally necessary.

Note: in the following examples "$" stands for your system prompt;
you're not expected to type that as part of the actual command.  "#"
stands for the command prompt when the commands must be executed by
root.

Most people can just type:

  $ make

in the top-level MadWifi source directory to build all the modules for
the currently running system.

And as I'd navigated my way into the folder via CLI, I typed "make" watched as my screen scrolled through the make process. However, at the end of the make process, there were several errors present:

```
root@darkside:/home/darkside/Desktop/madwifi-0.9.4# make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.27-11-generic/build SUBDIRS=/home/darkside/Desktop/madwifi-0.9.4 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-11-generic'
  CC [M]  /home/darkside/Desktop/madwifi-0.9.4/ath/if_ath.o
  CC [M]  /home/darkside/Desktop/madwifi-0.9.4/ath/if_ath_pci.o
  LD [M]  /home/darkside/Desktop/madwifi-0.9.4/ath/ath_pci.o
  CC [M]  /home/darkside/Desktop/madwifi-0.9.4/ath_hal/ah_os.o
  HOSTCC  /home/darkside/Desktop/madwifi-0.9.4/ath_hal/uudecode
  UUDECODE /home/darkside/Desktop/madwifi-0.9.4/ath_hal/i386-elf.hal.o
  LD [M]  /home/darkside/Desktop/madwifi-0.9.4/ath_hal/ath_hal.o
  CC [M]  /home/darkside/Desktop/madwifi-0.9.4/ath_rate/amrr/amrr.o
  LD [M]  /home/darkside/Desktop/madwifi-0.9.4/ath_rate/amrr/ath_rate_amrr.o
  CC [M]  /home/darkside/Desktop/madwifi-0.9.4/ath_rate/minstrel/minstrel.o
  LD [M]  /home/darkside/Desktop/madwifi-0.9.4/ath_rate/minstrel/ath_rate_minstrel.o
  CC [M]  /home/darkside/Desktop/madwifi-0.9.4/ath_rate/onoe/onoe.o
  LD [M]  /home/darkside/Desktop/madwifi-0.9.4/ath_rate/onoe/ath_rate_onoe.o
  CC [M]  /home/darkside/Desktop/madwifi-0.9.4/ath_rate/sample/sample.o
  LD [M]  /home/darkside/Desktop/madwifi-0.9.4/ath_rate/sample/ath_rate_sample.o
  CC [M]  /home/darkside/Desktop/madwifi-0.9.4/net80211/if_media.o
  CC [M]  /home/darkside/Desktop/madwifi-0.9.4/net80211/ieee80211.o
  CC [M]  /home/darkside/Desktop/madwifi-0.9.4/net80211/ieee80211_beacon.o
  CC [M]  /home/darkside/Desktop/madwifi-0.9.4/net80211/ieee80211_crypto.o
  CC [M]  /home/darkside/Desktop/madwifi-0.9.4/net80211/ieee80211_crypto_none.o
  CC [M]  /home/darkside/Desktop/madwifi-0.9.4/net80211/ieee80211_input.o
  CC [M]  /home/darkside/Desktop/madwifi-0.9.4/net80211/ieee80211_node.o
  CC [M]  /home/darkside/Desktop/madwifi-0.9.4/net80211/ieee80211_output.o
  CC [M]  /home/darkside/Desktop/madwifi-0.9.4/net80211/ieee80211_power.o
/home/darkside/Desktop/madwifi-0.9.4/net80211/ieee80211_power.c: In function 'ieee80211_pwrsave':
/home/darkside/Desktop/madwifi-0.9.4/net80211/ieee80211_power.c:240: error: implicit declaration of function '__skb_append'
make[3]: *** [/home/darkside/Desktop/madwifi-0.9.4/net80211/ieee80211_power.o] Error 1
make[2]: *** [/home/darkside/Desktop/madwifi-0.9.4/net80211] Error 2
make[1]: *** [_module_/home/darkside/Desktop/madwifi-0.9.4] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-11-generic'
make: *** [modules] Error 2
root@darkside:/home/darkside/Desktop/madwifi-0.9.4#
``` 


I understand that there are quite a few problems with Linux kernels attempting to interact with laptop power save functions, so I understand that first error, but the "make: *** [modules] Error 2" message at the bottom has me worried. Should I be?

Thanks again in advance for the help.

---

### Post by darksideforge on 2009-02-22
**Here is another, revised copy, of the lshw -C network command:**

```
darkside@darkside:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:05:07.0
       logical name: eth0
       version: 10
       serial: 00:1a:92:a9:bf:35
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.0.100 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 56:1e:a8:38:f7:b2
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
darkside@darkside:~$ 

```

**And here is the updated version of iwconfig (no change, as you can see):**

```
darkside@darkside:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

darkside@darkside:~$ 

```

---

### Post by superprash2003 on 2009-02-25
try this [http://www.prash-babu.com/2008/12/how-to-configure-atheros-ar5007eg-or.html](http://www.prash-babu.com/2008/12/how-to-configure-atheros-ar5007eg-or.html)

---

### Post by binbash on 2009-02-25
[http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/](http://madberry.org/2008/11/how-to-get-atheros-ar242x-to-work-on-810-intrepid-ibex/)

---

### Post by moonport on 2009-02-25
I fixed the same problem in my Compaq with MadWifi drivers:
[http://www.madwifi.org/](http://www.madwifi.org/)

---

