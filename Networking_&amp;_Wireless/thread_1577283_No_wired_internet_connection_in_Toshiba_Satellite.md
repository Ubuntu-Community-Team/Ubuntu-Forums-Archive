---
title: "No wired internet connection in Toshiba Satellite"
date: 2010-09-18
forum: Networking &amp; Wireless
---

### Post by MajinSaha on 2010-09-18
Ok, a similar post already exists at [http://ubuntuforums.org/showthread.php?t=932114](http://ubuntuforums.org/showthread.php?t=932114), but the solution for that one does not work for here.
I have Toshiba Satellite M305D-S4829, and the Ethernet card is Marvell Yukon 88E8040T PCI-E Fast Ethernet Controller. I can't get a wired internet connection. To put it simply, the lights are not even flashing.
Any suggestions that might work for Ubuntu 10.04, 64-bit edition ?

To help you get started, this is the line that I get from lspci command:

```
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040T PCI-E Fast Ethernet Controller (rev 12)
```

As you can see, Ubuntu recognizes the card, but there's still no connection.

---

### Post by bkratz on 2010-09-18
There is a lot of information here, the later posts are about 10.04.

[http://ubuntuforums.org/showthread.php?t=1319116](http://ubuntuforums.org/showthread.php?t=1319116)

---

### Post by MajinSaha on 2010-09-19
Thanks. That thread was helpful. I followed mathia's advice and got the connection. More specifically, I downloaded and installed a driver. The problem is this solution only was for a current session. Rebooting Ubuntu loses connection again. What should I do in this case ?
By the way, after I execute
```
modprobe sk98lin
```
I get the following:

WARNING: Deprecated config file /etc/modprobe.conf, all config files belong into /etc/modprobe.d/

Does this have any connection to my problem ? After I moved my modprobe.conf file to the catalog modprobe.d, there was no more output.

---

### Post by mathia on 2010-09-19
> **MajinSaha said:**
> Thanks. That thread was helpful. I followed mathia's advice and got the connection. More specifically, I downloaded and installed a driver. The problem is this solution only was for a current session. Rebooting Ubuntu loses connection again. What should I do in this case ?
By the way, after I execute
```
modprobe sk98lin
```I get the following:

WARNING: Deprecated config file /etc/modprobe.conf, all config files belong into /etc/modprobe.d/

Does this have any connection to my problem ? After I moved my modprobe.conf file to the catalog modprobe.d, there was no more output.

Hi MajinSaha,
after the reboot the sky2 driver has been loaded again. You should remove sky2 from initramfs and use sk98lin for your yukon device.

Please do as follows and let me know if it works:

sudo rmmod sky2
sudo rmmod sk98lin
sudo modprobe sk98lin
sudo echo "blacklist sky2" > /etc/modprobe.d/blacklist-sky2.conf 
sudo update-initramfs -u 
sudo reboot

---

### Post by MajinSaha on 2010-09-20
Hi mathia, good to see you here.
I did what you told me. Here's exactly what happened.

The second command 
> sudo rmmod sk98lin
gave me the output that sk98lin was not found in /proc/modules. I decided to ignore it to continued to move on. Right after
> sudo modprobe sk98lin
the lights started to flash, which is a good sign. So the card activated.
The command
> sudo echo "blacklist sky2" > /etc/modprobe.d/blacklist-sky2.conf 
didn't want to execute due to denied permission, despite presence of "sudo". So I had to load pico editor with sudo and manually type "blacklist sky2" in the newly created file blacklist-sky2.conf. This trick worked. The last two commands
> sudo update-initramfs -u 
sudo reboot
went well.
After reboot the cards activates and works. So the problems is partially solved, thanks to you ! Why partially ? 
Because it only tries to connect but fails. I'm very confident this has nothing to do with the provider. There should at least be a local connection, but the only thing I get is
"Wired network, disconnected - you are now offline".
So what would you recommend in this case ?

---

### Post by mathia on 2010-09-20
[QUOTE=MajinSaha;9866865]Hi mathia, good to see you here.

>After reboot the cards activates and works. So the problems is partially solved, thanks to >you ! Why partially ? 

- What is the output of ifconfig?
- Has  the Yukon device an valid IP address?
- Can you ping any remote station or your router?

>Because it only tries to connect but fails. I'm very confident this has nothing to do with >the provider. There should at least be a local connection, but the only thing I get is
>"Wired network, disconnected - you are now offline".

What is the output of :
$ sudo cat /proc/interrupts
Do you see any interrupts for Yukon device?

---

### Post by MajinSaha on 2010-09-20
I cannot put a lot of outputs here, since I'm typing in this forum from another computer and there's no way I can copy/paste. 
ifconfig shows the result for the Yukon card as (just part of it)

eth0 Link encap:Ethernet  HWaddr ff:ff:ff:ff:ff:ff
     inet6 addr: fe80::fdff:ffff:feff:ffff/64 Scope:Link
     UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
     ...
     Interrupt:28 Memory:f0400000-0

How do I check IP ?
Ping gives me "Unknown host" for any URL, even my provider's.
The output of the last command shows a large list. For Yukon device I believe it's
28:   8913   28   PCI-MSI-edge   eth0
The second number corresponds to CPU0, and the third to CPU1 (This laptop is dual core).

---

### Post by Iowan on 2010-09-20
Hmmm :-k HW addr seems a li'l odd...

---

### Post by mathia on 2010-09-20
> **MajinSaha said:**
> I cannot put a lot of outputs here, since I'm typing in this forum from another computer and there's no way I can copy/paste. 
ifconfig shows the result for the Yukon card as (just part of it)

eth0 Link encap:Ethernet  HWaddr ff:ff:ff:ff:ff:ff
     inet6 addr: fe80::fdff:ffff:feff:ffff/64 Scope:Link
     UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
     ...
     Interrupt:28 Memory:f0400000-0

How do I check IP ?
Ping gives me "Unknown host" for any URL, even my provider's.
The output of the last command shows a large list. For Yukon device I believe it's
28:   8913   28   PCI-MSI-edge   eth0
The second number corresponds to CPU0, and the third to CPU1 (This laptop is dual core).

Iowan is right. The HWaddr ff:ff:ff:ff:ff:ff is not normal.

Let's check some points:
1) Is your LAN device activated in BIOS?

2) Did you check your LAN device with other OS systems of funtionality? ( windows or other linux distro?)

