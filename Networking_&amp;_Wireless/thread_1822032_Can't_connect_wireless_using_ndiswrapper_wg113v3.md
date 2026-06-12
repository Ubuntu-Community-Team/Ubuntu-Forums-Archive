---
title: "Can't connect wireless using ndiswrapper wg113v3"
date: 2011-08-10
forum: Networking &amp; Wireless
---

### Post by kyletstrand on 2011-08-10
Hello, I just got a new pc and installed ubuntu 10.04.  I have not yet been able to connect wirelessly, but can connect using a hardwire connection.

```
kyle@Gracie-pants:~$ ndiswrapper -l
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
wg311v3 : driver installed
    device (11AB:1FAA) present
```

I updated the module files and all that jazz.

```
kyle@Gracie-pants:~$ iwconfig 
lo        no wireless extensions.

eth1      no wireless extensions.

eth0      no wireless extensions.

```

```
kyle@Gracie-pants:~$ sudo ifup wlan0
Ignoring unknown interface wlan0=wlan0.

```

```
kyle@Gracie-pants:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
01:06.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
02:00.0 VGA compatible controller: nVidia Corporation GT218 [GeForce 310] (rev a2)
02:00.1 Audio device: nVidia Corporation High Definition Audio Controller (rev a1)
04:00.0 PCI bridge: Texas Instruments XIO2000(A)/XIO2200(A) PCI Express-to-PCI Bridge (rev 03)
05:00.0 USB Controller: NEC Corporation USB (rev 43)
05:00.1 USB Controller: NEC Corporation USB (rev 43)
05:00.2 USB Controller: NEC Corporation USB 2.0 (rev 04)

```

```
$lshw
             *-network:1 UNCLAIMED
             description: Ethernet controller
             product: 88w8335 [Libertas] 802.11b/g Wireless
             vendor: Marvell Technology Group Ltd.
             physical id: 6
             bus info: pci@0000:01:06.0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: pm bus_master cap_list
             configuration: latency=64
             resources: memory:fcee0000-fceeffff memory:fceb0000-fcebffff

```

 I'm a bit confused about the network:1 UNCLAIMED and the fact that wlan0 does not exist in my iwconfig.  If anyone could offer me some insight on this, it would be greatly appreciated.

If anymore info is needed, let me know!

---

### Post by chili555 on 2011-08-10
Let's try to fix this first:> WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.Please do:```
sudo mv /etc/modprobe.d/ndiswrapper /etc/modprobe.d/ndiswrapper.conf
```Next, let's load ndiswrapper and see if there is an error or warning. Please run and post:```
sudo modprobe ndiswrapper
dmesg | grep ndis
```Thanks.

---

### Post by kyletstrand on 2011-08-10
Thanks for the reply!

I have done the following:

```
kyle@Gracie-pants:~$ sudo mv /etc/modprobe.d/ndiswrapper /etc/modprobe.d/ndiswrapper.conf
[sudo] password for kyle: 
kyle@Gracie-pants:~$ sudo modprobe ndiswrapper
kyle@Gracie-pants:~$ dmesg | grep ndis
[    6.682209] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
[    7.477246] ndiswrapper (check_nt_hdr:150): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[    7.477638] ndiswrapper (load_sys_files:206): couldn't prepare driver 'wg311v3'
[    7.478290] ndiswrapper (load_wrap_driver:108): couldn't load driver wg311v3; check system log for messages from 'loadndisdriver'
[   11.515265] usbcore: registered new interface driver ndiswrapper

```

And the error has been resolved but I'm about the reboot to see if anything new develops.  Just wanted to post before rebooting so I didn't lose my outputs :)

---

### Post by kyletstrand on 2011-08-10
The error message is now gone but I am still getting the same results with everything else.

```
kyle@Gracie-pants:~$ ndiswrapper -l
wg311v3 : driver installed
    device (11AB:1FAA) present
