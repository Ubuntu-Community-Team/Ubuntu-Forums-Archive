---
title: "Buffalo WLI-UC-GN usb Wifi on Toshiba dynabook with Jaunty"
date: 2009-09-21
forum: Networking &amp; Wireless
---

### Post by Eikokubyo on 2009-09-21
Hey all,
I just picked up this sexy usb wireless adapter, the Buffalo WLI-UC-GN. I really want to make it work on my dynabook 1610, but I don't know where to begin. I downloaded a community-maintained device driver which had the following instructions:

Build Instructions:  
====================

1> $tar -xvzf RT2870_Linux_STA_x.x.x.x.tgz
    go to "./RT2870_Linux_STA_x.x.x.x" directory.
    
2> In Makefile
	 set the "MODE = STA" in Makefile and chose the TARGET to Linux by set "TARGET = LINUX"
	 define the linux kernel source include file path LINUX_SRC
	 modify to meet your need.

3> In os/linux/config.mk 
	define the GCC and LD of the target machine
	define the compiler flags CFLAGS
	modify to meet your need.
	** Build for being controlled by NetworkManager or wpa_supplicant wext functions
	   Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y'.
	   => #>cd wpa_supplicant-x.x
	   => #>./wpa_supplicant -Dwext -ira0 -c wpa_supplicant.conf -d
	** Build for being controlled by WpaSupplicant with Ralink Driver
	   Please set 'HAS_WPA_SUPPLICANT=y' and 'HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n'.
	   => #>cd wpa_supplicant-0.5.7
	   => #>./wpa_supplicant -Dralink -ira0 -c wpa_supplicant.conf -d

4> $make
	# compile driver source code
	# To fix "error: too few arguments to function ¡¥iwe_stream_add_event"
	  => $patch -i os/linux/sta_ioctl.c.patch os/linux/sta_ioctl.c

5> $cp RT2870STA.dat  /etc/Wireless/RT2870STA/RT2870STA.dat
    
6> load driver, go to "os/linux/" directory.
    #[kernel 2.4]
    #    $/sbin/insmod rt2870sta.o
    #    $/sbin/ifconfig ra0 inet YOUR_IP up
        
    #[kernel 2.6]
    #    $/sbin/insmod rt2870sta.ko
    #    $/sbin/ifconfig ra0 inet YOUR_IP up

7> unload driver    
    $/sbin/ifconfig ra0 down
	$/sbin/rmmod rt2870sta

I don't understand #3, define the GCC and LD of the target machine, and the one that follows that, so I skipped it. Predictably, the process didn't get the adapter running.

I'm wondering if maybe somebody can help me understand the instructions above better, or if there is an easier way to make this adapter work, maybe you can point me towards it?

Thanks in advance for any help!

Cheers

---

### Post by grigjd3 on 2009-10-14
Isn't GCC typically the gnu c compiler?  It may well be asking for a path to the compiler.  I don't know what LD is.  Anyhow, just some thoughts.

---

### Post by chili555 on 2010-01-30
I believe rt2870sta is already built in to the kernel. It probably doesn't drive your device because it's possibly the wrong driver. Please let us see:```
lsusb
```Let's compare the device ID to the IDs recognized in rt2870sta, and other likely candidates. Here are the IDs:> #modinfo rt2870sta
filename:       /lib/modules/2.6.31-17-generic/kernel/drivers/staging/rt2870/rt2870sta.ko
version:        1.4.0.0
license:        GPL
description:    RT2870 Wireless Lan Linux Driver
author:         Paul Lin <paul_lin@ralinktech.com>
srcversion:     E5C45807808E721690B4101
alias:          usb:v[COLOR="Blue"]1737[/COLOR]p[COLOR="Blue"]0071[/COLOR]d*dc*dsc*dp*ic*isc*ip*
alias:          usb:v7392p7717d*dc*dsc*dp*ic*isc*ip*
--- snip ---We may be able to find a driver that actually works.

---

### Post by mas2ery on 2010-01-30
oh really? im sorry for my  haha  behavior, i just been a big fan of backtrack as i invested in devices  with atheros chipsets in the past just for its hype ,and  even though ive never been able to successfully crack any secured networks testing it, im always flabbergasted with the idea of it, and the backtrack 4 final must not use this said kernel that supports this rt3870L chip ?

---

### Post by mas2ery on 2010-01-30
maybe i also posted to wrong forum  ?  , but when i googled the issue , ubuntu was most of my results propbably cuz BT4 is based  on ubuntu and uduntu based on whatever

---

### Post by Eikokubyo on 2010-03-23
> **chili555 said:**
> I believe rt2870sta is already built in to the kernel. It probably doesn't drive your device because it's possibly the wrong driver. Please let us see:```
lsusb
```Let's compare the device ID to the IDs recognized in rt2870sta, and other likely candidates. Here are the IDs:We may be able to find a driver that actually works.

How should I go about searching for one? Run lsusb and then do something? Sorry - I'm just an adventurous desktop user, not a power user.

---

### Post by chili555 on 2010-03-23
> Run lsusb and then do something?Yes, post it. If you are really adventurous, google the usb.id and see which driver it needs. It may have conflicting drivers that need blacklisting. The usb.id will look something like 1737:0071, but maybe not exactly.

Post back if you get stuck.

---

### Post by Eikokubyo on 2010-03-23
> **chili555 said:**
> Yes, post it. If you are really adventurous, google the usb.id and see which driver it needs. It may have conflicting drivers that need blacklisting. The usb.id will look something like 1737:0071, but maybe not exactly.

Post back if you get stuck.

Dude, you are the coolest. I will check on it and post back. Thanks.

---

### Post by Eikokubyo on 2010-03-24
Alright, here is what lsusb gave me:

```
Bus 001 Device 003: ID 0411:015d MelCo., Inc. 
Bus 001 Device 002: ID 04bb:011c I-O Data Device, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

Looks like it isn't Ralink. I've never heard of MelCo before, though. I Googled the id but found mostly Ralink-related results, most of which I've already been through. Any ideas?

---

### Post by chili555 on 2010-03-24
Post #6 here says it works:  [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/441990](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/441990)

The poster uses 'vi' as a text editor, but we more commonly use gedit or nano. Otherwise, it looks pretty easy.

Please post back if you get stuck.

---

### Post by Eikokubyo on 2010-03-24
I got as far as the make install.
Here's what I got before getting booted out:

```
colquhoun@chiron:~/RT3070_LinuxSTA_V2.3.0.1_20100208$ sudo make
make -C tools
make[1]: Entering directory `/home/colquhoun/RT3070_LinuxSTA_V2.3.0.1_20100208/tools'
gcc -g bin2h.c -o bin2h
make[1]: Leaving directory `/home/colquhoun/RT3070_LinuxSTA_V2.3.0.1_20100208/tools'
/home/colquhoun/RT3070_LinuxSTA_V2.3.0.1_20100208/tools/bin2h
cp -f os/linux/Makefile.6 /home/colquhoun/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/Makefile
make -C /lib/modules/2.6.28-18-generic/build SUBDIRS=/home/colquhoun/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-18-generic'
  CC [M]  /home/colquhoun/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/../../common/crypt_md5.o
  CC [M]  /home/colquhoun/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/../../common/crypt_sha2.o
  CC [M]  /home/colquhoun/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/../../common/crypt_hmac.o
  CC [M]  /home/colquhoun/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/../../common/crypt_aes.o
  CC [M]  /home/colquhoun/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/../../common/crypt_arc4.o
  CC [M]  /home/colquhoun/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/../../common/mlme.o
  CC [M]  /home/colquhoun/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/../../common/cmm_wep.o
  CC [M]  /home/colquhoun/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/../../common/action.o
  CC [M]  /home/colquhoun/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/../../common/cmm_data.o
  CC [M]  /home/colquhoun/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/../../common/rtmp_init.o
