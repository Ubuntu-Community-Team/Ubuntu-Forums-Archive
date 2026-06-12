---
title: "Atheros AR8151 ethernet on Asus P8H67-V"
date: 2011-01-28
forum: Networking &amp; Wireless
---

### Post by m0gwai on 2011-01-28
Hi,
here's a solution to get the Atheros Gigabit ethernet on the Asus P8H67-V Sandy Brigde board to work.

The device is listed as:

```

07:00.0 Ethernet controller [0200]: Atheros Communications Device [1969:1083] (rev c0)
	Subsystem: ASUSTeK Computer Inc. Device [1043:847e]
	Flags: bus master, fast devsel, latency 0, IRQ 47
	Memory at fe400000 (64-bit, non-prefetchable) [size=256K]
	I/O ports at d000 [size=128]
	Capabilities: [40] Power Management version 3
	Capabilities: [48] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [58] Express Endpoint, MSI 00
	Capabilities: [6c] Vital Product Data
	Capabilities: [100] Advanced Error Reporting

``` 

Unfortunately, the 1969:1083 is not supported yet by the atl1e module in the kernel. Atheros offers linux drivers for the AR81 family on their website:

[[COLOR="Blue"]AR81Family Linux Driver[/COLOR]]("http://partner.atheros.com/Download.aspx?id=162")

Since some data structures of net_device changed in 2.6.35, the above driver does not compile with kernels > 2.6.34. I wrote a patch to adapt to the changes in net_device and the Makefile:

```

diff -urN src-old/atl1c_main.c src/atl1c_main.c
--- src-old/atl1c_main.c	2011-01-28 13:32:59.277576319 +0100
+++ src/atl1c_main.c	2011-01-28 11:48:39.677573301 +0100
@@ -336,7 +336,13 @@
 {
 	struct atl1c_adapter *adapter = netdev_priv(netdev);
 	struct atl1c_hw *hw = &adapter->hw;
+
+#if ( LINUX_VERSION_CODE >= KERNEL_VERSION(2,6,35) )
+	struct netdev_hw_addr *ha;
+#else
 	struct dev_mc_list *mc_ptr;
+#endif
+
 	u32 mac_ctrl_data = 0;
 	u32 hash_value;
 
@@ -359,10 +365,18 @@
 	AT_WRITE_REG_ARRAY(hw, REG_RX_HASH_TABLE, 1, 0);
 
 	/* comoute mc addresses' hash value ,and put it into hash table */
-	for (mc_ptr = netdev->mc_list; mc_ptr; mc_ptr = mc_ptr->next) {
-		hash_value = atl1c_hash_mc_addr(hw, mc_ptr->dmi_addr);
-		atl1c_hash_set(hw, hash_value);
+
+#if ( LINUX_VERSION_CODE >= KERNEL_VERSION(2,6,35) )
+	netdev_for_each_mc_addr(ha, netdev){
+	  hash_value = atl1c_hash_mc_addr(hw, ha->addr);
+	  atl1c_hash_set(hw, hash_value);
+	}
+#else
+	for(mc_ptr = netdev->mc_list; mc_ptr; mc_ptr = mc_ptr->next) {
+	  hash_value = atl1c_hash_mc_addr(hw, mc_ptr->dmi_addr);
+	  atl1c_hash_set(hw, hash_value);
 	}
+#endif
 }
 
 #ifdef NETIF_F_HW_VLAN_TX
diff -urN src-old/atl1e_main.c src/atl1e_main.c
--- src-old/atl1e_main.c	2011-01-28 13:32:59.277576319 +0100
+++ src/atl1e_main.c	2011-01-28 11:46:30.327572286 +0100
@@ -1829,7 +1829,13 @@
 {
     struct atl1e_adapter *adapter = netdev_priv(netdev);
     struct atl1e_hw *hw = &adapter->hw;
+
+#if ( LINUX_VERSION_CODE >= KERNEL_VERSION(2,6,35) )
+    struct netdev_hw_addr *ha;
+#else
     struct dev_mc_list *mc_ptr;
+#endif
+
     u32 rctl;
     u32 hash_value;
 
@@ -1856,10 +1862,17 @@
 
     /* comoute mc addresses' hash value ,and put it into hash table */
 
+#if ( LINUX_VERSION_CODE >= KERNEL_VERSION(2,6,35) )
+    netdev_for_each_mc_addr(ha, netdev){
+      hash_value = atl1e_hash_mc_addr(hw, ha->addr);
+      atl1e_hash_set(hw, hash_value);
+    }
+#else
     for(mc_ptr = netdev->mc_list; mc_ptr; mc_ptr = mc_ptr->next) {
         hash_value = atl1e_hash_mc_addr(hw, mc_ptr->dmi_addr);
         atl1e_hash_set(hw, hash_value);
     }
+#endif
 }
 
 
diff -urN src-old/Makefile src/Makefile
--- src-old/Makefile	2011-01-28 13:32:59.277576319 +0100
+++ src/Makefile	2011-01-28 11:33:56.707574257 +0100
@@ -89,12 +89,12 @@
     CONFIG_FILE  := $(KSRC)/include/linux/autoconf.h
   endif
 else
-  ifneq (,$(wildcard $(KOBJ)/include/linux/utsrelease.h))
-    VERSION_FILE := $(KOBJ)/include/linux/utsrelease.h
+  ifneq (,$(wildcard $(KOBJ)/include/generated/utsrelease.h))
+    VERSION_FILE := $(KOBJ)/include/generated/utsrelease.h
   else
     VERSION_FILE := $(KOBJ)/include/linux/version.h
   endif
-  CONFIG_FILE  := $(KSRC)/include/linux/autoconf.h
+  CONFIG_FILE  := $(KSRC)/include/generated/autoconf.h
 endif
 
 ifeq (,$(wildcard $(VERSION_FILE)))

```

