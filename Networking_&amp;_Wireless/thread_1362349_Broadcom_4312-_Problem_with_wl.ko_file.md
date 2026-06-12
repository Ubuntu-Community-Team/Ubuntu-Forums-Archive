---
title: "Broadcom 4312- Problem with wl.ko file"
date: 2009-12-23
forum: Networking &amp; Wireless
---

### Post by heeb2008 on 2009-12-23
I have been trying for weeks to get my wireless card to work with ubuntu. Today, I reinstalled Ubuntu and tried to use drivers that Broadcom had on their website ([http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)). 

The first thing I did was changed the name of the tar file from "hybrid-portsrc-x86_32-v5.10.91.9.3.tar.gz" to "hybrid-portsrc.tar.gz". I uploaded this file from a jump drive to Desktop. I then started to do the steps in the "Readme.txt"

```


michael@ubuntu:~/hybrid_wl$ tar xzf /home/michael/Desktop/hybrid-portsrc.tar.gz
michael@ubuntu:~/hybrid_wl$ make
KBUILD_NOPEDANTIC=1 make -C /lib/modules/`uname -r`/build M=`pwd`
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
  LD      /home/michael/hybrid_wl/built-in.o
  CC [M]  /home/michael/hybrid_wl/src/wl/sys/wl_linux.o
  CC [M]  /home/michael/hybrid_wl/src/wl/sys/wl_iw.o
  CC [M]  /home/michael/hybrid_wl/src/shared/linux_osl.o
  LD [M]  /home/michael/hybrid_wl/wl.o
ld: Relocatable linking with relocations from format elf32-i386 (/home/michael/hybrid_wl/lib/wlc_hybrid.o_shipped) to format elf64-x86-64 (/home/michael/hybrid_wl/wl.o) is not supported
make[2]: *** [/home/michael/hybrid_wl/wl.o] Error 1
make[1]: *** [_module_/home/michael/hybrid_wl] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
make: *** [all] Error 2
michael@ubuntu:~/hybrid_wl$ lsmod |grep "b43\|ssb\|wl"
b43                   136552  0 
mac80211              210104  1 b43
cfg80211              109144  2 b43,mac80211
led_class               5256  2 sdhci,b43
ssb                    40944  1 b43
michael@ubuntu:~/hybrid_wl$ rnmod b43
No command 'rnmod' found, did you mean:
 Command 'rmmod' from package 'module-init-tools' (main)
rnmod: command not found
michael@ubuntu:~/hybrid_wl$ rmmod b43
ERROR: Removing 'b43': Operation not permitted
michael@ubuntu:~/hybrid_wl$ sudo rmmodb43
[sudo] password for michael: 
Sorry, try again.
[sudo] password for michael: 
sudo: rmmodb43: command not found
michael@ubuntu:~/hybrid_wl$ sudo rmmod b43
michael@ubuntu:~/hybrid_wl$ 
michael@ubuntu:~/hybrid_wl$ sudo rmmod ssb

michael@ubuntu:~/hybrid_wl$ echo "blacklist ssb" >> /etc/modprobe.d/blacklist.conf
bash: /etc/modprobe.d/blacklist.conf: Permission denied
michael@ubuntu:~/hybrid_wl$ sudo echo "blacklist ssb" >> /etc/modprobe.d/blacklist.conf
bash: /etc/modprobe.d/blacklist.conf: Permission denied

```I then went into nautilus and blacklisted these drivers manually.

From there I got these error messages from nautilus.

```
(nautilus:2319): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed

** (nautilus:2319): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:2319): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:2319): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Initializing nautilus-gdu extension
Sense key: 0x70 0x00 0x00 0x00 0x00 0x00 0x00 0x0a 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 0x00 
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


--- Hash table keys for warning below:
--> l1792
--> inode/directory
--> root

(nautilus:2319): Eel-WARNING **: "unique eel_ref_str" hash table still has 3 elements at quit time (keys above)

(nautilus:2319): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 4 elements at quit time
Shutting down nautilus-gdu extension


```Then for the last steps, this is what I did

```

michael@ubuntu:~/hybrid_wl$ modprobe lib80211
FATAL: Error inserting lib80211 (/lib/modules/2.6.31-14-generic/kernel/net/wireless/lib80211.ko): Operation not permitted
michael@ubuntu:~/hybrid_wl$ sudo modprobe lib80211
michael@ubuntu:~/hybrid_wl$ sudo insmod wl.ko
insmod: can't read 'wl.ko': No such file or directory
michael@ubuntu:~/hybrid_wl$ insmod wl.ko
insmod: can't read 'wl.ko': No such file or directory

```
This is my lspci:

```

mjhebron@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G84 [GeForce 8600M GT] (rev a1)
03:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
0b:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
mjhebron@ubuntu:~$ 


```


I think the problem is with the "make" command. The only internet connection I have is a wireless connection (which is why I need to get this driver to work).

---

### Post by heeb2008 on 2009-12-23
Does anyone know what to do? Would the 8.04LTS version work w/o a new driver?

---

