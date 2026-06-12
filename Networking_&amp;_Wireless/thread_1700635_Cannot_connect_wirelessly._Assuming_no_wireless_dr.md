---
title: "Cannot connect wirelessly. Assuming no wireless driver."
date: 2011-03-05
forum: Networking &amp; Wireless
---

### Post by rottweiler1204 on 2011-03-05
I just bought a Dell Inspiron Mini 10 (Inspiron 1018) netbook and installed Ubuntu Netbook on it. I cannot for the life of me connect to the Internet wirelessly. I can, however, connect with a wire.
 
I've Googled countless searches on trying to get my wireless to work. I've come to the conclusion I don't have a wireless driver. Can someone please help me? 
 
When I run the **iwconfig **command, I get...
 
lo - no wireless extensions
eth0 - no wireless extensions
 
When I run **lshw -c Network**, I only get two network descriptions, *Ethernet interface* and *Network controller*, no wireless interface.
 
I appreciate all and any help provided :confused:

---

### Post by chili555 on 2011-03-05
> Network controller, no wireless interface.
I'm pretty confident that 'Network Controller' *is* your wireless card. Please post what it says in lshw. I'd also love to see the line that matches it in:```
lspci -nn
```

---

### Post by rottweiler1204 on 2011-03-05
**lspci -nn **reveals...
 
00:00.0 Host bridge [0600]: Intel Corporation N10 Family DMI Bridge [8086:a010]
00:02.0 VGA compatible controller [0300]: Intel Corporation N10 Family Integrated Graphics Controller [8086:a011]
00:02.1 Display controller [0380]: Intel Corporation N10 Family Integrated Graphics Controller [8086:a012]
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02)
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2)
00:1f.0 ISA bridge [0601]: Intel Corporation NM10 Family LPC Controller [8086:27bc] (rev 02)
00:1f.2 SATA controller [0106]: Intel Corporation N10/ICH7 Family SATA AHCI Controller [8086:27c1] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02)
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
07:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8176] (rev 01)

---