Change into the src directory of the Atheros driver and apply:

```

patch -p1 < /path/to/AR81Family-linux-v1-1.0.1.14.patch
```

It should build fine now. 
I tested it on 2.6.35-25-server and 2.6.38-rc2.

---

### Post by M911 on 2011-01-29
Hi!
 
Tnx for your text, but I´m a noobie in this and dont understand how to fix this!
 
Can you develop you post so I understand? Plz! 
 
Tnx for your help!

---

### Post by iykrichie on 2011-01-29
my latop's ethernet is an atheros and after I installed 10.04 I got it to work without problem having followed the post on this link [http://tuxthink.blogspot.com/2010/08/enabling-atheros-ethernet-controller-on.html](http://tuxthink.blogspot.com/2010/08/enabling-atheros-ethernet-controller-on.html) 

but I got some updates regrettably now its back to no wired network I have tried doing the same procedure again and it still didnt work  on Kernel Linux 2.6.32-28 generic but if I boot into the previous kernel Linux 2.6.32-21 generic it works well.



 *-network UNCLAIMED     
       description: Network controller
       product: Broadcom Corporation
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f0500000-f0503fff
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR8152 v1.1 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:04:00.0
       version: c1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list
       configuration: latency=0
       resources: memory:f0400000-f043ffff ioport:2000(size=128)

---

### Post by m0gwai on 2011-01-31
Hi M911,

this post explicitly deals with the Atheros ethernet chip with the PCI ID 1969:1083. You find the PCI ID by calling 

```
lspci -nn
```

and  looking for the Atheros Ethernet controller:

```

07:00.0 Ethernet controller [0200]: Atheros Communications Device [1969:1083] (rev c0)

```

My post gives a solution if you have this chip (or, actually, a chip of this family) and you want to use a kernel > 2.4.34 (e.g. if you want to use Maverick Meerkat, 10.10):

