---
title: "Ubuntu 9.10 X86_64 Dlink DWA-130-SW wireless can't be run"
date: 2010-03-28
forum: Networking &amp; Wireless
---

### Post by donya16 on 2010-03-28
My machine is hp pavilion p6310f PC with Athalon X64 QCore.
I can't get my wireless up.
Ubuntu : 9.10


1. Dlink DWA-130-sw wireless n 300 usb adapter

2.lsusb
   Bus 002 Device 003: ID 07d1:3300 D-Link System

ifconfig
eth0    Link encap:Ethernet  HWaddr 90:e6:ba:eb:53:ee  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::92e6:baff:feeb:53ee/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4504 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3978 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4730106 (4.7 MB)  TX bytes:812204 (812.2 KB)
          Interrupt:29 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)



iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


lsmod
Module                  Size  Used by
binfmt_misc            10220  1 
ppdev                   8232  0 
snd_hda_codec_realtek   277860  1 
iptable_filter          3872  0 
ip_tables              21200  1 iptable_filter
snd_hda_intel          31880  2 
snd_hda_codec          87584  2 snd_hda_codec_realtek,snd_hda_intel
lp                     11908  0 
snd_hwdep               9352  1 snd_hda_codec
snd_pcm_oss            44704  0 
x_tables               25832  1 ip_tables
parport                40528  2 ppdev,lp
snd_mixer_oss          18976  1 snd_pcm_oss
amd64_edac_mod         26688  0 
edac_core              48876  1 amd64_edac_mod
nvidia              10316904  36 
snd_pcm                93160  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           3460  0 
snd_seq_oss            33440  0 
snd_seq_midi            8192  0 
snd_rawmidi            27360  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
psmouse                57124  0 
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              26992  2 snd_pcm,snd_seq
serio_raw               6596  0 
i2c_nforce2             8168  0 
shpchp                 37756  0 
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ndiswrapper           245248  0 
snd                    77096  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               9088  1 snd
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm
usbhid                 43968  0 
usb_storage            65952  2 
ohci1394               33780  0 
ieee1394              100896  1 ohci1394
forcedeth              61292  0 
video                  23612  0 
output                  3680  1 video



lshw -C network
  *-network               
       description: Ethernet interface
       product: MCP77 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 90:e6:ba:eb:53:ee
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=192.168.1.100 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100MB/s
       resources: irq:29 memory:fce7c000-fce7cfff ioport:c880(size=8) memory:fce7e400-fce7e4ff memory:fce7e000-fce7e00



iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.



lsb_release -d
Description:    Ubuntu 9.10


uname -mr
2.6.31-14-generic x86_64


sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                                                                                                                       Ignoring unknown interface eth0=eth0.




Things I've tried :
1) use Synaptic to install ndiswrapper and ndisgtk 
 2) blacklist all linux native drivers bmc43xx, b43, b43legacy, ssb 
 3) use ndisgtk to install driver from CDROM from folder Win7x64
 4) however, I always receive the message "Unable to see if hardware is present". Then after the installation, if I click on "Configuration network", the message "could not find a network configuration tool" appears. 
 5) Run 
 $ sudo depmod -a 
 $ sudo modprobe ndiswrapper

---

### Post by chili555 on 2010-03-28
> 3) use ndisgtk to install driver from CDROM from folder [COLOR="Red"]Win7[/COLOR]x64If you read:```
man ndiswrapper-1.9
```It says:> NAME
       ndiswrapper  -  Linux kernel module and user space tool to load and run Windows XP drivers for wireless cardsHave you removed the Windows 7 .inf and .sys files and tried the XP or 2000 files?

Even in Ubuntu Land, we are betrayed again by 7!

---

### Post by donya16 on 2010-03-28
Hi Chilli555,
Thanks for the reply.
I tried the drivers from WinXP and Win2k folder but no luck.
It seems that somehow these drivers can't be loaded..
Following is /var/log/messges

> Mar 28 12:58:18  kernel: [  583.704890] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
Mar 28 12:58:18  kernel: [  583.860078] usb 2-3: reset high speed USB device using ehci_hcd and address 3
**Mar 28 12:58:18  loadndisdriver: loadndisdriver: load_driver(358): couldn't load driver net8192su**
Mar 28 12:58:18  kernel: [  584.020880] usbcore: registered new interface driver ndiswrapperAlso what is curious is the fact that I can't even see wireless interface in my ifconfig or iwconfig
> ifconfig
eth0      Link encap:Ethernet  HWaddr 90:e6:ba:eb:53:ee  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::92e6:baff:feeb:53ee/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1082 errors:0 dropped:0 overruns:0 frame:0
          TX packets:932 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1066714 (1.0 MB)  TX bytes:179874 (179.8 KB)
          Interrupt:29 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B> 

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.
Do I need to something special for wireless interface to show up here?

Does the procedure that I posted at the end of first post make sense?

Thanks again for all your help.

---

### Post by chili555 on 2010-03-28
What does this tell us?```
ndiswrapper -l
```Did you transfer the .inf file to a folder in your user directory? Were there other files on the CD? .sys files, perhaps?

