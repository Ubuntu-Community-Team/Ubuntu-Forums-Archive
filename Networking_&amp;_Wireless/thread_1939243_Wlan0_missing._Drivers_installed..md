---
title: "Wlan0 missing. Drivers installed."
date: 2012-03-11
forum: Networking &amp; Wireless
---

### Post by Sirkyuubi on 2012-03-11
Hello Everyone! I just finished installing Ubuntu 11.10 64bit. I have a  Dell Latitude D830, Core 2 duo, with Broadcom 4311 Dualband(Dell 1490) wireless card,  and Nvidia Quadro NVS 135. I love this laptop. Anyways, to my problem...  The wireless card drivers are installed, but when I type in iwconfig  wlan0 isn't there. Only lo, and eth0 show up. I have some output for you  all to look through, and I found a broadcom readme that I think could help.

P.S. The wireless card works in Win7 Ultimate. I have a dual boot setup.

Broadcom Wireless Linux Readme

```

Broadcom Linux hybrid wireless driver
Version 5.100.82.1XX

DISCLAIMER
----------
This is an Official Release of Broadcom's hybrid Linux driver for use with 
Broadcom based hardware.

WHERE TO GET THE RELEASE
------------------------
http://www.broadcom.com/support/802.11/linux_sta.php

IMPORTANT NOTE AND DISCUSSION OF HYBRID DRIVER
----------------------------------------------
There are separate tarballs for 32 bit and 64 bit x86 CPU architectures.
Make sure you use the appropriate tarball for your machine.

Other than 32 vs 64 bit, the hybrid binary is agnostic to the specific
versions (2.6.X) and distributions (Fedora, Ubuntu, SuSE, etc).  It performs
all interactions with the OS through OS specific files (wl_linux.c, wl_iw.c,
osl_linux.c) that are shipped in source form. You compile this source on
your system and link with a precompiled binary file (wlc_hybrid.o_shipped)
which contains the rest of the driver.

PRECOMPILED DRIVER
-------------------
Some distros (Ubuntu and Fedora at the least) already have a version of
this driver in their repositories precompiled, tested and ready to go.
You just use the package manager to install the proper package.  If
its available for your distro, this is usually an easier solution. See
the end of this document for further discussion.

ABOUT THIS RELEASE
-------------------
This is a rollup release.  It includes and deprecates all previous releases
and patches.  At the time of release there are no existing patches for this
release from Broadcom.

SUPPORTED DEVICES
-----------------
The cards with the following PCI Device IDs are supported with this driver.
Both Broadcom and and Dell product names are described.   Cards not listed
here may also work.

       BRCM            PCI          PCI          Dell
      Product Name      Vendor ID    Device ID    Product ID
          -------------     ----------    ---------       -----------
          4311 2.4 Ghz        0x14e4    0x4311      Dell 1390
          4311 Dualband        0x14e4    0x4312      Dell 1490
          4311 5 Ghz        0x14e4        0x4313      
          4312 2.4 Ghz        0x14e4    0x4315      Dell 1395
          4313 2.4 Ghz        0x14e4    0x4727         Dell 1501
          4321 Dualband        0x14e4    0x4328      Dell 1505
          4321 Dualband        0x14e4    0x4328      Dell 1500
          4321 2.4 Ghz        0x14e4    0x4329      
          4321 5 Ghz        0x14e4    0x432a      
          4322     Dualband    0x14e4    0x432b      Dell 1510
          4322 2.4 Ghz      0x14e4     0x432c      
          4322 5 Ghz        0x14e4     0x432d      
          43224 Dualband    0x14e4    0x4353      Dell 1520
          43225 2.4 Ghz     0x14e4    0x4357      
          43227 2.4 Ghz     0x14e4    0x4358
          43228 Dualband    0x14e4    0x4359      Dell 1530

To find the Device ID's of Broadcom cards on your machines do:
# lspci -n | grep 14e4

NOTABLE CHANGES
---------------
    Added Cfg80211 support (described below)
    Added Monitor mode     (described below)

REQUIREMENTS
------------
Building this driver requires that your machine have the proper tools,
packages, header files and libraries to build a standard a kernel module.  
This usually is done by installing the kernel developer or kernel source 
package and varies from distro to distro. Consult the documentation for
your specific OS.

If you cannot successfully build a module that comes with your distro's 
kernel developer or kernel source package, you will not be able to build 
this module either.

If you try to build this module but get an error message that looks like 
this:

make: *** /lib/modules/"release"/build: No such file or directory. Stop.

Then you do not have the proper packages installed, since installing the 
proper packages will create /lib/modules/"release"/build on your system.

On Fedora install 'kernel-devel' (Development Package for building kernel
modules to match the kernel) from the Package Manager (System->
Administration-> Add/Remove Software).

On Ubuntu, you will need headers and tools.  Try these commands:
# apt-get install build-essential linux-headers-generic
# apt-get build-dep linux

To check to see if you have this directory do this:

# ls /lib/modules/`uname -r`/build

BUILD INSTRUCTIONS
------------------
1. Setup the directory by untarring the proper tarball:

For 32 bit:     hybrid-portsrc.tar.gz
For 64 bit:     hybrid-portsrc-x86_64.tar.gz

Example:
# mkdir hybrid_wl
# cd hybrid_wl
# tar xzf <path>/hybrid-portsrc.tar or <path>/hybrid-portsrc-x86_64.tar.gz

2. Build the driver as a Linux loadable kernel module (LKM):

# make clean   (optional)
# make

When the build completes, it will produce a wl.ko file in the top level
directory.

If your driver does not build, check to make sure you have installed the
kernel package described in the requirements above.

This driver now supports the new linux cfg80211 wireless configuration API in
addition to the older Wireless Extensions (Wext).  The makefile will
automaticly build the right version for your system but it can be
overridden if needed:

# make API=WEXT
 or
# make API=CFG80211

INSTALL INSTRUCTIONS
--------------------

Upgrading from a previous version:
---------------------------------

If you were already running a previous version of wl, you'll want to provide
a clean transition from the older driver. (The path to previous driver is
usually /lib/modules/<kernel-version>/kernel/net/wireless)

# rmmod wl 
# mv <path-to-prev-driver>/wl.ko <path-to-prev-driver>/wl.ko.orig
# cp wl.ko <path-to-prev-driver>/wl.ko
# depmod
# modprobe wl

The new wl driver should now be operational and your all done.

Fresh installation:
------------------
1: Remove any other drivers for the Broadcom wireless device.

There are several other drivers (besides this one) that can drive 
Broadcom 802.11 chips such as b43, bcma and ssb. They will conflict with 
this driver and need to be uninstalled before this driver can be installed.
Any previous revisions of the wl driver also need to be removed.

Note: On some systems such as Ubuntu 9.10, the ssb module may load during
boot even though it is blacklisted (see note under Common Issues on how to
resolve this. Nevertheless, ssb still must be removed
(by hand or script) before wl is loaded. The wl driver will not function 
properly if ssb the module is loaded.

# lsmod  | grep "b43\|ssb\|bcma\|wl"

If any of these are installed, remove them:
# rmmod b43
# rmmod ssb
# rmmod bcma
# rmmod wl

To blacklist these drivers and prevent them from loading in the future:
# echo "blacklist ssb" >> /etc/modprobe.d/blacklist.conf
# echo "blacklist bcma" >> /etc/modprobe.d/blacklist.conf
# echo "blacklist b43" >> /etc/modprobe.d/blacklist.conf

2: Insmod the driver.

Otherwise, if you have not previously installed a wl driver, you'll need
to add a security module before using the wl module.  Most newer systems 
use lib80211 while others use ieee80211_crypt_tkip. See which one works for 
your system.

# modprobe lib80211 
  or 
# modprobe ieee80211_crypt_tkip

If your using the cfg80211 version of the driver, then cfg80211 needs to be
loaded:

# modprobe cfg80211

Then:
# insmod wl.ko

wl.ko is now operational.  It may take several seconds for the Network 
Manager to notice a new network driver has been installed and show the
surrounding wireless networks.

If there was an error, see Common issues below.

Common issues:
----------------
* After the insmod you may see this message:
  WARNING: modpost: missing MODULE_LICENSE()
  It is expected, not harmful and can be ignored.

* If you see this message:

  "insmod: error inserting 'wl.ko': -1 Unknown symbol in module"

  Usually this means that one of the required modules (as mentioned above) is
  not loaded. Try this:
  # modprobe lib80211 or ieee80211_crypt_tkip (depending on your os)
  # modprobe cfg80211
    
  Now re-try to insmod the wl driver:
  # insmod wl.ko
  
* If the wl driver loads but doesn't seem to do anything:
  the ssb module may be the cause.  Sometimes blacklisting ssb may not
  be enough to prevent it from loading and it loads anyway. (This is mostly
  seen on Ubuntu/Debian systems).

  Check to see if ssb, bcma, wl or b43 is loaded:
  # lsmod | grep "ssb\|wl\|b43\|bcma"

  If any of these are installed, remove them:
  # rmmod ssb
  # rmmod bcma
  # rmmod wl
  # insmod wl

  Back up the current boot ramfs and generate a new one:
  # cp /boot/initrd.img-`uname -r` somewheresafe
  # update-initramfs -u
  # reboot

3: Setup to always load at boot time.

The procedure to make a module load at boot time varies from distro to
distro.  Consult the docs for your specific distro to see how.  The 
following seems to work for my setup on Fedora and Ubuntu.  Check your 
docs to see the procedure for your distro.

Follow these steps to have the driver load as part of the boot process:

# load driver as described above
# cp wl.ko /lib/modules/`uname -r`/kernel/drivers/net/wireless 
# depmod -a

# echo modeprobe wl >> /etc/rc.local  (Fedora/SUSE)

Ubuntu ships a version of wl.ko, so those need to be disabled.  On my 
system the were several versions, so I searched and renamed the .ko's
like this:

# sh: for i in `find /lib /var -name wl\.ko`; do mv $i ${i}.orig; done


TX POWER EXPLAINED
------------------
'iwconfig eth1 txpower' & 'iwlist eth1 txpower' set and get the drivers 
user-requested transmit power level. This can go up to 32 dbm and allows
the user to lower the tx power to levels below the regulatory limit.
Internally, the actual tx power is always kept within regulatory limits
no matter what the user request is set to.


ISSUES FIXED AND WHAT'S NEW IN THIS RELEASE
-------------------------------------------
+ Added cfg80211 API support. The choice of API is done at compile time. If
kernel version >= 2.6.32, cfg80211 is used, otherwise wireless extension 
is used. (End users should notice little difference.)
+ Supports Linux kernel 2.6.38
+ Fix for problem with rebooting while wireless disabled via airline switch.
+ Fixed a kernel panic observed on some 64-bit systems

HOW TO USE MONITOR MODE
-----------------------
To enable monitor mode:
$ echo 1 > /proc/brcm_monitor0

Enabling monitor mode will create a 'prism0' network interface. Wireshark and
other netwokk tools can use this new prism0 interface.

To disable monitor mode:
$ echo 0 > /proc/brcm_monitor0


ISSUES FIXED AND WHAT'S NEW IN RECENT RELEASES
-------------------------------------------
+ Supports monitor mode
+ Supports cfg80211
+ Supports hidden networks
+ Supports rfkill


KNOWN ISSUES AND LIMITATIONS
----------------------------
#72238 - 20% lower throughput on channels 149, 153, 157, and 161
#72324 - Ubuntu 8.04: cannot ping when Linux STA is IBSS creator with WEP
enabled
#72216 - Ubuntu 8.04: standby/resume with WPA2 and wpa_supplicant causes
a continuous assoc/disassoc loop (issue with wpa_supplicant, restarting
wpa_supplicant fixes the issue)
#76739 Ubuntu9.04: unable to connect to hidden network after stdby/resume
#76793 Ubuntu9.04: STA fails to create IBSS network in 5 Ghz band


KNOWN ISSUES AND LIMITATIONS IN EXTERNAL COMPONENTS
----------------------------

wpa_supplicant 0.6.3 + nl80211 + WEP - (Note: This would only affect you if 
you are using wpa_supplicant directly from the command line and specify 
nl80211 interface, e.g. "wpa_supplicant -Dnl80211 -ieth1 ..". If you are using
network manager GUI to connect it should work file.)
wpa_supplicant 0.6.3 might have a bug that affect WEP connections created 
through nl80211. Upgrade to wpa_supplicant to 0.7.3 would solve this problem.

Ubuntu 10.10 kernel + nl80211 + WPA/WPA2 - (Note: This would only affect you if 
you are using wpa_supplicant directly from the command line and specify 
nl80211 interface, e.g. "wpa_supplicant -Dnl80211 -ieth1 ..". If you are using
network manager GUI to connect it should work file.)
Some kernel versions of Ubuntu such as 2.6.35-22 (released with Ubuntu 
10.10) may have problems that affect WPA/WPA2 connections created through 
nl80211. Upgrade to 2.6.35-25 or later should solve this problem.


HOW TO INSTALL A PRE-COMPILED DRIVER
-----------------------------------
Some of the major linux distros already supply a version of this driver, so
you don't have to compile your own.  Most of the distros keep this driver
along with other proprietary or non-GPL drivers in a separate repository.

For further information see the documentation for your specific distro.

Fedora:
------
su -c 'rpm -Uvh
http://download1.rpmfusion.org/free/fedora/rpmfusion-free-release-stable.noarch.rpm
http://download1.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-stable.noarch.rpm'

su -
yum update
yum install kmod-wl

Ubuntu:
------
Go to System->Administration->Hardware Drivers
Choose the Broadcom STA wireless driver
Activate

Sometimes the driver does not show up in the Hardware Drivers choices.  In
this case, try reintalling the driver from the GUI or shell like this:

From the GUI:
Package Manager (System>Administration>Synaptic Package Manager). Click the 
Reload button in the upper left corner of Synaptic to refresh your index then 
search for and reinstall the package named bcmwl-kernel-source.

From the shell:
sudo apt-get update
sudo apt-get --reinstall install bcmwl-kernel-source

In either GUI or text case, after reinstalling, reboot your machine.

Now go back to System->Administration->Hardware Drivers
and you should see the driver enabled and working.
```iwconfig