1) Download und unpack the driver from the Atheros website
2) Download the patch from my original post
3) cd into the src sub directory of the driver
4) excute
```
patch -p1 < /path/to/AR81Family-linux-v1-1.0.1.14.patch
```
5) build and install the new driver:
```
sudo make install
```
6) Load the driver:
```
sudo modprobe atl1e
```
7) Check wether the device is now working:
```
ifconfig -a
```

You should see a new ethX device now, which you can configure as usual. 

Hope this helps.

---

### Post by m0gwai on 2011-01-31
Hi iykrichie,

can you check wether the module is really updated for your newer kernel:

```
modinfo /lib/modules/2.6.32-28-server/kernel/drivers/net/atl1e/atl1e.ko
```

It should show the version of the driver you downloaded from Atheros.

---

### Post by ylb35 on 2011-01-31
many thanks it works great :-)

---

### Post by stasouv on 2011-02-05
> **m0gwai said:**
> Hi M911,

1) Download und unpack the driver from the Atheros website
2) Download the patch from my original post
3) cd into the src sub directory of the driver
4) excute
```
patch -p1 < /path/to/AR81Family-linux-v1-1.0.1.14.patch
```5) build and install the new driver:
```
sudo make install
```6) Load the driver:
```
sudo modprobe atl1e
```7) Check wether the device is now working:
```
ifconfig -a
```You should see a new ethX device now, which you can configure as usual. 

Hope this helps.

To start with, please forgive me if I don't use "by the book" terms, as I am a newbie.

To the matter, this exact way did not work for me, I could have fixed it by changing the autoconf.h location in the Makefile but I didn't have to bother.

However, what did work for me is:

1) as above, but not actually used. Into tmp Atheros drv
2) as above. I unpacked into a totally different directory, tmp Atheros patch
3) I changed into that directory (patch)
4) install it - It works!

```

 cd /tmp/Atheros/drv
tar xvvf AR81Family-linux-v1.0.1.14.tar.gz
cd /tmp/Atheros/patch
tar xvvf AR81Family-linux-v1-1.0.1.14.patch.tar.gz
sudo make install
sudo modprobe atl1e

```Neither further patching was required, nor any other command.

```

modinfo /lib/modules/2.6.32-28-generic/kernel/drivers/net/atl1e/atl1e.ko

filename:       /lib/modules/2.6.32-28-generic/kernel/drivers/net/atl1e/atl1e.ko
version:        1.0.1.14
license:        GPL
author:         Atheros Corporation, <xiong.huang@atheros.com>, Jie Yang <jie.yang@atheros.com>
description:    Atheros Gigabit Ethernet driver
srcversion:     D420C02689CDDB8DF937282
alias:          pci:v00001969d00002062sv*sd*bc*sc*i*
alias:          pci:v00001969d00001083sv*sd*bc*sc*i*
alias:          pci:v00001969d00001073sv*sd*bc*sc*i*
alias:          pci:v00001969d00002060sv*sd*bc*sc*i*
alias:          pci:v00001969d00001062sv*sd*bc*sc*i*
alias:          pci:v00001969d00001063sv*sd*bc*sc*i*
alias:          pci:v00001969d00001066sv*sd*bc*sc*i*
alias:          pci:v00001969d00001067sv*sd*bc*sc*i*
alias:          pci:v00001969d00001026sv*sd*bc*sc*i*
depends:        
vermagic:       2.6.32-28-generic SMP mod_unload modversions 
parm:           tx_desc_cnt:Transmit description count (array of int)
parm:           rx_mem_size:memory size of rx buffer(KB) (array of int)
parm:           TxRingSz:Transmit Ring Sizen (array of int)
parm:           RxfMemSize:memory size of rx buffer(KB) (array of int)
parm:           media_type:media_type Select (array of int)
parm:           int_mod_timer:Interrupt Moderator Timer (array of int)

```
So, I guess, thank you very much. This post was more than helpful to me. I hated having dist-upgraded and booting onto earlier kernel (2.6.32-25).

---