kyle@Gracie-pants:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

kyle@Gracie-pants:~$ sudo ifup wlan0
[sudo] password for kyle: 
Ignoring unknown interface wlan0=wlan0.

```

Do you think an uninstall of ndiswrapper and a complete manual unpacking install of the most recent version might help to remedy this?

---

### Post by chili555 on 2011-08-10
> kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010BI think you need to find the 64-bit Windows XP .inf file and remove the 32-bit. I think your installed ndiswrapper packages are just fine.

---

### Post by kyletstrand on 2011-08-10
Good call there. I didn't catch that. I will try that tomorrow night when I return home and keep you posted.

Thanks!

---

### Post by kyletstrand on 2011-08-11
Hello

I have made some progress using guide from this thread ([http://ubuntuforums.org/showthread.php?t=320111](http://ubuntuforums.org/showthread.php?t=320111)) to get 64 bit drivers working when only 32 bit are available.

I am now able to see wlan0 info: 

```
kyle@Gracie-pants:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Sensitivity=-200 dBm  
          RTS thr=2346 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

But I am still unable to connect to any wireless networks.  I just had an issue in which my system froze multiple times in a row while trying to connect to the wireless.   I have disabled wireless networks and it was not frozen.  So, I have been able to narrow that down.  I'm going to post this and reenable to try and get some info from my terminal in hopes that it won't crash.

---

### Post by kyletstrand on 2011-08-11
Yep froze again.  I'm at a loss once again when I was so close before :(

---

### Post by chili555 on 2011-08-11
What does syslog say is going on all this time?```
sudo cat /var/log/syslog | grep ndis | tail -n25
```Thanks.

---

