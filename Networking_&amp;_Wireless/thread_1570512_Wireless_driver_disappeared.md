---
title: "Wireless driver disappeared"
date: 2010-09-08
forum: Networking &amp; Wireless
---

### Post by szh on 2010-09-08
I am using Ubuntu 10.04. I installed the Broadcom STA Wireless driver from System -> Administration -> Hardware Drivers, and it seemed to work fine, but the next time I turned on my laptop, my wireless card wasn't recognized anymore! When I went to System -> Administration -> Hardware Drivers, the driver was gone from the list! Where did it go?
 
Update - Solution:
This is hardware issue, not a b43 issue.

---

### Post by chkneater on 2010-09-08
I'm sorry I can't answer your question directly, but I'm not understanding all the issues I've seen regarding Broadcom cards and 10.04.

Maybe try this, instead of using NM, the default manager, try Wicd.

sudo apt-get install Wicd

That is the code to use, WHEN you get internet service again. I have a strong feeling that it is the default network manager causing the issues.  Traditionally drivers weren't even needed for wireless cards.

Unpackage Wicd using Archive Manager, then look in the folder and there is a text named "Install" go figure.  Read that and do what it says.  Might help.

---

### Post by szh on 2010-09-08
> **chkneater said:**
> I'm sorry I can't answer your question directly, but I'm not understanding all the issues I've seen regarding Broadcom cards and 10.04.

Maybe try this, instead of using NM, the default manager, try Wicd.

sudo apt-get install Wicd

That is the code to use, WHEN you get internet service again. I have a strong feeling that it is the default network manager causing the issues.  Traditionally drivers weren't even needed for wireless cards.

Unpackage Wicd using Archive Manager, then look in the folder and there is a text named "Install" go figure.  Read that and do what it says.  Might help.

I tried that, but I got the same results.
I will clarify my question. I should have said:

My wireless card wasn't being recognized, so I installed the driver from System -> Administration -> Hardware Drivers, and it seemed to  work fine, but the next time I turned on my laptop, my wireless card  wasn't recognized anymore! When I went to System -> Administration  -> Hardware Drivers, the driver was gone from the list! Where did it  go?

---

### Post by utilitytrack on 2010-09-11
post here some diagnostic info:

```
$ uname -a
$ cat /proc/cmdline
$ lspci -nn | grep -E 'Ethernet|Network'
$ ps -f | grep -E -i 'supplicant|Netwo|nm-app|wicd'
# ifconfig -a
# lsmod
# cat /etc/network/interfaces
# ls -l /etc/modprobe.d/*

```

---