### Post by m0gwai on 2011-02-08
Not exactly sure what you did and why it worked. 
But as I said in the initial post: the patch is only needed for kernels > 2.6.34, it leaves the code as is for older kernel versions. 
Also, you have to repeat this procedure every time after a ubuntu kernel update.

---

### Post by denizov on 2011-03-30
Sorry guys, 

I just didn't realize that a reboot could be a good option after the modprobe ... thougt it should appear in ifconfig right after modprobe

thanks a lot for the instructions. I'm using Ubuntu for years now but there are many situations when I have to learn and learn again that the problem is mostly between keyboard and chair...










Hi,

after buying an Asus notebook and installing Ubuntu I've the same Problem as you mentioned above.

It's the same ethernet card (i checked) and I followed your instructions but at the end the device is not listed in ifconfig.

I use the patch

```
$ patch -p1 < ../../AR81Family-linux-v1-1.0.1.14.patch
patching file atl1c_main.c
patching file atl1e_main.c
patching file Makefile

```and follow the other steps


```
/AR81Family-linux-v1.0.1.14/src$ sudo make install
make -C /lib/modules/2.6.35-22-generic/build SUBDIRS=/home/x/Downloads/AR81Family-linux-v1.0.1.14/src modules
make[1]: Betrete Verzeichnis '/usr/src/linux-headers-2.6.35-22-generic'
  CC [M]  /home/x/Downloads/AR81Family-linux-v1.0.1.14/src/at_common_main.o
  CC [M]  /home/x/Downloads/AR81Family-linux-v1.0.1.14/src/atl1e_main.o
  CC [M]  /home/x/Downloads/AR81Family-linux-v1.0.1.14/src/atl1c_main.o
  CC [M]  /home/x/Downloads/AR81Family-linux-v1.0.1.14/src/atl1c_hw.o
  CC [M]  /home/x/Downloads/AR81Family-linux-v1.0.1.14/src/atl1e_hw.o
  CC [M]  /home/x/Downloads/AR81Family-linux-v1.0.1.14/src/atl1e_param.o
  CC [M]  /home/x/Downloads/AR81Family-linux-v1.0.1.14/src/atl1c_param.o
  CC [M]  /home/x/Downloads/AR81Family-linux-v1.0.1.14/src/atl1e_ethtool.o
  CC [M]  /home/x/Downloads/AR81Family-linux-v1.0.1.14/src/atl1c_ethtool.o
  CC [M]  /home/x/Downloads/AR81Family-linux-v1.0.1.14/src/kcompat.o
  LD [M]  /home/x/Downloads/AR81Family-linux-v1.0.1.14/src/atl1e.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/x/Downloads/AR81Family-linux-v1.0.1.14/src/atl1e.mod.o
  LD [M]  /home/xDownloads/AR81Family-linux-v1.0.1.14/src/atl1e.ko
make[1]: Verlasse Verzeichnis '/usr/src/linux-headers-2.6.35-22-generic'
gzip -c ../atl1e.7 > atl1e.7.gz
# remove all old versions of the driver
find /lib/modules/2.6.35-22-generic -name atl1e.ko -exec rm -f {} \; || true
find /lib/modules/2.6.35-22-generic -name atl1e.ko.gz -exec rm -f {} \; || true
install -D -m 644 atl1e.ko /lib/modules/2.6.35-22-generic/kernel/drivers/net/atl1e/atl1e.ko
/sbin/depmod -a || true
install -D -m 644 atl1e.7.gz /usr/share/man/man7/atl1e.7.gz
man -c -P'cat > /dev/null' atl1e || true
atl1e.

$ sudo modprobe atl1e

$ ifconfig

lo        Link encap:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metrik:1
          RX packets:76 errors:0 dropped:0 overruns:0 frame:0
          TX packets:76 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:5440 (5.4 KB)  TX bytes:5440 (5.4 KB)

wlan0     Link encap:Ethernet  Hardware Adresse 8c:a9:82:24:50:80  
          inet Adresse:192.168.2.27  Bcast:192.168.2.255  Maske:255.255.255.0
          inet6-Adresse: fe80::8ea9:82ff:fe24:5080/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX packets:6918 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6988 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:6210171 (6.2 MB)  TX bytes:1088434 (1.0 MB)
 
```Do you have any ideas?