```

lo        no wireless extensions.

eth0      no wireless extensions.
```ifconfig -a

```

eth0      Link encap:Ethernet  HWaddr 00:1d:09:af:44:c9  
          inet addr:192.168.2.6  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:9ff:feaf:44c9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:31244 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22161 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:39061599 (39.0 MB)  TX bytes:3088264 (3.0 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```lsmod

```

Module                  Size  Used by
parport_pc             36962  0 
ppdev                  17113  0 
nvidia              11713772  48 
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
dell_wmi               12681  0 
sparse_keymap          13890  1 dell_wmi
joydev                 17693  0 
snd_usb_audio         118064  2 
snd_usbmidi_lib        25371  1 snd_usb_audio
snd_hda_codec_idt      70553  1 
snd_hda_intel          33390  2 
snd_hda_codec         104802  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13668  2 snd_usb_audio,snd_hda_codec
dell_laptop            13831  0 
dcdbas                 14490  1 dell_laptop
snd_pcm                96755  3 snd_usb_audio,snd_hda_intel,snd_hda_codec
pcmcia                 49378  0 
snd_seq_midi           13324  0 
snd_rawmidi            30547  2 snd_usbmidi_lib,snd_seq_midi
psmouse                73882  0 
serio_raw              13166  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
yenta_socket           28084  0 
pcmcia_rsrc            18430  1 yenta_socket
pcmcia_core            22614  3 pcmcia,yenta_socket,pcmcia_rsrc
snd_timer              29991  2 snd_pcm,snd_seq
wl                   2568210  0 
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
lib80211               14991  1 wl
snd                    68266  19 snd_usb_audio,snd_usbmidi_lib,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
wmi                    19256  1 dell_wmi
video                  19412  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
binfmt_misc            17540  1 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
firewire_ohci          40722  0 
firewire_core          63626  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
tg3                   147729  0 
usbhid                 47198  0 
hid                    95463  1 usbhid
```

dmesg