### Post by szh on 2010-09-12
Here are the results:
```
szh@noam-laptop:~$ uname -a
Linux noam-laptop 2.6.32-24-generic #42-Ubuntu SMP Fri Aug 20 14:24:04 UTC 2010 i686 GNU/Linux
szh@noam-laptop:~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-2.6.32-24-generic root=UUID=6a721f2f-5bfa-4e2a-96b2-4033e74838e4 ro quiet splash
szh@noam-laptop:~$ lspci -nn | grep -E 'Ethernet|Network'
00:14.0 Bridge [0680]: nVidia Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
szh@noam-laptop:~$ ps -f | grep -E -i 'supplicant|Netwo|nm-app|wicd'
szh       1830  1808  0 09:54 pts/0    00:00:00 grep --color=auto -E -i supplicant|Netwo|nm-app|wicd
szh@noam-laptop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1b:24:ea:82:70  
          inet addr:192.168.200.253  Bcast:192.168.200.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:24ff:feea:8270/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1056 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1026 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1010944 (1.0 MB)  TX bytes:195077 (195.0 KB)
          Interrupt:20 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:204 errors:0 dropped:0 overruns:0 frame:0
          TX packets:204 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:14928 (14.9 KB)  TX bytes:14928 (14.9 KB)

szh@noam-laptop:~$ lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_codec_si3054     3396  1 
snd_hda_codec_realtek   203310  1 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_hda_intel          21941  2 
snd_hda_codec          74201  3 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  4 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
nouveau               467048  2 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ttm                    49943  1 nouveau
drm_kms_helper         29297  1 nouveau
uvcvideo               56990  0 
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
joydev                  8708  0 
drm                   162409  4 nouveau,ttm,drm_kms_helper
snd                    54148  17 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                63245  0 
serio_raw               3978  0 
i2c_nforce2             5199  0 
agpgart                31724  2 ttm,drm
i2c_algo_bit            5028  1 nouveau
k8temp                  3024  0 
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
video                  17375  0 
output                  1871  1 video
lp                      7028  0 
parport                32635  2 ppdev,lp
usbhid                 36110  0 
hid                    67032  1 usbhid
sata_nv                19440  2 
forcedeth              49556  0 
pata_amd                8766  0 
szh@noam-laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback
szh@noam-laptop:~$ ls -l /etc/modprobe.d/*
-rw-r--r-- 1 root root 2386 2010-01-28 19:01 /etc/modprobe.d/alsa-base.conf
-rw-r--r-- 1 root root  325 2010-04-14 00:26 /etc/modprobe.d/blacklist-ath_pci.conf
-rw-r--r-- 1 root root 1603 2010-04-14 00:26 /etc/modprobe.d/blacklist.conf
-rw-r--r-- 1 root root  213 2010-04-14 00:26 /etc/modprobe.d/blacklist-firewire.conf
-rw-r--r-- 1 root root  660 2010-04-14 00:26 /etc/modprobe.d/blacklist-framebuffer.conf
-rw-r--r-- 1 root root  156 2010-01-28 19:01 /etc/modprobe.d/blacklist-modem.conf
lrwxrwxrwx 1 root root   41 2010-09-06 17:57 /etc/modprobe.d/blacklist-oss.conf -> /lib/linux-sound-base/noOSS.modprobe.conf
-rw-r--r-- 1 root root 1077 2010-04-14 00:26 /etc/modprobe.d/blacklist-watchdog.conf
-rw-r--r-- 1 root root  210 2010-02-10 18:21 /etc/modprobe.d/broadcom-sta-common.conf
-rw-r--r-- 1 root root   16 2010-01-06 03:12 /etc/modprobe.d/libpisock9.conf
```I have no idea what any of that means.

---

### Post by utilitytrack on 2010-09-12
> [FONT="Courier New"][I]szh@noam-laptop:~$ lspci -nn | grep -E 'Ethernet|Network'
00:14.0 Bridge [0680]: nVidia Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
[/I][/FONT]

Hmm. It's strange. Do you sure that your PC/laptop have a wireless adaptor? Please write what PC/laptop you use and post outputs of [FONT="Courier New"]$ lspci -nn[/FONT] (full output for clarity); [FONT="Courier New"]$ cat /etc/modprobe.d/broadcom-sta-common.conf; $ cat /etc/modprobe.d/blacklist.conf[/FONT]

Also I suggest to turn off IPv6 protocol because it don't use and make unnecessary complexity. For this add [FONT="Courier New"]ipv6.disable=1[/FONT] to the kernel command line in file [FONT="Courier New"]/etc/default/grub[/FONT] (the result looks like: [FONT="Courier New"]GRUB_CMDLINE_LINUX_DEFAULT="ipv6.disable=1"[/FONT])

Next apply changes of bootloader configuration:
```
# update-grub

```

and reboot.

---