3) You can download and run the yukon dos diagnostic tool from Marvell to check the yukon device (the latest one is called yukondg_v6.56.1.3.zip). It's the same link you have downloaded the linux driver.

4) You can check the  IP address also with ifconfig command.At the moment your devcie has no IP address.

---

### Post by MajinSaha on 2010-09-21
Well, at least you could see something wrong in the output, that gives some clue what to look at.

1) My LAN is enabled in BIOS, I checked on the startup.

2) To be honest, the reason I decided to install internet in Ubuntu is because I don't have one in Windows Vista on the same machine. But what I have is common for literally tons of Vista users. We all get "Unidentified network" and "local only" access. So I doubt I have a hardware problem. Besides, Windows says the device is working properly. I spent three days searching forums and trying all possible advice, but nothing changed, and so was for many others. My intuition told me that you have more flexibility to change things in Ubuntu, and decided to give a try. That's why I'm here. 
But, as you asked, I'll try to load Knoppix from live CD and check. What should I try, more specifically, in this case ?

3) I failed to run the diagnostics tool, because it says it does not support 64bit architectures. As I said above, I have 64bit Toshiba. One failure after another, oh man...

Don't know what to do, I simply stuck.

---

### Post by mathia on 2010-09-21
> **MajinSaha said:**
> Well, at least you could see something wrong in the output, that gives some clue what to look at.

1) My LAN is enabled in BIOS, I checked on the startup.

2) To be honest, the reason I decided to install internet in Ubuntu is because I don't have one in Windows Vista on the same machine. But what I have is common for literally tons of Vista users. We all get "Unidentified network" and "local only" access. So I doubt I have a hardware problem. Besides, Windows says the device is working properly. I spent three days searching forums and trying all possible advice, but nothing changed, and so was for many others. My intuition told me that you have more flexibility to change things in Ubuntu, and decided to give a try. That's why I'm here. 
But, as you asked, I'll try to load Knoppix from live CD and check. What should I try, more specifically, in this case ?

3) I failed to run the diagnostics tool, because it says it does not support 64bit architectures. As I said above, I have 64bit Toshiba. One failure after another, oh man...

Don't know what to do, I simply stuck.

Just keep cool and don't be disappointed. :smile:

1) LAN is enabled in BIOS. That's good.

1A) Were you able to install the sk98lin driver v10.85.9.3 on ubuntu 10.04 and blacklist sky2 driver?

1B) Please post the install.log file of sk98lin driver from the DriverInstall directory.

1C) Please post the output of following command to me:
      $ sudo dmesg | grep sk


2) If you boot from knoppix live CD. Please login as root to the console and run the following commands:

2A) Please post the output of following command to me:
      $ sudo dmesg | grep sk

2B) Please run "ifconfig" command and post the output.

2C) If you have a router with dhcp activated connect the notebook to it.
      Please try "dhclient eth0" and see if you can get an IP address from your router.

2D) Can you ping the router?
       Let me know the results.


3) Diagnostic tool is not important. I did not see that you have a  64bit only system.


4) I saw you have Toshiba Satellite M305D-S4829 with Marvell 8040T device. I will download the handbook of your notebook.
     I will install ubuntu 10.04, 64-bit edition  on a 64 bit system and check if I can reproduce your issue, but it may take some time.

---

### Post by MajinSaha on 2010-09-22
Sorry, indeed there's no mentioning of 64bit. I mistook it for another post.

1A) Not only I managed to install sk98lin driver, but I did it several times. In neither of the cases I saw an error of any sort. The last line was even saying "Have fun...".
There's "blacklist-sky2" file in /etc/modprobe.d catalog. It only contains the line "blacklist sky2". There's "modprobe.conf" file in /etc catatlog, that contains nothing (0 bytes). There's also no "sky2.ko" file in .../kernel/drivers/net catalog. Does that answer "yes" to your question ?
1B) This is the output of "install.log" :
```
+++ Install mode: User
+++ Driver version: 10.85.9.3 (Aug-13-2010)
+++ Kernel version 2.6.32-24-generic
+++ smp_count=1
+++ cpu_number=2
+++ kernel_machine=x86_64
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

+++ Compile the driver
+++ ====================================
make: Entering directory `/usr/src/linux-headers-2.6.32-24-generic'
make -C /lib/modules/2.6.32-24-generic/build \
	KBUILD_SRC=/usr/src/linux-headers-2.6.32-24-generic \
	KBUILD_EXTMOD="/tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all" -f /usr/src/linux-headers-2.6.32-24-generic/Makefile \
	