### Post by kyletstrand on 2011-08-11
```
kyle@Gracie-pants:~$ sudo cat /var/log/syslog | grep ndis | tail -n25
[sudo] password for kyle: 
Aug 11 19:21:47 Gracie-pants kernel: [   14.755838] ndiswrapper (link_pe_images:575): fixing KI_USER_SHARED_DATA address in the driver
Aug 11 19:21:47 Gracie-pants kernel: [   14.756466] ndiswrapper: driver wg311v3 (NETGEAR,02/22/2005,3.1.1.7) loaded
Aug 11 19:21:47 Gracie-pants kernel: [   14.756966] ndiswrapper 0000:01:06.0: PCI INT A -> Link[LNKB] -> GSI 18 (level, low) -> IRQ 18
Aug 11 19:21:47 Gracie-pants kernel: [   14.757535] ndiswrapper: using IRQ 18
Aug 11 19:21:48 Gracie-pants kernel: [   15.038228] usbcore: registered new interface driver ndiswrapper
Aug 11 19:21:48 Gracie-pants NetworkManager: <info>  (wlan0): new 802.11 WiFi device (driver: 'ndiswrapper')
Aug 11 19:22:13 Gracie-pants kernel: [   40.915679] ndiswrapper (iw_set_auth:1602): invalid cmd 12
Aug 11 19:22:14 Gracie-pants kernel: [   42.019907] Modules linked in: snd_hda_codec_realtek binfmt_misc ppdev snd_hda_intel snd_hda_codec snd_hwdep snd_pcm_oss snd_mixer_oss snd_seq_dummy snd_pcm snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event ndiswrapper snd_seq snd_timer snd_seq_device snd fbcon tileblit font bitblit softcursor shpchp lp nvidia(P) vga16fb vgastate parport edac_core edac_mce_amd soundcore snd_page_alloc i2c_nforce2 usbhid hid usb_storage r8169 mii floppy pata_amd forcedeth sata_nv
Aug 11 19:22:14 Gracie-pants kernel: [   42.019931] Pid: 948, comm: wrapndis_wq Tainted: P           2.6.32-33-generic #72-Ubuntu GeForce6100PM-M2
Aug 11 19:22:14 Gracie-pants kernel: [   42.019957] Process wrapndis_wq (pid: 948, threadinfo ffff88006e222000, task ffff88006ee5c4d0)
Aug 11 19:22:14 Gracie-pants kernel: [   42.019993]  [<ffffffffa0cab717>] ? win2lin2+0xe/0x11 [ndiswrapper]
Aug 11 19:22:14 Gracie-pants kernel: [   42.020005]  [<ffffffffa0c90000>] ? iw_get_freq+0xb0/0xd0 [ndiswrapper]
Aug 11 19:22:14 Gracie-pants kernel: [   42.020017]  [<ffffffffa0c9c365>] ? KeReleaseSpinLock+0x55/0x60 [ndiswrapper]
Aug 11 19:22:14 Gracie-pants kernel: [   42.020029]  [<ffffffffa0c9dacd>] ? KeAcquireSpinLockRaiseToDpc+0x7d/0xc0 [ndiswrapper]
Aug 11 19:22:14 Gracie-pants kernel: [   42.020053]  [<ffffffffa0ca61c4>] ? mp_tx_packets+0x64/0x5a0 [ndiswrapper]
Aug 11 19:22:14 Gracie-pants kernel: [   42.020080]  [<ffffffffa0ca6788>] ? tx_worker+0x88/0x140 [ndiswrapper]
Aug 11 19:22:14 Gracie-pants kernel: [   42.020093]  [<ffffffffa0ca6700>] ? tx_worker+0x0/0x140 [ndiswrapper]
Aug 11 19:22:32 Gracie-pants kernel: [   59.791667] ndiswrapper (iw_set_auth:1602): invalid cmd 12
Aug 11 19:23:27 Gracie-pants kernel: [   10.278820] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
Aug 11 19:23:31 Gracie-pants kernel: [   15.070092] ndiswrapper (link_pe_images:575): fixing KI_USER_SHARED_DATA address in the driver
Aug 11 19:23:31 Gracie-pants kernel: [   15.070720] ndiswrapper: driver wg311v3 (NETGEAR,02/22/2005,3.1.1.7) loaded
Aug 11 19:23:31 Gracie-pants kernel: [   15.071247] ndiswrapper 0000:01:06.0: PCI INT A -> Link[LNKB] -> GSI 18 (level, low) -> IRQ 18
Aug 11 19:23:31 Gracie-pants kernel: [   15.071843] ndiswrapper: using IRQ 18
Aug 11 19:23:32 Gracie-pants kernel: [   15.365308] usbcore: registered new interface driver ndiswrapper
Aug 11 19:23:34 Gracie-pants NetworkManager: <info>  (wlan0): new 802.11 WiFi device (driver: 'ndiswrapper')

```

This is with wireless disabled.  I can't seem to keep my system up long enough to do anything with wireless enabled.

Will try and repost if possible.

---

### Post by kyletstrand on 2011-08-11
Here is what happens when it is trying to connect but ultimately fails and then freezes my system:

```
kyle@Gracie-pants:~$ sudo cat /var/log/syslog | grep ndis | tail -n25
Aug 11 19:21:47 Gracie-pants kernel: [   14.755838] ndiswrapper (link_pe_images:575): fixing KI_USER_SHARED_DATA address in the driver
Aug 11 19:21:47 Gracie-pants kernel: [   14.756466] ndiswrapper: driver wg311v3 (NETGEAR,02/22/2005,3.1.1.7) loaded
Aug 11 19:21:47 Gracie-pants kernel: [   14.756966] ndiswrapper 0000:01:06.0: PCI INT A -> Link[LNKB] -> GSI 18 (level, low) -> IRQ 18
Aug 11 19:21:47 Gracie-pants kernel: [   14.757535] ndiswrapper: using IRQ 18
Aug 11 19:21:48 Gracie-pants kernel: [   15.038228] usbcore: registered new interface driver ndiswrapper
Aug 11 19:21:48 Gracie-pants NetworkManager: <info>  (wlan0): new 802.11 WiFi device (driver: 'ndiswrapper')
Aug 11 19:22:13 Gracie-pants kernel: [   40.915679] ndiswrapper (iw_set_auth:1602): invalid cmd 12
Aug 11 19:22:14 Gracie-pants kernel: [   42.019907] Modules linked in: snd_hda_codec_realtek binfmt_misc ppdev snd_hda_intel snd_hda_codec snd_hwdep snd_pcm_oss snd_mixer_oss snd_seq_dummy snd_pcm snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event ndiswrapper snd_seq snd_timer snd_seq_device snd fbcon tileblit font bitblit softcursor shpchp lp nvidia(P) vga16fb vgastate parport edac_core edac_mce_amd soundcore snd_page_alloc i2c_nforce2 usbhid hid usb_storage r8169 mii floppy pata_amd forcedeth sata_nv
Aug 11 19:22:14 Gracie-pants kernel: [   42.019931] Pid: 948, comm: wrapndis_wq Tainted: P           2.6.32-33-generic #72-Ubuntu GeForce6100PM-M2
Aug 11 19:22:14 Gracie-pants kernel: [   42.019957] Process wrapndis_wq (pid: 948, threadinfo ffff88006e222000, task ffff88006ee5c4d0)
Aug 11 19:22:14 Gracie-pants kernel: [   42.019993]  [<ffffffffa0cab717>] ? win2lin2+0xe/0x11 [ndiswrapper]
Aug 11 19:22:14 Gracie-pants kernel: [   42.020005]  [<ffffffffa0c90000>] ? iw_get_freq+0xb0/0xd0 [ndiswrapper]
Aug 11 19:22:14 Gracie-pants kernel: [   42.020017]  [<ffffffffa0c9c365>] ? KeReleaseSpinLock+0x55/0x60 [ndiswrapper]
Aug 11 19:22:14 Gracie-pants kernel: [   42.020029]  [<ffffffffa0c9dacd>] ? KeAcquireSpinLockRaiseToDpc+0x7d/0xc0 [ndiswrapper]
Aug 11 19:22:14 Gracie-pants kernel: [   42.020053]  [<ffffffffa0ca61c4>] ? mp_tx_packets+0x64/0x5a0 [ndiswrapper]
Aug 11 19:22:14 Gracie-pants kernel: [   42.020080]  [<ffffffffa0ca6788>] ? tx_worker+0x88/0x140 [ndiswrapper]
Aug 11 19:22:14 Gracie-pants kernel: [   42.020093]  [<ffffffffa0ca6700>] ? tx_worker+0x0/0x140 [ndiswrapper]
Aug 11 19:22:32 Gracie-pants kernel: [   59.791667] ndiswrapper (iw_set_auth:1602): invalid cmd 12
Aug 11 19:23:27 Gracie-pants kernel: [   10.278820] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
Aug 11 19:23:31 Gracie-pants kernel: [   15.070092] ndiswrapper (link_pe_images:575): fixing KI_USER_SHARED_DATA address in the driver
Aug 11 19:23:31 Gracie-pants kernel: [   15.070720] ndiswrapper: driver wg311v3 (NETGEAR,02/22/2005,3.1.1.7) loaded
Aug 11 19:23:31 Gracie-pants kernel: [   15.071247] ndiswrapper 0000:01:06.0: PCI INT A -> Link[LNKB] -> GSI 18 (level, low) -> IRQ 18
Aug 11 19:23:31 Gracie-pants kernel: [   15.071843] ndiswrapper: using IRQ 18
Aug 11 19:23:32 Gracie-pants kernel: [   15.365308] usbcore: registered new interface driver ndiswrapper
Aug 11 19:23:34 Gracie-pants NetworkManager: <info>  (wlan0): new 802.11 WiFi device (driver: 'ndiswrapper')

```

---