```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.0.0-16-generic (buildd@roseapple) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) #29-Ubuntu SMP Tue Feb 14 12:48:51 UTC 2012 (Ubuntu 3.0.0-16.29-generic 3.0.20)
[    0.000000] Command line: BOOT_IMAGE=/vmlinuz-3.0.0-16-generic root=UUID=eac6d6b5-7d89-4bf2-8e93-f1a91eb863a0 ro quiet splash vt.handoff=7
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[    0.000000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 00000000dfe5a800 (usable)
[    0.000000]  BIOS-e820: 00000000dfe5a800 - 00000000e0000000 (reserved)
[    0.000000]  BIOS-e820: 00000000f8000000 - 00000000fc000000 (reserved)
[    0.000000]  BIOS-e820: 00000000fec00000 - 00000000fec10000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed18000 - 00000000fed1c000 (reserved)
[    0.000000]  BIOS-e820: 00000000fed20000 - 00000000fed90000 (reserved)
[    0.000000]  BIOS-e820: 00000000feda0000 - 00000000feda6000 (reserved)
[    0.000000]  BIOS-e820: 00000000fee00000 - 00000000fee10000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffe00000 - 0000000100000000 (reserved)
[    0.000000]  BIOS-e820: 0000000100002000 - 0000000120000000 (usable)
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] DMI 2.4 present.
[    0.000000] DMI: Dell Inc. Latitude D830                   /0HN338, BIOS A14 12/11/2008
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] No AGP bridge found
[    0.000000] last_pfn = 0x120000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CFFFF write-protect
[    0.000000]   D0000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 080000000 mask FC0000000 write-back
[    0.000000]   2 base 0C0000000 mask FE0000000 write-back
[    0.000000]   3 base 100000000 mask FE0000000 write-back
[    0.000000]   4 base 0DFF00000 mask FFFF00000 uncachable
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] original variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 2GB, type WB
[    0.000000] reg 1, base: 2GB, range: 1GB, type WB
[    0.000000] reg 2, base: 3GB, range: 512MB, type WB
[    0.000000] reg 3, base: 4GB, range: 512MB, type WB
[    0.000000] reg 4, base: 3583MB, range: 1MB, type UC
[    0.000000] total RAM covered: 4095M
[    0.000000] Found optimal setting for mtrr clean up
[    0.000000]  gran_size: 64K     chunk_size: 1G     num_reg: 4      lose cover RAM: 0G
[    0.000000] New variable MTRRs
[    0.000000] reg 0, base: 0GB, range: 4GB, type WB
[    0.000000] reg 1, base: 3583MB, range: 1MB, type UC
[    0.000000] reg 2, base: 3584MB, range: 512MB, type UC
[    0.000000] reg 3, base: 4GB, range: 512MB, type WB
[    0.000000] e820 update range: 00000000dff00000 - 0000000100000000 (usable) ==> (reserved)
[    0.000000] last_pfn = 0xdfe5a max_arch_pfn = 0x400000000
[    0.000000] initial memory mapped : 0 - 20000000
[    0.000000] Base memory trampoline at [ffff88000009a000] 9a000 size 20480
[    0.000000] init_memory_mapping: 0000000000000000-00000000dfe5a000
[    0.000000]  0000000000 - 00dfe00000 page 2M
[    0.000000]  00dfe00000 - 00dfe5a000 page 4k
[    0.000000] kernel direct mapping tables up to dfe5a000 @ 1fffa000-20000000
[    0.000000] init_memory_mapping: 0000000100000000-0000000120000000
[    0.000000]  0100000000 - 0120000000 page 2M
[    0.000000] kernel direct mapping tables up to 120000000 @ dfe54000-dfe5a000
[    0.000000] RAMDISK: 365be000 - 372d7000
[    0.000000] ACPI: RSDP 00000000000fbb10 00024 (v02 DELL  )
[    0.000000] ACPI: XSDT 00000000dfe5d200 00064 (v01 DELL    M08     27D80C0B ASL  00000061)
[    0.000000] ACPI: FACP 00000000dfe5d09c 000F4 (v04 DELL    M08     27D80C0B ASL  00000061)
[    0.000000] ACPI: DSDT 00000000dfe5d800 063B2 (v02 INT430 SYSFexxx 00001001 INTL 20050624)
[    0.000000] ACPI: FACS 00000000dfe6c000 00040
[    0.000000] ACPI: HPET 00000000dfe5d300 00038 (v01 DELL    M08     00000001 ASL  00000061)
[    0.000000] ACPI: APIC 00000000dfe5d400 00068 (v01 DELL    M08     27D80C0B ASL  00000047)
[    0.000000] ACPI: ASF! 00000000dfe5d000 0007E (v32 DELL    M08     27D80C0B ASL  00000061)
[    0.000000] ACPI: MCFG 00000000dfe5d3c0 0003E (v16 DELL    M08     27D80C0B ASL  00000061)
[    0.000000] ACPI: TCPA 00000000dfe5d700 00032 (v01                 00000000 ASL  00000000)
[    0.000000] ACPI: SLIC 00000000dfe5d49c 00176 (v01 DELL    M08     27D80C0B ASL  00000061)
[    0.000000] ACPI: SSDT 00000000dfe5b9c0 004CC (v01  PmRef    CpuPm 00003000 INTL 20050624)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at 0000000000000000-0000000120000000
[    0.000000] Initmem setup node 0 0000000000000000-0000000120000000
[    0.000000]   NODE_DATA [000000011fffb000 - 000000011fffffff]
[    0.000000]  [ffffea0000000000-ffffea0003ffffff] PMD -> [ffff88011b600000-ffff88011effffff] on node 0
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   DMA32    0x00001000 -> 0x00100000
[    0.000000]   Normal   0x00100000 -> 0x00120000
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[3] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x000dfe5a
[    0.000000]     0: 0x00100002 -> 0x00120000
[    0.000000] On node 0 totalpages: 1048039
[    0.000000]   DMA zone: 56 pages used for memmap
[    0.000000]   DMA zone: 5 pages reserved
[    0.000000]   DMA zone: 3922 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 14280 pages used for memmap
[    0.000000]   DMA32 zone: 898706 pages, LIFO batch:31
[    0.000000]   Normal zone: 1792 pages used for memmap
[    0.000000]   Normal zone: 129278 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] SMP: Allowing 2 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 0000000000100000
[    0.000000] PM: Registered nosave memory: 00000000dfe5a000 - 00000000dfe5b000
[    0.000000] PM: Registered nosave memory: 00000000dfe5b000 - 00000000e0000000
[    0.000000] PM: Registered nosave memory: 00000000e0000000 - 00000000f8000000
[    0.000000] PM: Registered nosave memory: 00000000f8000000 - 00000000fc000000
[    0.000000] PM: Registered nosave memory: 00000000fc000000 - 00000000fec00000
[    0.000000] PM: Registered nosave memory: 00000000fec00000 - 00000000fec10000
[    0.000000] PM: Registered nosave memory: 00000000fec10000 - 00000000fed18000
[    0.000000] PM: Registered nosave memory: 00000000fed18000 - 00000000fed1c000
[    0.000000] PM: Registered nosave memory: 00000000fed1c000 - 00000000fed20000
[    0.000000] PM: Registered nosave memory: 00000000fed20000 - 00000000fed90000
[    0.000000] PM: Registered nosave memory: 00000000fed90000 - 00000000feda0000
[    0.000000] PM: Registered nosave memory: 00000000feda0000 - 00000000feda6000
[    0.000000] PM: Registered nosave memory: 00000000feda6000 - 00000000fee00000
[    0.000000] PM: Registered nosave memory: 00000000fee00000 - 00000000fee10000
[    0.000000] PM: Registered nosave memory: 00000000fee10000 - 00000000ffe00000
[    0.000000] PM: Registered nosave memory: 00000000ffe00000 - 0000000100000000
[    0.000000] PM: Registered nosave memory: 0000000100000000 - 0000000100002000
[    0.000000] Allocating PCI resources starting at e0000000 (gap: e0000000:18000000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:2 nr_node_ids:1
[    0.000000] PERCPU: Embedded 27 pages/cpu @ffff88011fc00000 s79616 r8192 d22784 u1048576
[    0.000000] pcpu-alloc: s79616 r8192 d22784 u1048576 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 
[    0.000000] Built 1 zonelists in Node order, mobility grouping on.  Total pages: 1031906
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-3.0.0-16-generic root=UUID=eac6d6b5-7d89-4bf2-8e93-f1a91eb863a0 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 4037540k/4718592k available (6140k kernel code, 526436k absent, 154616k reserved, 6894k data, 988k init)
[    0.000000] SLUB: Genslabs=15, HWalign=64, Order=0-3, MinObjects=0, CPUs=2, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:16640 nr_irqs:512 16
[    0.000000] Extended CMOS year: 2000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 33554432 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 2193.843 MHz processor.
[    0.004004] Calibrating delay loop (skipped), value calculated using timer frequency.. 4387.68 BogoMIPS (lpj=8775372)
[    0.004009] pid_max: default: 32768 minimum: 301
[    0.004041] Security Framework initialized
[    0.004061] AppArmor: AppArmor initialized
[    0.004063] Yama: becoming mindful.
[    0.008053] Dentry cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.010441] Inode-cache hash table entries: 262144 (order: 9, 2097152 bytes)
[    0.011603] Mount-cache hash table entries: 256
[    0.011776] Initializing cgroup subsys cpuacct
[    0.011783] Initializing cgroup subsys memory
[    0.011794] Initializing cgroup subsys devices
[    0.011797] Initializing cgroup subsys freezer
[    0.011799] Initializing cgroup subsys net_cls
[    0.011801] Initializing cgroup subsys blkio
[    0.011809] Initializing cgroup subsys perf_event
[    0.011844] CPU: Physical Processor ID: 0
[    0.011846] CPU: Processor Core ID: 0
[    0.011848] mce: CPU supports 6 MCE banks
[    0.011858] CPU0: Thermal monitoring enabled (TM2)
[    0.011863] using mwait in idle threads.
[    0.014434] ACPI: Core revision 20110413
[    0.019685] ftrace: allocating 25748 entries in 101 pages
[    0.024516] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.066435] CPU0: Intel(R) Core(TM)2 Duo CPU     T7500  @ 2.20GHz stepping 0b
[    0.068003] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver.
[    0.068003] PEBS disabled due to CPU errata.
[    0.068003] ... version:                2
[    0.068003] ... bit width:              40
[    0.068003] ... generic registers:      2
[    0.068003] ... value mask:             000000ffffffffff
[    0.068003] ... max period:             000000007fffffff
[    0.068003] ... fixed-purpose events:   3
[    0.068003] ... event mask:             0000000700000003
[    0.068003] Booting Node   0, Processors  #1 Ok.
[    0.068003] smpboot cpu 1: start_ip = 9a000
[    0.156028] Brought up 2 CPUs
[    0.156031] Total of 2 processors activated (8775.42 BogoMIPS).
[    0.157311] devtmpfs: initialized
[    0.157395] print_constraints: dummy: 
[    0.157429] Time: 17:40:24  Date: 03/10/12
[    0.157466] NET: Registered protocol family 16
[    0.157496] Trying to unpack rootfs image as initramfs...
[    0.157600] ACPI: bus type pci registered
[    0.157662] PCI: MMCONFIG for domain 0000 [bus 00-3f] at [mem 0xf8000000-0xfbffffff] (base 0xf8000000)
[    0.157665] PCI: MMCONFIG at [mem 0xf8000000-0xfbffffff] reserved in E820
[    0.168309] PCI: Using configuration type 1 for base access
[    0.168317] dmi type 0xB1 record - unknown flag
[    0.169184] bio: create slab <bio-0> at 0
[    0.170464] ACPI: EC: Look up EC in DSDT
[    0.176995] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.181424] ACPI: SSDT 00000000dfe6c080 00043 (v01  LMPWR  DELLLOM 00001001 INTL 20050624)
[    0.181699] ACPI: Dynamic OEM Table Load:
[    0.181702] ACPI: SSDT           (null) 00043 (v01  LMPWR  DELLLOM 00001001 INTL 20050624)
[    0.181945] ACPI: SSDT 00000000dfe5c4f6 00286 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.182230] ACPI: Dynamic OEM Table Load:
[    0.182234] ACPI: SSDT           (null) 00286 (v01  PmRef  Cpu0Ist 00003000 INTL 20050624)
[    0.182340] ACPI: SSDT 00000000dfe5be8c 005E5 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.182613] ACPI: Dynamic OEM Table Load:
[    0.182616] ACPI: SSDT           (null) 005E5 (v01  PmRef  Cpu0Cst 00003001 INTL 20050624)
[    0.216267] ACPI: SSDT 00000000dfe5c77c 000C4 (v01  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    0.216561] ACPI: Dynamic OEM Table Load:
[    0.216565] ACPI: SSDT           (null) 000C4 (v01  PmRef  Cpu1Ist 00003000 INTL 20050624)
[    0.216640] ACPI: SSDT 00000000dfe5c471 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    0.216913] ACPI: Dynamic OEM Table Load:
[    0.216916] ACPI: SSDT           (null) 00085 (v01  PmRef  Cpu1Cst 00003000 INTL 20050624)
[    0.248236] ACPI: Interpreter enabled
[    0.248242] ACPI: (supports S0 S3 S4 S5)
[    0.248262] ACPI: Using IOAPIC for interrupt routing
[    0.310463] ACPI: ACPI Dock Station Driver: 3 docks/bays found
[    0.310468] HEST: Table not found.
[    0.310472] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.317981] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.332407] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7]
[    0.332411] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff]
[    0.332413] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff]
[    0.332416] pci_root PNP0A03:00: host bridge window [mem 0x000d0000-0x000dffff]
[    0.332418] pci_root PNP0A03:00: host bridge window [mem 0xe0000000-0xf7ffffff]
[    0.332421] pci_root PNP0A03:00: host bridge window [mem 0xfc000000-0xfebfffff]
[    0.332423] pci_root PNP0A03:00: host bridge window [mem 0xfec10000-0xfecfffff]
[    0.332426] pci_root PNP0A03:00: host bridge window [mem 0xfed1c000-0xfed1ffff]
[    0.332428] pci_root PNP0A03:00: host bridge window [mem 0xfed90000-0xfed9ffff]
[    0.332431] pci_root PNP0A03:00: host bridge window [mem 0xfed40000-0xfed44fff]
[    0.332433] pci_root PNP0A03:00: host bridge window [mem 0xfeda7000-0xfedfffff]
[    0.332435] pci_root PNP0A03:00: host bridge window [mem 0xfee10000-0xff9fffff]
[    0.332438] pci_root PNP0A03:00: host bridge window [mem 0xffc00000-0xffdfffff]
[    0.332457] pci 0000:00:00.0: [8086:2a00] type 0 class 0x000600
[    0.332509] pci 0000:00:01.0: [8086:2a01] type 1 class 0x000604
[    0.332555] pci 0000:00:01.0: PME# supported from D0 D3hot D3cold
[    0.332559] pci 0000:00:01.0: PME# disabled
[    0.332616] pci 0000:00:1a.0: [8086:2834] type 0 class 0x000c03
[    0.332675] pci 0000:00:1a.0: reg 20: [io  0x6f20-0x6f3f]
[    0.332721] pci 0000:00:1a.1: [8086:2835] type 0 class 0x000c03
[    0.332779] pci 0000:00:1a.1: reg 20: [io  0x6f00-0x6f1f]
[    0.332841] pci 0000:00:1a.7: [8086:283a] type 0 class 0x000c03
[    0.332866] pci 0000:00:1a.7: reg 10: [mem 0xfed1c400-0xfed1c7ff]
[    0.332978] pci 0000:00:1a.7: PME# supported from D0 D3hot D3cold
[    0.332984] pci 0000:00:1a.7: PME# disabled
[    0.333015] pci 0000:00:1b.0: [8086:284b] type 0 class 0x000403
[    0.333038] pci 0000:00:1b.0: reg 10: [mem 0xf6ffc000-0xf6ffffff 64bit]
[    0.333146] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.333151] pci 0000:00:1b.0: PME# disabled
[    0.333181] pci 0000:00:1c.0: [8086:283f] type 1 class 0x000604
[    0.333297] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.333302] pci 0000:00:1c.0: PME# disabled
[    0.333338] pci 0000:00:1c.1: [8086:2841] type 1 class 0x000604
[    0.333454] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.333459] pci 0000:00:1c.1: PME# disabled
[    0.333494] pci 0000:00:1c.3: [8086:2845] type 1 class 0x000604
[    0.333610] pci 0000:00:1c.3: PME# supported from D0 D3hot D3cold
[    0.333615] pci 0000:00:1c.3: PME# disabled
[    0.333650] pci 0000:00:1c.5: [8086:2849] type 1 class 0x000604
[    0.333764] pci 0000:00:1c.5: PME# supported from D0 D3hot D3cold
[    0.333769] pci 0000:00:1c.5: PME# disabled
[    0.333801] pci 0000:00:1d.0: [8086:2830] type 0 class 0x000c03
[    0.333861] pci 0000:00:1d.0: reg 20: [io  0x6f80-0x6f9f]
[    0.333906] pci 0000:00:1d.1: [8086:2831] type 0 class 0x000c03
[    0.333964] pci 0000:00:1d.1: reg 20: [io  0x6f60-0x6f7f]
[    0.334009] pci 0000:00:1d.2: [8086:2832] type 0 class 0x000c03
[    0.334068] pci 0000:00:1d.2: reg 20: [io  0x6f40-0x6f5f]
[    0.334128] pci 0000:00:1d.7: [8086:2836] type 0 class 0x000c03
[    0.334154] pci 0000:00:1d.7: reg 10: [mem 0xfed1c000-0xfed1c3ff]
[    0.334264] pci 0000:00:1d.7: PME# supported from D0 D3hot D3cold
[    0.334270] pci 0000:00:1d.7: PME# disabled
[    0.334296] pci 0000:00:1e.0: [8086:2448] type 1 class 0x000604
[    0.334399] pci 0000:00:1f.0: [8086:2815] type 0 class 0x000601
[    0.334518] pci 0000:00:1f.0: quirk: [io  0x1000-0x107f] claimed by ICH6 ACPI/GPIO/TCO
[    0.334525] pci 0000:00:1f.0: quirk: [io  0x1080-0x10bf] claimed by ICH6 GPIO
[    0.334530] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 1 PIO at 0900 (mask 007f)
[    0.334536] pci 0000:00:1f.0: ICH7 LPC Generic IO decode 3 PIO at 0c80 (mask 003f)
[    0.334597] pci 0000:00:1f.1: [8086:2850] type 0 class 0x000101
[    0.334615] pci 0000:00:1f.1: reg 10: [io  0x01f0-0x01f7]
[    0.334628] pci 0000:00:1f.1: reg 14: [io  0x03f4-0x03f7]
[    0.334640] pci 0000:00:1f.1: reg 18: [io  0x0170-0x0177]
[    0.334653] pci 0000:00:1f.1: reg 1c: [io  0x0374-0x0377]
[    0.334665] pci 0000:00:1f.1: reg 20: [io  0x6fa0-0x6faf]
[    0.334716] pci 0000:00:1f.2: [8086:2828] type 0 class 0x000101
[    0.334738] pci 0000:00:1f.2: reg 10: [io  0x6eb0-0x6eb7]
[    0.334751] pci 0000:00:1f.2: reg 14: [io  0x6eb8-0x6ebb]
[    0.334763] pci 0000:00:1f.2: reg 18: [io  0x6ec0-0x6ec7]
[    0.334775] pci 0000:00:1f.2: reg 1c: [io  0x6ec8-0x6ecb]
[    0.334788] pci 0000:00:1f.2: reg 20: [io  0x6ee0-0x6eef]
[    0.334800] pci 0000:00:1f.2: reg 24: [io  0xeff0-0xefff]
[    0.334850] pci 0000:00:1f.2: PME# supported from D3hot
[    0.334855] pci 0000:00:1f.2: PME# disabled
[    0.334872] pci 0000:00:1f.3: [8086:283e] type 0 class 0x000c05
[    0.334889] pci 0000:00:1f.3: reg 10: [mem 0xf6ffbf00-0xf6ffbfff]
[    0.334933] pci 0000:00:1f.3: reg 20: [io  0x10c0-0x10df]
[    0.335028] pci 0000:01:00.0: [10de:042b] type 0 class 0x000300
[    0.335048] pci 0000:01:00.0: reg 10: [mem 0xf5000000-0xf5ffffff]
[    0.335069] pci 0000:01:00.0: reg 14: [mem 0xe0000000-0xefffffff 64bit pref]
[    0.335091] pci 0000:01:00.0: reg 1c: [mem 0xf2000000-0xf3ffffff 64bit]
[    0.335105] pci 0000:01:00.0: reg 24: [io  0xdf00-0xdf7f]
[    0.335120] pci 0000:01:00.0: reg 30: [mem 0x00000000-0x0001ffff pref]
[    0.335231] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.335234] pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]
[    0.335238] pci 0000:00:01.0:   bridge window [mem 0xf2000000-0xf6efffff]
[    0.335242] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xefffffff 64bit pref]
[    0.335306] pci 0000:00:1c.0: PCI bridge to [bus 0b-0b]
[    0.335312] pci 0000:00:1c.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.335318] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff] (disabled)
[    0.335326] pci 0000:00:1c.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.335415] pci 0000:0c:00.0: [14e4:4312] type 0 class 0x000280
[    0.335439] pci 0000:0c:00.0: reg 10: [mem 0xf1ffc000-0xf1ffffff]
[    0.335612] pci 0000:0c:00.0: supports D1 D2
[    0.335641] pci 0000:0c:00.0: disabling ASPM on pre-1.1 PCIe device.  You can enable it with 'pcie_aspm=force'
[    0.335654] pci 0000:00:1c.1: PCI bridge to [bus 0c-0c]
[    0.335659] pci 0000:00:1c.1:   bridge window [io  0xf000-0x0000] (disabled)
[    0.335664] pci 0000:00:1c.1:   bridge window [mem 0xf1f00000-0xf1ffffff]
[    0.335673] pci 0000:00:1c.1:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.335738] pci 0000:00:1c.3: PCI bridge to [bus 0d-0e]
[    0.335743] pci 0000:00:1c.3:   bridge window [io  0xc000-0xcfff]
[    0.335748] pci 0000:00:1c.3:   bridge window [mem 0xf1c00000-0xf1efffff]
[    0.335757] pci 0000:00:1c.3:   bridge window [mem 0xf0000000-0xf01fffff 64bit pref]
[    0.335854] pci 0000:09:00.0: [14e4:1673] type 0 class 0x000200
[    0.335887] pci 0000:09:00.0: reg 10: [mem 0xf1bf0000-0xf1bfffff 64bit]
[    0.336097] pci 0000:09:00.0: PME# supported from D3hot D3cold
[    0.336104] pci 0000:09:00.0: PME# disabled
[    0.344048] pci 0000:00:1c.5: PCI bridge to [bus 09-09]
[    0.344053] pci 0000:00:1c.5:   bridge window [io  0xf000-0x0000] (disabled)
[    0.344059] pci 0000:00:1c.5:   bridge window [mem 0xf1b00000-0xf1bfffff]
[    0.344068] pci 0000:00:1c.5:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.344124] pci 0000:03:01.0: [1217:7135] type 2 class 0x000607
[    0.344151] pci 0000:03:01.0: reg 10: [mem 0x00000000-0x00000fff]
[    0.344198] pci 0000:03:01.0: supports D1 D2
[    0.344200] pci 0000:03:01.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.344207] pci 0000:03:01.0: PME# disabled
[    0.344240] pci 0000:03:01.4: [1217:00f7] type 0 class 0x000c00
[    0.344262] pci 0000:03:01.4: reg 10: [mem 0xf1aff000-0xf1afffff]
[    0.344275] pci 0000:03:01.4: reg 14: [mem 0xf1afe800-0xf1afefff]
[    0.344363] pci 0000:03:01.4: supports D1 D2
[    0.344365] pci 0000:03:01.4: PME# supported from D0 D1 D2 D3hot D3cold
[    0.344370] pci 0000:03:01.4: PME# disabled
[    0.344443] pci 0000:00:1e.0: PCI bridge to [bus 03-04] (subtractive decode)
[    0.344449] pci 0000:00:1e.0:   bridge window [io  0xf000-0x0000] (disabled)
[    0.344454] pci 0000:00:1e.0:   bridge window [mem 0xf1a00000-0xf1afffff]
[    0.344462] pci 0000:00:1e.0:   bridge window [mem 0xfff00000-0x000fffff pref] (disabled)
[    0.344465] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.344467] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.344470] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.344472] pci 0000:00:1e.0:   bridge window [mem 0x000d0000-0x000dffff] (subtractive decode)
[    0.344475] pci 0000:00:1e.0:   bridge window [mem 0xe0000000-0xf7ffffff] (subtractive decode)
[    0.344477] pci 0000:00:1e.0:   bridge window [mem 0xfc000000-0xfebfffff] (subtractive decode)
[    0.344480] pci 0000:00:1e.0:   bridge window [mem 0xfec10000-0xfecfffff] (subtractive decode)
[    0.344482] pci 0000:00:1e.0:   bridge window [mem 0xfed1c000-0xfed1ffff] (subtractive decode)
[    0.344485] pci 0000:00:1e.0:   bridge window [mem 0xfed90000-0xfed9ffff] (subtractive decode)
[    0.344487] pci 0000:00:1e.0:   bridge window [mem 0xfed40000-0xfed44fff] (subtractive decode)
[    0.344490] pci 0000:00:1e.0:   bridge window [mem 0xfeda7000-0xfedfffff] (subtractive decode)
[    0.344492] pci 0000:00:1e.0:   bridge window [mem 0xfee10000-0xff9fffff] (subtractive decode)
[    0.344495] pci 0000:00:1e.0:   bridge window [mem 0xffc00000-0xffdfffff] (subtractive decode)
[    0.344550] pci_bus 0000:04: [bus 04-07] partially hidden behind transparent bridge 0000:03 [bus 03-04]
[    0.344597] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.344816] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[    0.344915] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGP_._PRT]
[    0.344956] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP01._PRT]
[    0.344999] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP02._PRT]
[    0.345043] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP04._PRT]
[    0.345085] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.RP06._PRT]
[    0.345129]  pci0000:00: Requesting ACPI _OSC control (0x1d)
[    0.345133]  pci0000:00: ACPI _OSC request failed (AE_NOT_FOUND), returned control mask: 0x1d
[    0.345135] ACPI _OSC control for PCIe not granted, disabling ASPM
[    0.358059] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 11) *5
[    0.358124] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *3
[    0.358186] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 *10 11)
[    0.358247] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 *9 10 11)
[    0.358309] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[    0.358373] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 9 *10 11 12 14 15)
[    0.358439] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[    0.358494] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[    0.358642] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.358647] vgaarb: loaded
[    0.358649] vgaarb: bridge control possible 0000:01:00.0
[    0.358844] SCSI subsystem initialized
[    0.358928] libata version 3.00 loaded.
[    0.358974] usbcore: registered new interface driver usbfs
[    0.358985] usbcore: registered new interface driver hub
[    0.359017] usbcore: registered new device driver usb
[    0.359103] PCI: Using ACPI for IRQ routing
[    0.361806] PCI: pci_cache_line_size set to 64 bytes
[    0.361928] reserve RAM buffer: 000000000009f000 - 000000000009ffff 
[    0.361931] reserve RAM buffer: 00000000dfe5a800 - 00000000dfffffff 
[    0.362036] NetLabel: Initializing
[    0.362038] NetLabel:  domain hash size = 128
[    0.362039] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.362052] NetLabel:  unlabeled traffic allowed by default
[    0.362095] HPET: 3 timers in total, 0 timers will be used for per-cpu timer
[    0.362101] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 0
[    0.362105] hpet0: 3 comparators, 64-bit 14.318180 MHz counter
[    0.368220] Switching to clocksource hpet
[    0.371494] Switched to NOHz mode on CPU #0
[    0.371575] Switched to NOHz mode on CPU #1
[    0.375419] AppArmor: AppArmor Filesystem Enabled
[    0.375454] pnp: PnP ACPI init
[    0.375472] ACPI: bus type pnp registered
[    0.382694] pnp 00:00: [bus 00-ff]
[    0.382698] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.382700] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.382702] pnp 00:00: [io  0x0d00-0xffff window]
[    0.382705] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.382707] pnp 00:00: [mem 0x000d0000-0x000dffff window]
[    0.382709] pnp 00:00: [mem 0xe0000000-0xf7ffffff window]
[    0.382712] pnp 00:00: [mem 0xfc000000-0xfebfffff window]
[    0.382717] pnp 00:00: [mem 0xfec10000-0xfecfffff window]
[    0.382720] pnp 00:00: [mem 0xfed1c000-0xfed1ffff window]
[    0.382722] pnp 00:00: [mem 0xfed90000-0xfed9ffff window]
[    0.382724] pnp 00:00: [mem 0xfed40000-0xfed44fff window]
[    0.382726] pnp 00:00: [mem 0xfeda7000-0xfedfffff window]
[    0.382728] pnp 00:00: [mem 0xfee10000-0xff9fffff window]
[    0.382731] pnp 00:00: [mem 0xffc00000-0xffdfffff window]
[    0.382818] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.382848] pnp 00:01: [irq 12]
[    0.382878] pnp 00:01: Plug and Play ACPI device, IDs PNP0f13 (active)
[    0.382893] pnp 00:02: [io  0x0060]
[    0.382896] pnp 00:02: [io  0x0064]
[    0.382897] pnp 00:02: [io  0x0062]
[    0.382899] pnp 00:02: [io  0x0066]
[    0.382905] pnp 00:02: [irq 1]
[    0.382926] pnp 00:02: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.382944] pnp 00:03: [io  0x0070-0x0071]
[    0.382950] pnp 00:03: [irq 8]
[    0.382952] pnp 00:03: [io  0x0072-0x0077]
[    0.382973] pnp 00:03: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.382988] pnp 00:04: [io  0x0061]
[    0.382990] pnp 00:04: [io  0x0063]
[    0.382992] pnp 00:04: [io  0x0065]
[    0.382994] pnp 00:04: [io  0x0067]
[    0.383015] pnp 00:04: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.383029] pnp 00:05: [io  0x002e-0x002f]
[    0.383031] pnp 00:05: [io  0x0c80-0x0caf]
[    0.383033] pnp 00:05: [io  0x0cc0-0x0cff]
[    0.383034] pnp 00:05: [io  0x004e-0x004f]
[    0.383094] system 00:05: [io  0x0c80-0x0caf] has been reserved
[    0.383097] system 00:05: [io  0x0cc0-0x0cff] could not be reserved
[    0.383100] system 00:05: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.383118] pnp 00:06: [dma 4]
[    0.383120] pnp 00:06: [io  0x0000-0x000f]
[    0.383122] pnp 00:06: [io  0x0080-0x0085]
[    0.383123] pnp 00:06: [io  0x0087-0x008f]
[    0.383125] pnp 00:06: [io  0x00c0-0x00df]
[    0.383127] pnp 00:06: [io  0x0010-0x001f]
[    0.383128] pnp 00:06: [io  0x0090-0x0091]
[    0.383130] pnp 00:06: [io  0x0093-0x009f]
[    0.383153] pnp 00:06: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.383168] pnp 00:07: [io  0x00f0-0x00ff]
[    0.383174] pnp 00:07: [irq 13]
[    0.383197] pnp 00:07: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.383236] pnp 00:08: [mem 0xfed00000-0xfed003ff]
[    0.383284] system 00:08: [mem 0xfed00000-0xfed003ff] has been reserved
[    0.383287] system 00:08: Plug and Play ACPI device, IDs PNP0103 PNP0c01 (active)
[    0.388753] pnp 00:09: [irq 4]
[    0.388756] pnp 00:09: [io  0x03f8-0x03ff]
[    0.388817] pnp 00:09: Plug and Play ACPI device, IDs PNP0501 (active)
[    0.399384] pnp 00:0a: [mem 0xfed40000-0xfed44fff]
[    0.399387] pnp 00:0a: [io  0x0cb0-0x0cbb]
[    0.399436] system 00:0a: [io  0x0cb0-0x0cbb] has been reserved
[    0.399439] system 00:0a: [mem 0xfed40000-0xfed44fff] has been reserved
[    0.399443] system 00:0a: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.402344] pnp 00:0b: [io  0x0900-0x097f]
[    0.402346] pnp 00:0b: [io  0x0092]
[    0.402348] pnp 00:0b: [io  0x00b2-0x00b3]
[    0.402350] pnp 00:0b: [io  0x0020-0x0021]
[    0.402352] pnp 00:0b: [io  0x00a0-0x00a1]
[    0.402354] pnp 00:0b: [irq 0 disabled]
[    0.402355] pnp 00:0b: [io  0x04d0-0x04d1]
[    0.402357] pnp 00:0b: [io  0x1000-0x1005]
[    0.402359] pnp 00:0b: [io  0x1008-0x100f]
[    0.402375] pnp 00:0b: disabling [io  0x1000-0x1005] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.402378] pnp 00:0b: disabling [io  0x1008-0x100f] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.402434] system 00:0b: [io  0x0900-0x097f] has been reserved
[    0.402437] system 00:0b: [io  0x04d0-0x04d1] has been reserved
[    0.402441] system 00:0b: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.402457] pnp 00:0c: [io  0xf400-0xf4fe]
[    0.402459] pnp 00:0c: [io  0x0086]
[    0.402460] pnp 00:0c: [io  0x1006-0x1007]
[    0.402462] pnp 00:0c: [io  0x100a-0x1059]
[    0.402464] pnp 00:0c: [io  0x1060-0x107f]
[    0.402466] pnp 00:0c: [io  0x1080-0x10bf]
[    0.402467] pnp 00:0c: [io  0x10c0-0x10df]
[    0.402469] pnp 00:0c: [io  0x1010-0x102f]
[    0.402471] pnp 00:0c: [io  0x0809]
[    0.402485] pnp 00:0c: disabling [io  0x1006-0x1007] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.402489] pnp 00:0c: disabling [io  0x100a-0x1059] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.402492] pnp 00:0c: disabling [io  0x1060-0x107f] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.402495] pnp 00:0c: disabling [io  0x1010-0x102f] because it overlaps 0000:00:1f.0 BAR 13 [io  0x1000-0x107f]
[    0.402548] system 00:0c: [io  0xf400-0xf4fe] has been reserved
[    0.402551] system 00:0c: [io  0x1080-0x10bf] has been reserved
[    0.402553] system 00:0c: [io  0x10c0-0x10df] has been reserved
[    0.402556] system 00:0c: [io  0x0809] has been reserved
[    0.402559] system 00:0c: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.413603] pnp 00:0d: [mem 0x00000000-0x0009efff]
[    0.413607] pnp 00:0d: [mem 0x0009f000-0x0009ffff]
[    0.413609] pnp 00:0d: [mem 0x000c0000-0x000cffff]
[    0.413611] pnp 00:0d: [mem 0x000e0000-0x000fffff]
[    0.413613] pnp 00:0d: [mem 0x00100000-0xdfe5a7ff]
[    0.413615] pnp 00:0d: [mem 0xdfe5a800-0xdfefffff]
[    0.413617] pnp 00:0d: [mem 0xdff00000-0xdfffffff]
[    0.413619] pnp 00:0d: [mem 0xdff00000-0xe06fffff]
[    0.413620] pnp 00:0d: [mem 0xffe00000-0xffffffff]
[    0.413622] pnp 00:0d: [mem 0xffa00000-0xffbfffff]
[    0.413624] pnp 00:0d: [mem 0xfec00000-0xfec0ffff]
[    0.413626] pnp 00:0d: [mem 0xfee00000-0xfee0ffff]
[    0.413628] pnp 00:0d: [mem 0xfed20000-0xfed3ffff]
[    0.413630] pnp 00:0d: [mem 0xfed45000-0xfed8ffff]
[    0.413632] pnp 00:0d: [mem 0xfeda0000-0xfeda3fff]
[    0.413633] pnp 00:0d: [mem 0xfeda4000-0xfeda4fff]
[    0.413635] pnp 00:0d: [mem 0xfeda5000-0xfeda5fff]
[    0.413637] pnp 00:0d: [mem 0xfeda6000-0xfeda6fff]
[    0.413639] pnp 00:0d: [mem 0xfed18000-0xfed1bfff]
[    0.413644] pnp 00:0d: [mem 0xf8000000-0xfbffffff]
[    0.413653] pnp 00:0d: disabling [mem 0xdff00000-0xe06fffff] because it overlaps 0000:00:01.0 BAR 15 [mem 0xe0000000-0xefffffff 64bit pref]
[    0.413680] pnp 00:0d: disabling [mem 0xdff00000-0xe06fffff disabled] because it overlaps 0000:01:00.0 BAR 1 [mem 0xe0000000-0xefffffff 64bit pref]
[    0.413766] system 00:0d: [mem 0x00000000-0x0009efff] could not be reserved
[    0.413769] system 00:0d: [mem 0x0009f000-0x0009ffff] could not be reserved
[    0.413772] system 00:0d: [mem 0x000c0000-0x000cffff] could not be reserved
[    0.413775] system 00:0d: [mem 0x000e0000-0x000fffff] could not be reserved
[    0.413777] system 00:0d: [mem 0x00100000-0xdfe5a7ff] could not be reserved
[    0.413780] system 00:0d: [mem 0xdfe5a800-0xdfefffff] has been reserved
[    0.413783] system 00:0d: [mem 0xdff00000-0xdfffffff] has been reserved
[    0.413786] system 00:0d: [mem 0xffe00000-0xffffffff] has been reserved
[    0.413789] system 00:0d: [mem 0xffa00000-0xffbfffff] has been reserved
[    0.413791] system 00:0d: [mem 0xfec00000-0xfec0ffff] could not be reserved
[    0.413794] system 00:0d: [mem 0xfee00000-0xfee0ffff] has been reserved
[    0.413800] system 00:0d: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.413803] system 00:0d: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.413805] system 00:0d: [mem 0xfeda0000-0xfeda3fff] has been reserved
[    0.413808] system 00:0d: [mem 0xfeda4000-0xfeda4fff] has been reserved
[    0.413811] system 00:0d: [mem 0xfeda5000-0xfeda5fff] has been reserved
[    0.413813] system 00:0d: [mem 0xfeda6000-0xfeda6fff] has been reserved
[    0.413816] system 00:0d: [mem 0xfed18000-0xfed1bfff] has been reserved
[    0.413818] system 00:0d: [mem 0xf8000000-0xfbffffff] has been reserved
[    0.413822] system 00:0d: Plug and Play ACPI device, IDs PNP0c01 (active)
[    0.413873] pnp: PnP ACPI: found 14 devices
[    0.413875] ACPI: ACPI bus type pnp unregistered
[    0.419923] PCI: max bus depth: 2 pci_try_num: 3
[    0.420018] pci 0000:00:1e.0: BAR 15: can't assign mem pref (size 0x4000000)
[    0.420023] pci 0000:00:1e.0: BAR 13: assigned [io  0x2000-0x2fff]
[    0.420028] pci 0000:00:1c.5: BAR 15: assigned [mem 0xf0200000-0xf03fffff 64bit pref]
[    0.420031] pci 0000:00:1c.5: BAR 13: assigned [io  0x3000-0x3fff]
[    0.420035] pci 0000:00:1c.1: BAR 15: assigned [mem 0xf0400000-0xf05fffff 64bit pref]
[    0.420039] pci 0000:00:1c.1: BAR 13: assigned [io  0x4000-0x4fff]
[    0.420042] pci 0000:00:1c.0: BAR 14: assigned [mem 0xf0600000-0xf07fffff]
[    0.420046] pci 0000:00:1c.0: BAR 15: assigned [mem 0xf0800000-0xf09fffff 64bit pref]
[    0.420049] pci 0000:00:1c.0: BAR 13: assigned [io  0x5000-0x5fff]
[    0.420053] pci 0000:01:00.0: BAR 6: assigned [mem 0xf4000000-0xf401ffff pref]
[    0.420056] pci 0000:00:01.0: PCI bridge to [bus 01-01]
[    0.420059] pci 0000:00:01.0:   bridge window [io  0xd000-0xdfff]
[    0.420063] pci 0000:00:01.0:   bridge window [mem 0xf2000000-0xf6efffff]
[    0.420066] pci 0000:00:01.0:   bridge window [mem 0xe0000000-0xefffffff 64bit pref]
[    0.420071] pci 0000:00:1c.0: PCI bridge to [bus 0b-0b]
[    0.420074] pci 0000:00:1c.0:   bridge window [io  0x5000-0x5fff]
[    0.420081] pci 0000:00:1c.0:   bridge window [mem 0xf0600000-0xf07fffff]
[    0.420086] pci 0000:00:1c.0:   bridge window [mem 0xf0800000-0xf09fffff 64bit pref]
[    0.420094] pci 0000:00:1c.1: PCI bridge to [bus 0c-0c]
[    0.420098] pci 0000:00:1c.1:   bridge window [io  0x4000-0x4fff]
[    0.420104] pci 0000:00:1c.1:   bridge window [mem 0xf1f00000-0xf1ffffff]
[    0.420110] pci 0000:00:1c.1:   bridge window [mem 0xf0400000-0xf05fffff 64bit pref]
[    0.420118] pci 0000:00:1c.3: PCI bridge to [bus 0d-0e]
[    0.420122] pci 0000:00:1c.3:   bridge window [io  0xc000-0xcfff]
[    0.420128] pci 0000:00:1c.3:   bridge window [mem 0xf1c00000-0xf1efffff]
[    0.420133] pci 0000:00:1c.3:   bridge window [mem 0xf0000000-0xf01fffff 64bit pref]
[    0.420142] pci 0000:00:1c.5: PCI bridge to [bus 09-09]
[    0.420145] pci 0000:00:1c.5:   bridge window [io  0x3000-0x3fff]
[    0.420152] pci 0000:00:1c.5:   bridge window [mem 0xf1b00000-0xf1bfffff]
[    0.420157] pci 0000:00:1c.5:   bridge window [mem 0xf0200000-0xf03fffff 64bit pref]
[    0.420172] pci 0000:03:01.0: BAR 15: can't assign mem pref (size 0x4000000)
[    0.420181] pci 0000:03:01.0: BAR 16: can't assign mem (size 0x4000000)
[    0.420183] pci 0000:03:01.0: BAR 0: assigned [mem 0xf1a00000-0xf1a00fff]
[    0.420190] pci 0000:03:01.0: BAR 0: set to [mem 0xf1a00000-0xf1a00fff] (PCI address [0xf1a00000-0xf1a00fff])
[    0.420193] pci 0000:03:01.0: BAR 13: assigned [io  0x2000-0x20ff]
[    0.420195] pci 0000:03:01.0: BAR 14: assigned [io  0x2400-0x24ff]
[    0.420198] pci 0000:03:01.0: CardBus bridge to [bus 04-07]
[    0.420200] pci 0000:03:01.0:   bridge window [io  0x2000-0x20ff]
[    0.420206] pci 0000:03:01.0:   bridge window [io  0x2400-0x24ff]
[    0.420211] pci 0000:00:1e.0: PCI bridge to [bus 03-04]
[    0.420214] pci 0000:00:1e.0:   bridge window [io  0x2000-0x2fff]
[    0.420221] pci 0000:00:1e.0:   bridge window [mem 0xf1a00000-0xf1afffff]
[    0.420226] pci 0000:00:1e.0:   bridge window [mem pref disabled]
[    0.420253] pci 0000:00:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.420258] pci 0000:00:01.0: setting latency timer to 64
[    0.420265] pci 0000:00:1c.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.420270] pci 0000:00:1c.0: setting latency timer to 64
[    0.420282] pci 0000:00:1c.1: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.420287] pci 0000:00:1c.1: setting latency timer to 64
[    0.420298] pci 0000:00:1c.3: PCI INT D -> GSI 19 (level, low) -> IRQ 19
[    0.420303] pci 0000:00:1c.3: setting latency timer to 64
[    0.420311] pci 0000:00:1c.5: PCI INT B -> GSI 17 (level, low) -> IRQ 17
[    0.420316] pci 0000:00:1c.5: setting latency timer to 64
[    0.420326] pci 0000:00:1e.0: setting latency timer to 64
[    0.420335] pci 0000:03:01.0: enabling device (0000 -> 0003)
[    0.420339] pci 0000:03:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    0.420348] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.420350] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.420352] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.420355] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.420357] pci_bus 0000:00: resource 8 [mem 0xe0000000-0xf7ffffff]
[    0.420359] pci_bus 0000:00: resource 9 [mem 0xfc000000-0xfebfffff]
[    0.420361] pci_bus 0000:00: resource 10 [mem 0xfec10000-0xfecfffff]
[    0.420364] pci_bus 0000:00: resource 11 [mem 0xfed1c000-0xfed1ffff]
[    0.420366] pci_bus 0000:00: resource 12 [mem 0xfed90000-0xfed9ffff]
[    0.420368] pci_bus 0000:00: resource 13 [mem 0xfed40000-0xfed44fff]
[    0.420370] pci_bus 0000:00: resource 14 [mem 0xfeda7000-0xfedfffff]
[    0.420373] pci_bus 0000:00: resource 15 [mem 0xfee10000-0xff9fffff]
[    0.420375] pci_bus 0000:00: resource 16 [mem 0xffc00000-0xffdfffff]
[    0.420377] pci_bus 0000:01: resource 0 [io  0xd000-0xdfff]
[    0.420380] pci_bus 0000:01: resource 1 [mem 0xf2000000-0xf6efffff]
[    0.420382] pci_bus 0000:01: resource 2 [mem 0xe0000000-0xefffffff 64bit pref]
[    0.420385] pci_bus 0000:0b: resource 0 [io  0x5000-0x5fff]
[    0.420387] pci_bus 0000:0b: resource 1 [mem 0xf0600000-0xf07fffff]
[    0.420389] pci_bus 0000:0b: resource 2 [mem 0xf0800000-0xf09fffff 64bit pref]
[    0.420392] pci_bus 0000:0c: resource 0 [io  0x4000-0x4fff]
[    0.420394] pci_bus 0000:0c: resource 1 [mem 0xf1f00000-0xf1ffffff]
[    0.420397] pci_bus 0000:0c: resource 2 [mem 0xf0400000-0xf05fffff 64bit pref]
[    0.420399] pci_bus 0000:0d: resource 0 [io  0xc000-0xcfff]
[    0.420401] pci_bus 0000:0d: resource 1 [mem 0xf1c00000-0xf1efffff]
[    0.420404] pci_bus 0000:0d: resource 2 [mem 0xf0000000-0xf01fffff 64bit pref]
[    0.420406] pci_bus 0000:09: resource 0 [io  0x3000-0x3fff]
[    0.420408] pci_bus 0000:09: resource 1 [mem 0xf1b00000-0xf1bfffff]
[    0.420411] pci_bus 0000:09: resource 2 [mem 0xf0200000-0xf03fffff 64bit pref]
[    0.420413] pci_bus 0000:03: resource 0 [io  0x2000-0x2fff]
[    0.420415] pci_bus 0000:03: resource 1 [mem 0xf1a00000-0xf1afffff]
[    0.420418] pci_bus 0000:03: resource 4 [io  0x0000-0x0cf7]
[    0.420420] pci_bus 0000:03: resource 5 [io  0x0d00-0xffff]
[    0.420422] pci_bus 0000:03: resource 6 [mem 0x000a0000-0x000bffff]
[    0.420424] pci_bus 0000:03: resource 7 [mem 0x000d0000-0x000dffff]
[    0.420427] pci_bus 0000:03: resource 8 [mem 0xe0000000-0xf7ffffff]
[    0.420429] pci_bus 0000:03: resource 9 [mem 0xfc000000-0xfebfffff]
[    0.420431] pci_bus 0000:03: resource 10 [mem 0xfec10000-0xfecfffff]
[    0.420434] pci_bus 0000:03: resource 11 [mem 0xfed1c000-0xfed1ffff]
[    0.420436] pci_bus 0000:03: resource 12 [mem 0xfed90000-0xfed9ffff]
[    0.420438] pci_bus 0000:03: resource 13 [mem 0xfed40000-0xfed44fff]
[    0.420440] pci_bus 0000:03: resource 14 [mem 0xfeda7000-0xfedfffff]
[    0.420443] pci_bus 0000:03: resource 15 [mem 0xfee10000-0xff9fffff]
[    0.420445] pci_bus 0000:03: resource 16 [mem 0xffc00000-0xffdfffff]
[    0.420447] pci_bus 0000:04: resource 0 [io  0x2000-0x20ff]
[    0.420449] pci_bus 0000:04: resource 1 [io  0x2400-0x24ff]
[    0.420492] NET: Registered protocol family 2
[    0.420658] IP route cache hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.422028] TCP established hash table entries: 524288 (order: 11, 8388608 bytes)
[    0.426728] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.427311] TCP: Hash tables configured (established 524288 bind 65536)
[    0.427314] TCP reno registered
[    0.427325] UDP hash table entries: 2048 (order: 4, 65536 bytes)
[    0.427381] UDP-Lite hash table entries: 2048 (order: 4, 65536 bytes)
[    0.427534] NET: Registered protocol family 1
[    0.427766] pci 0000:01:00.0: Boot video device
[    0.427785] PCI: CLS 64 bytes, default 64
[    0.427788] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    0.427791] Placing 64MB software IO TLB between ffff8800dbe54000 - ffff8800dfe54000
[    0.427793] software IO TLB at phys 0xdbe54000 - 0xdfe54000
[    0.428205] audit: initializing netlink socket (disabled)
[    0.428217] type=2000 audit(1331401224.424:1): initialized
[    0.463027] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    0.489768] VFS: Disk quotas dquot_6.5.2
[    0.489828] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    0.490436] fuse init (API version 7.16)
[    0.490524] msgmni has been set to 7885
[    0.490858] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.490889] io scheduler noop registered
[    0.490890] io scheduler deadline registered
[    0.490931] io scheduler cfq registered (default)
[    0.491045] pcieport 0000:00:01.0: setting latency timer to 64
[    0.491082] pcieport 0000:00:01.0: irq 40 for MSI/MSI-X
[    0.491136] pcieport 0000:00:1c.0: setting latency timer to 64
[    0.491193] pcieport 0000:00:1c.0: irq 41 for MSI/MSI-X
[    0.491278] pcieport 0000:00:1c.1: setting latency timer to 64
[    0.491334] pcieport 0000:00:1c.1: irq 42 for MSI/MSI-X
[    0.491411] pcieport 0000:00:1c.3: setting latency timer to 64
[    0.491468] pcieport 0000:00:1c.3: irq 43 for MSI/MSI-X
[    0.491549] pcieport 0000:00:1c.5: setting latency timer to 64
[    0.491605] pcieport 0000:00:1c.5: irq 44 for MSI/MSI-X
[    0.491700] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.491722] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.491765] intel_idle: MWAIT substates: 0x22220
[    0.491767] intel_idle: does not run on family 6 model 15
[    0.491842] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.491888] ACPI: AC Adapter [AC] (on-line)
[    0.491962] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.492393] ACPI: Lid Switch [LID]
[    0.492434] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    0.492438] ACPI: Power Button [PBTN]
[    0.492476] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input2
[    0.492479] ACPI: Sleep Button [SBTN]
[    0.492506] ACPI: acpi_idle registered with cpuidle
[    0.492656] Monitor-Mwait will be used to enter C-1 state
[    0.492685] Monitor-Mwait will be used to enter C-2 state
[    0.492710] Monitor-Mwait will be used to enter C-3 state
[    0.492715] Marking TSC unstable due to TSC halts in idle
[    0.529969] thermal LNXTHERM:00: registered as thermal_zone0
[    0.529972] ACPI: Thermal Zone [THM] (74 C)
[    0.530001] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.530045] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.530061] ERST: Table is not found!
[    0.530147] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.550770] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.551054] Freeing initrd memory: 13412k freed
[    0.570114] ACPI: Battery Slot [BAT0] (battery present)
[    0.570156] ACPI: Battery Slot [BAT1] (battery absent)
[    0.617729] 00:09: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[    0.618023] Linux agpgart interface v0.103
[    0.619248] brd: module loaded
[    0.619743] loop: module loaded
[    0.619896] ata_piix 0000:00:1f.1: version 2.13
[    0.619910] ata_piix 0000:00:1f.1: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    0.619955] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.620284] scsi0 : ata_piix
[    0.620385] scsi1 : ata_piix
[    0.622068] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x6fa0 irq 14
[    0.622071] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x6fa8 irq 15
[    0.622101] ata_piix 0000:00:1f.2: PCI INT C -> GSI 18 (level, low) -> IRQ 18
[    0.622110] ata_piix 0000:00:1f.2: MAP [ P0 P2 P1 P3 ]
[    0.622129] ata2: port disabled. ignoring.
[    0.776064] ata_piix 0000:00:1f.2: setting latency timer to 64
[    0.776387] scsi2 : ata_piix
[    0.776462] scsi3 : ata_piix
[    0.778119] ata3: SATA max UDMA/133 cmd 0x6eb0 ctl 0x6eb8 bmdma 0x6ee0 irq 18
[    0.778127] ata4: SATA max UDMA/133 cmd 0x6ec0 ctl 0x6ec8 bmdma 0x6ee8 irq 18
[    0.778459] Fixed MDIO Bus: probed
[    0.778481] PPP generic driver version 2.4.2
[    0.778525] tun: Universal TUN/TAP device driver, 1.6
[    0.778527] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.778612] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.778633] ehci_hcd 0000:00:1a.7: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    0.778656] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.778660] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.778691] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.778726] ehci_hcd 0000:00:1a.7: debug port 1
[    0.782611] ehci_hcd 0000:00:1a.7: cache line size of 64 is not supported
[    0.782625] ehci_hcd 0000:00:1a.7: irq 22, io mem 0xfed1c400
[    0.784527] ata1.00: ATAPI: Optiarc DVD+/-RW AD-5560A, DD12, max UDMA/33
[    0.796017] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.796130] hub 1-0:1.0: USB hub found
[    0.796134] hub 1-0:1.0: 4 ports detected
[    0.796207] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.796219] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.796223] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.796255] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.796290] ehci_hcd 0000:00:1d.7: debug port 1
[    0.800164] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    0.800423] ata1.00: configured for UDMA/33
[    0.800426] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xfed1c000
[    0.801882] scsi 0:0:0:0: CD-ROM            Optiarc  DVD+-RW AD-5560A DD12 PQ: 0 ANSI: 5
[    0.805825] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    0.805828] cdrom: Uniform CD-ROM driver Revision: 3.20
[    0.805917] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    0.805967] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    0.816018] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.816114] hub 2-0:1.0: USB hub found
[    0.816118] hub 2-0:1.0: 6 ports detected
[    0.816192] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.816208] uhci_hcd: USB Universal Host Controller Interface driver
[    0.816236] uhci_hcd 0000:00:1a.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.816243] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.816246] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.816276] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.816306] uhci_hcd 0000:00:1a.0: irq 20, io base 0x00006f20
[    0.816423] hub 3-0:1.0: USB hub found
[    0.816427] hub 3-0:1.0: 2 ports detected
[    0.816492] uhci_hcd 0000:00:1a.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.816499] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.816502] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.816546] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.816584] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00006f00
[    0.816694] hub 4-0:1.0: USB hub found
[    0.816698] hub 4-0:1.0: 2 ports detected
[    0.816760] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[    0.816767] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.816770] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.816804] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    0.816835] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00006f80
[    0.816949] hub 5-0:1.0: USB hub found
[    0.816953] hub 5-0:1.0: 2 ports detected
[    0.817012] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.817019] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.817022] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.817054] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    0.817085] uhci_hcd 0000:00:1d.1: irq 21, io base 0x00006f60
[    0.817193] hub 6-0:1.0: USB hub found
[    0.817197] hub 6-0:1.0: 2 ports detected
[    0.817258] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    0.817265] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.817268] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.817299] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    0.817328] uhci_hcd 0000:00:1d.2: irq 22, io base 0x00006f40
[    0.817444] hub 7-0:1.0: USB hub found
[    0.817448] hub 7-0:1.0: 2 ports detected
[    0.817549] i8042: PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.820821] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.820827] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.820930] mousedev: PS/2 mouse device common for all mice
[    0.821066] rtc_cmos 00:03: RTC can wake from S4
[    0.821180] rtc_cmos 00:03: rtc core: registered rtc_cmos as rtc0
[    0.821213] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.821306] device-mapper: uevent: version 1.0.3
[    0.821379] device-mapper: ioctl: 4.20.0-ioctl (2011-02-02) initialised: dm-devel@redhat.com
[    0.821440] cpuidle: using governor ladder
[    0.821533] cpuidle: using governor menu
[    0.821536] EFI Variables Facility v0.08 2004-May-17
[    0.821774] TCP cubic registered
[    0.821895] NET: Registered protocol family 10
[    0.822349] NET: Registered protocol family 17
[    0.822366] Registering the dns_resolver key type
[    0.822468] PM: Hibernation image not present or could not be loaded.
[    0.822479] registered taskstats version 1
[    0.836382] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.841699]   Magic number: 4:667:693
[    0.841837] rtc_cmos 00:03: setting system clock to 2012-03-10 17:40:25 UTC (1331401225)
[    0.843304] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.843306] EDD information not available.
[    1.536149] usb 5-1: new full speed USB device number 2 using uhci_hcd
[    1.572235] ata3.00: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.572257] ata3.01: SATA link down (SStatus 0 SControl 300)
[    1.580579] ata3.00: ATA-7: ST9160823ASG, 3.ADD, max UDMA/133
[    1.580586] ata3.00: 312581808 sectors, multi 8: LBA48 NCQ (depth 0/32)
[    1.596621] ata3.00: configured for UDMA/133
[    1.596841] scsi 2:0:0:0: Direct-Access     ATA      ST9160823ASG     3.AD PQ: 0 ANSI: 5
[    1.597045] sd 2:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    1.597065] sd 2:0:0:0: Attached scsi generic sg1 type 0
[    1.597133] sd 2:0:0:0: [sda] Write Protect is off
[    1.597139] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.597241] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.649028]  sda: sda1 sda2 sda3 < sda5 sda6 sda7 >
[    1.649695] sd 2:0:0:0: [sda] Attached SCSI disk
[    1.988227] usb 5-2: new low speed USB device number 3 using uhci_hcd
[    2.124227] ata4.01: failed to resume link (SControl 0)
[    2.124283] ata4.00: SATA link down (SStatus 0 SControl 300)
[    2.124308] ata4.01: SATA link down (SStatus 0 SControl 0)
[    2.126077] Freeing unused kernel memory: 988k freed
[    2.126363] Write protecting the kernel read-only data: 12288k
[    2.133073] Freeing unused kernel memory: 2032k freed
[    2.138290] Freeing unused kernel memory: 1388k freed
[    2.155187] udevd[94]: starting version 173
[    2.170411] input: Logitech Logitech USB Headset as /devices/pci0000:00/0000:00:1d.0/usb5/5-1/5-1:1.3/input/input4
[    2.170519] generic-usb 0003:046D:0A0B.0001: input,hidraw0: USB HID v1.00 Device [Logitech Logitech USB Headset] on usb-0000:00:1d.0-1/input3
[    2.197423] input: USB Mouse as /devices/pci0000:00/0000:00:1d.0/usb5/5-2/5-2:1.0/input/input5
[    2.197534] generic-usb 0003:0461:4D08.0002: input,hidraw1: USB HID v1.00 Mouse [USB Mouse] on usb-0000:00:1d.0-2/input0
[    2.197555] usbcore: registered new interface driver usbhid
[    2.197557] usbhid: USB HID core driver
[    2.219537] tg3.c:v3.119 (May 18, 2011)
[    2.219556] tg3 0000:09:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    2.219568] tg3 0000:09:00.0: setting latency timer to 64
[    2.255633] tg3 0000:09:00.0: eth0: Tigon3 [partno(BCM95755m) rev a002] (PCI Express) MAC address 00:1d:09:af:44:c9
[    2.255639] tg3 0000:09:00.0: eth0: attached PHY is 5755 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[0])
[    2.255642] tg3 0000:09:00.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    2.255645] tg3 0000:09:00.0: eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    2.270482] firewire_ohci 0000:03:01.4: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    2.328157] firewire_ohci: Added fw-ohci device 0000:03:01.4, OHCI v1.10, 8 IR + 8 IT contexts, quirks 0x10
[    2.396066] usb 7-1: new full speed USB device number 2 using uhci_hcd
[    2.547528] hub 7-1:1.0: USB hub found
[    2.549449] hub 7-1:1.0: 4 ports detected
[    2.825497] EXT4-fs (sda7): mounted filesystem with ordered data mode. Opts: (null)
[    2.828179] firewire_core: created device fw0: GUID 434fc0002438e5a1, S400
[    2.829474] usb 7-1.2: new full speed USB device number 3 using uhci_hcd
[    4.951675] udevd[339]: starting version 173
[    5.329506] Adding 7865340k swap on /dev/sda6.  Priority:-1 extents:1 across:7865340k 
[    6.520143] lp: driver loaded but no devices found
[    7.021422] lib80211: common routines for IEEE802.11 drivers
[    7.021426] lib80211_crypt: registered algorithm 'NULL'
[    7.054334] wmi: Mapper loaded
[    7.318407] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[    7.327198] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:2f/LNXVIDEO:00/input/input6
[    7.327260] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[    7.327296] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
[    7.332484] input: Dell WMI hotkeys as /devices/virtual/input/input7
[    7.812680] yenta_cardbus 0000:03:01.0: CardBus bridge found [1028:01fe]
[    7.812717] yenta_cardbus 0000:03:01.0: CardBus bridge to [bus 04-07]
[    7.812720] yenta_cardbus 0000:03:01.0:   bridge window [io  0x2000-0x20ff]
[    7.812726] yenta_cardbus 0000:03:01.0:   bridge window [io  0x2400-0x24ff]
[    7.812731] yenta_cardbus 0000:03:01.0:   bridge window [mem 0xf0c00000-0xf0ffffff]
[    7.812738] yenta_cardbus 0000:03:01.0:   bridge window [mem 0xf1000000-0xf13fffff]
[    7.812747] yenta_cardbus 0000:03:01.0: O2: enabling read prefetch/write burst. If you experience problems or performance issues, use the yenta_socket parameter 'o2_speedup=off'
[    7.940972] yenta_cardbus 0000:03:01.0: ISA IRQ mask 0x0cb8, PCI irq 19
[    7.940977] yenta_cardbus 0000:03:01.0: Socket status: 30000006
[    7.940981] pci_bus 0000:03: Raising subordinate bus# of parent bus (#03) from #04 to #07
[    7.940991] yenta_cardbus 0000:03:01.0: pcmcia: parent PCI bridge window: [io  0x2000-0x2fff]
[    7.940994] yenta_cardbus 0000:03:01.0: pcmcia: parent PCI bridge window: [mem 0xf1a00000-0xf1afffff]
[    7.940997] pcmcia_socket pcmcia_socket0: cs: memory probe 0xf1a00000-0xf1afffff: excluding 0xf1a00000-0xf1a0ffff 0xf1af0000-0xf1afffff
[    8.202975] wl: module license 'MIXED/Proprietary' taints kernel.
[    8.202981] Disabling lock debugging due to kernel taint
[    8.213706] wl 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    8.213716] wl 0000:0c:00.0: setting latency timer to 64
[    8.216174] malloc in abgphy done
[    8.219510] malloc in abgphy done
[    8.219618] eth%d: 5.100.82.38 driver failed with code 21
[    8.580230] input: DualPoint Stick as /devices/platform/i8042/serio1/input/input8
[    8.600569] input: AlpsPS/2 ALPS DualPoint TouchPad as /devices/platform/i8042/serio1/input/input9
[    8.716999] type=1400 audit(1331430033.371:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=650 comm="apparmor_parser"
[    8.717010] type=1400 audit(1331430033.371:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=674 comm="apparmor_parser"
[    8.717256] type=1400 audit(1331430033.371:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=650 comm="apparmor_parser"
[    8.717269] type=1400 audit(1331430033.371:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=674 comm="apparmor_parser"
[    8.717421] type=1400 audit(1331430033.371:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=650 comm="apparmor_parser"
[    8.717441] type=1400 audit(1331430033.371:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=674 comm="apparmor_parser"
[    9.193428] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xcffff 0xe0000-0xfffff
[    9.193485] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff: excluding 0xa0000000-0xa0ffffff
[    9.193539] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff: excluding 0x60000000-0x60ffffff
[    9.763296] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    9.763369] HDA Intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[    9.763403] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    9.908438] usbcore: registered new interface driver snd-usb-audio
[   10.020632] input: HDA Intel Mic at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   10.020758] input: HDA Intel HP Out at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   11.349698] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   11.349711] nvidia 0000:01:00.0: setting latency timer to 64
[   11.349717] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[   11.349878] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  280.13  Wed Jul 27 16:53:56 PDT 2011
[   12.148196] vesafb: mode is 1920x1200x32, linelength=7680, pages=0
[   12.148199] vesafb: scrolling: redraw
[   12.148202] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[   12.148210] mtrr: type mismatch for f3000000,1000000 old: write-back new: write-combining
[   12.148214] mtrr: type mismatch for f3000000,800000 old: write-back new: write-combining
[   12.148217] mtrr: type mismatch for f3000000,400000 old: write-back new: write-combining
[   12.148220] mtrr: type mismatch for f3000000,200000 old: write-back new: write-combining
[   12.148223] mtrr: type mismatch for f3000000,100000 old: write-back new: write-combining
[   12.148226] mtrr: type mismatch for f3000000,80000 old: write-back new: write-combining
[   12.148230] mtrr: type mismatch for f3000000,40000 old: write-back new: write-combining
[   12.148233] mtrr: type mismatch for f3000000,20000 old: write-back new: write-combining
[   12.148236] mtrr: type mismatch for f3000000,10000 old: write-back new: write-combining
[   12.148239] mtrr: type mismatch for f3000000,8000 old: write-back new: write-combining
[   12.148242] mtrr: type mismatch for f3000000,4000 old: write-back new: write-combining
[   12.148245] mtrr: type mismatch for f3000000,2000 old: write-back new: write-combining
[   12.148249] mtrr: type mismatch for f3000000,1000 old: write-back new: write-combining
[   12.149903] vesafb: framebuffer at 0xf3000000, mapped to 0xffffc90005800000, using 9024k, total 9024k
[   12.150124] Console: switching to colour frame buffer device 240x75
[   12.150166] fb0: VESA VGA frame buffer device
[   12.150506] EXT4-fs (sda7): re-mounted. Opts: errors=remount-ro
[   14.573165] type=1400 audit(1331430039.227:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=933 comm="apparmor_parser"
[   14.574325] type=1400 audit(1331430039.227:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=933 comm="apparmor_parser"
[   14.574499] type=1400 audit(1331430039.227:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=933 comm="apparmor_parser"
[   14.733791] ppdev: user-space parallel port driver
[   14.912418] type=1400 audit(1331430039.567:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm-guest-session-wrapper" pid=932 comm="apparmor_parser"
[   14.984705] type=1400 audit(1331430039.639:12): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=934 comm="apparmor_parser"
[   14.987815] type=1400 audit(1331430039.639:13): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-previewer" pid=934 comm="apparmor_parser"
[   14.989852] type=1400 audit(1331430039.643:14): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince-thumbnailer" pid=934 comm="apparmor_parser"
[   15.016837] type=1400 audit(1331430039.671:15): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=940 comm="apparmor_parser"
[   15.017206] type=1400 audit(1331430039.671:16): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/telepathy-*" pid=940 comm="apparmor_parser"
[   15.045100] type=1400 audit(1331430039.699:17): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=949 comm="apparmor_parser"
[   16.845967] tg3 0000:09:00.0: irq 46 for MSI/MSI-X
[   16.881415] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   17.171892] init: failsafe main process (879) killed by TERM signal
[   17.290939] init: apport pre-start process (1000) terminated with status 1
[   17.293500] init: apport post-stop process (1025) terminated with status 1
[   18.505521] tg3 0000:09:00.0: eth0: Link is up at 100 Mbps, full duplex
[   18.505525] tg3 0000:09:00.0: eth0: Flow control is on for TX and on for RX
[   18.506184] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   21.688726] Bluetooth: Core ver 2.16
[   21.688751] NET: Registered protocol family 31
[   21.688753] Bluetooth: HCI device and connection manager initialized
[   21.688755] Bluetooth: HCI socket layer initialized
[   21.688757] Bluetooth: L2CAP socket layer initialized
[   21.690180] Bluetooth: SCO socket layer initialized
[   22.043338] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   22.043341] Bluetooth: BNEP filters: protocol multicast
[   22.139172] Bluetooth: RFCOMM TTY layer initialized
[   22.139177] Bluetooth: RFCOMM socket layer initialized
[   22.139178] Bluetooth: RFCOMM ver 1.11
[   25.411761] EXT4-fs (sda7): re-mounted. Opts: errors=remount-ro,commit=0
[   26.152364] init: plymouth-stop pre-start process (1251) terminated with status 1
[   29.304054] eth0: no IPv6 routers present
[   32.029551] EXT4-fs (sda7): re-mounted. Opts: errors=remount-ro,commit=0
```