Thanks

---

### Post by pboof on 2011-04-09
It works also wel on Acer Iconia LX.RF702.104, Thank :D

---

### Post by leohart on 2011-04-23
The Atheros website has the .tar.gz package which when trying to untar has the following error:

gzip: stdin: decompression OK, trailing garbage ignored
tar: Child returned status 2
tar: Error is not recoverable: exiting now

Can someone please upload a working package?

---

### Post by tamer4matrix on 2011-04-24
Makefile:61: *** Linux kernel source not found.   stop.
 
any idea?

---

### Post by dturley on 2011-05-05
The tar.gz package is still broken.  Does anyone know where to get a good one?

---

### Post by gandalf0815 on 2011-05-06
Whoohoo. This works on my Medion E6224 like a charm.
Thx

---

### Post by FrazAli on 2011-05-12
Just wanted to confirm that it worked for Slackware too. Had to reboot the system to get eth0 correctly configured.

My setup details:

uname -a
Linux SA 2.6.37.6 #3 SMP Sat April 9 22:49:32 CDT 2011 x86_64 Intel(R) Core(TM) i5-2500 CPU @ 3.30 GHz GenuineIntel GNU/Linux

Thanks to OP :)

---

### Post by stirfoo on 2011-06-05
Thanks m0gwai. I've been using Linux for almost a decade now and it just keeps getting better.[U][URL="http://ubuntuforums.org/member.php?u=1233146"]
[/URL][/U]

---

### Post by tosh755 on 2011-06-15
Hello mOgwai,
I had the same problem with a Toshiba 755 and openSuse 11.4.
Rather than changing the subdirectories from "linux" to "generated" in the Makefile, I preferred to create logical links from linux to ../generated, defined a logical link linux-2.6.37.6-0.5-default-obj -> linux-2.6.37.6-0.5-obj/x86_64/default in the /usr/src, and added /usr/src/linux-$(BUILD_KERNEL)-obj to the kernel search path in the Makefile.
Though handling the Makefile problem differently, your patches on the source files worked perfectly!
Thanks!:)

---

### Post by physe on 2011-06-16
It just worked on my Acer Aspire TimelineX 3830TG with Ubuntu 10.10 kernel 2.6.35-30-generic-pae (for future reference).

Thanks.

The tar.gz unpacks if you run the command via console (ignore the error).

---

### Post by GaganBrahmi on 2011-07-15
I tried to visit Atheros site for getting the package for driver, however they no longer have it.

Does anyone have the original compressed file that I can use or the new link where the package is still available?

---

### Post by corkscrew on 2011-07-17
Bump

Anyone know where to get the driver? none of the atheros links work since the company has been taken over

---

### Post by lesssonsvic on 2011-07-17
Hi. I have a Acer Aspire 5253-BZ820, I just install Ubuntu 10.04 Lucid 2.6.32-21-generic and I don't have Internet (Ethernet o wireless ... Win 7 works without problems):

lspci shows: 
Atheros Communications Device 1083 (revc c0)
Broadcom Corporation Device 4357 (rev 01).


Ethernet controller [0200]: Atheros Communications Device [1969:1083] (rev c0)

Network controller [0280]: Broadcom Corporation Device device [14e4:4357] (rev 01)

I try to follow this link, but I cant solve the problems. Any idea?
I'm new in ubuntu, I need all the necesary steps, all of them. Thanks.

---