### Post by chili555 on 2011-08-11
That looks as ugly as my ex-wife's lawyer! It looks like exactly what it is, a freeze waiting to happen. Call me a skeptical old driver h4x0r, but I doubt that the Netgear probably in truth a 32-bit .inf and a renamed 64-bit .sys will work. I learn something or two new every day so I try to remain open-minded.

Frankly, I'd think the Marvell 64-bit .inf and .sys would have a better chance of working. Would you want to try that? Frankly, you don't have much to lose.

Here is a snip from the Marvell .inf:> ;===========================================================================

; 

; Windows XP, 2000 NDIS driver INF for Libertas 802.11g/b Wireless

; Copyright (C) 2005 Marvell Semiconductor, Inc.

;

;=========================================================================== 

 

<snip> 


[Marvell.NT[COLOR="Red"]amd64[/COLOR]]

%W8335PCI.DeviceDesc% = W8335PCIx64.ndi, PCI\VEN_[COLOR="Red"]11AB[/COLOR]&DEV_[COLOR="Red"]1FAA[/COLOR]

%W8335PCI.DeviceDesc% = W8335PCIx64.ndi, PCI\VEN_11AB&DEV_1FAA&SUBSYS_54011148

%W8335PXPCI.DeviceDesc% = W8335PCIx64.ndi, PCI\VEN_11AB&DEV_1FAB

---

### Post by kyletstrand on 2011-08-11
Haha I was asuming that was what it was saying.

I'm taking a break from this and eating dinner and i'll try the marvell instead and inform of progress.

Thanks again for the help!

---

### Post by kyletstrand on 2011-08-11
Reinstalled the driver using the Marvell mrv8335x64 driver...and same results.