### Post by szh on 2010-09-12
Results:
```

szh@noam-laptop:~$ lspci -nn
00:00.0 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02f0] (rev a2)
00:00.1 RAM memory [0500]: nVidia Corporation C51 Memory Controller 0 [10de:02fa] (rev a2)
00:00.2 RAM memory [0500]: nVidia Corporation C51 Memory Controller 1 [10de:02fe] (rev a2)
00:00.3 RAM memory [0500]: nVidia Corporation C51 Memory Controller 5 [10de:02f8] (rev a2)
00:00.4 RAM memory [0500]: nVidia Corporation C51 Memory Controller 4 [10de:02f9] (rev a2)
00:00.5 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02ff] (rev a2)
00:00.6 RAM memory [0500]: nVidia Corporation C51 Memory Controller 3 [10de:027f] (rev a2)
00:00.7 RAM memory [0500]: nVidia Corporation C51 Memory Controller 2 [10de:027e] (rev a2)
00:02.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fc] (rev a1)
00:03.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fd] (rev a1)
00:05.0 VGA compatible controller [0300]: nVidia Corporation C51 [Geforce Go 6150] [10de:0244] (rev a2)
00:09.0 RAM memory [0500]: nVidia Corporation MCP51 Host Bridge [10de:0270] (rev a2)
00:0a.0 ISA bridge [0601]: nVidia Corporation MCP51 LPC Bridge [10de:0260] (rev a3)
00:0a.1 SMBus [0c05]: nVidia Corporation MCP51 SMBus [10de:0264] (rev a3)
00:0a.3 Co-processor [0b40]: nVidia Corporation MCP51 PMU [10de:0271] (rev a3)
00:0b.0 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026d] (rev a3)
00:0b.1 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026e] (rev a3)
00:0d.0 IDE interface [0101]: nVidia Corporation MCP51 IDE [10de:0265] (rev f1)
00:0e.0 IDE interface [0101]: nVidia Corporation MCP51 Serial ATA Controller [10de:0266] (rev f1)
00:10.0 PCI bridge [0604]: nVidia Corporation MCP51 PCI Bridge [10de:026f] (rev a2)
00:10.1 Audio device [0403]: nVidia Corporation MCP51 High Definition Audio [10de:026c] (rev a2)
00:14.0 Bridge [0680]: nVidia Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
szh@noam-laptop:~$ cat /etc/modprobe.d/broadcom-sta-common.conf
# wl module from Broadcom conflicts with ssb
# We must blacklist the following modules:
blacklist b44
blacklist b43legacy
blacklist b43
blacklist ssb
install wl /sbin/modprobe --ignore-install wl $CMDLINE_OPTS
szh@noam-laptop:~$ cat /etc/modprobe.d/blacklist.conf
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
szh@noam-laptop:~$ 

```
Thanks.

---

### Post by utilitytrack on 2010-09-12
I asked:
> Please write what PC/laptop you use

You inconsiderate. Please specify exactly model.

---

### Post by MaindotC on 2010-09-12
I don't see a wireless card in this list:
> **szh said:**
> Results:
```

szh@noam-laptop:~$ lspci -nn
00:00.0 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02f0] (rev a2)
00:00.1 RAM memory [0500]: nVidia Corporation C51 Memory Controller 0 [10de:02fa] (rev a2)
00:00.2 RAM memory [0500]: nVidia Corporation C51 Memory Controller 1 [10de:02fe] (rev a2)
00:00.3 RAM memory [0500]: nVidia Corporation C51 Memory Controller 5 [10de:02f8] (rev a2)
00:00.4 RAM memory [0500]: nVidia Corporation C51 Memory Controller 4 [10de:02f9] (rev a2)
00:00.5 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02ff] (rev a2)
00:00.6 RAM memory [0500]: nVidia Corporation C51 Memory Controller 3 [10de:027f] (rev a2)
00:00.7 RAM memory [0500]: nVidia Corporation C51 Memory Controller 2 [10de:027e] (rev a2)
00:02.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fc] (rev a1)
00:03.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fd] (rev a1)
00:05.0 VGA compatible controller [0300]: nVidia Corporation C51 [Geforce Go 6150] [10de:0244] (rev a2)
00:09.0 RAM memory [0500]: nVidia Corporation MCP51 Host Bridge [10de:0270] (rev a2)
00:0a.0 ISA bridge [0601]: nVidia Corporation MCP51 LPC Bridge [10de:0260] (rev a3)
00:0a.1 SMBus [0c05]: nVidia Corporation MCP51 SMBus [10de:0264] (rev a3)
00:0a.3 Co-processor [0b40]: nVidia Corporation MCP51 PMU [10de:0271] (rev a3)
00:0b.0 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026d] (rev a3)
00:0b.1 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026e] (rev a3)
00:0d.0 IDE interface [0101]: nVidia Corporation MCP51 IDE [10de:0265] (rev f1)
00:0e.0 IDE interface [0101]: nVidia Corporation MCP51 Serial ATA Controller [10de:0266] (rev f1)
00:10.0 PCI bridge [0604]: nVidia Corporation MCP51 PCI Bridge [10de:026f] (rev a2)
00:10.1 Audio device [0403]: nVidia Corporation MCP51 High Definition Audio [10de:026c] (rev a2)
00:14.0 Bridge [0680]: nVidia Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]

```
Thanks.