I'd suggest you drag and drop the files on the CD, including the XP files, to a new folder called, for example, ndis8192. You should have the folders from the CD in your ndis8192 folder, XP2000_32, XP2000_64, Vista, Win7, etc. Remove the not-working .inf file:```
sudo ndiswrapper -e net8192su
```Now use ndisgtk to load the XP_64 version of net8192su.inf, making sure that the .sys file(s) are in the same folder. 

Now does it say the hardware is present? Is a wireless interface, wlan0, perhaps, created?> Does the procedure that I posted at the end of first post make sense?Perfect, until you loaded Windows 7 files; as far as I know, ndiswrapper wants XP or 2000. This could be an exception. We will soon find out!

---

### Post by donya16 on 2010-03-28
> $ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
net8192su : driver installed
    device (07D1:3300) presentYes I transferred files from CD onto a folder in home directory.
> 
cd Driver/
~/Driver$ ll
total 28
drwxr-xr-x 2  4096 2009-12-09 22:15 VistaX64
drwxr-xr-x 2  4096 2009-12-09 22:17 VistaX86
drwxr-xr-x 2  4096 2009-12-09 22:18 Win2K
drwxr-xr-x 2  4096 2009-12-09 22:18 Win7X64
drwxr-xr-x 2  4096 2009-12-09 22:18 Win7X86
drwxr-xr-x 2  4096 2009-12-09 22:18 WinX64
drwxr-xr-x 2  4096 2009-12-09 22:18 WinXP2K

~/Driver$ ll WinXP2K/
total 592
-rw-r--r-- 1    7597 2009-12-09 19:47 net8192su.cat
-rw-r--r-- 1    7340 2009-12-09 19:47 net8192su.inf
-rw-r--r-- 1 588032 2009-12-09 19:47 rtl8192su.sys

I followed the instructions that you suggested by still I can't see any wireless interface created.

> $ ifconfig
eth0      Link encap:Ethernet  HWaddr 90:e6:ba:eb:53:ee  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::92e6:baff:feeb:53ee/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:566 errors:0 dropped:0 overruns:0 frame:0
          TX packets:604 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:555958 (555.9 KB)  TX bytes:80125 (80.1 KB)
          Interrupt:29 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)
> $ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

---

### Post by chili555 on 2010-03-28
Now it sees the device as present, so we are closer. What does /var/log/messages say after Mar 28 12:58:18 kernel: [ 584.020880]?

---

### Post by donya16 on 2010-03-28
It didn't say anything after  Mar 28 12:58:18 kernel: [ 584.020880]..
I rebooted the pc in the hope of that reboot might do some magic..
btw, I just noticed something in dmesg

> 
[    9.670712] **ndiswrapper (check_nt_hdr:150): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B**
[    9.670716] ndiswrapper (load_sys_files:206): couldn't prepare driver 'net8192su'
[    9.671135] ndiswrapper (load_wrap_driver:108): couldn't load driver net8192su; check system log for messages from 'loadndisdriver'
[    9.671170] usbcore: registered new interface driver ndiswrapper

---

### Post by chili555 on 2010-03-28
> [ 9.671135] ndiswrapper (load_wrap_driver:10: couldn't load driver net8192su; check system log for messages from 'loadndisdriver'And what did it say?```
sudo cat /var/log/syslog | grep ndis
```

---

### Post by donya16 on 2010-03-28
the syslog says essentially the same thing

> kernel: [    9.670712] ndiswrapper (check_nt_hdr:150): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
Mar 28 14:57:43  kernel: [    9.670716] ndiswrapper (load_sys_files:206): couldn't prepare driver 'net8192su'
Mar 28 14:57:43  kernel: [    9.671135] ndiswrapper (load_wrap_driver:108): couldn't load driver net8192su; check system log for messages from 'loadndisdriver'
Mar 28 14:57:43  kernel: [    9.671170] usbcore: registered new interface driver ndiswrapper

---

### Post by chili555 on 2010-03-28
> kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010BAre you quite sure you loaded the *WinX64* drivers? This suggests that you did not:> ~/Driver$ ll [COLOR="Red"]WinXP2K[/COLOR]/
total 592
-rw-r--r-- 1 7597 2009-12-09 19:47 net8192su.cat
-rw-r--r-- 1 7340 2009-12-09 19:47 net8192su.inf
-rw-r--r-- 1 588032 2009-12-09 19:47 rtl8192su.sysPlease check and redo if needed.

---

### Post by donya16 on 2010-03-28
I was loading from WinXP2k folder.
When I loaded from WinX64 folder, the ndisgtk crashed although the driver loaded this time.
Following is what I see in /var/log/messages

> Mar 28 16:42:09  kernel: [ 6274.732728] usbcore: deregistering interface driver ndiswrapper
Mar 28 16:42:09  kernel: [ 6274.734654] ndiswrapper (ntoskernel_exit:2677): object ffff88017a9f9230(2) was not freed, freeing it now
Mar 28 16:42:09  kernel: [ 6274.754017] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
Mar 28 16:42:09  kernel: [ 6274.911328] usb 2-3: reset high speed USB device using ehci_hcd and address 3
Mar 28 16:42:09  kernel: [ 6275.070930] ndiswrapper (link_pe_images:575): fixing KI_USER_SHARED_DATA address in the driver
Mar 28 16:42:09  kernel:** [ 6275.075645] ndiswrapper: driver net8192su (D-Link Corporation,08/05/2009,1084.12.0805.2009) loaded**
Mar 28 16:42:09  kernel: [ 6275.079603] PGD 17b5ea067 PUD 193cde067 PMD 0 
Mar 28 16:42:09  kernel: [ 6275.079627] CPU 3 
Mar 28 16:42:09  kernel: [ 6275.079631] Modules linked in: ndiswrapper(+) binfmt_misc ppdev snd_hda_codec_realtek snd_hda_intel snd_hda_codec nvidia(P) snd_hwdep snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss psmouse snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer serio_raw snd_seq_device iptable_filter shpchp i2c_nforce2 snd ip_tables amd64_edac_mod soundcore edac_core lp parport snd_page_alloc x_tables usbhid usb_storage ohci1394 ieee1394 video output forcedeth [last unloaded: ndiswrapper]
Mar 28 16:42:09  kernel: [ 6275.079703] Pid: 2964, comm: modprobe Tainted: P           2.6.31-14-generic #48-Ubuntu AY018AA-ABA p6310f
Mar 28 16:42:09  kernel: [ 6275.079710] RIP: 0010:[<ffffffffa0c7c2cb>]  [<ffffffffa0c7c2cb>] USBD_InterfaceIsDeviceHighSpeed+0xb/0x20 [ndiswrapper]
Mar 28 16:42:09  kernel: [ 6275.079757] RSP: 0018:ffff880166833800  EFLAGS: 00010246
Mar 28 16:42:09  kernel: [ 6275.079762] RAX: 0000000000000000 RBX: ffffc9000859a000 RCX: ffff88017b495a00
Mar 28 16:42:09  kernel: [ 6275.079768] RDX: 000000000000000f RSI: 0000000000000000 RDI: ffffc9000859a000
Mar 28 16:42:09  kernel: [ 6275.079773] RBP: ffff880166833800 R08: 0000000000000000 R09: ffff880166ac2400
Mar 28 16:42:09  kernel: [ 6275.079778] R10: ffffffffa0c6e8d0 R11: 0000000000000000 R12: ffff880166ac2400
Mar 28 16:42:09  kernel: [ 6275.079784] R13: ffff880166833910 R14: 0000000000000000 R15: 0000000000000001
Mar 28 16:42:09  kernel: [ 6275.079790] FS:  00007fdf8e0ed6f0(0000) GS:ffff88002808e000(0000) knlGS:0000000000000000
Mar 28 16:42:09  kernel: [ 6275.079796] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
Mar 28 16:42:09  kernel: [ 6275.079802] CR2: 000000000000001c CR3: 000000017093c000 CR4: 00000000000006e0
Mar 28 16:42:09  kernel: [ 6275.079807] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Mar 28 16:42:09  kernel: [ 6275.079813] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Mar 28 16:42:09  kernel: [ 6275.079819] Process modprobe (pid: 2964, threadinfo ffff880166832000, task ffff880187cc0000)
Mar 28 16:42:09  kernel: [ 6275.079827]  0000000000000000 ffffc900084cd699 0000000000000001 ffffc9000859a000
Mar 28 16:42:09  kernel: [ 6275.079835] <0> 0000000000000000 ffffc9000859a000 0000000000000012 ffff880166815580
Mar 28 16:42:09  kernel: [ 6275.079844] <0> 0000000100000000 ffff880166833848 ffff880166833848 ffff880166833868
Mar 28 16:42:09  kernel: [ 6275.079891]  [<ffffffffa0c6d86b>] ? ExFreePool+0xb/0x10 [ndiswrapper]
Mar 28 16:42:09  kernel: [ 6275.079930]  [<ffffffffa0c7c440>] ? USBD_InterfaceReference+0x0/0x20 [ndiswrapper]
Mar 28 16:42:09  kernel: [ 6275.079969]  [<ffffffffa0c7c420>] ? USBD_InterfaceDereference+0x0/0x20 [ndiswrapper]
Mar 28 16:42:09  kernel: [ 6275.080008]  [<ffffffffa0c7c280>] ? USBD_InterfaceGetUSBDIVersion+0x0/0x40 [ndiswrapper]
Mar 28 16:42:09  kernel: [ 6275.080047]  [<ffffffffa0c7c950>] ? USBD_InterfaceQueryBusTime+0x0/0x30 [ndiswrapper]
Mar 28 16:42:09  kernel: [ 6275.080086]  [<ffffffffa0c7c3f0>] ? USBD_InterfaceSubmitIsoOutUrb+0x0/0x30 [ndiswrapper]
Mar 28 16:42:09  kernel: [ 6275.080125]  [<ffffffffa0c7c3c0>] ? USBD_InterfaceQueryBusInformation+0x0/0x30 [ndiswrapper]
Mar 28 16:42:09  kernel: [ 6275.080163]  [<ffffffffa0c7c2c0>] ? USBD_InterfaceIsDeviceHighSpeed+0x0/0x20 [ndiswrapper]
Mar 28 16:42:09  kernel: [ 6275.080204]  [<ffffffffa0c7a03a>] ? mp_init+0x6a/0x200 [ndiswrapper]
Mar 28 16:42:09  kernel: [ 6275.080240]  [<ffffffffa0c720d9>] ? IofCompleteRequest+0x59/0x1c0 [ndiswrapper]
Mar 28 16:42:09  kernel: [ 6275.080278]  [<ffffffffa0c7456d>] ? pdoDispatchPnp+0x3d/0xf0 [ndiswrapper]
Mar 28 16:42:09  kernel: [ 6275.080317]  [<ffffffffa0c7b117>] ? ndis_start_device+0x27/0x860 [ndiswrapper]
Mar 28 16:42:09  kernel: [ 6275.080353]  [<ffffffffa0c71705>] ? IofCallDriver+0x65/0xc0 [ndiswrapper]
Mar 28 16:42:09  kernel: [ 6275.080366]  [<ffffffff815295d4>] ? _spin_unlock_bh+0x14/0x20
Mar 28 16:42:09  kernel: [ 6275.080402]  [<ffffffffa0c71690>] ? IoReleaseCancelSpinLock+0x10/0x20 [ndiswrapper]
Mar 28 16:42:09  kernel: [ 6275.080439]  [<ffffffffa0c716d9>] ? IofCallDriver+0x39/0xc0 [ndiswrapper]
Mar 28 16:42:09  kernel: [ 6275.080475]  [<ffffffffa0c71c61>] ? IoSyncForwardIrp+0x91/0xd0 [ndiswrapper]
Mar 28 16:42:09  kernel: [ 6275.080514]  [<ffffffffa0c7b9f3>] ? NdisDispatchPnp+0xa3/0x150 [ndiswrapper]
Mar 28 16:42:09  kernel: [ 6275.080553]  [<ffffffffa0c7dec7>] ? win2lin2+0xe/0x11 [ndiswrapper]
Mar 28 16:42:09  kernel: [ 6275.080589]  [<ffffffffa0c71690>] ? IoReleaseCancelSpinLock+0x10/0x20 [ndiswrapper]
Mar 28 16:42:09  kernel: [ 6275.080626]  [<ffffffffa0c71705>] ? IofCallDriver+0x65/0xc0 [ndiswrapper]
Mar 28 16:42:09  kernel: [ 6275.080635]  [<ffffffff815295d4>] ? _spin_unlock_bh+0x14/0x20
Mar 28 16:42:09  kernel: [ 6275.080670]  [<ffffffffa0c71690>] ? IoReleaseCancelSpinLock+0x10/0x20 [ndiswrapper]
Mar 28 16:42:09  kernel: [ 6275.080707]  [<ffffffffa0c716d9>] ? IofCallDriver+0x39/0xc0 [ndiswrapper]
Mar 28 16:42:09  kernel: [ 6275.080743]  [<ffffffffa0c73638>] ? IoSendIrpTopDev+0xd8/0x120 [ndiswrapper]
Mar 28 16:42:09  kernel: [ 6275.080752]  [<ffffffff815295d4>] ? _spin_unlock_bh+0x14/0x20
Mar 28 16:42:09  kernel: [ 6275.080788]  [<ffffffffa0c71543>] ? IoAttachDeviceToDeviceStack+0x63/0x80 [ndiswrapper]
Mar 28 16:42:09  kernel: [ 6275.080826]  [<ffffffffa0c739f7>] ? pnp_start_device+0x47/0x90 [ndiswrapper]
Mar 28 16:42:09  kernel: [ 6275.080863]  [<ffffffffa0c73cf1>] ? wrap_pnp_start_device+0x121/0x180 [ndiswrapper]
Mar 28 16:42:09  kernel: [ 6275.080901]  [<ffffffffa0c73e34>] ? wrap_pnp_start_usb_device+0xe4/0x110 [ndiswrapper]
Mar 28 16:42:09  kernel: [ 6275.080910]  [<ffffffff81527ef9>] ? mutex_lock+0x19/0x50
Mar 28 16:42:09  kernel: [ 6275.080920]  [<ffffffff813a25ed>] ? usb_autopm_do_device+0x7d/0x120
Mar 28 16:42:09  kernel: [ 6275.080929]  [<ffffffff813a2e71>] ? usb_probe_interface+0xb1/0x190
Mar 28 16:42:09  kernel: [ 6275.080938]  [<ffffffff81320d74>] ? really_probe+0x64/0x160
Mar 28 16:42:09  kernel: [ 6275.080945]  [<ffffffff81320e93>] ? driver_probe_device+0x23/0x30
Mar 28 16:42:09  kernel: [ 6275.080951]  [<ffffffff81320f33>] ? __driver_attach+0x93/0xa0
Mar 28 16:42:09  kernel: [ 6275.080958]  [<ffffffff81320ea0>] ? __driver_attach+0x0/0xa0
Mar 28 16:42:09  kernel: [ 6275.080966]  [<ffffffff81320258>] ? bus_for_each_dev+0x68/0x90
Mar 28 16:42:09  kernel: [ 6275.080975]  [<ffffffff81320bf9>] ? driver_attach+0x19/0x20
Mar 28 16:42:09  kernel: [ 6275.080983]  [<ffffffff8132050d>] ? bus_add_driver+0xcd/0x2a0
Mar 28 16:42:09  kernel: [ 6275.080990]  [<ffffffff81321228>] ? driver_register+0x78/0x140
Mar 28 16:42:09  kernel: [ 6275.081000]  [<ffffffff81184d1c>] ? sysfs_add_file+0xc/0x10
Mar 28 16:42:09  kernel: [ 6275.081008]  [<ffffffff813a22c8>] ? usb_register_driver+0xb8/0x130
Mar 28 16:42:09  kernel: [ 6275.081031]  [<ffffffffa0017000>] ? wrapper_init+0x0/0xb0 [ndiswrapper]
Mar 28 16:42:09  kernel: [ 6275.081058]  [<ffffffffa0c65d2a>] ? loader_init+0xca/0x150 [ndiswrapper]
Mar 28 16:42:09  kernel: [ 6275.081081]  [<ffffffffa001707b>] ? wrapper_init+0x7b/0xb0 [ndiswrapper]
Mar 28 16:42:09  kernel: [ 6275.081091]  [<ffffffff8100a047>] ? do_one_initcall+0x37/0x1a0
Mar 28 16:42:09  kernel: [ 6275.081101]  [<ffffffff81091b67>] ? sys_init_module+0xd7/0x230
Mar 28 16:42:09  kernel: [ 6275.081110]  [<ffffffff81012002>] ? system_call_fastpath+0x16/0x1b
Mar 28 16:42:09  kernel: [ 6275.081219]  RSP <ffff880166833800>
Mar 28 16:42:09  kernel: [ 6275.081228] ---[ end trace 4f5ff14b1b8970f5 ]---

---

### Post by chili555 on 2010-03-28
And then what happened? ```
ndiswrapper -l
iwconfig
```

---

### Post by donya16 on 2010-03-28
> $ ndiswrapper -l
This does not respond


> $ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.
Another bit of info:
After this crash I rebooted.
I took absurdly long to boot.
I checked in /var/log/syslog to see what happened

> Mar 28 16:52:16  kernel: [   10.435899] last sysfs file: /sys/module/snd/initstate
Mar 28 16:52:16  kernel: [   10.435901] CPU 3 
Mar 28 16:52:16  kernel: [   10.435903] Modules linked in: snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer iptable_filter ip_tables nvidia(P) snd_seq_device snd lp soundcore x_tables amd64_edac_mod snd_page_alloc psmouse shpchp edac_core serio_raw i2c_nforce2 ndiswrapper(+) parport usbhid usb_storage ohci1394 ieee1394 video forcedeth output
Mar 28 16:52:16  kernel: [   10.435919] Pid: 681, comm: modprobe Tainted: P           2.6.31-14-generic #48-Ubuntu AY018AA-ABA p6310f
Mar 28 16:52:16  kernel: [   10.435921] RIP: 0010:[<ffffffffa00982cb>]  [<ffffffffa00982cb>] USBD_InterfaceIsDeviceHighSpeed+0xb/0x20 [ndiswrapper]
Mar 28 16:52:16  kernel: [   10.435935] RSP: 0018:ffff88019701d800  EFLAGS: 00010246
Mar 28 16:52:16  kernel: [   10.435936] RAX: 0000000000000000 RBX: ffffc9000630b000 RCX: ffff88019608ff00
Mar 28 16:52:16  kernel: [   10.435938] RDX: 000000000000000f RSI: 0000000000000000 RDI: ffffc9000630b000
Mar 28 16:52:16  kernel: [   10.435939] RBP: ffff88019701d800 R08: 0000000000000000 R09: ffff880193978a00
Mar 28 16:52:16  kernel: [   10.435941] R10: ffffffffa008a8d0 R11: 0000000000000000 R12: ffff880193978a00
Mar 28 16:52:16  kernel: [   10.435942] R13: ffff88019701d910 R14: 0000000000000000 R15: 0000000000000001
Mar 28 16:52:16  kernel: [   10.435944] FS:  00007f267df5d6f0(0000) GS:ffff88002808e000(0000) knlGS:0000000000000000
Mar 28 16:52:16  kernel: [   10.435946] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
Mar 28 16:52:16  kernel: [   10.435947] CR2: 000000000000001c CR3: 0000000197075000 CR4: 00000000000006e0
Mar 28 16:52:16  kernel: [   10.435949] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Mar 28 16:52:16  kernel: [   10.435950] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Mar 28 16:52:16  kernel: [   10.435952] Process modprobe (pid: 681, threadinfo ffff88019701c000, task ffff88019393c410)
Mar 28 16:52:16  kernel: [   10.435954] Stack:
Mar 28 16:52:16  kernel: [   10.435955]  0000000000000000 ffffc9000623e699 0000000000000001 ffffc9000630b000
Mar 28 16:52:16  kernel: [   10.435957] <0> 0000000000000000 ffffc9000630b000 0000000000000012 ffff880196e06580
Mar 28 16:52:16  kernel: [   10.435959] <0> 0000000100000000 ffff88019701d848 ffff88019701d848 ffff88019701d868
Mar 28 16:52:16  kernel: [   10.435962] Call Trace:
Mar 28 16:52:16  kernel: [   10.435974]  [<ffffffffa008986b>] ? ExFreePool+0xb/0x10 [ndiswrapper]
Mar 28 16:52:16  kernel: [   10.435985]  [<ffffffffa0098440>] ? USBD_InterfaceReference+0x0/0x20 [ndiswrapper]
Mar 28 16:52:16  kernel: [   10.435997]  [<ffffffffa0098420>] ? USBD_InterfaceDereference+0x0/0x20 [ndiswrapper]
Mar 28 16:52:16  kernel: [   10.436008]  [<ffffffffa0098280>] ? USBD_InterfaceGetUSBDIVersion+0x0/0x40 [ndiswrapper]
Mar 28 16:52:16  kernel: [   10.436019]  [<ffffffffa0098950>] ? USBD_InterfaceQueryBusTime+0x0/0x30 [ndiswrapper]
Mar 28 16:52:16  kernel: [   10.436031]  [<ffffffffa00983f0>] ? USBD_InterfaceSubmitIsoOutUrb+0x0/0x30 [ndiswrapper]
Mar 28 16:52:16  kernel: [   10.436042]  [<ffffffffa00983c0>] ? USBD_InterfaceQueryBusInformation+0x0/0x30 [ndiswrapper]
Mar 28 16:52:16  kernel: [   10.436053]  [<ffffffffa00982c0>] ? USBD_InterfaceIsDeviceHighSpeed+0x0/0x20 [ndiswrapper]
Mar 28 16:52:16  kernel: [   10.436065]  [<ffffffffa009603a>] ? mp_init+0x6a/0x200 [ndiswrapper]
Mar 28 16:52:16  kernel: [   10.436076]  [<ffffffffa008e0d9>] ? IofCompleteRequest+0x59/0x1c0 [ndiswrapper]
Mar 28 16:52:16  kernel: [   10.436087]  [<ffffffffa009056d>] ? pdoDispatchPnp+0x3d/0xf0 [ndiswrapper]
Mar 28 16:52:16  kernel: [   10.436098]  [<ffffffffa0097117>] ? ndis_start_device+0x27/0x860 [ndiswrapper]
Mar 28 16:52:16  kernel: [   10.436109]  [<ffffffffa008d705>] ? IofCallDriver+0x65/0xc0 [ndiswrapper]
Mar 28 16:52:16  kernel: [   10.436114]  [<ffffffff815295d4>] ? _spin_unlock_bh+0x14/0x20
Mar 28 16:52:16  kernel: [   10.436124]  [<ffffffffa008d690>] ? IoReleaseCancelSpinLock+0x10/0x20 [ndiswrapper]
Mar 28 16:52:16  kernel: [   10.436135]  [<ffffffffa008d6d9>] ? IofCallDriver+0x39/0xc0 [ndiswrapper]
Mar 28 16:52:16  kernel: [   10.436146]  [<ffffffffa008dc61>] ? IoSyncForwardIrp+0x91/0xd0 [ndiswrapper]
Mar 28 16:52:16  kernel: [   10.436157]  [<ffffffffa00979f3>] ? NdisDispatchPnp+0xa3/0x150 [ndiswrapper]
Mar 28 16:52:16  kernel: [   10.436169]  [<ffffffffa0099ec7>] ? win2lin2+0xe/0x11 [ndiswrapper]
Mar 28 16:52:16  kernel: [   10.436179]  [<ffffffffa008d690>] ? IoReleaseCancelSpinLock+0x10/0x20 [ndiswrapper]
Mar 28 16:52:16  kernel: [   10.436190]  [<ffffffffa008d705>] ? IofCallDriver+0x65/0xc0 [ndiswrapper]
Mar 28 16:52:16  kernel: [   10.436193]  [<ffffffff815295d4>] ? _spin_unlock_bh+0x14/0x20
Mar 28 16:52:16  kernel: [   10.436203]  [<ffffffffa008d690>] ? IoReleaseCancelSpinLock+0x10/0x20 [ndiswrapper]
Mar 28 16:52:16  kernel: [   10.436214]  [<ffffffffa008d6d9>] ? IofCallDriver+0x39/0xc0 [ndiswrapper]
Mar 28 16:52:16  kernel: [   10.436224]  [<ffffffffa008f638>] ? IoSendIrpTopDev+0xd8/0x120 [ndiswrapper]
Mar 28 16:52:16  kernel: [   10.436227]  [<ffffffff815295d4>] ? _spin_unlock_bh+0x14/0x20
Mar 28 16:52:16  kernel: [   10.436238]  [<ffffffffa008d543>] ? IoAttachDeviceToDeviceStack+0x63/0x80 [ndiswrapper]
Mar 28 16:52:16  kernel: [   10.436249]  [<ffffffffa008f9f7>] ? pnp_start_device+0x47/0x90 [ndiswrapper]
Mar 28 16:52:16  kernel: [   10.436260]  [<ffffffffa008fcf1>] ? wrap_pnp_start_device+0x121/0x180 [ndiswrapper]
Mar 28 16:52:16  kernel: [   10.436271]  [<ffffffffa008fe34>] ? wrap_pnp_start_usb_device+0xe4/0x110 [ndiswrapper]
Mar 28 16:52:16  kernel: [   10.436273]  [<ffffffff81527ef9>] ? mutex_lock+0x19/0x50
Mar 28 16:52:16  kernel: [   10.436277]  [<ffffffff813a25ed>] ? usb_autopm_do_device+0x7d/0x120
Mar 28 16:52:16  kernel: [   10.436280]  [<ffffffff813a2e71>] ? usb_probe_interface+0xb1/0x190
Mar 28 16:52:16  kernel: [   10.436283]  [<ffffffff81320d74>] ? really_probe+0x64/0x160
Mar 28 16:52:16  kernel: [   10.436285]  [<ffffffff81320e93>] ? driver_probe_device+0x23/0x30
Mar 28 16:52:16  kernel: [   10.436287]  [<ffffffff81320f33>] ? __driver_attach+0x93/0xa0
Mar 28 16:52:16  kernel: [   10.436289]  [<ffffffff81320ea0>] ? __driver_attach+0x0/0xa0
Mar 28 16:52:16  kernel: [   10.436291]  [<ffffffff81320258>] ? bus_for_each_dev+0x68/0x90
Mar 28 16:52:16  kernel: [   10.436294]  [<ffffffff81320bf9>] ? driver_attach+0x19/0x20
Mar 28 16:52:16  kernel: [   10.436296]  [<ffffffff8132050d>] ? bus_add_driver+0xcd/0x2a0
Mar 28 16:52:16  kernel: [   10.436298]  [<ffffffff81321228>] ? driver_register+0x78/0x140
Mar 28 16:52:16  kernel: [   10.436301]  [<ffffffff81184d1c>] ? sysfs_add_file+0xc/0x10
Mar 28 16:52:16  kernel: [   10.436304]  [<ffffffff813a22c8>] ? usb_register_driver+0xb8/0x130
Mar 28 16:52:16  kernel: [   10.436311]  [<ffffffffa0017000>] ? wrapper_init+0x0/0xb0 [ndiswrapper]
Mar 28 16:52:16  kernel: [   10.436319]  [<ffffffffa0081d2a>] ? loader_init+0xca/0x150 [ndiswrapper]
Mar 28 16:52:16  kernel: [   10.436326]  [<ffffffffa001707b>] ? wrapper_init+0x7b/0xb0 [ndiswrapper]
Mar 28 16:52:16  kernel: [   10.436329]  [<ffffffff8100a047>] ? do_one_initcall+0x37/0x1a0
Mar 28 16:52:16  kernel: [   10.436332]  [<ffffffff81091b67>] ? sys_init_module+0xd7/0x230
Mar 28 16:52:16  kernel: [   10.436335]  [<ffffffff81012002>] ? system_call_fastpath+0x16/0x1b
Mar 28 16:52:16  kernel: [   10.436336] Code: 10 01 00 00 0f 45 c1 89 46 04 c7 02 01 00 00 00 c9 c3 66 66 66 66 66 2e 0f 1f 84 00 00 00 00 00 48 8b 87 98 00 00 00 55 48 89 e5 <83> 78 1c 03 c9 0f 94 c0 c3 66 66 66 2e 0f 1f 84 00 00 00 00 00 
Mar 28 16:52:16  kernel: [   10.436355] RIP  [<ffffffffa00982cb>] USBD_InterfaceIsDeviceHighSpeed+0xb/0x20 [ndiswrapper]
Mar 28 16:52:16  kernel: [   10.436366]  RSP <ffff88019701d800>
Mar 28 16:52:16  kernel: [   10.436367] CR2: 000000000000001c
Mar 28 16:52:16  kernel: [   10.436369] ---[ end trace fa37500d0b16d0f1 ]---
Mar 28 16:52:17  kernel: [   11.203380] HDA Intel 0000:00:07.0: power state changed by ACPI to D0
Mar 28 16:52:17  kernel: [   11.203682] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 20
Mar 28 16:52:17  kernel: [   11.203686] HDA Intel 0000:00:07.0: PCI INT A -> Link[LAZA] -> GSI 20 (level, low) -> IRQ 20
Mar 28 16:52:17  kernel: [   11.203723] HDA Intel 0000:00:07.0: setting latency timer to 64
Mar 28 16:52:17  udev-configure-printer: add /module/lp
Mar 28 16:52:17  udev-configure-printer: Failed to get parent
Mar 28 16:52:17  avahi-daemon[980]: Found user 'avahi' (UID 105) and group 'avahi' (GID 111).
Mar 28 16:52:17  avahi-daemon[980]: Successfully dropped root privileges.
Mar 28 16:52:17  avahi-daemon[980]: avahi-daemon 0.6.25 starting up.
Mar 28 16:52:17  avahi-daemon[980]: Successfully called chroot().
Mar 28 16:52:17  avahi-daemon[980]: Successfully dropped remaining capabilities.
Mar 28 16:52:17  avahi-daemon[980]: No service file found in /etc/avahi/services.
Mar 28 16:52:17  avahi-daemon[980]: Network interface enumeration completed.
Mar 28 16:52:17  avahi-daemon[980]: Registering HINFO record with values 'X86_64'/'LINUX'.
Mar 28 16:52:17  avahi-daemon[980]: Server startup complete. Host name is heartofgold.local. Local service cookie is 2389096832.
Mar 28 16:52:18  NetworkManager: <info>  starting...
Mar 28 16:52:18  NetworkManager: <info>  Trying to start the modem-manager...
Mar 28 16:52:18  NetworkManager:    SCPlugin-Ifupdown: init!
Mar 28 16:52:18  NetworkManager:    SCPlugin-Ifupdown: update_system_hostname
Mar 28 16:52:18  NetworkManager:    SCPluginIfupdown: management mode: unmanaged
Mar 28 16:52:18  NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:0a.0/net/eth0, iface: eth0)
Mar 28 16:52:18  NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:0a.0/net/eth0, iface: eth0): no ifupdown configuration found.
Mar 28 16:52:18  NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/lo, iface: lo)
Mar 28 16:52:18  NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration found.
Mar 28 16:52:18  NetworkManager:    SCPlugin-Ifupdown: end _init.
Mar 28 16:52:18  NetworkManager: Loaded plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the NetworkManager mailing list.
Mar 28 16:52:18  NetworkManager: Loaded plugin keyfile: (c) 2007 - 2008 Red Hat, Inc.  To report bugs please use the NetworkManager mailing list.
Mar 28 16:52:18  NetworkManager: <info>  Wireless now enabled by radio killswitch
Mar 28 16:52:18  NetworkManager:    SCPlugin-Ifupdown: (33227872) ... get_connections.
Mar 28 16:52:18  NetworkManager:    SCPlugin-Ifupdown: (33227872) ... get_connections (managed=false): return empty list.
Mar 28 16:52:18  modem-manager: Loaded plugin Option High-Speed
Mar 28 16:52:18  modem-manager: Loaded plugin Nokia
Mar 28 16:52:18  modem-manager: Loaded plugin MotoC
Mar 28 16:52:18  modem-manager: Loaded plugin Huawei
Mar 28 16:52:18  modem-manager: Loaded plugin Option
Mar 28 16:52:18  modem-manager: Loaded plugin Ericsson MBM
Mar 28 16:52:18  modem-manager: Loaded plugin ZTE
Mar 28 16:52:18  modem-manager: Loaded plugin Gobi
Mar 28 16:52:18  modem-manager: Loaded plugin Generic
Mar 28 16:52:18  modem-manager: Loaded plugin Sierra
Mar 28 16:52:18  modem-manager: Loaded plugin Novatel
Mar 28 16:52:18  kernel: [   12.319600] __ratelimit: 6 callbacks suppressed
Mar 28 16:52:18  kernel: [   12.319604] type=1505 audit(1269820338.633:13): operation="profile_replace" pid=1120 name=/usr/share/gdm/guest-session/Xsession
Mar 28 16:52:18  kernel: [   12.320859] type=1505 audit(1269820338.633:14): operation="profile_replace" pid=1121 name=/sbin/dhclient3
Mar 28 16:52:18  kernel: [   12.321066] type=1505 audit(1269820338.633:15): operation="profile_replace" pid=1121 name=/usr/lib/NetworkManager/nm-dhcp-client.action
Mar 28 16:52:18  kernel: [   12.321182] type=1505 audit(1269820338.633:16): operation="profile_replace" pid=1121 name=/usr/lib/connman/scripts/dhclient-script
Mar 28 16:52:18  kernel: [   12.323933] type=1505 audit(1269820338.643:17): operation="profile_replace" pid=1122 name=/usr/bin/evince
Mar 28 16:52:18  kernel: [   12.327339] type=1505 audit(1269820338.643:18): operation="profile_replace" pid=1122 name=/usr/bin/evince-previewer
Mar 28 16:52:18  kernel: [   12.329381] type=1505 audit(1269820338.643:19): operation="profile_replace" pid=1122 name=/usr/bin/evince-thumbnailer
Mar 28 16:52:18  kernel: [   12.333519] type=1505 audit(1269820338.643:20): operation="profile_replace" pid=1124 name=/usr/lib/cups/backend/cups-pdf
Mar 28 16:52:18  kernel: [   12.333776] type=1505 audit(1269820338.653:21): operation="profile_replace" pid=1124 name=/usr/sbin/cupsd
Mar 28 16:52:18  kernel: [   12.335212] type=1505 audit(1269820338.653:22): operation="profile_replace" pid=1125 name=/usr/sbin/mysqld
Mar 28 16:52:18  kernel: [   12.580029] hda_codec: Unknown model for ALC888, trying auto-probe from BIOS...
Mar 28 16:52:18  kernel: [   12.620097] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:07.0/input/input7
Mar 28 16:52:19  NetworkManager:    Ifupdown: get unmanaged devices count: 0
Mar 28 16:52:19  anacron[1209]: Anacron 2.3 started on 2010-03-28
Mar 28 16:52:19  NetworkManager: <info>  (eth0): carrier is OFF
Mar 28 16:52:19  NetworkManager: <info>  (eth0): new Ethernet device (driver: 'forcedeth')
Mar 28 16:52:19  NetworkManager: <info>  (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Mar 28 16:52:19  NetworkManager: <info>  (eth0): now managed
Mar 28 16:52:19  NetworkManager: <info>  (eth0): device state change: 1 -> 2 (reason 2)
Mar 28 16:52:19  NetworkManager: <info>  (eth0): bringing up device.
Mar 28 16:52:19  NetworkManager: <info>  (eth0): preparing device.
Mar 28 16:52:19  NetworkManager: <info>  (eth0): deactivating device (reason: 2).
Mar 28 16:52:19  NetworkManager: Added default wired connection 'Auto eth0' for /sys/devices/pci0000:00/0000:00:0a.0/net/eth0
Mar 28 16:52:19  kernel: [   13.186974]   alloc irq_desc for 29 on node 0
Mar 28 16:52:19  kernel: [   13.186977]   alloc kstat_irqs on node 0
Mar 28 16:52:19  kernel: [   13.186985] forcedeth 0000:00:0a.0: irq 29 for MSI/MSI-X
Mar 28 16:52:19  NetworkManager: <info>  (eth0): carrier now ON (device state 2)
Mar 28 16:52:19  NetworkManager: <info>  (eth0): device state change: 2 -> 3 (reason 40)
Mar 28 16:52:19  NetworkManager: <info>  modem-manager is now available
Mar 28 16:52:19  NetworkManager: <WARN>  default_adapter_cb(): bluez error getting default adapter: The name org.bluez was not provided by any .service files
Mar 28 16:52:19  NetworkManager: <info>  Trying to start the supplicant...
Mar 28 16:52:19  NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0'
Mar 28 16:52:19  NetworkManager: <info>  (eth0): device state change: 3 -> 4 (reason 0)
Mar 28 16:52:19  NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Mar 28 16:52:19  NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started...
Mar 28 16:52:19  NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Mar 28 16:52:19  NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
Mar 28 16:52:19  NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting...
Mar 28 16:52:19  NetworkManager: <info>  (eth0): device state change: 4 -> 5 (reason 0)
Mar 28 16:52:19  NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful.
Mar 28 16:52:19  NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Mar 28 16:52:19  NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete.
Mar 28 16:52:19  NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
Mar 28 16:52:19  NetworkManager: <info>  (eth0): device state change: 5 -> 7 (reason 0)
Mar 28 16:52:19  NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction (timeout in 45 seconds)
Mar 28 16:52:19  cron[1196]: (CRON) INFO (pidfile fd = 3)
Mar 28 16:52:19  anacron[1209]: Normal exit (0 jobs run)
Mar 28 16:52:19  cron[1264]: (CRON) STARTUP (fork ok)
Mar 28 16:52:19  init: apport pre-start process (1193) terminated with status 1
Mar 28 16:52:19  init: apport post-stop process (1289) terminated with status 1
Mar 28 16:52:20  NetworkManager: <info>  dhclient started with pid 1290
Mar 28 16:52:20  NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Mar 28 16:52:20  NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Mar 28 16:52:20  NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) started...
Mar 28 16:52:20  NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP6 Configure Get) complete.
Mar 28 16:52:20  dhclient: Internet Systems Consortium DHCP Client V3.1.2
Mar 28 16:52:20  dhclient: Copyright 2004-2008 Internet Systems Consortium.
Mar 28 16:52:20  dhclient: All rights reserved.
Mar 28 16:52:20  dhclient: For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)
Mar 28 16:52:20  dhclient: 
Mar 28 16:52:20  NetworkManager: <info>  DHCP: device eth0 state changed (null) -> preinit
Mar 28 16:52:20  dhclient: Listening on LPF/eth0/90:e6:ba:eb:53:ee
Mar 28 16:52:20  dhclient: Sending on   LPF/eth0/90:e6:ba:eb:53:ee
Mar 28 16:52:20  dhclient: Sending on   Socket/fallback
Mar 28 16:52:20  cron[1264]: (CRON) INFO (Running @reboot jobs)
Mar 28 16:52:20  avahi-daemon[980]: Registering new address record for fe80::92e6:baff:feeb:53ee on eth0.*.
Mar 28 16:52:20  acpid: client connected from 1370[107:114]
Mar 28 16:52:21  mysqld_safe: Starting mysqld daemon with databases from /var/lib/mysql
Mar 28 16:52:21  mysqld: 100328 16:52:21 [Note] Plugin 'FEDERATED' is disabled.
Mar 28 16:52:22  mysqld: 100328 16:52:22  InnoDB: Started; log sequence number 0 44233
Mar 28 16:52:23  dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Mar 28 16:52:23  kernel: [   16.811838] usplash:427 freeing invalid memtype ffffffffe7000000-ffffffffe7e00000
Mar 28 16:52:23  gdm-binary[1249]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Mar 28 16:52:23  gdm-simple-slave[1506]: WARNING: Unable to load file '/etc/gdm/custom.conf': No such file or directory
Mar 28 16:52:23  gdm-binary[1249]: WARNING: Unable to find users: no seat-id found
Mar 28 16:52:24  dhclient: DHCPOFFER of 192.168.1.100 from 192.168.1.1
Mar 28 16:52:24  dhclient: DHCPREQUEST of 192.168.1.100 on eth0 to 255.255.255.255 port 67
Mar 28 16:52:24  dhclient: DHCPACK of 192.168.1.100 from 192.168.1.1
Mar 28 16:52:24  dhclient: bound to 192.168.1.100 -- renewal in 34869 seconds.
Mar 28 16:52:24  NetworkManager: <info>  DHCP: device eth0 state changed preinit -> bound
Mar 28 16:52:24  NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Mar 28 16:52:24  NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) started...
Mar 28 16:52:24  NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Mar 28 16:52:24  NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP4 Configure Get) complete.
Mar 28 16:52:24  NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Mar 28 16:52:24  avahi-daemon[980]: Joining mDNS multicast group on interface eth0.IPv4 with address 192.168.1.100.
Mar 28 16:52:24  avahi-daemon[980]: New relevant interface eth0.IPv4 for mDNS.
Mar 28 16:52:24  avahi-daemon[980]: Registering new address record for 192.168.1.100 on eth0.IPv4.
Mar 28 16:52:24  mysqld: 100328 16:52:24 [Note] Event Scheduler: Loaded 0 events
Mar 28 16:52:24  mysqld: 100328 16:52:24 [Note] /usr/sbin/mysqld: ready for connections.
Mar 28 16:52:24  mysqld: Version: '5.1.37-1ubuntu5.1'  socket: '/var/run/mysqld/mysqld.sock'  port: 3306  (Ubuntu)
Mar 28 16:52:24  kernel: [   18.088394] __ratelimit: 15 callbacks suppressed
Mar 28 16:52:24  kernel: [   18.088441] type=1503 audit(1269820344.403:28): operation="open" pid=1511 parent=1510 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Mar 28 16:52:24  kernel: [   18.274198] type=1503 audit(1269820344.593:29): operation="open" pid=1522 parent=1521 profile="/usr/sbin/mysqld" requested_mask="r::" denied_mask="r::" fsuid=0 ouid=0 name="/sys/devices/system/cpu/"
Mar 28 16:52:24  /etc/mysql/debian-start[1534]: Upgrading MySQL tables if necessary.
Mar 28 16:52:24  acpid: client connected from 1507[0:0]
Mar 28 16:52:25  NetworkManager: <info>  (eth0): writing resolv.conf to /sbin/resolvconf
Mar 28 16:52:25  /etc/mysql/debian-start[1539]: Looking for 'mysql' as: /usr/bin/mysql
Mar 28 16:52:25  /etc/mysql/debian-start[1539]: Looking for 'mysqlcheck' as: /usr/bin/mysqlcheck
Mar 28 16:52:25  /etc/mysql/debian-start[1539]: This installation of MySQL is already upgraded to 5.1.37, use --force if you still need to run mysql_upgrade
Mar 28 16:52:25  /etc/mysql/debian-start[1686]: Checking for insecure root accounts.
Mar 28 16:52:25  /etc/mysql/debian-start[1690]: Triggering myisam-recover for all MyISAM tables
Mar 28 16:52:25  acpid: client connected from 1507[0:0]
Mar 28 16:52:26  kernel: [   19.784081] ppdev: user-space parallel port driver
Mar 28 16:52:26  udev-configure-printer: add /devices/pci0000:00/0000:00:02.0/usb3
Mar 28 16:52:26  udev-configure-printer: Failed to get parent
Mar 28 16:52:26  udev-configure-printer: add /devices/pci0000:00/0000:00:02.0/usb3/3-0:1.0
Mar 28 16:52:26  udev-configure-printer: parent devpath is /devices/pci0000:00/0000:00:02.0/usb3
Mar 28 16:52:26  udev-configure-printer: Device vendor/product is 1D6B:0001
Mar 28 16:52:26  udev-configure-printer: add /devices/pci0000:00/0000:00:02.0/usb3/3-3
Mar 28 16:52:26  udev-configure-printer: add /devices/pci0000:00/0000:00:02.0/usb3/3-3/3-3:1.0
Mar 28 16:52:26  udev-configure-printer: add /devices/pci0000:00/0000:00:02.1/usb1
Mar 28 16:52:26  udev-configure-printer: add /devices/pci0000:00/0000:00:02.1/usb1/1-0:1.0
Mar 28 16:52:26  udev-configure-printer: add /devices/pci0000:00/0000:00:02.1/usb1/1-1
Mar 28 16:52:26  udev-configure-printer: add /devices/pci0000:00/0000:00:02.1/usb1/1-1/1-1:1.0
Mar 28 16:52:26  udev-configure-printer: add /devices/pci0000:00/0000:00:04.0/usb4
Mar 28 16:52:26  udev-configure-printer: add /devices/pci0000:00/0000:00:04.0/usb4/4-0:1.0
Mar 28 16:52:26  udev-configure-printer: add /devices/pci0000:00/0000:00:04.0/usb4/4-1
Mar 28 16:52:26  udev-configure-printer: add /devices/pci0000:00/0000:00:04.0/usb4/4-1/4-1:1.0
Mar 28 16:52:26  udev-configure-printer: add /devices/pci0000:00/0000:00:04.0/usb4/4-1/4-1:1.1
Mar 28 16:52:26  udev-configure-printer: add /devices/pci0000:00/0000:00:04.0/usb4/4-1/4-1:1.1/usb/hiddev0
Mar 28 16:52:26  udev-configure-printer: add /devices/pci0000:00/0000:00:04.1/usb2
Mar 28 16:52:26  udev-configure-printer: add /devices/pci0000:00/0000:00:04.1/usb2/2-0:1.0
Mar 28 16:52:26  udev-configure-printer: add /devices/pci0000:00/0000:00:04.1/usb2/2-3
Mar 28 16:52:26  udev-configure-printer: add /devices/pci0000:00/0000:00:04.1/usb2/2-3/2-3:1.0
Mar 28 16:52:26  udev-configure-printer: add /devices/pci0000:00/0000:00:04.1/usb2/2-4
Mar 28 16:52:26  udev-configure-printer: add /devices/pci0000:00/0000:00:04.1/usb2/2-4/2-4:1.0
Mar 28 16:52:29  console-kit-daemon[1016]: WARNING: Couldn't read /proc/985/environ: Failed to open file '/proc/985/environ': No such file or directory
Mar 28 16:52:29  kernel: [   23.410026] eth0: no IPv6 routers present
Mar 28 16:52:37  NetworkManager: <info>  (eth0): device state change: 7 -> 8 (reason 0)
Mar 28 16:52:37  NetworkManager: <info>  (eth0): writing resolv.conf to /sbin/resolvconf
Mar 28 16:52:37  NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Mar 28 16:52:37  NetworkManager: <info>  Activation (eth0) successful, device activated.
Mar 28 16:52:37  NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Mar 28 16:52:39  ntpdate[2068]: adjust time server 91.189.94.4 offset -0.359672 sec
Mar 28 16:52:54  gnome-session[2014]: devkit-power-gobject-WARNING: Couldn't enumerate devices: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Mar 28 16:53:19  gdm-simple-greeter[2082]: devkit-power-gobject-WARNING: Couldn't enumerate devices: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Mar 28 16:53:44  gdm-simple-greeter[2082]: devkit-power-gobject-WARNING: Error invoking GetAll() to get properties: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Mar 28 16:54:09  gdm-simple-greeter[2082]: devkit-power-gobject-WARNING: Error invoking GetAll() to get properties: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Mar 28 16:55:17  gdm-simple-greeter[2082]: last message repeated 2 times
Mar 28 16:55:28  gdm-simple-greeter[2082]: devkit-power-gobject-WARNING: Error invoking GetAll() to get properties: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Mar 28 16:56:01  gnome-session[2130]: devkit-power-gobject-WARNING: Couldn't enumerate devices: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Mar 28 16:56:06  ntfs-3g[2371]: Version 2009.4.4 external FUSE 27
Mar 28 16:56:06  ntfs-3g[2371]: Mounted /dev/sdb5 (Read-Write, label "HP Pocket Media Drive", NTFS 3.1)
Mar 28 16:56:06  ntfs-3g[2371]: Cmdline options: rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,dmask=0077
Mar 28 16:56:06  ntfs-3g[2371]: Mount options: rw,nosuid,nodev,uhelper=devkit,silent,allow_other,nonempty,default_permissions,relatime,fsname=/dev/sdb5,blkdev,blksize=4096
Mar 28 16:56:34  gnome-session[2130]: devkit-power-gobject-WARNING: Error invoking GetAll() to get properties: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Mar 28 16:56:59  gnome-session[2130]: devkit-power-gobject-WARNING: Error invoking GetAll() to get properties: Did not receive a reply. Possible causes include: the remote application did not send a reply, 


---

### Post by chili555 on 2010-03-28
I haven't a clue. I suggest you ask over on General Help: [http://ubuntuforums.org/forumdisplay.php?f=331](http://ubuntuforums.org/forumdisplay.php?f=331)

To save all that copying and pasting, simply give them a link to this thread.

Sorry this happened.

---

### Post by donya16 on 2010-03-30
Hi Chili555,
Thanks for all the suggestions..
I've updated to ubuntu 10.04 and tried all the drivers and it still does not work.
I'm giving up on this particular adapter and buy something else..
Do you have a suggestion for usb adapter (which supports 802.11n) which works 
with ubuntu 10.04?
Thanks again..

---

### Post by chili555 on 2010-03-30
All I can suggest is here: [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

I am dying to figure out what makes these devices *NOT* tick. I am going to buy one.

---

### Post by donya16 on 2010-03-31
Finally bought wireless n 300 usb adapter from netgear : wn111 v2.
Got the drivers files off the web(netmw245.inf and sys file). Works fine now with ubuntu 10.04 64 bit. If anybody wants the drivers please email me.:popcorn:.

---

