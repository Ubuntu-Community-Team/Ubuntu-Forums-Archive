---
title: "having troubles with ndiswrapper"
date: 2010-11-14
forum: Networking &amp; Wireless
---

### Post by Exorbio on 2010-11-14
Hello!  I'm new to linux and ubuntu.  I'm having several issues and I've already posted about this on the installation forum.  I don't know where the problem actually lies.  Here's some basic stats:

Ubuntu 10.10 i386 32-bit (other versions won't install at all)
AMD Phenom X4 9100-e Quad-core
ATi Radeon HD 3200 Integrated Graphics
Wireless Adapter: ZyXEL G-220 v3

I've set up ndiswrapper and the driver and things work temporarily.  Eventually, though my connection is dropped and the only way to get it back is to open Window Wireless Drivers, uninstall the driver and then re-install it.  Then it will work for a little while longer.

Some possibly related issues: 

--sometimes when I go into the Window Wireless Drivers, my system will completely freeze upon request for authentication. Sometimes it will freeze when I'm trying to reinstall the driver.
--once it does this it will always do it until I uninstall the ndisgtk and reinstall.
--when I try to uninstall the ndisgtk, it gets hung up in that process as well.  So then I reboot and can reinstall it.
--I've tried step 7 in the sticky, but I only have the wireless connection, so when I try to install build-essential, it gets hung trying to download from the internet.  This actually caused an issue where I could no longer get the install CD to mount automatically.  I don't what to do in terminal, so I redid the entire install.
-- the signal strength and bandwidth diminish as I download anything big.  I've had to do the uninstall and reinstall driver while trying to download updates in the update manager.


Maybe Unrelated:

--once I get the updates downloaded, the system will crash when I reboot to complete the update installations.  It won't just crash though.  After I select to boot ubuntu, I get a blank screen and a silent tower.


Please help.  I've been at this for 3 days now.

---

### Post by Exorbio on 2010-11-21
I think I've taken care of the crashing.  I was finally able to install my graphics card drivers.


I'm still having problems with ndiswrapper.  When I restart from windows and boot into Ubuntu,
I get the following output on my screen over and over again.

```

hub 2-0:1.0: cannot reset port 3 (err = -108) 
hub 2-0:1.0: cannot enable port 3. Maybe the USB cable is bad?
hub 2-0:1.0: hub_port_status failed (err = -108) 
BUG: soft lockup - CPU#3 stuck for 61s! [ntos_wq:643] 
Process ntos_wq (pid:643, ti = f1a34000 task  = f2928cb0 task .ti = f1a34000 
Stack: 
Call Trace: 
Code: 90 e4 92 5d c0 89 86 8c 01 00 00 8d 43 04 e8 2d bc 46 c8 31 c0 c7 03 
01 00 00 00 89 73 1c ba 01 00 00 00 87 17 85 d2 74 09 f3 90 <83> 3f 00 74 f3 
eb f7 8b 1c 24 8b 74 24 04 8b 7c 24 08 89 ec 5d 
INFO: task ureadahead:340 blocked for more than 120 seconds

```If I shutdown the tower completely and boot straight into Ubuntu, things seem ok.
But I am also still experiencing the problem where I lose internet connection and I
have to uninstall and reinstall the USB adapter driver.

---

### Post by Exorbio on 2010-11-21
After trying option #7 under the sticky (compiling ndiswrapper from source), I receieved errors when running the make and make install commands.

After running "make" I get this:
```

make -C driver
make[1]: Entering directory `/home/ken/Desktop/ndiswrapper-1.56/driver'
make -C /usr/src/linux-headers-2.6.35-22-generic M=/home/ken/Desktop/ndiswrapper-1.56/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.35-22-generic'
  LD      /home/ken/Desktop/ndiswrapper-1.56/driver/built-in.o
  MKEXPORT /home/ken/Desktop/ndiswrapper-1.56/driver/crt_exports.h
  MKEXPORT /home/ken/Desktop/ndiswrapper-1.56/driver/hal_exports.h
  MKEXPORT /home/ken/Desktop/ndiswrapper-1.56/driver/ndis_exports.h
  MKEXPORT /home/ken/Desktop/ndiswrapper-1.56/driver/ntoskernel_exports.h
  MKEXPORT /home/ken/Desktop/ndiswrapper-1.56/driver/ntoskernel_io_exports.h
  MKEXPORT /home/ken/Desktop/ndiswrapper-1.56/driver/rtl_exports.h
  MKEXPORT /home/ken/Desktop/ndiswrapper-1.56/driver/usb_exports.h
  CC [M]  /home/ken/Desktop/ndiswrapper-1.56/driver/crt.o
  CC [M]  /home/ken/Desktop/ndiswrapper-1.56/driver/hal.o
  CC [M]  /home/ken/Desktop/ndiswrapper-1.56/driver/iw_ndis.o
  CC [M]  /home/ken/Desktop/ndiswrapper-1.56/driver/loader.o
  CC [M]  /home/ken/Desktop/ndiswrapper-1.56/driver/ndis.o
  CC [M]  /home/ken/Desktop/ndiswrapper-1.56/driver/ntoskernel.o
  CC [M]  /home/ken/Desktop/ndiswrapper-1.56/driver/ntoskernel_io.o
  CC [M]  /home/ken/Desktop/ndiswrapper-1.56/driver/pe_linker.o
  CC [M]  /home/ken/Desktop/ndiswrapper-1.56/driver/pnp.o
  CC [M]  /home/ken/Desktop/ndiswrapper-1.56/driver/proc.o
  CC [M]  /home/ken/Desktop/ndiswrapper-1.56/driver/rtl.o
  CC [M]  /home/ken/Desktop/ndiswrapper-1.56/driver/wrapmem.o
  CC [M]  /home/ken/Desktop/ndiswrapper-1.56/driver/wrapndis.o
/home/ken/Desktop/ndiswrapper-1.56/driver/wrapndis.c: In function ‘set_multicast_list’:
/home/ken/Desktop/ndiswrapper-1.56/driver/wrapndis.c:953: error: ‘struct net_device’ has no member named ‘mc_count’
/home/ken/Desktop/ndiswrapper-1.56/driver/wrapndis.c:956: error: ‘struct net_device’ has no member named ‘mc_count’
/home/ken/Desktop/ndiswrapper-1.56/driver/wrapndis.c:960: error: ‘struct net_device’ has no member named ‘mc_count’
/home/ken/Desktop/ndiswrapper-1.56/driver/wrapndis.c:960: warning: type defaults to ‘int’ in declaration of ‘_min2’
/home/ken/Desktop/ndiswrapper-1.56/driver/wrapndis.c:960: error: ‘struct net_device’ has no member named ‘mc_count’
/home/ken/Desktop/ndiswrapper-1.56/driver/wrapndis.c:967: error: ‘struct net_device’ has no member named ‘mc_list’
/home/ken/Desktop/ndiswrapper-1.56/driver/wrapndis.c:968: error: dereferencing pointer to incomplete type
/home/ken/Desktop/ndiswrapper-1.56/driver/wrapndis.c:969: error: dereferencing pointer to incomplete type
/home/ken/Desktop/ndiswrapper-1.56/driver/wrapndis.c:971: error: dereferencing pointer to incomplete type
make[3]: *** [/home/ken/Desktop/ndiswrapper-1.56/driver/wrapndis.o] Error 1
make[2]: *** [_module_/home/ken/Desktop/ndiswrapper-1.56/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/ken/Desktop/ndiswrapper-1.56/driver'
make: *** [all] Error 2

```

after I run the "make install" command I get his:
```

make -C driver install
make[1]: Entering directory `/home/ken/Desktop/ndiswrapper-1.56/driver'
make -C /usr/src/linux-headers-2.6.35-22-generic M=/home/ken/Desktop/ndiswrapper-1.56/driver
make[2]: Entering directory `/usr/src/linux-headers-2.6.35-22-generic'
  CC [M]  /home/ken/Desktop/ndiswrapper-1.56/driver/wrapndis.o
/home/ken/Desktop/ndiswrapper-1.56/driver/wrapndis.c: In function ‘set_multicast_list’:
/home/ken/Desktop/ndiswrapper-1.56/driver/wrapndis.c:953: error: ‘struct net_device’ has no member named ‘mc_count’
/home/ken/Desktop/ndiswrapper-1.56/driver/wrapndis.c:956: error: ‘struct net_device’ has no member named ‘mc_count’
/home/ken/Desktop/ndiswrapper-1.56/driver/wrapndis.c:960: error: ‘struct net_device’ has no member named ‘mc_count’
/home/ken/Desktop/ndiswrapper-1.56/driver/wrapndis.c:960: warning: type defaults to ‘int’ in declaration of ‘_min2’
/home/ken/Desktop/ndiswrapper-1.56/driver/wrapndis.c:960: error: ‘struct net_device’ has no member named ‘mc_count’
/home/ken/Desktop/ndiswrapper-1.56/driver/wrapndis.c:967: error: ‘struct net_device’ has no member named ‘mc_list’
/home/ken/Desktop/ndiswrapper-1.56/driver/wrapndis.c:968: error: dereferencing pointer to incomplete type
/home/ken/Desktop/ndiswrapper-1.56/driver/wrapndis.c:969: error: dereferencing pointer to incomplete type
/home/ken/Desktop/ndiswrapper-1.56/driver/wrapndis.c:971: error: dereferencing pointer to incomplete type
make[3]: *** [/home/ken/Desktop/ndiswrapper-1.56/driver/wrapndis.o] Error 1
make[2]: *** [_module_/home/ken/Desktop/ndiswrapper-1.56/driver] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.35-22-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/ken/Desktop/ndiswrapper-1.56/driver'
make: *** [install] Error 2

```

any ideas?

---

### Post by barcade134 on 2010-12-18
I was having the same problem compiling.  There is a patch file that you can [downloaded here]("http://sourceforge.net/tracker/download.php?group_id=93482&atid=604452&file_id=382833&aid=3042172").  Move this file into the directory with the rest of your files.  Then do the following:

```
patch -p1 < ndis*.patch
```The flags are the letter p and the number one not the letter l.  It should compile now.  I am still trying to get my Netgear WNDA3100v2 to work but at least I am one step closer now.  (I hope)

---