test -e include/linux/autoconf.h -a -e include/config/auto.conf || (		\
	echo;								\
	echo "  ERROR: Kernel configuration is invalid.";		\
	echo "         include/linux/autoconf.h or include/config/auto.conf are missing.";	\
	echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";	\
	echo;								\
	/bin/false)
mkdir -p /tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/.tmp_versions ; rm -f /tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/.tmp_versions/*
make -f /usr/src/linux-headers-2.6.32-24-generic/scripts/Makefile.build obj=/tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all
   rm -f /tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/built-in.o; ar rcs /tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/built-in.o
  cc -Wp,-MD,/tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/.skge.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.4.3/include -I/usr/src/linux-headers-lbm- -Iinclude -Iinclude2 -I/usr/src/linux-headers-2.6.32-24-generic/include -I/usr/src/linux-headers-2.6.32-24-generic/arch/x86/include -include include/linux/autoconf.h -Iubuntu/include -I/usr/src/linux-headers-2.6.32-24-generic/ubuntu/include   -I/tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -fconserve-stack   -I/tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all -DSK_USE_CSUM -DSK_DIAG_SUPPORT -DGENESIS -DYUKON -DYUK2 -DCONFIG_SK98LIN_ZEROCOPY -DSK_EXTREME -DSK_NO_RLMT -DSK_LINUX  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(skge)"  -D"KBUILD_MODNAME=KBUILD_STR(sk98lin)"  -c -o /tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/.tmp_skge.o /tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/skge.c
  cc -Wp,-MD,/tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/.sky2.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.4.3/include -I/usr/src/linux-headers-lbm- -Iinclude -Iinclude2 -I/usr/src/linux-headers-2.6.32-24-generic/include -I/usr/src/linux-headers-2.6.32-24-generic/arch/x86/include -include include/linux/autoconf.h -Iubuntu/include -I/usr/src/linux-headers-2.6.32-24-generic/ubuntu/include   -I/tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -fconserve-stack   -I/tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all -DSK_USE_CSUM -DSK_DIAG_SUPPORT -DGENESIS -DYUKON -DYUK2 -DCONFIG_SK98LIN_ZEROCOPY -DSK_EXTREME -DSK_NO_RLMT -DSK_LINUX  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(sky2)"  -D"KBUILD_MODNAME=KBUILD_STR(sk98lin)"  -c -o /tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/.tmp_sky2.o /tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/sky2.c
  set -e ; perl /usr/src/linux-headers-2.6.32-24-generic/scripts/recordmcount.pl "x86_64" "64" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/sky2.o";
  cc -Wp,-MD,/tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/.skethtool.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.4.3/include -I/usr/src/linux-headers-lbm- -Iinclude -Iinclude2 -I/usr/src/linux-headers-2.6.32-24-generic/include -I/usr/src/linux-headers-2.6.32-24-generic/arch/x86/include -include include/linux/autoconf.h -Iubuntu/include -I/usr/src/linux-headers-2.6.32-24-generic/ubuntu/include   -I/tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -fconserve-stack   -I/tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all -DSK_USE_CSUM -DSK_DIAG_SUPPORT -DGENESIS -DYUKON -DYUK2 -DCONFIG_SK98LIN_ZEROCOPY -DSK_EXTREME -DSK_NO_RLMT -DSK_LINUX  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(skethtool)"  -D"KBUILD_MODNAME=KBUILD_STR(sk98lin)"  -c -o /tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/.tmp_skethtool.o /tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/skethtool.c
  set -e ; perl /usr/src/linux-headers-2.6.32-24-generic/scripts/recordmcount.pl "x86_64" "64" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/skge.o";
  cc -Wp,-MD,/tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/.sky2le.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.4.3/include -I/usr/src/linux-headers-lbm- -Iinclude -Iinclude2 -I/usr/src/linux-headers-2.6.32-24-generic/include -I/usr/src/linux-headers-2.6.32-24-generic/arch/x86/include -include include/linux/autoconf.h -Iubuntu/include -I/usr/src/linux-headers-2.6.32-24-generic/ubuntu/include   -I/tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -fconserve-stack   -I/tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all -DSK_USE_CSUM -DSK_DIAG_SUPPORT -DGENESIS -DYUKON -DYUK2 -DCONFIG_SK98LIN_ZEROCOPY -DSK_EXTREME -DSK_NO_RLMT -DSK_LINUX  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(sky2le)"  -D"KBUILD_MODNAME=KBUILD_STR(sk98lin)"  -c -o /tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/.tmp_sky2le.o /tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/sky2le.c
  set -e ; perl /usr/src/linux-headers-2.6.32-24-generic/scripts/recordmcount.pl "x86_64" "64" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/skethtool.o";
  cc -Wp,-MD,/tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/.skdim.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.4.3/include -I/usr/src/linux-headers-lbm- -Iinclude -Iinclude2 -I/usr/src/linux-headers-2.6.32-24-generic/include -I/usr/src/linux-headers-2.6.32-24-generic/arch/x86/include -include include/linux/autoconf.h -Iubuntu/include -I/usr/src/linux-headers-2.6.32-24-generic/ubuntu/include   -I/tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -fconserve-stack   -I/tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all -DSK_USE_CSUM -DSK_DIAG_SUPPORT -DGENESIS -DYUKON -DYUK2 -DCONFIG_SK98LIN_ZEROCOPY -DSK_EXTREME -DSK_NO_RLMT -DSK_LINUX  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(skdim)"  -D"KBUILD_MODNAME=KBUILD_STR(sk98lin)"  -c -o /tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/.tmp_skdim.o /tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/skdim.c
  set -e ; perl /usr/src/linux-headers-2.6.32-24-generic/scripts/recordmcount.pl "x86_64" "64" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/sky2le.o";
  cc -Wp,-MD,/tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/.skaddr.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.4.3/include -I/usr/src/linux-headers-lbm- -Iinclude -Iinclude2 -I/usr/src/linux-headers-2.6.32-24-generic/include -I/usr/src/linux-headers-2.6.32-24-generic/arch/x86/include -include include/linux/autoconf.h -Iubuntu/include -I/usr/src/linux-headers-2.6.32-24-generic/ubuntu/include   -I/tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -fconserve-stack   -I/tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all -DSK_USE_CSUM -DSK_DIAG_SUPPORT -DGENESIS -DYUKON -DYUK2 -DCONFIG_SK98LIN_ZEROCOPY -DSK_EXTREME -DSK_NO_RLMT -DSK_LINUX  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(skaddr)"  -D"KBUILD_MODNAME=KBUILD_STR(sk98lin)"  -c -o /tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/.tmp_skaddr.o /tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/skaddr.c
  set -e ; perl /usr/src/linux-headers-2.6.32-24-generic/scripts/recordmcount.pl "x86_64" "64" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/skdim.o";
  cc -Wp,-MD,/tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/.skgehwt.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.4.3/include -I/usr/src/linux-headers-lbm- -Iinclude -Iinclude2 -I/usr/src/linux-headers-2.6.32-24-generic/include -I/usr/src/linux-headers-2.6.32-24-generic/arch/x86/include -include include/linux/autoconf.h -Iubuntu/include -I/usr/src/linux-headers-2.6.32-24-generic/ubuntu/include   -I/tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -fconserve-stack   -I/tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all -DSK_USE_CSUM -DSK_DIAG_SUPPORT -DGENESIS -DYUKON -DYUK2 -DCONFIG_SK98LIN_ZEROCOPY -DSK_EXTREME -DSK_NO_RLMT -DSK_LINUX  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(skgehwt)"  -D"KBUILD_MODNAME=KBUILD_STR(sk98lin)"  -c -o /tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/.tmp_skgehwt.o /tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/skgehwt.c
  set -e ; perl /usr/src/linux-headers-2.6.32-24-generic/scripts/recordmcount.pl "x86_64" "64" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/skaddr.o";
  set -e ; perl /usr/src/linux-headers-2.6.32-24-generic/scripts/recordmcount.pl "x86_64" "64" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/skgehwt.o";
  cc -Wp,-MD,/tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/.skgeinit.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.4.3/include -I/usr/src/linux-headers-lbm- -Iinclude -Iinclude2 -I/usr/src/linux-headers-2.6.32-24-generic/include -I/usr/src/linux-headers-2.6.32-24-generic/arch/x86/include -include include/linux/autoconf.h -Iubuntu/include -I/usr/src/linux-headers-2.6.32-24-generic/ubuntu/include   -I/tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -fconserve-stack   -I/tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all -DSK_USE_CSUM -DSK_DIAG_SUPPORT -DGENESIS -DYUKON -DYUK2 -DCONFIG_SK98LIN_ZEROCOPY -DSK_EXTREME -DSK_NO_RLMT -DSK_LINUX  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(skgeinit)"  -D"KBUILD_MODNAME=KBUILD_STR(sk98lin)"  -c -o /tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/.tmp_skgeinit.o /tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/skgeinit.c
  cc -Wp,-MD,/tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/.skgepnmi.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.4.3/include -I/usr/src/linux-headers-lbm- -Iinclude -Iinclude2 -I/usr/src/linux-headers-2.6.32-24-generic/include -I/usr/src/linux-headers-2.6.32-24-generic/arch/x86/include -include include/linux/autoconf.h -Iubuntu/include -I/usr/src/linux-headers-2.6.32-24-generic/ubuntu/include   -I/tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -fconserve-stack   -I/tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all -DSK_USE_CSUM -DSK_DIAG_SUPPORT -DGENESIS -DYUKON -DYUK2 -DCONFIG_SK98LIN_ZEROCOPY -DSK_EXTREME -DSK_NO_RLMT -DSK_LINUX  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(skgepnmi)"  -D"KBUILD_MODNAME=KBUILD_STR(sk98lin)"  -c -o /tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/.tmp_skgepnmi.o /tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/skgepnmi.c
  set -e ; perl /usr/src/linux-headers-2.6.32-24-generic/scripts/recordmcount.pl "x86_64" "64" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/skgeinit.o";
  cc -Wp,-MD,/tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/.skgesirq.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.4.3/include -I/usr/src/linux-headers-lbm- -Iinclude -Iinclude2 -I/usr/src/linux-headers-2.6.32-24-generic/include -I/usr/src/linux-headers-2.6.32-24-generic/arch/x86/include -include include/linux/autoconf.h -Iubuntu/include -I/usr/src/linux-headers-2.6.32-24-generic/ubuntu/include   -I/tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -fconserve-stack   -I/tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all -DSK_USE_CSUM -DSK_DIAG_SUPPORT -DGENESIS -DYUKON -DYUK2 -DCONFIG_SK98LIN_ZEROCOPY -DSK_EXTREME -DSK_NO_RLMT -DSK_LINUX  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(skgesirq)"  -D"KBUILD_MODNAME=KBUILD_STR(sk98lin)"  -c -o /tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/.tmp_skgesirq.o /tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/skgesirq.c
  set -e ; perl /usr/src/linux-headers-2.6.32-24-generic/scripts/recordmcount.pl "x86_64" "64" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/skgepnmi.o";
  cc -Wp,-MD,/tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/.sktwsi.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.4.3/include -I/usr/src/linux-headers-lbm- -Iinclude -Iinclude2 -I/usr/src/linux-headers-2.6.32-24-generic/include -I/usr/src/linux-headers-2.6.32-24-generic/arch/x86/include -include include/linux/autoconf.h -Iubuntu/include -I/usr/src/linux-headers-2.6.32-24-generic/ubuntu/include   -I/tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -fconserve-stack   -I/tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all -DSK_USE_CSUM -DSK_DIAG_SUPPORT -DGENESIS -DYUKON -DYUK2 -DCONFIG_SK98LIN_ZEROCOPY -DSK_EXTREME -DSK_NO_RLMT -DSK_LINUX  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(sktwsi)"  -D"KBUILD_MODNAME=KBUILD_STR(sk98lin)"  -c -o /tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/.tmp_sktwsi.o /tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/sktwsi.c
  set -e ; perl /usr/src/linux-headers-2.6.32-24-generic/scripts/recordmcount.pl "x86_64" "64" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/skgesirq.o";
  cc -Wp,-MD,/tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/.sklm80.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.4.3/include -I/usr/src/linux-headers-lbm- -Iinclude -Iinclude2 -I/usr/src/linux-headers-2.6.32-24-generic/include -I/usr/src/linux-headers-2.6.32-24-generic/arch/x86/include -include include/linux/autoconf.h -Iubuntu/include -I/usr/src/linux-headers-2.6.32-24-generic/ubuntu/include   -I/tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -fconserve-stack   -I/tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all -DSK_USE_CSUM -DSK_DIAG_SUPPORT -DGENESIS -DYUKON -DYUK2 -DCONFIG_SK98LIN_ZEROCOPY -DSK_EXTREME -DSK_NO_RLMT -DSK_LINUX  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(sklm80)"  -D"KBUILD_MODNAME=KBUILD_STR(sk98lin)"  -c -o /tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/.tmp_sklm80.o /tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/sklm80.c
  set -e ; perl /usr/src/linux-headers-2.6.32-24-generic/scripts/recordmcount.pl "x86_64" "64" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/sktwsi.o";
  cc -Wp,-MD,/tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/.skqueue.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.4.3/include -I/usr/src/linux-headers-lbm- -Iinclude -Iinclude2 -I/usr/src/linux-headers-2.6.32-24-generic/include -I/usr/src/linux-headers-2.6.32-24-generic/arch/x86/include -include include/linux/autoconf.h -Iubuntu/include -I/usr/src/linux-headers-2.6.32-24-generic/ubuntu/include   -I/tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -fconserve-stack   -I/tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all -DSK_USE_CSUM -DSK_DIAG_SUPPORT -DGENESIS -DYUKON -DYUK2 -DCONFIG_SK98LIN_ZEROCOPY -DSK_EXTREME -DSK_NO_RLMT -DSK_LINUX  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(skqueue)"  -D"KBUILD_MODNAME=KBUILD_STR(sk98lin)"  -c -o /tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/.tmp_skqueue.o /tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/skqueue.c
  set -e ; perl /usr/src/linux-headers-2.6.32-24-generic/scripts/recordmcount.pl "x86_64" "64" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/sklm80.o";
  cc -Wp,-MD,/tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/.sktimer.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.4.3/include -I/usr/src/linux-headers-lbm- -Iinclude -Iinclude2 -I/usr/src/linux-headers-2.6.32-24-generic/include -I/usr/src/linux-headers-2.6.32-24-generic/arch/x86/include -include include/linux/autoconf.h -Iubuntu/include -I/usr/src/linux-headers-2.6.32-24-generic/ubuntu/include   -I/tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -fconserve-stack   -I/tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all -DSK_USE_CSUM -DSK_DIAG_SUPPORT -DGENESIS -DYUKON -DYUK2 -DCONFIG_SK98LIN_ZEROCOPY -DSK_EXTREME -DSK_NO_RLMT -DSK_LINUX  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(sktimer)"  -D"KBUILD_MODNAME=KBUILD_STR(sk98lin)"  -c -o /tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/.tmp_sktimer.o /tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/sktimer.c
  set -e ; perl /usr/src/linux-headers-2.6.32-24-generic/scripts/recordmcount.pl "x86_64" "64" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/skqueue.o";
  cc -Wp,-MD,/tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/.skvpd.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.4.3/include -I/usr/src/linux-headers-lbm- -Iinclude -Iinclude2 -I/usr/src/linux-headers-2.6.32-24-generic/include -I/usr/src/linux-headers-2.6.32-24-generic/arch/x86/include -include include/linux/autoconf.h -Iubuntu/include -I/usr/src/linux-headers-2.6.32-24-generic/ubuntu/include   -I/tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -fconserve-stack   -I/tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all -DSK_USE_CSUM -DSK_DIAG_SUPPORT -DGENESIS -DYUKON -DYUK2 -DCONFIG_SK98LIN_ZEROCOPY -DSK_EXTREME -DSK_NO_RLMT -DSK_LINUX  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(skvpd)"  -D"KBUILD_MODNAME=KBUILD_STR(sk98lin)"  -c -o /tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/.tmp_skvpd.o /tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/skvpd.c
  set -e ; perl /usr/src/linux-headers-2.6.32-24-generic/scripts/recordmcount.pl "x86_64" "64" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/sktimer.o";
  cc -Wp,-MD,/tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/.skxmac2.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.4.3/include -I/usr/src/linux-headers-lbm- -Iinclude -Iinclude2 -I/usr/src/linux-headers-2.6.32-24-generic/include -I/usr/src/linux-headers-2.6.32-24-generic/arch/x86/include -include include/linux/autoconf.h -Iubuntu/include -I/usr/src/linux-headers-2.6.32-24-generic/ubuntu/include   -I/tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -fconserve-stack   -I/tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all -DSK_USE_CSUM -DSK_DIAG_SUPPORT -DGENESIS -DYUKON -DYUK2 -DCONFIG_SK98LIN_ZEROCOPY -DSK_EXTREME -DSK_NO_RLMT -DSK_LINUX  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(skxmac2)"  -D"KBUILD_MODNAME=KBUILD_STR(sk98lin)"  -c -o /tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/.tmp_skxmac2.o /tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/skxmac2.c
  set -e ; perl /usr/src/linux-headers-2.6.32-24-generic/scripts/recordmcount.pl "x86_64" "64" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/skvpd.o";
  cc -Wp,-MD,/tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/.skproc.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.4.3/include -I/usr/src/linux-headers-lbm- -Iinclude -Iinclude2 -I/usr/src/linux-headers-2.6.32-24-generic/include -I/usr/src/linux-headers-2.6.32-24-generic/arch/x86/include -include include/linux/autoconf.h -Iubuntu/include -I/usr/src/linux-headers-2.6.32-24-generic/ubuntu/include   -I/tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -fconserve-stack   -I/tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all -DSK_USE_CSUM -DSK_DIAG_SUPPORT -DGENESIS -DYUKON -DYUK2 -DCONFIG_SK98LIN_ZEROCOPY -DSK_EXTREME -DSK_NO_RLMT -DSK_LINUX  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(skproc)"  -D"KBUILD_MODNAME=KBUILD_STR(sk98lin)"  -c -o /tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/.tmp_skproc.o /tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/skproc.c
  set -e ; perl /usr/src/linux-headers-2.6.32-24-generic/scripts/recordmcount.pl "x86_64" "64" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/skxmac2.o";
  cc -Wp,-MD,/tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/.skcsum.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.4.3/include -I/usr/src/linux-headers-lbm- -Iinclude -Iinclude2 -I/usr/src/linux-headers-2.6.32-24-generic/include -I/usr/src/linux-headers-2.6.32-24-generic/arch/x86/include -include include/linux/autoconf.h -Iubuntu/include -I/usr/src/linux-headers-2.6.32-24-generic/ubuntu/include   -I/tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -fconserve-stack   -I/tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all -DSK_USE_CSUM -DSK_DIAG_SUPPORT -DGENESIS -DYUKON -DYUK2 -DCONFIG_SK98LIN_ZEROCOPY -DSK_EXTREME -DSK_NO_RLMT -DSK_LINUX  -DMODULE -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(skcsum)"  -D"KBUILD_MODNAME=KBUILD_STR(sk98lin)"  -c -o /tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/.tmp_skcsum.o /tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/skcsum.c
  set -e ; perl /usr/src/linux-headers-2.6.32-24-generic/scripts/recordmcount.pl "x86_64" "64" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/skproc.o";
(cat /dev/null;   echo kernel//tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/sk98lin.ko;) > /tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/modules.order
  set -e ; perl /usr/src/linux-headers-2.6.32-24-generic/scripts/recordmcount.pl "x86_64" "64" "objdump" "objcopy" "cc" "ld" "nm" "" "" "1" "/tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/skcsum.o";
  ld -m elf_x86_64   -r -o /tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/sk98lin.o /tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/skge.o /tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/sky2.o /tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/skethtool.o /tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/sky2le.o /tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/skdim.o /tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/skaddr.o /tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/skgehwt.o /tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/skgeinit.o /tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/skgepnmi.o /tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/skgesirq.o /tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/sktwsi.o /tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/sklm80.o /tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/skqueue.o /tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/sktimer.o /tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/skvpd.o /tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/skxmac2.o /tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/skproc.o /tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/skcsum.o 
make -f /usr/src/linux-headers-2.6.32-24-generic/scripts/Makefile.modpost
  scripts/mod/modpost -m -a -i /usr/src/linux-headers-2.6.32-24-generic/Module.symvers -I /tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/Module.symvers  -o /tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/Module.symvers -S -w  -s
  cc -Wp,-MD,/tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/.sk98lin.mod.o.d  -nostdinc -isystem /usr/lib/gcc/x86_64-linux-gnu/4.4.3/include -I/usr/src/linux-headers-lbm- -Iinclude -Iinclude2 -I/usr/src/linux-headers-2.6.32-24-generic/include -I/usr/src/linux-headers-2.6.32-24-generic/arch/x86/include -include include/linux/autoconf.h -Iubuntu/include -I/usr/src/linux-headers-2.6.32-24-generic/ubuntu/include   -I/tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all -D__KERNEL__ -Wall -Wundef -Wstrict-prototypes -Wno-trigraphs -fno-strict-aliasing -fno-common -Werror-implicit-function-declaration -Wno-format-security -fno-delete-null-pointer-checks -O2 -m64 -mtune=generic -mno-red-zone -mcmodel=kernel -funit-at-a-time -maccumulate-outgoing-args -fstack-protector -DCONFIG_AS_CFI=1 -DCONFIG_AS_CFI_SIGNAL_FRAME=1 -pipe -Wno-sign-compare -fno-asynchronous-unwind-tables -mno-sse -mno-mmx -mno-sse2 -mno-3dnow -Wframe-larger-than=1024 -fno-omit-frame-pointer -fno-optimize-sibling-calls -pg -Wdeclaration-after-statement -Wno-pointer-sign -fno-strict-overflow -fno-dwarf2-cfi-asm -fconserve-stack   -I/tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all -DSK_USE_CSUM -DSK_DIAG_SUPPORT -DGENESIS -DYUKON -DYUK2 -DCONFIG_SK98LIN_ZEROCOPY -DSK_EXTREME -DSK_NO_RLMT -DSK_LINUX  -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(sk98lin.mod)"  -D"KBUILD_MODNAME=KBUILD_STR(sk98lin)"  -DMODULE -c -o /tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/sk98lin.mod.o /tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/sk98lin.mod.c
  ld -r -m elf_x86_64 -T /usr/src/linux-headers-2.6.32-24-generic/scripts/module-common.lds --build-id -o /tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/sk98lin.ko /tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/sk98lin.o /tmp/Sk98IoUPmqjKAahqiKaiZpMcV/all/sk98lin.mod.o
make: Leaving directory `/usr/src/linux-headers-2.6.32-24-generic'
Check the driver
====================================

```
1C) And this is the output of $ sudo dmesg | grep sk:
```

[    0.000000]   0 base 0000000000 mask FF80000000 write-back
[    0.000000]   1 base 0080000000 mask FFE0000000 write-back
[    0.000000]   2 base 00A0000000 mask FFF0000000 write-back
[    0.000000]   3 base 00B0000000 mask FFF8000000 write-back
[    0.000000]   4 base 00B8000000 mask FFFC000000 write-back
[    0.000000]   5 base 00BC000000 mask FFFE000000 write-back
[    0.000000] NR_CPUS:64 nr_cpumask_bits:64 nr_cpu_ids:2 nr_node_ids:1
[    0.030006] Calibrating delay loop (skipped), value calculated using timer frequency.. 4000.10 BogoMIPS (lpj=20000540)
[    0.034595] ... value mask:             0000ffffffffffff
[    0.034602] ... event mask:             000000000000000f
[    0.460288] VFS: Disk quotas dquot_6.5.2
[    0.470521] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.764045] PM: Resume from disk failed.
[    0.764157] registered taskstats version 1
[    2.079698] sd 2:0:0:0: [sda] Attached SCSI disk
[    6.218442] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[   15.222945] sk98lin 0000:02:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   15.222960] sk98lin: Network Device Driver v10.85.9.3
[   15.223013] sk98lin 0000:02:00.0: setting latency timer to 64
[   15.269833] sk98lin 0000:02:00.0: irq 28 for MSI/MSI-X

```
I'll try Knoppix later and will let you know.

It's actually fun to learn by doing mistakes, so I'm trying not to be disappointed. Just hoping this learning will yield happy ending.
And it's really amazing that guys here help so thoroughly. I appreciate it.

---

### Post by mathia on 2010-09-22
Hi,
I checked the log files und could not see any error or unresolved symbols during the driver compilation. So I wait for the knoppix results.

---

### Post by MajinSaha on 2010-09-23
Ok, but how do I save the file where I put the output to in Knoppix ?
When I use "dmesg | grep > output", I want to use that file in the future. But copying to the filesystem or a flashdrive fails, since I just don't know how to get access to them.

Anyway, when I executed that command, I didn't find anything that was resembling sky2 or sk98lin in the output which was about 10 lines and started with 
```
Kernel command line: ramdisk_size=100000 init=/etc/init lang=us apm=power-off
vga=791 initrd=minirt.gz nomce loglevel=0 quiet BOOT_IMAGE=knoppix BOOT_IMAGE=linux
...
```
The result of ifconfig:
```
lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:14 errors:0 dropped:0 overruns:0 frame:0
TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
collisions: 0 txqueuelen:0
RX bytes:700(700.0 b) TX bytes:700 (700.0 b)
```

dhclient gives me "command not found". I don't have a router. The whole apartment building is wired somehow and my cable goes up to the attic where the installation is (don't know what it looks like).

By the way, when I type "lspci" in Knoppix, it gives "Marvell unknown device 4355 (rev 12)". I believe this has to do with a bug that was in earlier releases of Ubuntu (08.04). This Knoppix edition is dated 2007.

Anyway, that's that. Since you didn't find any mistakes in the driver installation log, I'm starting to think this might be providers' thing. Maybe it's not properly configured to work under Ubuntu. I asked them how to connect through Ubuntu, and they gave me the instructions on how to download and install a VPN connection(that requires login and password). But the local connection must be estabished without it (otherwise it wouldn't be possible to download "insall.sh" from their website), so I'm still confused.:confused: All I'm getting are constant efforts to connect in the upper right corner of the screen, but with no success.

---

### Post by mathia on 2010-09-23
Hi,
in your command you forgot to use "grep sk". Please do as follows and post the results.

2) If you boot from knoppix live CD ( use always latest version! ). 
- Use an USB stick for log files and it will be automatically mounted on knoppix as e.g.: /media/usb.
- Please login as root to the console and run the following commands:

2A) Please post the output of following command to me:
      $ dmesg | grep sk > /media/usb/output.log

2B) Please run "ifconfig" command and post the output.
$ ifconfig -a >> /media/usb/output.log

2C) If you have a router with dhcp activated connect the notebook to it.
      Please try "dhclient eth0" and see if you can get an IP address from your router.

2D) Can you ping the router?
       Let me know the results.

---

### Post by MajinSaha on 2010-09-24
In fact, I have not forgotten to type "grep sk" in the terminal. I only forgot to type that in the post. As I said, command
$ sudo dmseg | grep sk
gives what I showed in the last post. No sign of sky2 or sk98lin.
So far I did everything you mentioned, it was written in the previous post.

If you insist, I can try to get complete output using a flash drive for A), but it says "permission denied", or "read-only file system", whenever I'm trying to use > in there, even though I'm attaching sudo. How do I deal with permissions ? How do I login as a root ?

For B) check the previous post. I've typed the whole output myself.

dhclient: command not found. And I do not have a router.

---

### Post by mathia on 2010-09-26
Hi [B]MajinSaha,

[/B]1) >How do I deal with permissions ? How do I login as a root ?

Just open a console and type:
$ sudo su
and type your root password or press enter if you do not have any root password.

2) >dhclient: command not found. And I do not have a router.

So please explain how do you connect to internet?

3) As I told you before I have downloaded the manual of your notebook.
From "satellite_M305D-S4829.pdf":
Operating System C1 2
&#8226;
Genuine Windows Vista® Home Premium (SP1,64-bit version)
Processor and Chipset3
&#8226;
AMD Turion&#8482; X2 Dual-Core Mobile Processor RM-70
o
2.0 GHz, 1MB L2 Cache, HyperTransport&#8482; 3: up to 3.6(GT/sec)
&#8226;
AMD M780V chipset

Could you please confirm that you have the same system?
Normaly the 64bit extended system are compatible to run 32bit application.
I can not understand why the yukon diagnostic tool could not run on your system?

     4 ) I have installed ubuntu 10.04, 64-bit edition  on a ACER 64 bit system and tried to reproduce your issue. But I saw that everything worked perfectly with 8040T device both with sky2 v1.25 and with sk98lin v10.85.9.3 driver.

What I am missing is the link up message in dmesg or /var/log/messages in your log files:

These are the output from my log files:

[    1.048331] sky2 driver version 1.25
[    1.108619] sky2 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.108636] sky2 0000:02:00.0: setting latency timer to 64
[    1.108672] sky2 0000:02:00.0: Yukon-2 FE+ chip revision 0
[    1.108769] sky2 0000:02:00.0: irq 27 for MSI/MSI-X
[  170.168532] sky2 eth0: enabling interface
[  170.169262] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  172.925182] [COLOR=Red]sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both[/COLOR]
[  172.925819] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  183.160020] eth0: no IPv6 routers present
[  399.844677] sky2 eth0: disabling interface
[  400.100076] sky2 0000:02:00.0: PCI INT A disabled

[  995.186724] sk98lin 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[  995.186746] sk98lin: Network Device Driver v10.85.9.3
[  995.186749] (C)Copyright 1999-2010 Marvell(R).
[  995.186801] sk98lin 0000:02:00.0: setting latency timer to 64
[  995.188885] eth0: Generic Marvell Yukon chipset Ethernet device
[ 1090.005833] sk98lin 0000:02:00.0: irq 27 for MSI/MSI-X
[ 1090.006667] ADDRCONF(NETDEV_UP): eth0: link is not ready
[COLOR=Red][ 1092.720156] eth0: network connection up using port A
[ 1092.720163]     interrupt src:   MSI
[ 1092.720166]     speed:           100
[ 1092.720169]     autonegotiation: yes
[ 1092.720172]     duplex mode:     full
[ 1092.720175]     flowctrl:        symmetric
[ 1092.720178]     tcp offload:     enabled
[ 1092.720181]     scatter-gather:  enabled
[ 1092.720184]     tx-checksum:     enabled
[ 1092.720186]     rx-checksum:     enabled
[ 1092.720189]     rx-polling:      enabled[/COLOR]
[ 1092.720809] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 1103.530020] eth0: no IPv6 routers present

Here is the summerized output of my lspci:
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon HD 3200 Graphics
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040T PCI-E Fast Ethernet Controller (rev 13)
03:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller
04:05.0 Ethernet controller: Intel Corporation 82541GI Gigabit Ethernet Controller
04:06.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)

5) I saw you use the  kernel version 2.6.32-24-generic ( from your install.log).
Did you update the kernel on your ubuntu system?

This is the output of my  uname -a:
Linux ubuntu64 2.6.32-21-server #32-Ubuntu SMP Fri Apr 16 09:17:34 UTC 2010 x86_64 GNU/Linux

6) Summary:
1 - We saw the MAC address of your yukon device is "eth0 Link encap:Ethernet  HWaddr ff:ff:ff:ff:ff:ff"
and we saw no link up event with 8040T device.
This is not normal and it seems that your yukon network device has no valid configuration data anymore and it should be
reprogrammed by Toshiba support personal again.

2 - You can install "ubuntu-10.04.1-desktop-amd64.iso" or try to install other linux distributions such as OpenSuSE 11.3 x86-64 or Fedora 13 x86-64 and give it a try with those distributions. If you see the same symptoms so you can be sure that you have definitely a network hardware problem.

I hope this could help.

Regards,
Mathia

---

### Post by mathia on 2010-09-30
Hi MajinSaha,

are you still there?

---

### Post by MajinSaha on 2010-10-03
Thanks for doing all that stuff for me.
2) The explanation was about 2-3 of my posts ago(the cable goes all the way from the apartment to the attick)
3) Yes, I have that configuration.
5) I haven't uploaded Kernel or anything since the day I installed Ubuntu, and that was about 3 weeks ago. I don't have an internet.

Ok, I'll try other Linux-type OS and see.

---