```
kyle@Gracie-pants:~$ sudo cat /var/log/syslog | grep ndis | tail -n25
[sudo] password for kyle: 
Aug 11 21:37:35 Gracie-pants kernel: [   10.319333] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
Aug 11 21:37:39 Gracie-pants kernel: [   14.675231] ndiswrapper (link_pe_images:575): fixing KI_USER_SHARED_DATA address in the driver
Aug 11 21:37:39 Gracie-pants kernel: [   14.675862] ndiswrapper: driver mrv8335x64 (Marvell,07/01/2005,3.2.0.7) loaded
Aug 11 21:37:39 Gracie-pants kernel: [   14.676385] ndiswrapper 0000:01:06.0: PCI INT A -> Link[LNKB] -> GSI 18 (level, low) -> IRQ 18
Aug 11 21:37:39 Gracie-pants kernel: [   14.676941] ndiswrapper: using IRQ 18
Aug 11 21:37:39 Gracie-pants kernel: [   14.958216] usbcore: registered new interface driver ndiswrapper
Aug 11 21:37:40 Gracie-pants NetworkManager: <info>  (wlan0): new 802.11 WiFi device (driver: 'ndiswrapper')
Aug 11 21:37:59 Gracie-pants kernel: [   34.516538] ndiswrapper (iw_set_auth:1602): invalid cmd 12
Aug 11 21:38:00 Gracie-pants kernel: [   35.618195] Modules linked in: snd_hda_codec_realtek binfmt_misc ppdev ndiswrapper snd_hda_intel snd_hda_codec snd_hwdep snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd fbcon tileblit font bitblit softcursor nvidia(P) vga16fb vgastate edac_core edac_mce_amd shpchp soundcore snd_page_alloc lp parport i2c_nforce2 usbhid hid usb_storage floppy r8169 pata_amd mii sata_nv forcedeth
Aug 11 21:38:00 Gracie-pants kernel: [   35.618286]  [<ffffffffa0d83717>] ? win2lin2+0xe/0x11 [ndiswrapper]
Aug 11 21:38:00 Gracie-pants kernel: [   35.618303]  [<ffffffffa0d83717>] ? win2lin2+0xe/0x11 [ndiswrapper]
Aug 11 21:38:00 Gracie-pants kernel: [   35.618314]  [<ffffffffa0d6e681>] ? NdisMSynchronizeWithInterrupt+0x11/0x20 [ndiswrapper]
Aug 11 21:38:00 Gracie-pants kernel: [   35.618327]  [<ffffffffa0d7722e>] ? IoFreeMdl+0xe/0x10 [ndiswrapper]
Aug 11 21:38:00 Gracie-pants kernel: [   35.618347]  [<ffffffffa0d6c76d>] ? deserialized_irq_handler+0x1d/0x40 [ndiswrapper]
Aug 11 21:38:00 Gracie-pants kernel: [   35.618363]  [<ffffffffa0d83742>] ? win2lin4+0x14/0x17 [ndiswrapper]
Aug 11 21:38:00 Gracie-pants kernel: [   35.618375]  [<ffffffffa0d7565c>] ? kdpc_worker+0xec/0x170 [ndiswrapper]
Aug 11 21:38:00 Gracie-pants kernel: [   35.618386]  [<ffffffffa0d7563a>] ? kdpc_worker+0xca/0x170 [ndiswrapper]
Aug 11 21:38:00 Gracie-pants kernel: [   35.618398]  [<ffffffffa0d75570>] ? kdpc_worker+0x0/0x170 [ndiswrapper]
Aug 11 21:39:16 Gracie-pants kernel: [   10.291203] ndiswrapper version 1.55 loaded (smp=yes, preempt=no)
Aug 11 21:39:21 Gracie-pants kernel: [   14.729270] ndiswrapper (link_pe_images:575): fixing KI_USER_SHARED_DATA address in the driver
Aug 11 21:39:21 Gracie-pants kernel: [   14.729902] ndiswrapper: driver mrv8335x64 (Marvell,07/01/2005,3.2.0.7) loaded
Aug 11 21:39:21 Gracie-pants kernel: [   14.730516] ndiswrapper 0000:01:06.0: PCI INT A -> Link[LNKB] -> GSI 18 (level, low) -> IRQ 18
Aug 11 21:39:21 Gracie-pants kernel: [   14.731205] ndiswrapper: using IRQ 18
Aug 11 21:39:22 Gracie-pants kernel: [   15.028351] usbcore: registered new interface driver ndiswrapper
Aug 11 21:39:22 Gracie-pants NetworkManager: <info>  (wlan0): new 802.11 WiFi device (driver: 'ndiswrapper')

```

If it's anything, the network manager seems to be the first program to freeze followed by the entire system.

Lost ](*,)

---

### Post by chili555 on 2011-08-12
I'll be out for a few hours, but this mysterious gem is present with either driver.> ndiswrapper (iw_set_auth:1602): invalid cmd 12Let's Google it.

[https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/459716](https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/459716)

Please let us see:```
ndiswrapper -v
uname -r
```

---

### Post by kyletstrand on 2011-08-12
I looked at the bugs a little bit, but I will have more time later after work.

```
kyle@Gracie-pants:~$ ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.32-33-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko
version:        1.55
vermagic:       2.6.32-33-generic SMP mod_unload modversions 

```

```
kyle@Gracie-pants:~$ uname -r
2.6.32-33-generic

```

---

### Post by kyletstrand on 2011-08-12
Based on what I've been able to read up on this bug sheet, it looks as though it's that it can't recognize WPA, but patching should allow WEP to work.
 
I am going to try patching using the following to see if it works
 