### Post by chili555 on 2011-03-05
Please see: [http://ubuntuforums.org/showthread.php?t=1630650&highlight=10ec%3A8176&page=2](http://ubuntuforums.org/showthread.php?t=1630650&highlight=10ec%3A8176&page=2)

Post #15 and following. Please post back if you get stuck.

---

### Post by rottweiler1204 on 2011-03-05
I got stuck. No surprise there. I went to post #15 and double checked that I has *linux-headers-generic *and *build-essential* installed, which I do. 
 
I download the driver rtl8192ce_linux_2.6.0005.1116.2010 and extract it. Then I do the following:
 
**cd Downloads**
**cd rtl8192ce_linux_2.6.0005.1116.2010**
**sudo su**
**make**
 
At **make, **it seems to screw up. A lot of commands not found, not found, errors, and blah blah blah. 
 
In the rtl8192... folder, there's no "make", but there's a "Makefile". Is that the problem?
 
Oi, this is so confusing.

---

### Post by chili555 on 2011-03-05
> At make, it seems to screw up. A lot of commands not found, not found, errors, and blah blah blah. Can you copy and paste from the terminal to a text document and transfer it on a USB drive and post them here?

If you have already closed the terminal, open a new one and repeat the steps with one change so we have a clean slate:```
cd Downloads
cd rtl8192ce_linux_2.6.0005.1116.2010
sudo su
[COLOR="Red"]make clean[/COLOR]
make
```> In the rtl8192... folder, there's no "make", but there's a "Makefile". Is that the problem?Nope. The command 'make' says, very roughly, see if there is a Makefile, open it in a terminal and execute all the commands in there. It is supposed to make the driver module ready for installation taylor-made for your kernel and gcc versions.> this is so confusing. No worries, Dr. Chili is here to help. Almost no-one gets it perfectly the first time they ever compile a driver, including me.

---

### Post by rottweiler1204 on 2011-03-05
**make clean**
 
[EMAIL="root@nicole-Inspiron-1018:/home/nicole/Downloads/rtl8192ce_linux_2.6.0005.1116.2010"]root@nicole-Inspiron-1018:/home/nicole/Downloads/rtl8192ce_linux_2.6.0005.1116.2010[/EMAIL]# make clean
make[1]: Entering directory `/home/nicole/Downloads/rtl8192ce_linux_2.6.0005.1116.2010/HAL/rtl8192'
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm -fr .tmp_versions
rm -fr Modules.symvers
rm -fr Module.symvers
rm -fr Module.markers
rm -fr modules.order
rm -fr tags
make[2]: Entering directory `/home/nicole/Downloads/rtl8192ce_linux_2.6.0005.1116.2010/HAL/rtl8192/rtl8192c'
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
rm -fr .tmp_versions
rm -fr Modules.symvers
rm -fr Module.symvers
rm -fr Module.markers
rm -fr modules.order
rm -fr tags
make[2]: Leaving directory `/home/nicole/Downloads/rtl8192ce_linux_2.6.0005.1116.2010/HAL/rtl8192/rtl8192c'
make[1]: Leaving directory `/home/nicole/Downloads/rtl8192ce_linux_2.6.0005.1116.2010/HAL/rtl8192'
make[1]: Entering directory `/home/nicole/Downloads/rtl8192ce_linux_2.6.0005.1116.2010/rtllib'
rm -fr *.mod.c *.mod *.o .*.cmd *.mod.* *.ko *.o *~
rm -rf .tmp_versions
rm -rf Module.symvers
rm -fr Module.markers
rm -fr modules.order
rm -fr tags
make[1]: Leaving directory `/home/nicole/Downloads/rtl8192ce_linux_2.6.0005.1116.2010/rtllib'
 
**make**

[EMAIL="root@nicole-Inspiron-1018:/home/nicole/Downloads/rtl8192ce_linux_2.6.0005.1116.2010"]root@nicole-Inspiron-1018:/home/nicole/Downloads/rtl8192ce_linux_2.6.0005.1116.2010[/EMAIL]# make
/usr/src/linux-headers-2.6.35-27-generic/scripts/gcc-version.sh: line 25: gcc: command not found
/usr/src/linux-headers-2.6.35-27-generic/scripts/gcc-version.sh: line 26: gcc: command not found
make[1]: Entering directory `/usr/src/linux-headers-2.6.35-27-generic'
/usr/src/linux-headers-2.6.35-27-generic/arch/x86/Makefile:81: stack protector enabled but no compiler support
make[1]: gcc: Command not found
  CC [M]  /home/nicole/Downloads/rtl8192ce_linux_2.6.0005.1116.2010/HAL/rtl8192/rtl_core.o
/bin/sh: gcc: not found
make[2]: *** [/home/nicole/Downloads/rtl8192ce_linux_2.6.0005.1116.2010/HAL/rtl8192/rtl_core.o] Error 127
make[1]: *** [_module_/home/nicole/Downloads/rtl8192ce_linux_2.6.0005.1116.2010/HAL/rtl8192] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-27-generic'
make: *** [all] Error 2

---

### Post by chili555 on 2011-03-05
> /usr/src/linux-headers-2.6.35-27-generic/scripts/gcc-version.sh: line 25: gcc: command not foundWould you please check again in System > Administration > Synaptic that you have *build-essential* installed? It has a little green box indicating it's installed? Please see attached.

You will need to carry that little netbook over to the router and get an internet connection in order to download.

---

### Post by rottweiler1204 on 2011-03-05
Omg, I am so blonde! I didn't have *build-essential* installed and once it was, the commands worked perfect, and I now have wireless! Thank you so much!!!!!

---

### Post by chili555 on 2011-03-05
Awesome! Great job. noW u r uh linuxian!

---