/home/colquhoun/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/../../common/rtmp_init.c: In function &#8216;NICInitAsicFromEEPROM&#8217;:
/home/colquhoun/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/../../common/rtmp_init.c:2488: warning: unused variable &#8216;RFValue&#8217;
  CC [M]  /home/colquhoun/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/../../common/cmm_tkip.o
  CC [M]  /home/colquhoun/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/../../common/cmm_aes.o
  CC [M]  /home/colquhoun/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/../../common/cmm_sync.o
  CC [M]  /home/colquhoun/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/../../common/eeprom.o
  CC [M]  /home/colquhoun/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/../../common/cmm_sanity.o
  CC [M]  /home/colquhoun/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/../../common/cmm_info.o
  CC [M]  /home/colquhoun/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/../../common/cmm_cfg.o
  CC [M]  /home/colquhoun/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/../../common/cmm_wpa.o
  CC [M]  /home/colquhoun/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/../../common/dfs.o
  CC [M]  /home/colquhoun/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/../../common/spectrum.o
  CC [M]  /home/colquhoun/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/../../common/rtmp_timer.o
  CC [M]  /home/colquhoun/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/../../common/rt_channel.o
  CC [M]  /home/colquhoun/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/../../common/cmm_profile.o
  CC [M]  /home/colquhoun/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/../../common/cmm_asic.o
  CC [M]  /home/colquhoun/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/../../common/cmm_cmd.o
  CC [M]  /home/colquhoun/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/../../sta/assoc.o
/home/colquhoun/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/../../sta/assoc.c: In function &#8216;MlmeAssocReqAction&#8217;:
/home/colquhoun/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/../../sta/assoc.c:377: warning: unused variable &#8216;pInfo&#8217;
/home/colquhoun/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/../../sta/assoc.c:374: warning: unused variable &#8216;infoPos&#8217;
  CC [M]  /home/colquhoun/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/../../sta/auth.o
  CC [M]  /home/colquhoun/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/../../sta/auth_rsp.o
  CC [M]  /home/colquhoun/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/../../sta/sync.o
  CC [M]  /home/colquhoun/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/../../sta/sanity.o
  CC [M]  /home/colquhoun/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/../../sta/rtmp_data.o
  CC [M]  /home/colquhoun/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/../../sta/connect.o
  CC [M]  /home/colquhoun/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/../../sta/wpa.o
  CC [M]  /home/colquhoun/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/../../sta/sta_cfg.o
  CC [M]  /home/colquhoun/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/../../common/rtmp_init_inf.o
  CC [M]  /home/colquhoun/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/../../os/linux/rt_profile.o
  CC [M]  /home/colquhoun/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/../../os/linux/sta_ioctl.o
  CC [M]  /home/colquhoun/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/../../os/linux/rt_linux.o
/home/colquhoun/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/../../os/linux/rt_linux.c: In function &#8216;RtmpOSTaskAttach&#8217;:
/home/colquhoun/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/../../os/linux/rt_linux.c:1283: warning: passing argument 1 of &#8216;kthread_create&#8217; from incompatible pointer type
/home/colquhoun/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/../../os/linux/rt_linux.c:1283: warning: format not a string literal and no format arguments
  CC [M]  /home/colquhoun/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/../../os/linux/rt_main_dev.o
/home/colquhoun/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/../../os/linux/rt_main_dev.c: In function &#8216;RtmpOSIRQRequest&#8217;:
/home/colquhoun/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/../../os/linux/rt_main_dev.c:951: warning: unused variable &#8216;net_dev&#8217;
  CC [M]  /home/colquhoun/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/../../common/ba_action.o
  CC [M]  /home/colquhoun/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/../../common/cmm_mac_usb.o
  CC [M]  /home/colquhoun/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/../../common/rtusb_io.o
  CC [M]  /home/colquhoun/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/../../common/rtusb_bulk.o
  CC [M]  /home/colquhoun/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/../../common/rtusb_data.o
  CC [M]  /home/colquhoun/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/../../common/cmm_data_usb.o
  CC [M]  /home/colquhoun/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/../../common/ee_prom.o
  CC [M]  /home/colquhoun/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/../../common/ee_efuse.o
  CC [M]  /home/colquhoun/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/../../common/rtmp_mcu.o
  CC [M]  /home/colquhoun/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/../../chips/rt30xx.o
  CC [M]  /home/colquhoun/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/../../common/rt_rf.o
  CC [M]  /home/colquhoun/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/../../chips/rt3070.o
  CC [M]  /home/colquhoun/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/../../common/rtusb_dev_id.o
  CC [M]  /home/colquhoun/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/../../os/linux/rt_usb.o
  CC [M]  /home/colquhoun/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/../../os/linux/rt_usb_util.o
  CC [M]  /home/colquhoun/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/../../os/linux/usb_main_dev.o
/home/colquhoun/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/../../os/linux/usb_main_dev.c:1: error: expected declaration specifiers or &#8216;...&#8217; before string constant
/home/colquhoun/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/../../os/linux/usb_main_dev.c:1: warning: data definition has no type or storage class
/home/colquhoun/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/../../os/linux/usb_main_dev.c:1: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;MODULE_LICENSE&#8217;
/home/colquhoun/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/../../os/linux/usb_main_dev.c:1: warning: function declaration isn&#8217;t a prototype
make[2]: *** [/home/colquhoun/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux/../../os/linux/usb_main_dev.o] Error 1
make[1]: *** [_module_/home/colquhoun/RT3070_LinuxSTA_V2.3.0.1_20100208/os/linux] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-18-generic'
make: *** [LINUX] Error 2

```

I had tried installing using this driver previously but didn't get very far. That could be the reason for the "directory already exists" error. The others, I have no idea. You are a saint for helping me through this.

---

### Post by chili555 on 2010-03-24
> usb_main_dev.c:1: error: expected declaration specifiers or ‘...’ before string constantIsn't usb_main_dev.c the file you edited? This suggests there is an error somewhere. .c files are intolerant of errors in spacing, indentation, brackets, etc.

I think the poster from the bug report didn't quite describe it correctly; I think the relevant lines should be like:> // Following information will be show when you run 'modinfo'
// *** If you have a solution for the bug in current version of driver, please mail to me.
// Otherwise post to forum in ralinktech's web site([www.ralinktech.com](www.ralinktech.com)) and let all users help you. ***
MODULE_AUTHOR("Paul Lin <paul_lin@ralinktech.com>");
MODULE_DESCRIPTION("RT2870 Wireless Lan Linux Driver");
[COLOR="Blue"]MODULE_LICENSE("GPL");[/COLOR]
#ifdef CONFIG_STA_SUPPORT
#ifdef MODULE_VERSION
MODULE_VERSION(STA_DRIVER_VERSION);
#endif
#endif // CONFIG_STA_SUPPORT //Please place the line as shown above and remove it if it is elsewhere and do:```
sudo make clean
sudo make
```Proceed with the remainder of the process and post back.

With those changes, it makes for me with warnings but no errors.

---

### Post by Eikokubyo on 2010-03-24
Wow. Almost got it:

```
colquhoun@chiron:~/RT3070_LinuxSTA_V2.3.0.1_20100208$ sudo modprobe rt3070sta
FATAL: Error inserting rt3070sta (/lib/modules/2.6.28-18-generic/kernel/drivers/net/wireless/rt3070sta.ko): Unknown symbol in module, or unknown parameter (see dmesg)
colquhoun@chiron:~/RT3070_LinuxSTA_V2.3.0.1_20100208$ 