```
diff --git a/iw_ndis.c b/iw_ndis.c
index 434260e..3f5e12c 100644
--- a/iw_ndis.c
+++ b/iw_ndis.c
@@ -1591,6 +1591,12 @@ static int iw_set_auth(struct net_device *dev,
                if (wrqu->param.value)
                        deauthenticate(wnd);
                break;
+ case IW_AUTH_MFP:
+ if (wrqu->param.value == IW_AUTH_MFP_DISABLED ||
+ wrqu->param.value == IW_AUTH_MFP_OPTIONAL)
+ break;
+ WARNING("MFP not implemented");
+ return -EOPNOTSUPP;
        case IW_AUTH_TKIP_COUNTERMEASURES:
        case IW_AUTH_DROP_UNENCRYPTED:
        case IW_AUTH_RX_UNENCRYPTED_EAPOL:
```
 
Of course I am not at home, but I will do it later.
 
I guess we'll see what happens with this.

---

### Post by kyletstrand on 2011-08-12
I'm going to follow the instructions here to fix the 
```
invalid cmd 12 
```
 
And then the patching may resolve and allow the WPA to work.

---

### Post by chili555 on 2011-08-12
You could also install the latest 1.56 version. [http://sourceforge.net/projects/ndiswrapper/files/stable/1.56/](http://sourceforge.net/projects/ndiswrapper/files/stable/1.56/)

---

### Post by kyletstrand on 2011-08-12
I think I will try the installing the latest version and then patch from there if needed.

---

### Post by chili555 on 2011-08-12
According to the changelog, all necessary patches are included:> ndiswrapper (1.56+r2729-1) unstable; urgency=low

  * Imported Upstream version 1.56+r2729
    - Support for Kernels 2.6.36 - 2.6.38 (LP: #660664, Closes: #604880)
  * **Drop patch for Linux 2.6.35, included in snapshot**

 -- Julian Andres Klode <jak@debian.org>  Mon, 14 Mar 2011 15:21:40 +0100

ndiswrapper (1.56-3) unstable; urgency=low

  * Use a reworked and working Linux 2.6.35 support patch (LP: #613796)

 -- Julian Andres Klode <jak@debian.org>  Mon, 13 Sep 2010 19:59:08 +0200

ndiswrapper (1.56-2) unstable; urgency=low

  * Only suggest ndiswrapper-dkms on Ubuntu
  * Add support for Linux 2.6.35 (LP: #590090)
  * Set Standards-Version to 3.9.1

 -- Julian Andres Klode <jak@debian.org>  Tue, 03 Aug 2010 14:21:33 +0200

ndiswrapper (1.56-1) unstable; urgency=low

  * Imported Upstream version 1.56
  * **Drop all patches, they are shipped upstream now.**
  * debian/ndiswrapper.8, debian/loadnsisdriver.8: Escape the "-".
<snip>You can always try it and then patch later if needed and then recompile.

---

### Post by kyletstrand on 2011-08-12
Compiled newest version and get the same results

```
kyle@Gracie-pants:~$ sudo cat /var/log/syslog | grep ndis | tail -n25
[sudo] password for kyle: 
Aug 12 13:32:55 Gracie-pants kernel: [15420.043892] ndiswrapper: using IRQ 18
Aug 12 13:32:55 Gracie-pants kernel: [15420.329274] usbcore: registered new interface driver ndiswrapper
Aug 12 13:32:56 Gracie-pants NetworkManager: <info>  (wlan0): new 802.11 WiFi device (driver: 'ndiswrapper')
Aug 12 13:42:20 Gracie-pants kernel: [   10.499773] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
Aug 12 13:42:24 Gracie-pants kernel: [   14.957088] ndiswrapper (link_pe_images:565): fixing KI_USER_SHARED_DATA address in the driver
Aug 12 13:42:24 Gracie-pants kernel: [   14.957853] ndiswrapper: driver mrv8335x64 (Marvell,07/01/2005,3.2.0.7) loaded
Aug 12 13:42:24 Gracie-pants kernel: [   14.958347] ndiswrapper 0000:01:06.0: PCI INT A -> Link[LNKB] -> GSI 18 (level, low) -> IRQ 18
Aug 12 13:42:24 Gracie-pants kernel: [   14.958898] ndiswrapper: using IRQ 18
Aug 12 13:42:24 Gracie-pants kernel: [   15.237869] usbcore: registered new interface driver ndiswrapper
Aug 12 13:42:26 Gracie-pants NetworkManager: <info>  (wlan0): new 802.11 WiFi device (driver: 'ndiswrapper')
Aug 12 13:42:44 Gracie-pants kernel: [   34.715696] ndiswrapper (iw_set_auth:1602): invalid cmd 12
Aug 12 13:42:45 Gracie-pants kernel: [   35.819386] Modules linked in: snd_hda_codec_realtek binfmt_misc ppdev ndiswrapper fbcon tileblit font bitblit softcursor snd_hda_intel snd_hda_codec snd_hwdep snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device snd edac_core edac_mce_amd shpchp soundcore snd_page_alloc nvidia(P) vga16fb vgastate i2c_nforce2 lp parport usbhid hid usb_storage floppy r8169 mii pata_amd forcedeth sata_nv
Aug 12 13:42:45 Gracie-pants kernel: [   35.819478]  [<ffffffffa0d521b7>] ? win2lin2+0xe/0x11 [ndiswrapper]
Aug 12 13:42:45 Gracie-pants kernel: [   35.819505]  [<ffffffffa0d3b6dd>] ? deserialized_irq_handler+0x1d/0x40 [ndiswrapper]
Aug 12 13:42:45 Gracie-pants kernel: [   35.819521]  [<ffffffffa0d521e2>] ? win2lin4+0x14/0x17 [ndiswrapper]
Aug 12 13:42:45 Gracie-pants kernel: [   35.819532]  [<ffffffffa0d4457c>] ? kdpc_worker+0xec/0x170 [ndiswrapper]
Aug 12 13:42:45 Gracie-pants kernel: [   35.819544]  [<ffffffffa0d4455a>] ? kdpc_worker+0xca/0x170 [ndiswrapper]
Aug 12 13:42:45 Gracie-pants kernel: [   35.819556]  [<ffffffffa0d44490>] ? kdpc_worker+0x0/0x170 [ndiswrapper]
Aug 12 13:44:21 Gracie-pants kernel: [   11.668177] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
Aug 12 13:44:26 Gracie-pants kernel: [   16.528445] ndiswrapper (link_pe_images:565): fixing KI_USER_SHARED_DATA address in the driver
Aug 12 13:44:26 Gracie-pants kernel: [   16.529210] ndiswrapper: driver mrv8335x64 (Marvell,07/01/2005,3.2.0.7) loaded
Aug 12 13:44:26 Gracie-pants kernel: [   16.529701] ndiswrapper 0000:01:06.0: PCI INT A -> Link[LNKB] -> GSI 18 (level, low) -> IRQ 18
Aug 12 13:44:26 Gracie-pants kernel: [   16.530340] ndiswrapper: using IRQ 18
Aug 12 13:44:26 Gracie-pants kernel: [   16.825362] usbcore: registered new interface driver ndiswrapper
Aug 12 13:44:28 Gracie-pants NetworkManager: <info>  (wlan0): new 802.11 WiFi device (driver: 'ndiswrapper')

```

Maybe patch next?

---

### Post by kyletstrand on 2011-08-12
Patched, uninstalled, recompiled, same results.

Ugh...

---

### Post by kyletstrand on 2011-08-12
I went back to v1.55 and patched there and i'm still getting that dreadful error.

I'm giving up for a while. I know this isn't impossible though.

Ack...

---

### Post by chili555 on 2011-08-13
> I know this isn't impossible though.

Ack...Yes, indeed. I'm Googling and I'll look forward to your next post.

---

### Post by kyletstrand on 2011-08-15
After hours of bashing my head against the wall on this, we just decided it was best to just move the tower to be near the router.  hah...

I feel slightly defeated, but I will come at it again with a fresh head soon.

Thanks for all the help chilli.

---