It would look something like this:```
x@x:~$ lspci | grep Network
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
```

Is this a USB device?  If so please post the output of lsusb.

---

### Post by szh on 2010-09-13
I am using an HP Pavilion tx1000. The wireless card is NOT usb.

---

### Post by bkratz on 2010-09-13
> **szh said:**
> I am using an HP Pavilion tx1000. The wireless card is NOT usb.

I have seen a few laptops with the wireless card on an internal usb connection, so it is probably worth doing, just to check.

---

### Post by utilitytrack on 2010-09-13
to **szh**

please check BIOS settings that related with network subsystem;
and also give here output of 
```
# lsusb
```

---

### Post by szh on 2010-09-13
After installing the driver from HP with ndiswrapper and blacklisting other drivers:
```
szh@noam-laptop:~$ lspci | grep Network
03:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 02)
szh@noam-laptop:~$ lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 0eef:0001 D-WAV Scientific Co., Ltd eGalax TouchScreen
Bus 001 Device 004: ID 08ff:1600 AuthenTec, Inc. AES1600
Bus 001 Device 003: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera
Bus 001 Device 002: ID 04b4:6560 Cypress Semiconductor Corp. CY7C65640 USB-2.0 "TetraHub"
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
szh@noam-laptop:~$ 
```

---