```

I didn't have the 2.6.31-20 kernel, only the 2.6.28-18 kernel (and two earlier ones before that) so I had to adjust the commands to install the .ko file in there. That may or may not be the problem. I ran dmesg and it ran longer than my buffer. I scanned through what survived, but couldn't figure out if any of the info was relevant. Here is what survived:
```
[    0.762156] ACPI: PCI Interrupt Link [LNKA] (IRQs *10)
[    0.762372] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 5 6 7 *11)
[    0.762679] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 6 7 *11)
[    0.762892] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 6 7 *11)
[    0.763104] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 *11)
[    0.763315] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 5 6 7 *11)
[    0.763528] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 6 7 *11)
[    0.763741] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 *11)
[    0.764056] ACPI: Power Resource [PFAN] (off)
[    0.764184] ACPI: WMI: Mapper loaded
[    0.764426] SCSI subsystem initialized
[    0.764488] libata version 3.00 loaded.
[    0.764556] usbcore: registered new interface driver usbfs
[    0.764581] usbcore: registered new interface driver hub
[    0.764623] usbcore: registered new device driver usb
[    0.764794] PCI: Using ACPI for IRQ routing
[    0.764813] pci 0000:00:1d.0: BAR 4: can't allocate resource
[    0.764819] pci 0000:00:1d.1: BAR 4: can't allocate resource
[    0.764915] Bluetooth: Core ver 2.13
[    0.764915] NET: Registered protocol family 31
[    0.764915] Bluetooth: HCI device and connection manager initialized
[    0.764915] Bluetooth: HCI socket layer initialized
[    0.764915] NET: Registered protocol family 8
[    0.764915] NET: Registered protocol family 20
[    0.764915] NetLabel: Initializing
[    0.764915] NetLabel:  domain hash size = 128
[    0.764915] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.764915] NetLabel:  unlabeled traffic allowed by default
[    0.764915] AppArmor: AppArmor Filesystem Enabled
[    0.764915] pnp: PnP ACPI init
[    0.764915] ACPI: bus type pnp registered
[    0.765847] pnp 00:00: mem resource (0x0-0x9ffff) overlaps 0000:00:02.1 BAR 0 (0x0-0x7ffffff), disabling
[    0.765854] pnp 00:00: mem resource (0xe0000-0xeffff) overlaps 0000:00:02.1 BAR 0 (0x0-0x7ffffff), disabling
[    0.765860] pnp 00:00: mem resource (0xf0000-0xfffff) overlaps 0000:00:02.1 BAR 0 (0x0-0x7ffffff), disabling
[    0.765866] pnp 00:00: mem resource (0x100000-0x4ef3ffff) overlaps 0000:00:02.1 BAR 0 (0x0-0x7ffffff), disabling
[    0.766577] pnp 00:08: io resource (0x10-0x1f) overlaps 0000:00:1d.0 BAR 4 (0x0-0x1f), disabling
[    0.766593] pnp 00:08: io resource (0x10-0x1f) overlaps 0000:00:1d.1 BAR 4 (0x0-0x1f), disabling
[    0.766689] pnp 00:08: io resource (0x62-0x62) overlaps 0000:00:1f.5 BAR 0 (0x0-0xff), disabling
[    0.766694] pnp 00:08: io resource (0x66-0x66) overlaps 0000:00:1f.5 BAR 0 (0x0-0xff), disabling
[    0.766699] pnp 00:08: io resource (0x80-0x80) overlaps 0000:00:1f.5 BAR 0 (0x0-0xff), disabling
[    0.766705] pnp 00:08: io resource (0x84-0x86) overlaps 0000:00:1f.5 BAR 0 (0x0-0xff), disabling
[    0.766710] pnp 00:08: io resource (0x88-0x88) overlaps 0000:00:1f.5 BAR 0 (0x0-0xff), disabling
[    0.766715] pnp 00:08: io resource (0x8c-0x8e) overlaps 0000:00:1f.5 BAR 0 (0x0-0xff), disabling
[    0.766721] pnp 00:08: io resource (0xe0-0xef) overlaps 0000:00:1f.5 BAR 0 (0x0-0xff), disabling
[    0.766729] pnp 00:08: io resource (0x10-0x1f) overlaps 0000:00:1f.5 BAR 0 (0x0-0xff), disabling
[    0.766734] pnp 00:08: io resource (0x24-0x25) overlaps 0000:00:1f.5 BAR 0 (0x0-0xff), disabling
[    0.766740] pnp 00:08: io resource (0x28-0x29) overlaps 0000:00:1f.5 BAR 0 (0x0-0xff), disabling
[    0.766745] pnp 00:08: io resource (0x2c-0x2d) overlaps 0000:00:1f.5 BAR 0 (0x0-0xff), disabling
[    0.766751] pnp 00:08: io resource (0x30-0x31) overlaps 0000:00:1f.5 BAR 0 (0x0-0xff), disabling
[    0.766756] pnp 00:08: io resource (0x34-0x35) overlaps 0000:00:1f.5 BAR 0 (0x0-0xff), disabling
[    0.766762] pnp 00:08: io resource (0x38-0x39) overlaps 0000:00:1f.5 BAR 0 (0x0-0xff), disabling
[    0.766768] pnp 00:08: io resource (0x3c-0x3d) overlaps 0000:00:1f.5 BAR 0 (0x0-0xff), disabling
[    0.766773] pnp 00:08: io resource (0x50-0x53) overlaps 0000:00:1f.5 BAR 0 (0x0-0xff), disabling
[    0.766779] pnp 00:08: io resource (0x63-0x63) overlaps 0000:00:1f.5 BAR 0 (0x0-0xff), disabling
[    0.766784] pnp 00:08: io resource (0x65-0x65) overlaps 0000:00:1f.5 BAR 0 (0x0-0xff), disabling
[    0.766790] pnp 00:08: io resource (0x72-0x77) overlaps 0000:00:1f.5 BAR 0 (0x0-0xff), disabling
[    0.766795] pnp 00:08: io resource (0x90-0x9f) overlaps 0000:00:1f.5 BAR 0 (0x0-0xff), disabling
[    0.766801] pnp 00:08: io resource (0xa4-0xa5) overlaps 0000:00:1f.5 BAR 0 (0x0-0xff), disabling
[    0.766807] pnp 00:08: io resource (0xa8-0xa9) overlaps 0000:00:1f.5 BAR 0 (0x0-0xff), disabling
[    0.766812] pnp 00:08: io resource (0xac-0xad) overlaps 0000:00:1f.5 BAR 0 (0x0-0xff), disabling
[    0.768010] pnp 00:08: io resource (0xb0-0xb5) overlaps 0000:00:1f.5 BAR 0 (0x0-0xff), disabling
[    0.768016] pnp 00:08: io resource (0xb8-0xb9) overlaps 0000:00:1f.5 BAR 0 (0x0-0xff), disabling
[    0.768021] pnp 00:08: io resource (0xbc-0xbd) overlaps 0000:00:1f.5 BAR 0 (0x0-0xff), disabling
[    0.768031] pnp 00:08: io resource (0x10-0x1f) overlaps 0000:00:1f.5 BAR 1 (0x0-0x3f), disabling
[    0.768036] pnp 00:08: io resource (0x24-0x25) overlaps 0000:00:1f.5 BAR 1 (0x0-0x3f), disabling
[    0.768042] pnp 00:08: io resource (0x28-0x29) overlaps 0000:00:1f.5 BAR 1 (0x0-0x3f), disabling
[    0.768047] pnp 00:08: io resource (0x2c-0x2d) overlaps 0000:00:1f.5 BAR 1 (0x0-0x3f), disabling
[    0.768053] pnp 00:08: io resource (0x30-0x31) overlaps 0000:00:1f.5 BAR 1 (0x0-0x3f), disabling
[    0.768059] pnp 00:08: io resource (0x34-0x35) overlaps 0000:00:1f.5 BAR 1 (0x0-0x3f), disabling
[    0.768064] pnp 00:08: io resource (0x38-0x39) overlaps 0000:00:1f.5 BAR 1 (0x0-0x3f), disabling
[    0.768070] pnp 00:08: io resource (0x3c-0x3d) overlaps 0000:00:1f.5 BAR 1 (0x0-0x3f), disabling
[    0.768081] pnp 00:08: io resource (0x62-0x62) overlaps 0000:00:1f.6 BAR 0 (0x0-0xff), disabling
[    0.768086] pnp 00:08: io resource (0x66-0x66) overlaps 0000:00:1f.6 BAR 0 (0x0-0xff), disabling
[    0.768092] pnp 00:08: io resource (0x80-0x80) overlaps 0000:00:1f.6 BAR 0 (0x0-0xff), disabling
[    0.768097] pnp 00:08: io resource (0x84-0x86) overlaps 0000:00:1f.6 BAR 0 (0x0-0xff), disabling
[    0.768102] pnp 00:08: io resource (0x88-0x88) overlaps 0000:00:1f.6 BAR 0 (0x0-0xff), disabling
[    0.768108] pnp 00:08: io resource (0x8c-0x8e) overlaps 0000:00:1f.6 BAR 0 (0x0-0xff), disabling
[    0.768113] pnp 00:08: io resource (0xe0-0xef) overlaps 0000:00:1f.6 BAR 0 (0x0-0xff), disabling
[    0.768121] pnp 00:08: io resource (0x10-0x1f) overlaps 0000:00:1f.6 BAR 0 (0x0-0xff), disabling
[    0.768127] pnp 00:08: io resource (0x24-0x25) overlaps 0000:00:1f.6 BAR 0 (0x0-0xff), disabling
[    0.768132] pnp 00:08: io resource (0x28-0x29) overlaps 0000:00:1f.6 BAR 0 (0x0-0xff), disabling
[    0.768138] pnp 00:08: io resource (0x2c-0x2d) overlaps 0000:00:1f.6 BAR 0 (0x0-0xff), disabling
[    0.768143] pnp 00:08: io resource (0x30-0x31) overlaps 0000:00:1f.6 BAR 0 (0x0-0xff), disabling
[    0.768149] pnp 00:08: io resource (0x34-0x35) overlaps 0000:00:1f.6 BAR 0 (0x0-0xff), disabling
[    0.768154] pnp 00:08: io resource (0x38-0x39) overlaps 0000:00:1f.6 BAR 0 (0x0-0xff), disabling
[    0.768160] pnp 00:08: io resource (0x3c-0x3d) overlaps 0000:00:1f.6 BAR 0 (0x0-0xff), disabling
[    0.768165] pnp 00:08: io resource (0x50-0x53) overlaps 0000:00:1f.6 BAR 0 (0x0-0xff), disabling
[    0.768171] pnp 00:08: io resource (0x63-0x63) overlaps 0000:00:1f.6 BAR 0 (0x0-0xff), disabling
[    0.768177] pnp 00:08: io resource (0x65-0x65) overlaps 0000:00:1f.6 BAR 0 (0x0-0xff), disabling
[    0.768182] pnp 00:08: io resource (0x72-0x77) overlaps 0000:00:1f.6 BAR 0 (0x0-0xff), disabling
[    0.768188] pnp 00:08: io resource (0x90-0x9f) overlaps 0000:00:1f.6 BAR 0 (0x0-0xff), disabling
[    0.768193] pnp 00:08: io resource (0xa4-0xa5) overlaps 0000:00:1f.6 BAR 0 (0x0-0xff), disabling
[    0.768199] pnp 00:08: io resource (0xa8-0xa9) overlaps 0000:00:1f.6 BAR 0 (0x0-0xff), disabling
[    0.768205] pnp 00:08: io resource (0xac-0xad) overlaps 0000:00:1f.6 BAR 0 (0x0-0xff), disabling
[    0.768210] pnp 00:08: io resource (0xb0-0xb5) overlaps 0000:00:1f.6 BAR 0 (0x0-0xff), disabling
[    0.768216] pnp 00:08: io resource (0xb8-0xb9) overlaps 0000:00:1f.6 BAR 0 (0x0-0xff), disabling
[    0.768221] pnp 00:08: io resource (0xbc-0xbd) overlaps 0000:00:1f.6 BAR 0 (0x0-0xff), disabling
[    0.768228] pnp 00:08: io resource (0x62-0x62) overlaps 0000:00:1f.6 BAR 1 (0x0-0x7f), disabling
[    0.768233] pnp 00:08: io resource (0x66-0x66) overlaps 0000:00:1f.6 BAR 1 (0x0-0x7f), disabling
[    0.768241] pnp 00:08: io resource (0x10-0x1f) overlaps 0000:00:1f.6 BAR 1 (0x0-0x7f), disabling
[    0.768247] pnp 00:08: io resource (0x24-0x25) overlaps 0000:00:1f.6 BAR 1 (0x0-0x7f), disabling
[    0.768253] pnp 00:08: io resource (0x28-0x29) overlaps 0000:00:1f.6 BAR 1 (0x0-0x7f), disabling
[    0.768258] pnp 00:08: io resource (0x2c-0x2d) overlaps 0000:00:1f.6 BAR 1 (0x0-0x7f), disabling
[    0.768264] pnp 00:08: io resource (0x30-0x31) overlaps 0000:00:1f.6 BAR 1 (0x0-0x7f), disabling
[    0.768269] pnp 00:08: io resource (0x34-0x35) overlaps 0000:00:1f.6 BAR 1 (0x0-0x7f), disabling
[    0.768275] pnp 00:08: io resource (0x38-0x39) overlaps 0000:00:1f.6 BAR 1 (0x0-0x7f), disabling
[    0.768280] pnp 00:08: io resource (0x3c-0x3d) overlaps 0000:00:1f.6 BAR 1 (0x0-0x7f), disabling
[    0.768286] pnp 00:08: io resource (0x50-0x53) overlaps 0000:00:1f.6 BAR 1 (0x0-0x7f), disabling
[    0.768292] pnp 00:08: io resource (0x63-0x63) overlaps 0000:00:1f.6 BAR 1 (0x0-0x7f), disabling
[    0.768297] pnp 00:08: io resource (0x65-0x65) overlaps 0000:00:1f.6 BAR 1 (0x0-0x7f), disabling
[    0.768303] pnp 00:08: io resource (0x72-0x77) overlaps 0000:00:1f.6 BAR 1 (0x0-0x7f), disabling
[    0.769043] pnp: PnP ACPI: found 9 devices
[    0.769047] ACPI: ACPI bus type pnp unregistered
[    0.769052] PnPBIOS: Disabled by ACPI PNP
[    0.769068] system 00:00: iomem range 0x4ef40000-0x4ef4ffff could not be reserved
[    0.769073] system 00:00: iomem range 0x4ef50000-0x4effffff has been reserved
[    0.769078] system 00:00: iomem range 0xfec10000-0xfec1ffff has been reserved
[    0.769083] system 00:00: iomem range 0xfeda0000-0xfedbffff has been reserved
[    0.769088] system 00:00: iomem range 0xffb80000-0xffbfffff has been reserved
[    0.769093] system 00:00: iomem range 0xfff00000-0xffffffff has been reserved
[    0.769106] system 00:08: ioport range 0x1e0-0x1e7 has been reserved
[    0.769110] system 00:08: ioport range 0x480-0x48f has been reserved
[    0.769115] system 00:08: ioport range 0x680-0x6ff has been reserved
[    0.769120] system 00:08: ioport range 0xd800-0xd87f has been reserved
[    0.769124] system 00:08: ioport range 0xd880-0xd89f has been reserved
[    0.769129] system 00:08: ioport range 0xd8a0-0xd8bf has been reserved
[    0.769133] system 00:08: ioport range 0xe000-0xe07f has been reserved
[    0.769138] system 00:08: ioport range 0xe080-0xe0ff has been reserved
[    0.769143] system 00:08: ioport range 0xe400-0xe47f has been reserved
[    0.769147] system 00:08: ioport range 0xe480-0xe4ff has been reserved
[    0.769152] system 00:08: ioport range 0xe800-0xe87f has been reserved
[    0.769157] system 00:08: ioport range 0xe880-0xe8ff has been reserved
[    0.769161] system 00:08: ioport range 0xec00-0xec7f has been reserved
[    0.769166] system 00:08: ioport range 0xec80-0xecff has been reserved
[    0.769171] system 00:08: ioport range 0xeeac-0xeeac has been reserved
[    0.769175] system 00:08: ioport range 0xeeb0-0xeebf has been reserved
[    0.769180] system 00:08: ioport range 0xeec0-0xeeff has been reserved
[    0.769191] system 00:08: ioport range 0x4d0-0x4d1 has been reserved
[    0.804049] pci 0000:01:0b.0: CardBus bridge, secondary bus 0000:02
[    0.804054] pci 0000:01:0b.0:   IO window: 0x00c000-0x00c0ff
[    0.804060] pci 0000:01:0b.0:   IO window: 0x00c400-0x00c4ff
[    0.804066] pci 0000:01:0b.0:   PREFETCH window: 0x58000000-0x5bffffff
[    0.804073] pci 0000:01:0b.0:   MEM window: 0x64000000-0x67ffffff
[    0.804079] pci 0000:01:0b.1: CardBus bridge, secondary bus 0000:04
[    0.804083] pci 0000:01:0b.1:   IO window: 0x00c800-0x00c8ff
[    0.804089] pci 0000:01:0b.1:   IO window: 0x00cc00-0x00ccff
[    0.804095] pci 0000:01:0b.1:   PREFETCH window: 0x5c000000-0x5fffffff
[    0.804102] pci 0000:01:0b.1:   MEM window: 0x68000000-0x6bffffff
[    0.804108] pci 0000:00:1e.0: PCI bridge, secondary bus 0000:01
[    0.804113] pci 0000:00:1e.0:   IO window: 0xc000-0xcfff
[    0.804120] pci 0000:00:1e.0:   MEM window: 0xcff00000-0xcfffffff
[    0.804126] pci 0000:00:1e.0:   PREFETCH window: 0x00000058000000-0x0000005fffffff
[    0.804142] pci 0000:00:1e.0: setting latency timer to 64
[    0.804152] pci 0000:01:0b.0: enabling device (0000 -> 0003)
[    0.804491] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[    0.804495] PCI: setting IRQ 11 as level-triggered
[    0.804501] pci 0000:01:0b.0: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    0.804515] pci 0000:01:0b.1: enabling device (0000 -> 0003)
[    0.804838] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[    0.804844] pci 0000:01:0b.1: PCI INT B -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    0.804854] bus: 00 index 0 io port: [0x00-0xffff]
[    0.804858] bus: 00 index 1 mmio: [0x000000-0xffffffff]
[    0.804862] bus: 01 index 0 io port: [0xc000-0xcfff]
[    0.804866] bus: 01 index 1 mmio: [0xcff00000-0xcfffffff]
[    0.804870] bus: 01 index 2 mmio: [0x58000000-0x5fffffff]
[    0.804873] bus: 01 index 3 io port: [0x00-0xffff]
[    0.804877] bus: 01 index 4 mmio: [0x000000-0xffffffff]
[    0.804881] bus: 02 index 0 io port: [0xc000-0xc0ff]
[    0.804884] bus: 02 index 1 io port: [0xc400-0xc4ff]
[    0.804888] bus: 02 index 2 mmio: [0x58000000-0x5bffffff]
[    0.804892] bus: 02 index 3 mmio: [0x64000000-0x67ffffff]
[    0.804896] bus: 04 index 0 io port: [0xc800-0xc8ff]
[    0.804900] bus: 04 index 1 io port: [0xcc00-0xccff]
[    0.804904] bus: 04 index 2 mmio: [0x5c000000-0x5fffffff]
[    0.804907] bus: 04 index 3 mmio: [0x68000000-0x6bffffff]
[    0.804921] NET: Registered protocol family 2
[    0.805088] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.805477] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.806535] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.807198] TCP: Hash tables configured (established 131072 bind 65536)
[    0.807203] TCP reno registered
[    0.807412] NET: Registered protocol family 1
[    0.807620] checking if image is initramfs...<7>Switched to high resolution mode on CPU 0
[    1.337278]  it is
[    1.908732] Freeing initrd memory: 7383k freed
[    1.908811] Simple Boot Flag at 0x7c set to 0x1
[    1.908860] cpufreq: No nForce2 chipset.
[    1.909096] audit: initializing netlink socket (disabled)
[    1.909143] type=2000 audit(1269466138.908:1): initialized
[    1.922480] highmem bounce pool size: 64 pages
[    1.922490] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    1.924707] VFS: Disk quotas dquot_6.5.1
[    1.924799] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.925809] fuse init (API version 7.10)
[    1.925945] msgmni has been set to 1718
[    1.926238] alg: No test for stdrng (krng)
[    1.926257] io scheduler noop registered
[    1.926260] io scheduler anticipatory registered
[    1.926263] io scheduler deadline registered
[    1.926287] io scheduler cfq registered (default)
[    1.926315] pci 0000:00:02.0: Boot video device
[    1.926389] pci 0000:01:08.0: Firmware left e100 interrupts enabled; disabling
[    1.929889] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.929905] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.930088] ACPI: AC Adapter [ADP1] (on-line)
[    1.930921] ACPI Warning (nspredef-0858): \_SB_.BAT1._BIF: Return Package type mismatch at index 12 - found Integer, expected String/Buffer [20080926]
[    1.931358] ACPI: Battery Slot [BAT1] (battery present)
[    1.931463] input: Power Button (FF) as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input0
[    1.931467] ACPI: Power Button (FF) [PWRF]
[    1.931545] input: Power Button (CM) as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1
[    1.931556] ACPI: Power Button (CM) [PWRB]
[    1.931631] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
[    1.931696] ACPI: Lid Switch [LID]
[    1.932199] fan PNP0C0B:00: registered as cooling_device0
[    1.932209] ACPI: Fan [FAN] (off)
[    1.932441] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[    1.932471] processor ACPI_CPU:00: registered as cooling_device1
[    1.935090] thermal LNXTHERM:01: registered as thermal_zone0
[    1.935690] ACPI: Thermal Zone [THRM] (26 C)
[    1.935755] isapnp: Scanning for PnP cards...
[    2.288375] isapnp: No Plug & Play device found
[    2.290378] Serial: 8250/16550 driver4 ports, IRQ sharing enabled
[    2.290917] serial 0000:00:1f.6: power state changed by ACPI to D0
[    2.290925] serial 0000:00:1f.6: enabling device (0000 -> 0001)
[    2.291274] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 11
[    2.291281] serial 0000:00:1f.6: PCI INT B -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
[    2.291289] serial 0000:00:1f.6: PCI INT B disabled
[    2.292356] brd: module loaded
[    2.292845] loop: module loaded
[    2.292964] Fixed MDIO Bus: probed
[    2.292974] PPP generic driver version 2.4.2
[    2.293062] input: Macintosh mouse button emulation as /devices/virtual/input/input3
[    2.293105] Driver 'sd' needs updating - please use bus_type methods
[    2.293120] Driver 'sr' needs updating - please use bus_type methods
[    2.293238] ata_piix 0000:00:1f.1: version 2.12
[    2.293249] ata_piix 0000:00:1f.1: PCI INT A -> Link[LNKC] -> GSI 11 (level, low) -> IRQ 11
[    2.293302] ata_piix 0000:00:1f.1: setting latency timer to 64
[    2.293406] scsi0 : ata_piix
[    2.293523] scsi1 : ata_piix
[    2.294045] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14
[    2.294050] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq 15
[    2.456564] ata1.00: ATA-6: HTS424040M9AT00, MA2OA71A, max UDMA/100
[    2.456569] ata1.00: 78140160 sectors, multi 0: LBA48 
[    2.472526] ata1.00: configured for UDMA/100
[    2.472561] ata2: port disabled. ignoring.
[    2.472752] scsi 0:0:0:0: Direct-Access     ATA      HTS424040M9AT00  MA2O PQ: 0 ANSI: 5
[    2.472902] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors: (40.0 GB/37.2 GiB)
[    2.472930] sd 0:0:0:0: [sda] Write Protect is off
[    2.472934] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.472975] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.473065] sd 0:0:0:0: [sda] 78140160 512-byte hardware sectors: (40.0 GB/37.2 GiB)
[    2.473088] sd 0:0:0:0: [sda] Write Protect is off
[    2.473092] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.473130] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.473136]  sda: sda1 sda2 < sda5 > sda3
[    2.535394] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.535460] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    2.536464] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    2.536488] ehci_hcd 0000:00:1d.7: enabling device (0000 -> 0002)
[    2.536844] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
[    2.536850] ehci_hcd 0000:00:1d.7: PCI INT D -> Link[LNKH] -> GSI 11 (level, low) -> IRQ 11
[    2.536883] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    2.536888] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    2.536997] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    2.540915] ehci_hcd 0000:00:1d.7: debug port 1
[    2.540923] ehci_hcd 0000:00:1d.7: cache line size of 32 is not supported
[    2.540935] ehci_hcd 0000:00:1d.7: irq 11, io mem 0x60080000
[    2.556031] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    2.556142] usb usb1: configuration #1 chosen from 1 choice
[    2.556189] hub 1-0:1.0: USB hub found
[    2.556203] hub 1-0:1.0: 6 ports detected
[    2.556370] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    2.556396] uhci_hcd: USB Universal Host Controller Interface driver
[    2.556762] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 10
[    2.556767] PCI: setting IRQ 10 as level-triggered
[    2.556773] uhci_hcd 0000:00:1d.0: PCI INT A -> Link[LNKA] -> GSI 10 (level, low) -> IRQ 10
[    2.556782] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    2.556786] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.556852] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    2.556877] uhci_hcd 0000:00:1d.0: irq 10, io base 0x000018c0
[    2.556987] usb usb2: configuration #1 chosen from 1 choice
[    2.557034] hub 2-0:1.0: USB hub found
[    2.557045] hub 2-0:1.0: 2 ports detected
[    2.557163] uhci_hcd 0000:00:1d.1: PCI INT B -> Link[LNKD] -> GSI 11 (level, low) -> IRQ 11
[    2.557171] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    2.557176] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.557245] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    2.557267] uhci_hcd 0000:00:1d.1: irq 11, io base 0x000018e0
[    2.557388] usb usb3: configuration #1 chosen from 1 choice
[    2.557439] hub 3-0:1.0: USB hub found
[    2.557448] hub 3-0:1.0: 2 ports detected
[    2.557641] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    2.562869] serio: i8042 KBD port at 0x60,0x64 irq 1
[    2.562878] serio: i8042 AUX port at 0x60,0x64 irq 12
[    2.563036] mice: PS/2 mouse device common for all mice
[    2.563315] rtc_cmos 00:07: RTC can wake from S4
[    2.563363] rtc_cmos 00:07: rtc core: registered rtc_cmos as rtc0
[    2.563382] rtc0: alarms up to one year, 114 bytes nvram
[    2.563478] device-mapper: uevent: version 1.0.3
[    2.563621] device-mapper: ioctl: 4.14.0-ioctl (2008-04-23) initialised: dm-devel@redhat.com
[    2.563691] device-mapper: multipath: version 1.0.5 loaded
[    2.563695] device-mapper: multipath round-robin: version 1.0.0 loaded
[    2.563809] EISA: Probing bus 0 at eisa.0
[    2.563817] Cannot allocate resource for EISA slot 1
[    2.563841] EISA: Detected 0 cards.
[    2.563935] cpuidle: using governor ladder
[    2.564050] cpuidle: using governor menu
[    2.564926] TCP cubic registered
[    2.565087] NET: Registered protocol family 10
[    2.565730] lo: Disabled Privacy Extensions
[    2.566227] NET: Registered protocol family 17
[    2.566257] Bluetooth: L2CAP ver 2.11
[    2.566260] Bluetooth: L2CAP socket layer initialized
[    2.566265] Bluetooth: SCO (Voice Link) ver 0.6
[    2.566267] Bluetooth: SCO socket layer initialized
[    2.566305] Bluetooth: RFCOMM socket layer initialized
[    2.566318] Bluetooth: RFCOMM TTY layer initialized
[    2.566321] Bluetooth: RFCOMM ver 1.10
[    2.566540] IO APIC resources could be not be allocated.
[    2.566591] Using IPI No-Shortcut mode
[    2.566693] registered taskstats version 1
[    2.566845]   Magic number: 2:938:500
[    2.566932] rtc_cmos 00:07: setting system clock to 2010-03-24 21:28:59 UTC (1269466139)
[    2.566937] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    2.566940] EDD information not available.
[    2.567348] Freeing unused kernel memory: 532k freed
[    2.567532] Write protecting the kernel text: 4120k
[    2.567597] Write protecting the kernel read-only data: 1524k
[    2.602176] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input4
[    3.095434] e100: Intel(R) PRO/100 Network Driver, 3.5.23-k6-NAPI
[    3.095440] e100: Copyright(c) 1999-2006 Intel Corporation
[    3.095914] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 11
[    3.095921] e100 0000:01:08.0: PCI INT A -> Link[LNKE] -> GSI 11 (level, low) -> IRQ 11
[    3.118393] e100 0000:01:08.0: PME# disabled
[    3.127052] e100: eth0: e100_probe: addr 0xcffff000, irq 11, MAC addr 00:0e:7b:f4:ad:75
[    3.455820] Marking TSC unstable due to TSC halts in idle
[    3.813279] PM: Starting manual resume from disk
[    3.813285] PM: Resume from partition 8:5
[    3.813287] PM: Checking hibernation image.
[    3.813505] PM: Resume from disk failed.
[    3.872739] kjournald starting.  Commit interval 5 seconds
[    3.872754] EXT3-fs: mounted filesystem with ordered data mode.
[   12.609493] udev: starting version 141
[   13.323599] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   13.538003] acpi device:0d: registered as cooling_device2
[   13.538390] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/device:0c/input/input5
[   13.542921] ACPI: Video Device [VGA] (multi-head: yes  rom: yes  post: no)
[   13.576392] intel_rng: FWH not detected
[   13.964558] Linux agpgart interface v0.103
[   13.973621] input: PC Speaker as /devices/platform/pcspkr/input/input6
[   14.033934] toshiba_acpi: Toshiba Laptop ACPI Extras version 0.19-dev-acpikeys
[   14.033940] toshiba_acpi:     HCI method: \_SB_.VALZ.GHCI
[   14.034840] toshiba_acpi: Toshiba hotkeys are sent as ACPI events
[   14.034845] toshiba_acpi: ktoshkeyd will check 2 times per second
[   14.035550] toshiba_acpi: Dropped 0 keys from the queue on startup
[   14.151082] agpgart-intel 0000:00:00.0: Intel 855GM Chipset
[   14.151901] agpgart-intel 0000:00:00.0: detected 16252K stolen memory
[   14.153888] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0xd8000000
[   14.232698] yenta_cardbus 0000:01:0b.0: CardBus bridge found [1179:0001]
[   14.247567] iTCO_vendor_support: vendor-support=0
[   14.251015] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.05
[   14.251186] iTCO_wdt: Found a ICH4-M TCO device (Version=1, TCOBASE=0xd860)
[   14.251294] iTCO_wdt: initialized. heartbeat=30 sec (nowayout=0)
[   14.338703] synaptics was reset on resume, see synaptics_resume_reset if you have trouble on resume
[   14.361982] yenta_cardbus 0000:01:0b.0: ISA IRQ mask 0x00b8, PCI irq 11
[   14.361989] yenta_cardbus 0000:01:0b.0: Socket status: 30000007
[   14.361998] yenta_cardbus 0000:01:0b.0: pcmcia: parent PCI bridge I/O window: 0xc000 - 0xcfff
[   14.362004] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc000-0xcfff: clean.
[   14.362346] yenta_cardbus 0000:01:0b.0: pcmcia: parent PCI bridge Memory window: 0xcff00000 - 0xcfffffff
[   14.362352] yenta_cardbus 0000:01:0b.0: pcmcia: parent PCI bridge Memory window: 0x58000000 - 0x5fffffff
[   14.362985] yenta_cardbus 0000:01:0b.1: CardBus bridge found [1179:0001]
[   14.493575] yenta_cardbus 0000:01:0b.1: ISA IRQ mask 0x00b8, PCI irq 11
[   14.493582] yenta_cardbus 0000:01:0b.1: Socket status: 30000007
[   14.493588] pci_bus 0000:01: Raising subordinate bus# of parent bus (#01) from #04 to #07
[   14.493600] yenta_cardbus 0000:01:0b.1: pcmcia: parent PCI bridge I/O window: 0xc000 - 0xcfff
[   14.493606] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xc000-0xcfff: clean.
[   14.493947] yenta_cardbus 0000:01:0b.1: pcmcia: parent PCI bridge Memory window: 0xcff00000 - 0xcfffffff
[   14.493953] yenta_cardbus 0000:01:0b.1: pcmcia: parent PCI bridge Memory window: 0x58000000 - 0x5fffffff
[   14.555198] Intel ICH 0000:00:1f.5: power state changed by ACPI to D0
[   14.555210] Intel ICH 0000:00:1f.5: enabling device (0000 -> 0003)
[   14.555222] Intel ICH 0000:00:1f.5: PCI INT B -> Link[LNKB] -> GSI 11 (level, low) -> IRQ 11
[   14.555304] Intel ICH 0000:00:1f.5: setting latency timer to 64
[   14.800124] Clocksource tsc unstable (delta = -228713095 ns)
[   15.066097] input: PS/2 Mouse as /devices/platform/i8042/serio1/input/input7
[   15.099716] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: clean.
[   15.100671] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: clean.
[   15.101051] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   15.101389] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   15.101920] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   15.107207] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio1/input/input8
[   15.140132] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x100-0x3af: clean.
[   15.141012] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x3e0-0x4ff: clean.
[   15.141392] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x820-0x8ff: clean.
[   15.141730] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xc00-0xcf7: clean.
[   15.142260] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xa00-0xaff: clean.
[   15.480048] intel8x0_measure_ac97_clock: measured 55286 usecs
[   15.480053] intel8x0: clocking to 48000
[   15.707993] lp: driver loaded but no devices found
[   15.804347] Adding 1461872k swap on /dev/sda5.  Priority:-1 extents:1 across:1461872k
[   16.358060] EXT3 FS on sda1, internal journal
[   17.424881] kjournald starting.  Commit interval 5 seconds
[   17.428287] EXT3 FS on sda3, internal journal
[   17.428295] EXT3-fs: mounted filesystem with ordered data mode.
[   17.874911] type=1505 audit(1269466154.805:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=1865
[   17.962567] type=1505 audit(1269466154.893:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=1869
[   17.962745] type=1505 audit(1269466154.893:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=1869
[   17.962819] type=1505 audit(1269466154.893:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=1869
[   17.962888] type=1505 audit(1269466154.893:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=1869
[   18.221341] type=1505 audit(1269466155.153:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=1874
[   18.221724] type=1505 audit(1269466155.153:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=1874
[   18.286264] type=1505 audit(1269466155.217:9): operation="profile_load" name="/usr/sbin/mysqld" name2="default" pid=1878
[   18.333616] type=1505 audit(1269466155.265:10): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=1882
[   25.207942] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   25.207947] Bluetooth: BNEP filters: protocol multicast
[   25.289627] Bridge firewalling registered
[   26.970463] ppdev: user-space parallel port driver
[   28.500373] [drm] Initialized drm 1.1.0 20060810
[   28.617981] pci 0000:00:02.0: power state changed by ACPI to D0
[   28.617999] pci 0000:00:02.0: PCI INT A -> Link[LNKA] -> GSI 10 (level, low) -> IRQ 10
[   28.618007] pci 0000:00:02.0: setting latency timer to 64
[   28.618315] [drm] Initialized i915 1.6.0 20080730 on minor 0
[   28.720124] [drm:i915_setparam] *ERROR* unknown parameter 4
[   28.720163] [drm:i915_getparam] *ERROR* Unknown parameter 6
[   30.612847] [drm:i915_getparam] *ERROR* Unknown parameter 6
[   31.085344] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   31.088138] e100: eth0: e100_watchdog: link up, 100Mbps, full-duplex
[   31.089074] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   41.740156] eth0: no IPv6 routers present
[  189.244207] usb 1-2: new high speed USB device using ehci_hcd and address 2
[  189.423532] usb 1-2: configuration #1 chosen from 1 choice
[  189.582347] Initializing USB Mass Storage driver...
[  189.585106] scsi2 : SCSI emulation for USB Mass Storage devices
[  189.585620] usbcore: registered new interface driver usb-storage
[  189.585630] USB Mass Storage support registered.
[  189.644464] usb-storage: device found at 2
[  189.644472] usb-storage: waiting for device to settle before scanning
[  194.644415] usb-storage: device scan complete
[  194.645131] scsi 2:0:0:0: Direct-Access     Generic  USB SD Reader    1.00 PQ: 0 ANSI: 0
[  194.645758] scsi 2:0:0:1: Direct-Access     Generic  USB CF Reader    1.01 PQ: 0 ANSI: 0
[  194.646383] scsi 2:0:0:2: Direct-Access     Generic  USB SM Reader    1.02 PQ: 0 ANSI: 0
[  194.647008] scsi 2:0:0:3: Direct-Access     Generic  USB MS Reader    1.03 PQ: 0 ANSI: 0
[  194.653550] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[  194.653711] sd 2:0:0:0: Attached scsi generic sg1 type 0
[  194.700190] sd 2:0:0:1: [sdc] Attached SCSI removable disk
[  194.700351] sd 2:0:0:1: Attached scsi generic sg2 type 0
[  194.701778] sd 2:0:0:2: [sdd] Attached SCSI removable disk
[  194.701896] sd 2:0:0:2: Attached scsi generic sg3 type 0
[  194.703160] sd 2:0:0:3: [sde] Attached SCSI removable disk
[  194.703279] sd 2:0:0:3: Attached scsi generic sg4 type 0
[  216.834013] sd 2:0:0:3: [sde] 7897088 512-byte hardware sectors: (4.04 GB/3.76 GiB)
[  216.834982] sd 2:0:0:3: [sde] Write Protect is off
[  216.834991] sd 2:0:0:3: [sde] Mode Sense: 03 00 00 00
[  216.834998] sd 2:0:0:3: [sde] Assuming drive cache: write through
[  216.835869] sd 2:0:0:3: [sde] 7897088 512-byte hardware sectors: (4.04 GB/3.76 GiB)
[  216.838757] sd 2:0:0:3: [sde] Write Protect is off
[  216.838765] sd 2:0:0:3: [sde] Mode Sense: 03 00 00 00
[  216.838772] sd 2:0:0:3: [sde] Assuming drive cache: write through
[  216.838783]  sde: sde1
[ 1332.359031] rt3070sta: module license 'unspecified' taints kernel.
[ 1332.359575] rt3070sta: Unknown symbol usb_alloc_urb
[ 1332.360059] rt3070sta: Unknown symbol usb_free_urb
[ 1332.361252] rt3070sta: Unknown symbol usb_register_driver
[ 1332.362256] rt3070sta: Unknown symbol usb_put_dev
[ 1332.362591] rt3070sta: Unknown symbol usb_get_dev
[ 1332.363286] rt3070sta: Unknown symbol usb_submit_urb
[ 1332.365071] rt3070sta: Unknown symbol usb_control_msg
[ 1332.366239] rt3070sta: Unknown symbol usb_deregister
[ 1332.367883] rt3070sta: Unknown symbol usb_kill_urb
[ 1332.368256] rt3070sta: Unknown symbol usb_buffer_free
[ 1332.369646] rt3070sta: Unknown symbol usb_buffer_alloc
[ 1366.728193] usb 1-1: new high speed USB device using ehci_hcd and address 3
[ 1366.926310] usb 1-1: configuration #1 chosen from 1 choice
[ 1371.911368] rt3070sta: Unknown symbol usb_alloc_urb
[ 1371.911806] rt3070sta: Unknown symbol usb_free_urb
[ 1371.913036] rt3070sta: Unknown symbol usb_register_driver
[ 1371.914041] rt3070sta: Unknown symbol usb_put_dev
[ 1371.914377] rt3070sta: Unknown symbol usb_get_dev
[ 1371.915073] rt3070sta: Unknown symbol usb_submit_urb
[ 1371.916888] rt3070sta: Unknown symbol usb_control_msg
[ 1371.918073] rt3070sta: Unknown symbol usb_deregister
[ 1371.919703] rt3070sta: Unknown symbol usb_kill_urb
[ 1371.920066] rt3070sta: Unknown symbol usb_buffer_free
[ 1371.921456] rt3070sta: Unknown symbol usb_buffer_alloc
[ 1377.047260] rt3070sta: Unknown symbol usb_alloc_urb
[ 1377.047699] rt3070sta: Unknown symbol usb_free_urb
[ 1377.048929] rt3070sta: Unknown symbol usb_register_driver
[ 1377.049934] rt3070sta: Unknown symbol usb_put_dev
[ 1377.050269] rt3070sta: Unknown symbol usb_get_dev
[ 1377.050965] rt3070sta: Unknown symbol usb_submit_urb
[ 1377.052783] rt3070sta: Unknown symbol usb_control_msg
[ 1377.053952] rt3070sta: Unknown symbol usb_deregister
[ 1377.055599] rt3070sta: Unknown symbol usb_kill_urb
[ 1377.055934] rt3070sta: Unknown symbol usb_buffer_free
[ 1377.057349] rt3070sta: Unknown symbol usb_buffer_alloc
[ 1378.569082] rt3070sta: Unknown symbol usb_alloc_urb
[ 1378.569520] rt3070sta: Unknown symbol usb_free_urb
[ 1378.570694] rt3070sta: Unknown symbol usb_register_driver
[ 1378.571724] rt3070sta: Unknown symbol usb_put_dev
[ 1378.572095] rt3070sta: Unknown symbol usb_get_dev
[ 1378.572791] rt3070sta: Unknown symbol usb_submit_urb
[ 1378.574554] rt3070sta: Unknown symbol usb_control_msg
[ 1378.575723] rt3070sta: Unknown symbol usb_deregister
[ 1378.577405] rt3070sta: Unknown symbol usb_kill_urb
[ 1378.577740] rt3070sta: Unknown symbol usb_buffer_free
[ 1378.579130] rt3070sta: Unknown symbol usb_buffer_alloc
colquhoun@chiron:~/RT3070_LinuxSTA_V2.3.0.1_20100208$ 

```

Sorry. Almost there. It almost seems like it wants me to edit out the "unknown symbol" in the .ko file, but I don't know what to look for.

---

### Post by chili555 on 2010-03-25
I was a bit afraid of that, I am sorry to say. I don't know what kernel this thing is written for, but the latest revision is not working well with 2.6.31-x.

Let's try a completely different approach. Let's see if we can get the built-in rt3070sta to recognize your device. Remove the device. First we must remove the not-working-unknown-symbol version:```
cd ~/RT3070_LinuxSTA_V2.3.0.1_20100208
sudo su
make uninstall
exit
```Now we are going to try to trick the built-in rt3070sta into seeing your device. Create two new files:```
sudo gedit /etc/udev/rules.d/network_drivers.rules
```Add one long line:```
ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="0411", ATTR{idProduct}=="015d", RUN+="/sbin/modprobe -qba rt3070sta"
```Proofread carefully, save and close gedit. Now do:```
sudo gedit /etc/modprobe.d/network_drivers.conf
```Add one long line:```
install rt3070sta /sbin/modprobe --ignore-install rt3070sta $CMDLINE_OPTS; /bin/echo "0411 015d" > /sys/bus/usb/drivers/rt2870/new_id

```Proofread carefully, save and close gedit. Reboot with the device inserted and report your success.

---

### Post by Eikokubyo on 2010-03-25
I did everything as written and it seems to have gone off without a hitch! Now when I click on the network applet in the tray, under my "Wired Networks," I find a heading for "Wireless Networks!"

Nothing under that, though, even with my wireless router running. I may have to do some manual configuration (connect to hidden wireless network doesn't seem to detect it; maybe I need to "create" it first). Anyway, I will have to look through the Ubuntu documentation for that; you have already done so much to help.

Thank you SO much. In English, what exactly did you do to get it running?

Cheers!

---

### Post by chili555 on 2010-03-25
> In English, what exactly did you do to get it running?I copied someone else's post and adapted it a bit. What a cheater!!

Please post back if it doesn't connect easily.

---

### Post by Eikokubyo on 2010-03-25
> **chili555 said:**
> I copied someone else's post and adapted it a bit. What a cheater!!

Please post back if it doesn't connect easily.

Hey man, good enough for me.
I'm going to have to put it up for the night - I'm in Japan and it's almost tomorrow here. Will post back if I can't get the thing connected. But you've gotten me much closer to that goal than I could've on my own. Thank you.

Cheers

---

### Post by Eikokubyo on 2010-03-26
Alright, fought with it all yesterday and this morning. Installed wicd, didn't find the network, reinstalled Network Manager, that still didn't work. When the wifi adapter is in, I get the "Wireless Networks" heading in the popup NM applet, when it's out, I only get the "Wired Networks" heading. So I know that the software can "see" the adapter. For some reason it just can't see the network. It's an Airport Express, so I went to my Mac and looked at the Network Settings there; everything seems to be in place, SSID, WPA Personal authentication and all that. I even doublechecked the hashed version of the password. It all matches up. The checkbox for "Enable Wireless" is checked too.

I'm going to keep scouring the internet. If I can fix it, I'll post the fix here. Thanks

---

### Post by Eikokubyo on 2010-07-04
Hey!
Just an update - I upgraded to Karmic last night and as of today the thing is working perfectly - I am typing this untethered. Thanks to chili555 for all your help. Even though I didn't get it to work until I upgraded, I learned alot in the process. Cheers mate.

---