### Post by potter999 on 2011-08-06
you can get the driver files here   [http://ifile.it/cfzeko0](http://ifile.it/cfzeko0)

---

### Post by rijalsetiawan on 2011-08-14
> **potter999 said:**
> you can get the driver files here   [http://ifile.it/cfzeko0](http://ifile.it/cfzeko0)

thank you very much Mr.potter999 :KS:KS

---

### Post by Diamond2 on 2011-08-15
> **potter999 said:**
> you can get the driver files here   [http://ifile.it/cfzeko0](http://ifile.it/cfzeko0)

Thank you! :guitar:

---

### Post by 175n on 2011-10-04
> **potter999 said:**
> you can get the driver files here   [http://ifile.it/cfzeko0](http://ifile.it/cfzeko0)

Thanks!

---

### Post by pdc on 2011-10-04
gosh;

and you trust this !!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by tunefish85 on 2011-10-28
Thank you veryveryvery much for re-upping the driver file potter999!
It Works!!

---

### Post by scrooge_74 on 2011-11-01
README files says is for 2.6 kernels will it work on a 3.0 ?

---

### Post by zalber on 2011-11-03
Thanks a lot; it works in my asus p5g41t-m !

---

### Post by 3dbDown on 2011-11-04
sorry, my error

---

### Post by 3dbDown on 2011-11-04
My question (originally posted here) was actually answered by FrazAli (above; re Slackware applicability?), sorry, missed it in my panic & confusion while trying to integrate all the pieces.
 
BUT I STILL AM NOT UP, alas !
 
Setup is MSI H61M-P23/B3 Sandy bridge mainboard with the 1969-1083 Atheros chip on-board, distro is Slackware 13.37 (linux 2.6.37.6). Device shows in lspci output, but apparently the atl1e driver is incompat with linux 2.6.37.6, so no eth0 displayed by ifconfig.
 
At first I was trying to patch the source atl1e_main.c in the "build" directory, which failed, so I went to the /usr/src/.../atl1e/ dir, but the same problem
 
Don't know why FrazAli had success using **_m0gwai's solution_** ( [http://ubuntuforums.org/showthread.php?t=1677122](http://ubuntuforums.org/showthread.php?t=1677122) )and I don't, but when attempting to patch (step 1) I get failure:
 
can't find file to patch at input line 4
perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------------------
|diff -urN src-old/atl1c_main.c src/atl1c_main.c
|--- src-old/atl1c_main.c    2011-01-28 13:32:59.277576319 +0100
|+++ src/atl1c_main.c  2011-01-28 11:48:39.677573301 +0100
--------------------------------------------------
File to Patch:
 
In m0gwai's discussion and code block, it *appears* that the code will patch either the atl1c **or **the atl1e driver/module file, but when I input the atl1e_main.c where asked  which file to patch, I just get many more failure blocks (way too many to reproduce manually here)
 
I am truely a "Patch Virgin" ! This IS my first rodeo.
 
Are the failure reports nominal?
I get a null response when I: 
diff atl1e_main.c atl1e_main.c.orig
... so it appears that nothing has happened.
 
any thoughts?

---

### Post by fsandefur on 2011-11-09
this all looks great..got everything set up per the instructions...and....

I get this:

      The program 'Patch' is not currently installed. You can install it by typing
           sudo apt -get install patch

which seems a little pointless since apt cannot get ot the internet since the network card in question is misbehaving.

This is a fresh install of 10.04.3 LTS 64 bit on a brand new system.

Help?  Suggestions?  Life preserver?

---

### Post by eminent_ed on 2011-11-15
Hi [fsandefur]("http://ubuntuforums.org/member.php?u=1490807")

I installed that same server now.

Suggestion : During installation, you can select "manually select packages". You should be able to find *patch*  there.

---

### Post by nico45 on 2011-11-22
> **m0gwai said:**
> 
here's a solution to get the Atheros Gigabit ethernet on the Asus P8H67-V Sandy Brigde board to work.

Thank you for saving my day and my nerves ! :)

---

### Post by ledzgio on 2011-12-05
Is this solution available on kernel 3.x? can I compile those drivers under the new kernel? do you know any solution?


every suggestion will be really appreciated.

thanks

---

### Post by nonatz92 on 2011-12-18
Can anyone please upload the patched file? I get errors while patching (sorry, that I cannot post them, I had to reboot on Windows)

---

### Post by ijustneedadownload on 2012-01-01
Hi,

attached you can find **the patched** AR8151 ethernet driver. It compiled well on my 2.6.37.6 Slackware machine.

**Kudos to m0gwai, thanks for the patch.**

_Step by Step (add sudo if on Ubuntu):_
- extract driver (tar xjf AR81Family-linux-v1.0.1.14.tar.bz2)
- cd AR81Family-linux-v1.0.1.14/src/
- make install
- modprobe atl1e
- ifconfig eth0 (should show the interface)

_OR you can go with one big junk (add sudo if on Ubuntu):_
tar xjf AR81Family-linux-v1.0.1.14.tar.bz2 && cd AR81Family-linux-v1.0.1.14/src/ && make install && modprobe atl1e && ifconfig eth0
 
Regards

---

### Post by ijustneedadownload on 2012-01-01
> **ledzgio said:**
> Is this solution available on kernel 3.x? can I compile those drivers under the new kernel? do you know any solution?


every suggestion will be really appreciated.

thanks

Why don't you just try it?

---

### Post by sebthemonster on 2012-01-04
Thanks a lot at all of us ! You save my day life ;)

---

### Post by damo12 on 2012-01-04
Hi everyone,

I've just upgraded my laptop and wanted to configure the LAN port.  After some reading around (including this thread), I managed to get this running with a fresh install of Ubuntu 10.4.3 (64 bit).  I found the driver extremely difficult to get hold of so I've attached it to this post in case anyone else is having the same problem.

This is how I managed it using the attached driver:

[LIST=1]
[*]Copy the driver to a convenient location
[*]Open terminal
[*]Type: sudo tar -xzvf /[driver location]/AR81Family-linux-v1.0.1.14.zip
[*]Type: sudo make install
[*]Type: sudo modprobe atle
[*]Type: exit
[/LIST]

I found that once it had been installed and was working correctly, Ubuntu installed its latest updates which then wiped the driver from the system.  Once I re-ran the above steps it's working fine again.

For any noobies out there, if you're not sure of the location of where you've saved the driver, navigate to the folder where it is and press "Ctrl+L" and you will see the address at the top of the window.

I hope this is useful to you.

---

### Post by ijustneedadownload on 2012-01-21
Hey guys,

I've compiled linux 3.2.1 on my Slack to test the support of AR8151. It works out of the box with the experimental drivers that are built in to the kernel. Just check the Atheros section when making the kernel config and enable the driver whichs module would/will be called 'atl1e'.

---

### Post by gotzon on 2012-01-31
> **m0gwai said:**
> Hi,
here's a solution to get the Atheros Gigabit ethernet on the Asus P8H67-V Sandy Brigde board to work.
Unfortunately, the 1969:1083 is not supported yet by the atl1e module in the kernel. Atheros offers linux drivers for the AR81 family on their website:

[[COLOR=Blue]AR81Family Linux Driver[/COLOR]]("http://partner.atheros.com/Download.aspx?id=162")

.
When I try to download this driver, I am taking this error: 
**Bad Request (Invalid Hostname)**



Someone can put the drivers on any host?? rapidshare or something?? Thanks a lot!!

---

### Post by damo12 on 2012-01-31
Hi gotzon,

I've just checked and can still download the file located at [http://ubuntuforums.org/showpost.php?p=11586563&postcount=40]("http://ubuntuforums.org/showpost.php?p=11586563&postcount=40").

If that's still not working for you, I'll see if I can post it somewhere else.

---

### Post by jack3010 on 2012-02-02
my ubuntu server 10.04.3 LTS 2.6.32-38-server
after i patch driver , make install and Linux kernel source not configured - missing autoconf.h.  Stop.
please help me.

---

### Post by salehabbas on 2012-02-10
> 
1) Download und unpack the driver from the Atheros website


Hi there,
Where can i download the driver ?
i am using CentOS 6.0 
and my network card is atheros ar8151

thanks a lot

---

### Post by pawn18 on 2012-02-11
nevermind

---

### Post by drwatson32 on 2012-03-05
> **damo12 said:**
> Hi everyone,

I've just upgraded my laptop and wanted to configure the LAN port.  After some reading around (including this thread), I managed to get this running with a fresh install of Ubuntu 10.4.3 (64 bit).  I found the driver extremely difficult to get hold of so I've attached it to this post in case anyone else is having the same problem.

This is how I managed it using the attached driver:

[LIST=1]
[*]Copy the driver to a convenient location
[*]Open terminal
[*]Type: sudo tar -xzvf /[driver location]/AR81Family-linux-v1.0.1.14.zip
[*]Type: sudo make install
[*]Type: sudo modprobe atle
[*]Type: exit
[/LIST]

I found that once it had been installed and was working correctly, Ubuntu installed its latest updates which then wiped the driver from the system.  Once I re-ran the above steps it's working fine again.

For any noobies out there, if you're not sure of the location of where you've saved the driver, navigate to the folder where it is and press "Ctrl+L" and you will see the address at the top of the window.

I hope this is useful to you.

I've followed your instruction and got some problems.
Just in case, I'm posting workarounds here:
on step 2 I've entered "unzip AR81Family-linux-v1.0.1.14.zip"
on step 5 I've entered "sudo modprobe atl1e".

---

### Post by JPM electronics on 2012-03-14
Hi
Installed from mOgwai;s driver and his first page installing guide.
Works well with Asus P5G41T-MLX3 too. :)

---

### Post by dadanym on 2012-03-14
> **m0gwai said:**
> Hi M911,

this post explicitly deals with the Atheros ethernet chip with the PCI ID 1969:1083. You find the PCI ID by calling 

```
lspci -nn
```and  looking for the Atheros Ethernet controller:

```

07:00.0 Ethernet controller [0200]: Atheros Communications Device [1969:1083] (rev c0)

```My post gives a solution if you have this chip (or, actually, a chip of this family) and you want to use a kernel > 2.4.34 (e.g. if you want to use Maverick Meerkat, 10.10):

1) Download und unpack the driver from the Atheros website
2) Download the patch from my original post
3) cd into the src sub directory of the driver
4) excute
```
patch -p1 < /path/to/AR81Family-linux-v1-1.0.1.14.patch
```5) build and install the new driver:
```
sudo make install
```6) Load the driver:
```
sudo modprobe atl1e
```7) Check wether the device is now working:
```
ifconfig -a
```You should see a new ethX device now, which you can configure as usual. 