---

### Post by praseodym on 2012-03-11
Did you compile the driver or did you install it via "additional drivers"? The 4311 device normally works with the b43 driver, but the firmware is needed:
```

wget [http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz) 
sudo tar xvf 2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/
```

---

### Post by Sirkyuubi on 2012-03-11
I did not compile the drivers. The drivers came installed when I installed ubuntu.

---

### Post by Sirkyuubi on 2012-03-12
Does anyone have any ideas??

---

### Post by chili555 on 2012-03-12
Let's have a look at:```
lspci -nn | grep 0280
dmesg | grep wl
rfkill list all
```Thanks.

---

### Post by Sirkyuubi on 2012-03-12
lspci -nn | grep 0280

```

0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11a/b/g [14e4:4312] (rev 01)
```

dmesg | grep wl
```

[   17.007851] wl: module license 'MIXED/Proprietary' taints kernel.
[   17.154798] wl 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   17.154807] wl 0000:0c:00.0: setting latency timer to 64
```

rfkill list all
```

0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```

---

### Post by chili555 on 2012-03-12
The correct driver for this device is not *wl*, no matter what 'Wireless Drivers' thinks. It is *b43* and proprietary firmware. With the ethernet cable hooked up and connected, please do:```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install b43-fwcutter firmware-b43-installer
sudo reboot -n
```Any improvement?

---

### Post by Sirkyuubi on 2012-03-12
Yes! Its working. U rock!!

I feel free now!! *Dance Dance*

HAHA!

Now I wonder why network manager doesn't have wep 64/128 It only have wep 40/128.

---

### Post by chili555 on 2012-03-12
> Now I wonder why network manager doesn't have wep 64/128 It only have wep 40/128.They are one and the same: [http://en.wikipedia.org/wiki/Wired_Equivalent_Privacy](http://en.wikipedia.org/wiki/Wired_Equivalent_Privacy)> Standard **64-bit WEP** uses a **40 bit key** (also known as **WEP-40**), which is concatenated with a 24-bit initialization vector (IV) to form the RC4 key.WEP is quite insecure and I'd suggest changing the router to use WPA2 if possible.

Please use Thread Tools at the top and Mark Solved.

---

### Post by Sirkyuubi on 2012-03-12
Yes. I'm aware of the insecurities of wep. I'm just too lazy to go through and change all the computers, printers, and other devices to wpa2, but I think I'm going to have to do it anyways since the wep 40/128 is not taking my passkey. At 5 digits the continue button fills in, but my key is longer than 5 digits and the button greys out.

---

### Post by FerroPower on 2012-12-21
Thanks this thread helped me tooo (Dell Inspiron 1545)

---

### Post by ezeakeal on 2013-01-03
> **chili555 said:**
> The correct driver for this device is not *wl*, no matter what 'Wireless Drivers' thinks. It is *b43* and proprietary firmware. With the ethernet cable hooked up and connected, please do:```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install b43-fwcutter firmware-b43-installer
sudo reboot -n
```Any improvement?

Just want to thank chili555 for the help here. Worked for me recently in 12.10 where after some package upgrades caused an issue!

---

### Post by JaredChu on 2013-04-23
> **chili555 said:**
> The correct driver for this device is not *wl*, no matter what 'Wireless Drivers' thinks. It is *b43* and proprietary firmware. With the ethernet cable hooked up and connected, please do:```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install b43-fwcutter firmware-b43-installer
sudo reboot -n
```Any improvement?

It work! many thanks for your help. :guitar:

---