### Post by utilitytrack on 2010-09-13
It's good that you set up wireless adapter with ndiswrapper.
Pay attention that for BCM4311 is possible to use open source b43 driver: see [http://linuxwireless.org/en/users/Drivers/b43]("http://linuxwireless.org/en/users/Drivers/b43")

Also: please again post output of
```
$ lspci -nn | grep -E 'Ethernet|Network'
```

---

### Post by szh on 2010-09-13
Here:
```
00:14.0 Bridge [0680]: nVidia Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
03:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 02)
```
I tried the b43 driver, but it didn't help me. Not sure why.

---

### Post by utilitytrack on 2010-09-13
Your wireless network work properly now?

Please specify address of page on wich you downloaded driver.
And also give output of
```
$ dmesg | grep -E -i 'ndis|wifi|wlan|4311'
```

---

### Post by szh on 2010-09-13
> **utilitytrack said:**
> Your wireless network work properly now?

Please specify address of page on wich you downloaded driver.
And also give output of
```
$ dmesg | grep -E -i 'ndis|wifi|wlan|4311'
```

Only my ethernet network is working. I downloaded the driver from [http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareIndex.jsp?lang=en&cc=us&prodNameId=3185027&prodTypeId=321957&prodSeriesId=3185026&swLang=8&taskId=135&swEnvOID=2100#11395]("http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareIndex.jsp?lang=en&cc=us&prodNameId=3185027&prodTypeId=321957&prodSeriesId=3185026&swLang=8&taskId=135&swEnvOID=2100#11395").
Results:
```
[   26.869267] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[   29.038383] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterInterruptEx'
[   29.038394] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[   29.038402] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[   29.038410] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[   29.038417] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[   29.038436] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterScatterGatherDma'
[   29.038446] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterInterruptEx'
[   29.038458] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSynchronizeWithInterruptEx'
[   29.038466] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[   29.038474] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[   29.038484] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMGetBusData'
[   29.038492] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMRegisterScatterGatherDma'
[   29.038502] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[   29.038514] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[   29.038521] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[   29.038529] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSetBusData'
[   29.038536] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[   29.038551] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[   29.038564] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[   29.038573] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[   29.038581] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[   29.038588] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[   29.038596] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[   29.038607] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[   29.038618] ndiswrapper (import:242): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[   29.038621] ndiswrapper (load_sys_files:206): couldn't prepare driver 'bcmwl6'
[   29.039164] ndiswrapper (load_wrap_driver:108): couldn't load driver bcmwl6; check system log for messages from 'loadndisdriver'
[   29.041047] usbcore: registered new interface driver ndiswrapper

```
In WICD preferences, wired interface is "eth0" and wireless interface is empty. "Create an ad-hoc network" is available.

---

### Post by beew on 2010-09-13
Looks like this may be a problem with HP, same thing happens in Windows apparently.

[http://www.xiirus.net/articles/article-hp-pavilion-tx1220us-disappearing-wireless-network-card-fix-t522o.aspx](http://www.xiirus.net/articles/article-hp-pavilion-tx1220us-disappearing-wireless-network-card-fix-t522o.aspx)

---

### Post by bkratz on 2010-09-13
I may be blind (been accused of that) but all I see on the page link is vista drivers. Ndiswrapper really like xp drivers.

---

### Post by MaindotC on 2010-09-13
> **szh said:**
> I tried the b43 driver, but it didn't help me. Not sure why.

Let's continue trying to support the b43 as that is the correct, native driver to use on your machine.  You said you tried b43 but it didn't help.  Can you describe that in detail?  For example, I realize that after a reboot your b43 driver disappeared and I'm sorry that happened.  Then you tried ndiswrapper, right?  And after that did you try the b43 again?  I don't know if you tried looking in Hardware Drivers or if that menu gave you the option to install the b43.  If you did, did you remove ndiswrapper before installing the b43?

---

### Post by utilitytrack on 2010-09-13
to **strAlan**

It seems on some hardware problem with wireless adapter. According to [http://www.xiirus.net/articles/article-hp-pavilion-tx1220us-disappearing-wireless-network-card-fix-t522o.aspx]("http://www.xiirus.net/articles/article-hp-pavilion-tx1220us-disappearing-wireless-network-card-fix-t522o.aspx") even BIOS upgrade did not help. Very bad, because as you understand, in such case any our manipulations with any drivers don't help.

to **szh**
May be is possible to exchange laptop for warranty? Also, if you have OtherOS installed, it's will be good if you test wireless with it. After this, we can make more definite conclusions.

---

### Post by szh on 2010-09-13
> **beew said:**
> Looks like this may be a problem with HP, same thing happens in Windows apparently.

[http://www.xiirus.net/articles/article-hp-pavilion-tx1220us-disappearing-wireless-network-card-fix-t522o.aspx](http://www.xiirus.net/articles/article-hp-pavilion-tx1220us-disappearing-wireless-network-card-fix-t522o.aspx)

I am pretty sure this is correct. Before I even had a wireless router, I remember seeing the option to use wireless - in Ubuntu. When I got a wireless router, the wireless option disappeared. I am also having the problem now when I boot windows.

---

### Post by utilitytrack on 2010-09-13
Please answer to my last post.

---

### Post by MaindotC on 2010-09-13
> **szh said:**
> I am pretty sure this is correct. Before I even had a wireless router, I remember seeing the option to use wireless - in Ubuntu. When I got a wireless router, the wireless option disappeared. I am also having the problem now when I boot windows.

Well, if that IS the case, and you can't exchange the laptop, I advise getting an Intel card - specifically the [4965]("http://www.intel.com/p/en_US/support/highlights/wireless/4965agn").  I don't know how complicated the HP laptops are to open up (my experience with an Acer was a nightmare the way they had that thing designed) but if HP has videos on their site for stuff like taking off the keyboard or installing more memory, like I have with my T60 on the Lenovo site, it should be a few screws and a quick swap of the wireless card.

I still can't get over the fact that his wireless was working until a reboot - that just shouldn't happen.

---

### Post by szh on 2010-09-13
I also tried updating the BIOS, but it did nothing. I probably won't buy from HP in the future.

---

### Post by utilitytrack on 2010-09-13
> **szh said:**
> I also tried updating the BIOS, but it did nothing. I probably won't buy from HP in the future.

Ok, it's for the future; but what you will doing now? May be simply return laptop to the shop? Or take him to the service?

---

### Post by szh on 2010-09-13
I don't really know. Any ideas?

---

### Post by utilitytrack on 2010-09-13
I already gave some ideas in my previous posts. You decide. Anyway we on this forum can't help to solve hardware problems, unfortunately.

---

### Post by szh on 2010-09-13
Okay. Thanks everyone for the help. I learned my lesson to buy computers with Ubuntu factory installed and to research a lot before buying a computer.

---

### Post by MaindotC on 2010-09-13
> **szh said:**
> I learned my lesson to buy computers with Ubuntu factory installed and to research a lot before buying a computer.

That isn't entirely what you should learn.  It doesn't hurt to buy a machine that is fully supported by Ubuntu from [ZaReason]("http://www.zareason.com/shop/home.php") or [system76]("http://system76.com/") but Linux should be able to run on anything that meets basic computing requirements.  I'm sure you want a machine that "just works" and I totally understand that, but please don't be afraid to rely on the support channels for troubleshooting issues such as here on UF, bug reports, driver developer forums, company support ([Broadcom does provide wireless drivers for Linux and you may be able to get customer support from them]("http://www.broadcom.com/support/ethernet_nic/")), irc, or mailing lists.

---

### Post by szh on 2010-09-13
I understand what you mean.

---

### Post by utilitytrack on 2010-09-13
If we turned this thread to advertizing, I also can say: pay attention on small Lenovo S10 netbooks, linux kernel has full support of their capabilities. Good luck!

---

### Post by szh on 2010-09-13
Thanks!

---

### Post by pastalavista on 2010-09-13
Look in Synaptic for 'b43-fwcutter' and if it's not installed, install it. If it is installed, look in /etc/modprobe.d and make sure it isn't blacklisted.

---

### Post by szh on 2010-09-13
> **pastalavista said:**
> Look in Synaptic for 'b43-fwcutter' and if it's not installed, install it. If it is installed, look in /etc/modprobe.d and make sure it isn't blacklisted.

I tried that already. Thanks for trying to help.

---

### Post by szh on 2010-09-13
Strangely, when I started up Windows, I got a notice "Installing Driver Software" again. Now, the wireless card works on Windows. I am not going to try it on Linux again, because the behavior is unpredictable and it seems to only work on some boots. Very annoying. I am not sure why it keeps reinstalling the driver by itself. Also, I installed the HP wireless assistant when I installed the driver, and that disappears and comes back with the driver.

---

### Post by szh on 2010-09-13
I rebooted, and now it's gone again.

---

### Post by MaindotC on 2010-09-13
Ok now I think it's a safe bet that either the BIOS interrupts are firing incorrectly or that wireless card has a problem.  Going back to one of your posts - lspci doesn't require anything to be installed in order to detect and identify hardware.  Look at the [unofficial wiki](http://en.wikipedia.org/wiki/Lspci) - it only needs libpci and libpci determines how lspci defines each hardware device, so installing the driver or ndiswrapper is irrelevant.  I just wanted you to know so in the future you are confident that you can rely on the itegrity of the output from lspci.

The coincidence that lspci didn't correctly recognize it before you installed ndiswrapper or whatever just reinforces that this is a hardware issue.  **Be sure to edit your first post to state "Update:" and the solution (or just that this is hardware issue not b43 issue) so other users do not have to read the entire thread.**

---