Hope this helps.

thx very much... permission to use the code
i realy newbie:confused:
thx again:)

---

### Post by dadanym on 2012-03-15
i'am realy newbie... 1st day left in Ubuntu Desktop 8.10

i use AR8151 ethernet on Asus P5G41T-L MX3 and this is my experiences::confused:

1. in other internet connection i use this link to get driver

[http://code.google.com/p/kyosls/downloads/detail?name=AR81Family-linux-v1.0.1.14.tar.gz&can=2&q=](http://code.google.com/p/kyosls/downloads/detail?name=AR81Family-linux-v1.0.1.14.tar.gz&can=2&q=)

2. copy AR81Family-linux-v1-1.0.1.14.patch.tar.gz to ubuntu home on Asus P5G41T-L MX3 with Ubuntu Desktop 8.10 by flashdisk

3. then in Terminal (Applications - Accessories - Terminal)

4. sudo su

5. tar xvvf AR81Family-linux-v1-1.0.1.14.patch.tar.gz

and then the code show up.... bla...bla...

6. sudo make install

other code show up...

7. sudo modprobe atl1e

8. ifconfig -a

other code show up... about what you install

9. (Systems - Administrations - Network Tools)

10. change "Network device" with "Ethernet Interface (eth0)" in pull up menu

THAT'S IT....


THK TO UBUNTUFORUMS.ORG
:popcorn:

---

