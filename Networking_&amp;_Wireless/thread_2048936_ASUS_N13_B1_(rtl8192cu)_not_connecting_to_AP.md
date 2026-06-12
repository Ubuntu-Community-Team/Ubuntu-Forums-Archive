---
title: "ASUS N13 B1 (rtl8192cu) not connecting to AP"
date: 2012-08-27
forum: Networking &amp; Wireless
---

### Post by Lemons on 2012-08-27
Hello Everyone,

I have been having some troubles getting my ASUS N13 (HW version B1) running. I have been searching around these forums and nothing so far has worked, so I figured I would make a post.

Heres what I got so far:

$ lsb_release -a
```
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.1 LTS
Release:	12.04
Codename:	precise
```

$ lsusb
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 04e8:685e Samsung Electronics Co., Ltd GT-I9100 Phone [Galaxy S II] (USB Debugging mode)
**Bus 002 Device 002: ID 0b05:17ab ASUSTek Computer, Inc.** 
Bus 004 Device 002: ID 0443:000d Gateway, Inc. 
Bus 004 Device 003: ID 046d:c51b Logitech, Inc. V220 Cordless Optical Mouse for Notebooks
Bus 004 Device 004: ID 0443:000c Gateway, Inc. 
```

$ lshw
```
  *-network:0
       description: Wireless interface
       physical id: 2
       bus info: usb@2:1
       logical name: wlan0
       serial: c8:60:00:d4:9d:3d
       capabilities: ethernet physical wireless
      ** configuration: broadcast=yes driver=rtl8192cu multicast=yes wireless=unassociated**
  *-network:1
       description: Ethernet interface
       physical id: 3
       logical name: easytether0
       serial: 02:00:54:74:68:72
       size: 10Mbit/s
       capabilities: ethernet physical
       configuration: autonegotiation=off broadcast=yes driver=tun driverversion=1.6 duplex=full firmware=N/A ip=192.168.117.2 multicast=yes port=twisted pair speed=10Mbit/s
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
```

$ modinfo rtl8192cu | grep -e modules -e 17AB
```
filename:       /lib/modules/3.2.0-30-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192cu/rtl8192cu.ko
alias:          usb:v0B05p17ABd*dc*dsc*dp*ic*isc*ip*
```

Now, I have tried compiling the driver from the site ([http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true](http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=21&PFid=48&Level=5&Conn=4&DownTypeID=3&GetDown=false&Downloads=true)) and havn't had any luck with it. I can see its installed (as the 8192cu driver instead of rtl8192cu) and is linked to the device:

$ modinfo 8192cu | grep -e modules -e 17AB
```
filename:       /lib/modules/3.2.0-30-generic/kernel/drivers/net/wireless/8192cu.ko
alias:          usb:v0B05p17ABd*dc*dsc*dp*ic*isc*ip*
```

But I have been unabled to get it to choose that driver (as you can see in the lshw output). I have tried blacklisting the driver in /etc/modprobe.d/blacklist.conf with no luck.

At this point I'm at a lost. If anyone could take a look at this and help me out it would be much appreciated. If you need any other information just ask and I'll post it ASAP.

Thanks in advance!

---

### Post by chili555 on 2012-08-27
Here is a long thread about rtl8192cu and the compiled 8192cu and how *NEITHER* of them work. [http://ubuntuforums.org/showthread.php?t=2036445&highlight=rtl8192cu](http://ubuntuforums.org/showthread.php?t=2036445&highlight=rtl8192cu)  Please see post #55.

Please make sure you have the same device before you proceed.```
lsusb
```

---

### Post by Lemons on 2012-08-27
I've gotten it to work with the rtl8192cu driver, but had to disable authentication (which is fine temporarily).

Output of lsusb is in the first post, but here it is again:
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 04e8:685e Samsung Electronics Co., Ltd GT-I9100 Phone [Galaxy S II] (USB Debugging mode)
Bus 002 Device 003: ID 0b05:17ab ASUSTek Computer, Inc. 
Bus 004 Device 002: ID 0443:000d Gateway, Inc. 
Bus 004 Device 003: ID 046d:c51b Logitech, Inc. V220 Cordless Optical Mouse for Notebooks
Bus 004 Device 004: ID 0443:000c Gateway, Inc. 
```

Edit: Sorry, misunderstood your post (I think), the thread talks about a route using ndiswrapper. I'll try that and post here if I have any issues.

---

### Post by chili555 on 2012-08-27
I hope I'm not too blunt, but:> but had to disable authentication (which is fine temporarily)....in my opinion, it's never fine.

I look forward to your results.

---

### Post by Lemons on 2012-08-27
In regards of the authentication, I agree with you on that. I did it as a test to make sure the driver is correct, and to see how it worked.

I got as far as getting ndiswrapper installed and started running into some problems. I tried the file you pointed to, and I got the "Hardware Present: Yes" in ndisgtk. The problem is apparently due to me running a 64-bit version of ubuntu.

Source of drivers (specifically for my card): [http://dlcdnet.asus.com/pub/ASUS/wireless/USB-N13_B1/DR_USB_N13_B1_1005.zip](http://dlcdnet.asus.com/pub/ASUS/wireless/USB-N13_B1/DR_USB_N13_B1_1005.zip)

Output from dmesg when loading the 32-bit driver:
```
[   45.062056] ndiswrapper version 1.57 loaded (smp=yes, preempt=no)
[   45.086654] usbcore: registered new interface driver ndiswrapper
[  389.492366] usbcore: deregistering interface driver ndiswrapper
[  425.529529] ndiswrapper version 1.57 loaded (smp=yes, preempt=no)
[  425.802973] ndiswrapper (check_nt_hdr:141): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[  425.802982] ndiswrapper (load_sys_files:199): couldn't prepare driver 'netrtwlanu'
[  425.803146] ndiswrapper (load_wrap_driver:121): couldn't load driver 'netrtwlanu'
[  425.803224] usbcore: registered new interface driver ndiswrapper
```

So I then tried to load the WinXP 64-bit driver, which results in a system freeze and incomplete conf file for ndiswrapper (I got messages on the startup screen saying that). I tried the vista and win7 drivers (64-bit) to no avail. Output for win7:

```
[  818.389604] ndiswrapper version 1.57 loaded (smp=yes, preempt=no)
[  818.659363] ndiswrapper (import:232): unknown symbol: ntoskrnl.exe:'PoUnregisterPowerSettingCallback'
[  818.659376] ndiswrapper (import:232): unknown symbol: ntoskrnl.exe:'PoRegisterPowerSettingCallback'
[  818.659416] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMFreePort'
[  818.659426] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMNetPnPEvent'
[  818.659437] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMAllocatePort'
[  818.659447] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
[  818.659458] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
[  818.659469] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateMdl'
[  818.659479] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
[  818.659490] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
[  818.659501] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
[  818.659511] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeMdl'
[  818.659521] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
[  818.659532] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferAndNetBufferList'
[  818.659575] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
[  818.659586] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
[  818.659603] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisRegisterDeviceEx'
[  818.659614] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisGetDeviceReservedExtension'
[  818.659624] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisDeregisterDeviceEx'
[  818.659635] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
[  818.659657] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
[  818.659667] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
[  818.659688] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
[  818.659699] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
[  818.659709] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
[  818.659719] ndiswrapper (import:232): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
[  818.659734] ndiswrapper (import:232): unknown symbol: WDFLDR.SYS:'WdfVersionBind'
[  818.659743] ndiswrapper (import:232): unknown symbol: WDFLDR.SYS:'WdfVersionBindClass'
[  818.659752] ndiswrapper (import:232): unknown symbol: WDFLDR.SYS:'WdfVersionUnbindClass'
[  818.659761] ndiswrapper (import:232): unknown symbol: WDFLDR.SYS:'WdfVersionUnbind'
[  818.659766] ndiswrapper (load_sys_files:199): couldn't prepare driver 'netrtwlanu'
[  818.659907] ndiswrapper (load_wrap_driver:121): couldn't load driver 'netrtwlanu'
[  818.659996] usbcore: registered new interface driver ndiswrapper
```

---

### Post by chili555 on 2012-08-27
I'd remove the driver you installed:```
sudo ndiswrapper -e netrtwlanu
```Then try the drivers I attached.

---

### Post by Lemons on 2012-08-27
Same issue as with the 64-bit winxp driver I used before (Shows the installing screen for a few seconds, then freezes).

Edit: Did a little digging around and got it to accept the driver you sent by doing:

$ ndiswrapper -i netrtwlanu.inf
```
couldn't find SourceDisksFiles section - continuing anyway...
installing netrtwlanu ...
couldn't get manufacturer section - installation may be incomplete
```

Which results in an incomplete installation and invalid driver:

$ ndiswrapper -l
```
netrtwlanu : invalid driver!
```

I did the same for the one in the link I sent, and it installed fine. Tried to restart the computer to test it and it panic'd, managed to undo that.

---

### Post by chili555 on 2012-08-27
Let's see:```
ls /etc/ndiswrapper
dmesg | grep ndis
```Thanks.

---

### Post by Lemons on 2012-08-27
I managed to get your working, the files somehow didn't have any content (all 0 byte files). Decompressed them again from the zip and installed fine, except it does not show a wireless card in the network manager.

```
$ ndiswrapper -l
netrtwlanu : driver installed
	device (0B05:17AB) present (alternate driver: rtl8192cu)
```

Output you asked for:

```
$ ls /etc/ndiswrapper
netrtwlanu
```

```
$ dmesg | grep ndis
[   45.586256] ndiswrapper version 1.57 loaded (smp=yes, preempt=no)

```

Using the same command after connecting through my phone's wifi (using easytether) is:

```
$ dmesg | grep ndis
[   45.586256] ndiswrapper version 1.57 loaded (smp=yes, preempt=no)
[  241.948375]  [<ffffffffa0cf7d48>] load_wrap_driver+0x138/0x1f0 [ndiswrapper]
[  241.948416]  [<ffffffffa0d07377>] wrap_pnp_start_device+0x37/0x1e0 [ndiswrapper]
[  241.948465]  [<ffffffffa0d07e1f>] wrap_pnp_start_usb_device+0xef/0x120 [ndiswrapper]
[  241.948630]  [<ffffffffa0cf92ab>] loader_init+0xbb/0x150 [ndiswrapper]
[  241.948655]  [<ffffffffa0d3a073>] wrapper_init+0x73/0x1000 [ndiswrapper]
```

Edit: fixed typo of easyconnect, suppose to be easytether

---

### Post by chili555 on 2012-08-27
> (alternate driver: rtl8192cu)That simply means you need to blacklist rtl8192cu and 8192cu and reboot.

---

### Post by Lemons on 2012-08-27
I do have them in the blacklist, but not sure if its correct (as I stated earlier I was having trouble with blacklisting rtl8192cu and it still loading). The drivers also does not show up with lshw or lsmod.

Contents of /etc/modprobe.d/blacklist.conf
```
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

blacklist 8192cu
blacklist rtl8192cu
```

---

### Post by chili555 on 2012-08-27
Your blacklists are perfect and if they don't show up in lsmod, they are not loaded; they are simply available. After a reboot, what does this tell us?```
dmesg | grep ndis
```I will be off for the evening; see you tomorrow.

---

### Post by Lemons on 2012-08-27
After a fresh reboot, I only get this:

```
$ dmesg | grep ndis
[   47.134903] ndiswrapper version 1.57 loaded (smp=yes, preempt=no)
```

I appreciate you help tremendously this far, thank you. Have a good night.

---

### Post by chili555 on 2012-08-28
That's interesting in its brevity! Let's see if we can provoke some error or warning messages:```
sudo modprobe ndiswrapper
ndiswrapper -l
dmesg | grep ndis
```We are interested in any messages at all.

Let's also check the integrity of the files you downloaded:```
md5sum Desktop/WinX64/*  [COLOR="Red"]<--or wherever you extracted the file[/COLOR]
```Here is what I get:> [COLOR="Red"]88f40f2ad0497f9a7bccae3f84df60c7[/COLOR]  Desktop/Forum/katsumodo/RTLWlanU_WindowsDriver_1015.6.0210.2012_UI_1.00.0187.b2_CU.L/RTWLANU_Driver/WinX64/netrtwlanu.cat
[COLOR="Red"]084fb38819b5243654ff5d06c52a3f0c[/COLOR]  Desktop/Forum/katsumodo/RTLWlanU_WindowsDriver_1015.6.0210.2012_UI_1.00.0187.b2_CU.L/RTWLANU_Driver/WinX64/netrtwlanu.inf
[COLOR="Red"]89e30bece1a4ca66016c20f209d6cd44[/COLOR]  Desktop/Forum/katsumodo/RTLWlanU_WindowsDriver_1015.6.0210.2012_UI_1.00.0187.b2_CU.L/RTWLANU_Driver/WinX64/RTLBt.inf
[COLOR="Red"]0c0bd0185562b14d9284d21516d15598[/COLOR]  Desktop/Forum/katsumodo/RTLWlanU_WindowsDriver_1015.6.0210.2012_UI_1.00.0187.b2_CU.L/RTWLANU_Driver/WinX64/rtwlanu.sys

---

### Post by Lemons on 2012-08-28
Heres the MD5 checks, same as yours:
```
88f40f2ad0497f9a7bccae3f84df60c7  netrtwlanu.cat
084fb38819b5243654ff5d06c52a3f0c  netrtwlanu.inf
89e30bece1a4ca66016c20f209d6cd44  RTLBt.inf
0c0bd0185562b14d9284d21516d15598  rtwlanu.sys
```

On of my last tests resulted in:
```
Aug 28 13:03:30 serv kernel: [  400.705177] ndiswrapper version 1.57 loaded (smp=yes, preempt=no)
Aug 28 13:03:30 serv kernel: [  400.828144] usb 2-1: reset high-speed USB device number 2 using ehci_hcd
Aug 28 13:03:30 serv kernel: [  400.973651] ndiswrapper: driver netrtwlanu (Realtek Semiconductor Corp.,02/10/2012,1015.6.0210.2012) loaded
```

Followed immediately by a crash.

I also get this in /var/log/syslog earlier today with an attempt to start the ndiswrapper module.
```
Aug 28 03:50:14 serv kernel: [  233.278122] ndiswrapper version 1.57 loaded (smp=yes, preempt=no)
Aug 28 03:50:14 serv kernel: [  233.412111] usb 2-1: reset high-speed USB device number 2 using ehci_hcd
Aug 28 03:50:14 serv kernel: [  233.562232] ndiswrapper: driver netrtwlanu (Realtek Semiconductor Corp.,09/06/2011,1015.2.0906.2011) loaded
Aug 28 03:50:16 serv udevd[673]: '/sbin/modprobe -bv usb:v0B05p17ABd0200dc00dsc00dp00icFFiscFFipFF' [3492] terminated by signal 9 (Killed)
Aug 28 03:50:16 serv kernel: [  235.349708] wlan0: ethernet device c8:60:00:d4:9d:3d using NDIS driver: netrtwlanu, version: 0x1, NDIS version: 0x500, vendor: 'Realtek RTL8192C Wireless LAN USB NIC                                     ', 0B05:17AB.F.conf
Aug 28 03:50:16 serv kernel: [  235.349760] ndiswrapper (KeWaitForMultipleObjects:1119): attempt to wait with irql 2
Aug 28 03:50:16 serv kernel: [  235.349781] ndiswrapper (KeWaitForMultipleObjects:1119): attempt to wait with irql 2
Aug 28 03:50:16 serv kernel: [  235.349813] ndiswrapper (KeWaitForMultipleObjects:1119): attempt to wait with irql 2
Aug 28 03:50:16 serv kernel: [  235.349831] ndiswrapper (KeWaitForMultipleObjects:1119): attempt to wait with irql 2
Aug 28 03:50:16 serv kernel: [  235.349858] ndiswrapper (KeWaitForMultipleObjects:1119): attempt to wait with irql 2
Aug 28 03:50:16 serv kernel: [  235.349880] ndiswrapper (KeWaitForMultipleObjects:1119): attempt to wait with irql 2
Aug 28 03:50:16 serv kernel: [  235.349908] kernel tried to execute NX-protected page - exploit attempt? (uid: 0)
Aug 28 03:50:16 serv kernel: [  235.349913] BUG: unable to handle kernel paging request at ffffc90000000000
Aug 28 03:50:16 serv kernel: [  235.349920] IP: [<ffffc90000000000>] 0xffffc8ffffffffff
Aug 28 03:50:16 serv kernel: [  235.349932] PGD 23600f067 PUD 236020067 PMD 236021067 PTE 80000000fed00173
Aug 28 03:50:16 serv kernel: [  235.349942] Oops: 0011 [#1] SMP 
Aug 28 03:50:16 serv kernel: [  235.349948] CPU 6 
Aug 28 03:50:16 serv kernel: [  235.349950] Modules linked in: ndiswrapper(O+) pci_stub vboxpci(O) vboxnetadp(O) vboxnetflt(O) vboxdrv(O) ip6table_filter ip6_tables ebtable_nat ebtables ipt_MASQUERADE iptable_nat nf_nat nf_conntrack_ipv4 nf_defrag_ipv4 xt_state nf_conntrack ipt_REJECT xt_CHECKSUM iptable_mangle xt_tcpudp iptable_filter ip_tables x_tables bridge stp kvm_amd kvm rfcomm parport_pc ppdev bnep bluetooth binfmt_misc dm_crypt arc4 eeepc_wmi asus_wmi sparse_keymap snd_hda_codec_realtek nvidia(P) snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi snd_rawmidi cdc_acm snd_seq_midi_event snd_seq psmouse serio_raw ath5k edac_core ath k10temp fam15h_power edac_mce_amd snd_timer mac80211 snd_seq_device cfg80211 snd soundcore snd_page_alloc sp5100_tco i2c_piix4 mac_hid wmi it87 hwmon_vid lp parport usbhid hid r8169 usb_storage
Aug 28 03:50:16 serv kernel: [  235.350053] 
Aug 28 03:50:16 serv kernel: [  235.350058] Pid: 3492, comm: modprobe Tainted: P           O 3.2.0-30-generic #48-Ubuntu To be filled by O.E.M. To be filled by O.E.M./M5A97
Aug 28 03:50:16 serv kernel: [  235.350069] RIP: 0010:[<ffffc90000000000>]  [<ffffc90000000000>] 0xffffc8ffffffffff
Aug 28 03:50:16 serv kernel: [  235.350080] RSP: 0018:ffff8801e1f4d3c8  EFLAGS: 00010296
Aug 28 03:50:16 serv kernel: [  235.350084] RAX: 0000000000000000 RBX: 0000000000000001 RCX: 0000000000000000
Aug 28 03:50:16 serv kernel: [  235.350089] RDX: 0000000000000001 RSI: 0000000114357000 RDI: ffffc90014357000
Aug 28 03:50:16 serv kernel: [  235.350094] RBP: 0000000111ecb001 R08: 000000000000000a R09: 0000000000000000
Aug 28 03:50:16 serv kernel: [  235.350098] R10: 0000000000000000 R11: 0000000000000000 R12: ffff8801e1f4d498
Aug 28 03:50:16 serv kernel: [  235.350103] R13: 0000000000000001 R14: 0000000000000000 R15: 0000000000000680
Aug 28 03:50:16 serv kernel: [  235.350109] FS:  00007f370f175700(0000) GS:ffff88023ed80000(0000) knlGS:00000000f77db700
Aug 28 03:50:16 serv kernel: [  235.350114] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
Aug 28 03:50:16 serv kernel: [  235.350119] CR2: ffffc90000000000 CR3: 00000001df385000 CR4: 00000000000406e0
Aug 28 03:50:16 serv kernel: [  235.350124] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Aug 28 03:50:16 serv kernel: [  235.350129] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Aug 28 03:50:16 serv kernel: [  235.350134] Process modprobe (pid: 3492, threadinfo ffff8801e1f4c000, task ffff8801fae31700)
Aug 28 03:50:16 serv kernel: [  235.350138] Stack:
Aug 28 03:50:16 serv kernel: [  235.350141]  0000000000000001 0000000111ecb001 ffffc90014357000 ffffc90014357000
Aug 28 03:50:16 serv kernel: [  235.350152]  ffff8801e1f4d408 000000000d01011b ffff8801e1f4d6b0 ffff8801ef3c2800
Aug 28 03:50:16 serv kernel: [  235.350161]  0000000000000004 ffffc90014357000 ffff8801e1f4d548 ffffc90011ecb000
Aug 28 03:50:16 serv kernel: [  235.350170] Call Trace:
Aug 28 03:50:16 serv kernel: [  235.350190]  [<ffffffff8103dcf9>] ? default_spin_lock_flags+0x9/0x10
Aug 28 03:50:16 serv kernel: [  235.350199]  [<ffffffff8165a6ae>] ? _raw_spin_lock_irqsave+0x2e/0x40
Aug 28 03:50:16 serv kernel: [  235.350206]  [<ffffffff8103dcf9>] ? default_spin_lock_flags+0x9/0x10
Aug 28 03:50:16 serv kernel: [  235.350236]  [<ffffffffa11f6c72>] ? lin2win6+0x22/0x28 [ndiswrapper]
Aug 28 03:50:16 serv kernel: [  235.350246]  [<ffffffff81658f1d>] ? mutex_lock+0x1d/0x50
Aug 28 03:50:16 serv kernel: [  235.350277]  [<ffffffffa11ece24>] ? mp_request+0x184/0x420 [ndiswrapper]
Aug 28 03:50:16 serv kernel: [  235.350301]  [<ffffffffa11f6f35>] ? get_encryption_capa.constprop.29+0x248/0x3fb [ndiswrapper]
Aug 28 03:50:16 serv kernel: [  235.350335]  [<ffffffffa11f0380>] ? NdisDispatchPnp+0xab0/0xd90 [ndiswrapper]
Aug 28 03:50:16 serv kernel: [  235.350366]  [<ffffffffa11e5a74>] ? IoInitializeIrp+0x34/0x70 [ndiswrapper]
Aug 28 03:50:16 serv kernel: [  235.350391]  [<ffffffffa11f6928>] ? win2lin_NdisDispatchPnp_2+0x18/0x20 [ndiswrapper]
Aug 28 03:50:16 serv kernel: [  235.350415]  [<ffffffffa11f6910>] ? win2lin_NdisDispatchDeviceControl_2+0x20/0x20 [ndiswrapper]
Aug 28 03:50:16 serv kernel: [  235.350438]  [<ffffffffa11f6bdd>] ? lin2win2+0xd/0x20 [ndiswrapper]
Aug 28 03:50:16 serv kernel: [  235.350446]  [<ffffffff8165a529>] ? _raw_spin_unlock_bh+0x19/0x20
Aug 28 03:50:16 serv kernel: [  235.350475]  [<ffffffffa11e625e>] ? IofCallDriver+0x6e/0xc0 [ndiswrapper]
Aug 28 03:50:16 serv kernel: [  235.350504]  [<ffffffffa11e8067>] ? IoSendIrpTopDev+0xd7/0x120 [ndiswrapper]
Aug 28 03:50:16 serv kernel: [  235.350534]  [<ffffffffa11e82bc>] ? alloc_pdo+0x6c/0xf0 [ndiswrapper]
Aug 28 03:50:16 serv kernel: [  235.350565]  [<ffffffffa11e844a>] ? wrap_pnp_start_device+0x10a/0x1e0 [ndiswrapper]
Aug 28 03:50:16 serv kernel: [  235.350596]  [<ffffffffa11e8e1f>] ? wrap_pnp_start_usb_device+0xef/0x120 [ndiswrapper]
Aug 28 03:50:16 serv kernel: [  235.350606]  [<ffffffff81400ba6>] ? __pm_runtime_set_status+0x146/0x230
Aug 28 03:50:16 serv kernel: [  235.350613]  [<ffffffff814009d9>] ? __pm_runtime_resume+0x69/0x90
Aug 28 03:50:16 serv kernel: [  235.350622]  [<ffffffff81498fa3>] ? usb_probe_interface+0xd3/0x1e0
Aug 28 03:50:16 serv kernel: [  235.350630]  [<ffffffff813f5a28>] ? really_probe+0x68/0x190
Aug 28 03:50:16 serv kernel: [  235.350637]  [<ffffffff813f5cb5>] ? driver_probe_device+0x45/0x70
Aug 28 03:50:16 serv kernel: [  235.350644]  [<ffffffff813f5d8b>] ? __driver_attach+0xab/0xb0
Aug 28 03:50:16 serv kernel: [  235.350650]  [<ffffffff813f5ce0>] ? driver_probe_device+0x70/0x70
Aug 28 03:50:16 serv kernel: [  235.350657]  [<ffffffff813f5ce0>] ? driver_probe_device+0x70/0x70
Aug 28 03:50:16 serv kernel: [  235.350663]  [<ffffffff813f4b1c>] ? bus_for_each_dev+0x5c/0x90
Aug 28 03:50:16 serv kernel: [  235.350670]  [<ffffffff813f57ee>] ? driver_attach+0x1e/0x20
Aug 28 03:50:16 serv kernel: [  235.350677]  [<ffffffff813f5440>] ? bus_add_driver+0x1a0/0x270
Aug 28 03:50:16 serv kernel: [  235.350684]  [<ffffffff813f62f6>] ? driver_register+0x76/0x140
Aug 28 03:50:16 serv kernel: [  235.350692]  [<ffffffff811ecc61>] ? sysfs_add_file+0x11/0x20
Aug 28 03:50:16 serv kernel: [  235.350699]  [<ffffffff81497e11>] ? usb_register_driver+0xa1/0x190
Aug 28 03:50:16 serv kernel: [  235.350709]  [<ffffffffa121b000>] ? 0xffffffffa121afff
Aug 28 03:50:16 serv kernel: [  235.350731]  [<ffffffffa11da2ab>] ? loader_init+0xbb/0x150 [ndiswrapper]
Aug 28 03:50:16 serv kernel: [  235.350752]  [<ffffffffa121b073>] ? wrapper_init+0x73/0x1000 [ndiswrapper]
Aug 28 03:50:16 serv kernel: [  235.350761]  [<ffffffff81002040>] ? do_one_initcall+0x40/0x180
Aug 28 03:50:16 serv kernel: [  235.350770]  [<ffffffff810a83ee>] ? sys_init_module+0xbe/0x230
Aug 28 03:50:16 serv kernel: [  235.350778]  [<ffffffff81662a02>] ? system_call_fastpath+0x16/0x1b
Aug 28 03:50:16 serv kernel: [  235.350782] Code: <10> 82 53 43 7e b1 29 04 00 00 00 00 00 00 00 00 03 00 00 00 00 00 
Aug 28 03:50:16 serv kernel: [  235.350829] RIP  [<ffffc90000000000>] 0xffffc8ffffffffff
Aug 28 03:50:16 serv kernel: [  235.350839]  RSP <ffff8801e1f4d3c8>
Aug 28 03:50:16 serv kernel: [  235.350843] CR2: ffffc90000000000
Aug 28 03:50:16 serv kernel: [  235.350848] ---[ end trace ef217e23074a2f84 ]---
Aug 28 03:50:16 serv NetworkManager[1141]:    SCPlugin-Ifupdown: devices added (path: /sys/devices/pci0000:00/0000:00:13.2/usb2/2-1/2-1:1.0/net/wlan0, iface: wlan0)
Aug 28 03:50:16 serv NetworkManager[1141]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:13.2/usb2/2-1/2-1:1.0/net/wlan0, iface: wlan0): no ifupdown configuration found.
Aug 28 03:50:16 serv NetworkManager[1141]: <warn> failed to allocate link cache: (-10) Operation not supported
```

And heres a log using ndiswrapper-1.58rc1 with "make DEBUG=6 IO_DEBUG=1 EVENT_DEBUG=1 USB_DEBUG=1" as described on [http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Bugs_HowTo](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Bugs_HowTo)
```
Aug 28 14:27:32 serv kernel: [ 1870.225627] ndiswrapper (wrapper_exit:106): Enter 
Aug 28 14:27:32 serv kernel: [ 1870.225635] ndiswrapper (loader_exit:860): Enter 
Aug 28 14:27:32 serv kernel: [ 1870.225779] usbcore: deregistering interface driver ndiswrapper
Aug 28 14:27:32 serv kernel: [ 1870.225803] ndiswrapper (loader_exit:870): Exit
Aug 28 14:27:32 serv kernel: [ 1870.225808] ndiswrapper (usb_exit:1482): Exit
Aug 28 14:27:32 serv kernel: [ 1870.225819] ndiswrapper (notifier_event:1761): Enter 0x9
Aug 28 14:27:32 serv kernel: [ 1870.225823] ndiswrapper (notifier_event:1761): Enter 0x2
Aug 28 14:27:32 serv kernel: [ 1870.225827] ndiswrapper (notifier_event:1761): Enter 0x6
Aug 28 14:27:32 serv kernel: [ 1870.225831] ndiswrapper (notifier_event:1761): Enter 0x11
Aug 28 14:27:32 serv kernel: [ 1870.225836] ndiswrapper (notifier_event:1761): Enter 0x9
Aug 28 14:27:32 serv kernel: [ 1870.225840] ndiswrapper (notifier_event:1761): Enter 0x2
Aug 28 14:27:32 serv kernel: [ 1870.225844] ndiswrapper (notifier_event:1761): Enter 0x6
Aug 28 14:27:32 serv kernel: [ 1870.225848] ndiswrapper (notifier_event:1761): Enter 0x11
Aug 28 14:27:32 serv kernel: [ 1870.225852] ndiswrapper (notifier_event:1761): Enter 0x9
Aug 28 14:27:32 serv kernel: [ 1870.225856] ndiswrapper (notifier_event:1761): Enter 0x2
Aug 28 14:27:32 serv kernel: [ 1870.225860] ndiswrapper (notifier_event:1761): Enter 0x6
Aug 28 14:27:32 serv kernel: [ 1870.225864] ndiswrapper (notifier_event:1761): Enter 0x11
Aug 28 14:27:32 serv kernel: [ 1870.225868] ndiswrapper (notifier_event:1761): Enter 0x9
Aug 28 14:27:32 serv kernel: [ 1870.225872] ndiswrapper (notifier_event:1761): Enter 0x2
Aug 28 14:27:32 serv kernel: [ 1870.225875] ndiswrapper (notifier_event:1761): Enter 0x6
Aug 28 14:27:32 serv kernel: [ 1870.225879] ndiswrapper (notifier_event:1761): Enter 0x11
Aug 28 14:27:32 serv kernel: [ 1870.225922] ndiswrapper (ndis_exit:3021): Enter 
Aug 28 14:27:32 serv kernel: [ 1870.225954] ndiswrapper (ndis_exit:3024): Exit
Aug 28 14:27:32 serv kernel: [ 1870.225959] ndiswrapper (ntoskernel_exit:2590): Enter 
Aug 28 14:27:32 serv kernel: [ 1870.225963] ndiswrapper (ntoskernel_exit:2593): freeing timers
Aug 28 14:27:32 serv kernel: [ 1870.225967] ndiswrapper (ntoskernel_exit:2613): freeing MDLs
Aug 28 14:27:32 serv kernel: [ 1870.226041] ndiswrapper (ntoskernel_exit:2632): freeing callbacks
Aug 28 14:27:32 serv kernel: [ 1870.226075] ndiswrapper (ntoskernel_exit:2661): Enter freeing objects
Aug 28 14:27:32 serv kernel: [ 1870.226081] ndiswrapper (ntoskernel_exit:2676): Exit
Aug 28 14:27:40 serv loadndisdriver: loadndisdriver: load_device(432): 1002, 5a14, 1002, 5a14
Aug 28 14:27:40 serv loadndisdriver: loadndisdriver: load_device(445): .
Aug 28 14:27:40 serv loadndisdriver: loadndisdriver: load_device(445): ..
Aug 28 14:27:40 serv loadndisdriver: loadndisdriver: load_device(456): 0000, 0000, 0000, 0000
Aug 28 14:27:40 serv loadndisdriver: loadndisdriver: load_device(458): res: -1
Aug 28 14:27:40 serv loadndisdriver: loadndisdriver: load_device(432): 1002, 439d, 1002, 439d
Aug 28 14:27:40 serv loadndisdriver: loadndisdriver: load_device(445): .
Aug 28 14:27:40 serv loadndisdriver: loadndisdriver: load_device(445): ..
Aug 28 14:27:40 serv loadndisdriver: loadndisdriver: load_device(456): 0000, 0000, 0000, 0000
Aug 28 14:27:40 serv loadndisdriver: loadndisdriver: load_device(458): res: -1
Aug 28 14:27:40 serv kernel: [ 1877.712599] ndiswrapper version 1.58rc1 loaded (smp=yes, preempt=no)
Aug 28 14:27:40 serv kernel: [ 1877.712603] ndiswrapper (ntoskernel_init:2513): 129734706134908210
Aug 28 14:27:40 serv kernel: [ 1877.712693] ndiswrapper (ntoskernel_init:2538): ntos_wq: ffff8801de630e40
Aug 28 14:27:40 serv kernel: [ 1877.712697] ndiswrapper (add_bus_driver:174): bus driver PCI is at ffff8801fd990c30
Aug 28 14:27:40 serv kernel: [ 1877.712700] ndiswrapper (add_bus_driver:174): bus driver USB is at ffff8801fd990630
Aug 28 14:27:40 serv kernel: [ 1877.712756] ndiswrapper (ntoskernel_init:2552): ffff8801de75c800
Aug 28 14:27:40 serv kernel: [ 1877.712812] ndiswrapper (ndis_init:3014): ndis_wq: ffff880227822300
Aug 28 14:27:40 serv kernel: [ 1877.712888] ndiswrapper (wrapndis_init:2171): wrapndis_wq: ffff880227822b40
Aug 28 14:27:40 serv kernel: [ 1877.712892] ndiswrapper (notifier_event:1761): Enter 0x5
Aug 28 14:27:40 serv kernel: [ 1877.712895] ndiswrapper (notifier_event:1761): Enter 0x1
Aug 28 14:27:40 serv kernel: [ 1877.712897] ndiswrapper (notifier_event:1761): Enter 0x5
Aug 28 14:27:40 serv kernel: [ 1877.712899] ndiswrapper (notifier_event:1761): Enter 0x1
Aug 28 14:27:40 serv kernel: [ 1877.712902] ndiswrapper (notifier_event:1761): Enter 0x5
Aug 28 14:27:40 serv kernel: [ 1877.712904] ndiswrapper (notifier_event:1761): Enter 0x1
Aug 28 14:27:40 serv kernel: [ 1877.712906] ndiswrapper (notifier_event:1761): Enter 0x5
Aug 28 14:27:40 serv kernel: [ 1877.712909] ndiswrapper (notifier_event:1761): Enter 0x1
Aug 28 14:27:40 serv kernel: [ 1877.712999] ndiswrapper (wrap_pnp_start_pci_device:573): Enter called for 1002:5a14:1002:5a14
Aug 28 14:27:40 serv kernel: [ 1877.713004] ndiswrapper (load_wrap_device:671): Enter 1002, 5a14, 1002, 5a14
Aug 28 14:27:40 serv kernel: [ 1877.713008] ndiswrapper (load_wrap_device:687): 1002, 5a14, 1002, 5a14, 0005
Aug 28 14:27:40 serv kernel: [ 1877.714564] ndiswrapper (wrapper_ioctl:753): Enter cmd: 1074359808
Aug 28 14:27:40 serv kernel: [ 1877.714574] ndiswrapper (wrapper_ioctl:764): 0000, 0000, 0000, 0000
Aug 28 14:27:40 serv kernel: [ 1877.714585] ndiswrapper (wrapper_ioctl:814): Exit
Aug 28 14:27:40 serv kernel: [ 1877.714600] ndiswrapper (load_wrap_device:713): Exit
Aug 28 14:27:40 serv kernel: [ 1877.714608] ndiswrapper (wrap_pnp_start_pci_device:582): Exit
Aug 28 14:27:40 serv kernel: [ 1877.714614] ndiswrapper (wrapper_ioctl_release:819): Enter 
Aug 28 14:27:40 serv kernel: [ 1877.714643] ndiswrapper (wrap_pnp_start_pci_device:573): Enter called for 1002:439d:1002:439d
Aug 28 14:27:40 serv kernel: [ 1877.714650] ndiswrapper (load_wrap_device:671): Enter 1002, 439d, 1002, 439d
Aug 28 14:27:40 serv kernel: [ 1877.714657] ndiswrapper (load_wrap_device:687): 1002, 439d, 1002, 439d, 0005
Aug 28 14:27:40 serv kernel: [ 1877.715943] ndiswrapper (wrapper_ioctl:753): Enter cmd: 1074359808
Aug 28 14:27:40 serv kernel: [ 1877.715950] ndiswrapper (wrapper_ioctl:764): 0000, 0000, 0000, 0000
Aug 28 14:27:40 serv kernel: [ 1877.715957] ndiswrapper (wrapper_ioctl:814): Exit
Aug 28 14:27:40 serv kernel: [ 1877.715977] ndiswrapper (load_wrap_device:713): Exit
Aug 28 14:27:40 serv kernel: [ 1877.715983] ndiswrapper (wrapper_ioctl_release:819): Enter 
Aug 28 14:27:40 serv kernel: [ 1877.715992] ndiswrapper (wrap_pnp_start_pci_device:582): Exit
Aug 28 14:27:40 serv kernel: [ 1877.716046] ndiswrapper (wrap_pnp_start_pci_device:573): Enter called for 1002:4384:0000:0000
Aug 28 14:27:40 serv kernel: [ 1877.716058] ndiswrapper (load_wrap_device:671): Enter 1002, 4384, 0000, 0000
Aug 28 14:27:40 serv kernel: [ 1877.716070] ndiswrapper (load_wrap_device:687): 1002, 4384, 0000, 0000, 0005
Aug 28 14:27:40 serv loadndisdriver: loadndisdriver: load_device(432): 1002, 4384, 0000, 0000
Aug 28 14:27:40 serv loadndisdriver: loadndisdriver: load_device(445): .
Aug 28 14:27:40 serv loadndisdriver: loadndisdriver: load_device(445): ..
Aug 28 14:27:40 serv loadndisdriver: loadndisdriver: load_device(456): 0000, 0000, 0000, 0000
Aug 28 14:27:40 serv loadndisdriver: loadndisdriver: load_device(458): res: -1
Aug 28 14:27:40 serv loadndisdriver: loadndisdriver: load_device(432): 1022, 1600, 0000, 0000
Aug 28 14:27:40 serv loadndisdriver: loadndisdriver: load_device(445): .
Aug 28 14:27:40 serv loadndisdriver: loadndisdriver: load_device(445): ..
Aug 28 14:27:40 serv loadndisdriver: loadndisdriver: load_device(456): 0000, 0000, 0000, 0000
Aug 28 14:27:40 serv loadndisdriver: loadndisdriver: load_device(458): res: -1
Aug 28 14:27:40 serv loadndisdriver: loadndisdriver: load_device(432): 1022, 1601, 0000, 0000
Aug 28 14:27:40 serv loadndisdriver: loadndisdriver: load_device(445): .
Aug 28 14:27:40 serv loadndisdriver: loadndisdriver: load_device(445): ..
Aug 28 14:27:40 serv kernel: [ 1877.717194] ndiswrapper (wrapper_ioctl:753): Enter cmd: 1074359808
Aug 28 14:27:40 serv kernel: [ 1877.717201] ndiswrapper (wrapper_ioctl:764): 0000, 0000, 0000, 0000
Aug 28 14:27:40 serv kernel: [ 1877.717208] ndiswrapper (wrapper_ioctl:814): Exit
Aug 28 14:27:40 serv kernel: [ 1877.717226] ndiswrapper (wrapper_ioctl_release:819): Enter 
Aug 28 14:27:40 serv kernel: [ 1877.717293] ndiswrapper (load_wrap_device:713): Exit
Aug 28 14:27:40 serv kernel: [ 1877.717301] ndiswrapper (wrap_pnp_start_pci_device:582): Exit
Aug 28 14:27:40 serv kernel: [ 1877.717404] ndiswrapper (wrap_pnp_start_pci_device:573): Enter called for 1022:1600:0000:0000
Aug 28 14:27:40 serv loadndisdriver: loadndisdriver: load_device(456): 0000, 0000, 0000, 0000
Aug 28 14:27:40 serv kernel: [ 1877.717412] ndiswrapper (load_wrap_device:671): Enter 1022, 1600, 0000, 0000
Aug 28 14:27:40 serv loadndisdriver: loadndisdriver: load_device(458): res: -1
Aug 28 14:27:40 serv kernel: [ 1877.717421] ndiswrapper (load_wrap_device:687): 1022, 1600, 0000, 0000, 0005
Aug 28 14:27:40 serv kernel: [ 1877.718527] ndiswrapper (wrapper_ioctl:753): Enter cmd: 1074359808
Aug 28 14:27:40 serv kernel: [ 1877.718534] ndiswrapper (wrapper_ioctl:764): 0000, 0000, 0000, 0000
Aug 28 14:27:40 serv kernel: [ 1877.718540] ndiswrapper (wrapper_ioctl:814): Exit
Aug 28 14:27:40 serv kernel: [ 1877.718560] ndiswrapper (wrapper_ioctl_release:819): Enter 
Aug 28 14:27:40 serv kernel: [ 1877.718625] ndiswrapper (load_wrap_device:713): Exit
Aug 28 14:27:40 serv kernel: [ 1877.718633] ndiswrapper (wrap_pnp_start_pci_device:582): Exit
Aug 28 14:27:40 serv kernel: [ 1877.718830] ndiswrapper (wrap_pnp_start_pci_device:573): Enter called for 1022:1601:0000:0000
Aug 28 14:27:40 serv kernel: [ 1877.718833] ndiswrapper (load_wrap_device:671): Enter 1022, 1601, 0000, 0000
Aug 28 14:27:40 serv kernel: [ 1877.718836] ndiswrapper (load_wrap_device:687): 1022, 1601, 0000, 0000, 0005
Aug 28 14:27:40 serv kernel: [ 1877.720179] ndiswrapper (wrapper_ioctl:753): Enter cmd: 1074359808
Aug 28 14:27:40 serv kernel: [ 1877.720188] ndiswrapper (wrapper_ioctl:764): 0000, 0000, 0000, 0000
Aug 28 14:27:40 serv kernel: [ 1877.720195] ndiswrapper (wrapper_ioctl:814): Exit
Aug 28 14:27:40 serv kernel: [ 1877.720209] ndiswrapper (load_wrap_device:713): Exit
Aug 28 14:27:40 serv kernel: [ 1877.720215] ndiswrapper (wrapper_ioctl_release:819): Enter 
Aug 28 14:27:40 serv kernel: [ 1877.720223] ndiswrapper (wrap_pnp_start_pci_device:582): Exit
Aug 28 14:27:40 serv loadndisdriver: loadndisdriver: load_device(432): 1022, 1602, 0000, 0000
Aug 28 14:27:40 serv loadndisdriver: loadndisdriver: load_device(445): .
Aug 28 14:27:40 serv loadndisdriver: loadndisdriver: load_device(445): ..
Aug 28 14:27:40 serv loadndisdriver: loadndisdriver: load_device(456): 0000, 0000, 0000, 0000
Aug 28 14:27:40 serv loadndisdriver: loadndisdriver: load_device(458): res: -1
Aug 28 14:27:40 serv loadndisdriver: loadndisdriver: load_device(432): 1022, 1605, 0000, 0000
Aug 28 14:27:40 serv loadndisdriver: loadndisdriver: load_device(445): .
Aug 28 14:27:40 serv loadndisdriver: loadndisdriver: load_device(445): ..
Aug 28 14:27:40 serv loadndisdriver: loadndisdriver: load_device(456): 0000, 0000, 0000, 0000
Aug 28 14:27:40 serv loadndisdriver: loadndisdriver: load_device(458): res: -1
Aug 28 14:27:40 serv kernel: [ 1877.720343] ndiswrapper (wrap_pnp_start_pci_device:573): Enter called for 1022:1602:0000:0000
Aug 28 14:27:40 serv kernel: [ 1877.720346] ndiswrapper (load_wrap_device:671): Enter 1022, 1602, 0000, 0000
Aug 28 14:27:40 serv kernel: [ 1877.720350] ndiswrapper (load_wrap_device:687): 1022, 1602, 0000, 0000, 0005
Aug 28 14:27:40 serv kernel: [ 1877.721570] ndiswrapper (wrapper_ioctl:753): Enter cmd: 1074359808
Aug 28 14:27:40 serv kernel: [ 1877.721578] ndiswrapper (wrapper_ioctl:764): 0000, 0000, 0000, 0000
Aug 28 14:27:40 serv kernel: [ 1877.721585] ndiswrapper (wrapper_ioctl:814): Exit
Aug 28 14:27:40 serv kernel: [ 1877.721605] ndiswrapper (wrapper_ioctl_release:819): Enter 
Aug 28 14:27:40 serv kernel: [ 1877.721671] ndiswrapper (load_wrap_device:713): Exit
Aug 28 14:27:40 serv kernel: [ 1877.721679] ndiswrapper (wrap_pnp_start_pci_device:582): Exit
Aug 28 14:27:40 serv kernel: [ 1877.721866] ndiswrapper (wrap_pnp_start_pci_device:573): Enter called for 1022:1605:0000:0000
Aug 28 14:27:40 serv kernel: [ 1877.721871] ndiswrapper (load_wrap_device:671): Enter 1022, 1605, 0000, 0000
Aug 28 14:27:40 serv kernel: [ 1877.721876] ndiswrapper (load_wrap_device:687): 1022, 1605, 0000, 0000, 0005
Aug 28 14:27:40 serv kernel: [ 1877.723120] ndiswrapper (wrapper_ioctl:753): Enter cmd: 1074359808
Aug 28 14:27:40 serv kernel: [ 1877.723128] ndiswrapper (wrapper_ioctl:764): 0000, 0000, 0000, 0000
Aug 28 14:27:40 serv kernel: [ 1877.723135] ndiswrapper (wrapper_ioctl:814): Exit
Aug 28 14:27:40 serv kernel: [ 1877.723152] ndiswrapper (wrapper_ioctl_release:819): Enter 
Aug 28 14:27:40 serv kernel: [ 1877.723218] ndiswrapper (load_wrap_device:713): Exit
Aug 28 14:27:40 serv kernel: [ 1877.723226] ndiswrapper (wrap_pnp_start_pci_device:582): Exit
Aug 28 14:27:40 serv kernel: [ 1877.723277] ndiswrapper (wrap_pnp_start_pci_device:573): Enter called for 168c:001a:17f9:0018
Aug 28 14:27:40 serv kernel: [ 1877.723288] ndiswrapper (load_wrap_device:671): Enter 168c, 001a, 17f9, 0018
Aug 28 14:27:40 serv kernel: [ 1877.723296] ndiswrapper (load_wrap_device:687): 168c, 001a, 17f9, 0018, 0005
Aug 28 14:27:40 serv loadndisdriver: loadndisdriver: load_device(432): 168c, 001a, 17f9, 0018
Aug 28 14:27:40 serv loadndisdriver: loadndisdriver: load_device(445): .
Aug 28 14:27:40 serv loadndisdriver: loadndisdriver: load_device(445): ..
Aug 28 14:27:40 serv loadndisdriver: loadndisdriver: load_device(456): 0000, 0000, 0000, 0000
Aug 28 14:27:40 serv loadndisdriver: loadndisdriver: load_device(458): res: -1
Aug 28 14:27:40 serv loadndisdriver: loadndisdriver: load_device(432): 0b05, 17ab, 0000, 0000
Aug 28 14:27:40 serv loadndisdriver: loadndisdriver: load_device(445): .
Aug 28 14:27:40 serv loadndisdriver: loadndisdriver: load_device(445): ..
Aug 28 14:27:40 serv loadndisdriver: loadndisdriver: load_device(456): 0000, 0000, 0000, 0000
Aug 28 14:27:40 serv loadndisdriver: loadndisdriver: load_device(458): res: -1
Aug 28 14:27:40 serv kernel: [ 1877.724478] ndiswrapper (wrapper_ioctl:753): Enter cmd: 1074359808
Aug 28 14:27:40 serv kernel: [ 1877.724485] ndiswrapper (wrapper_ioctl:764): 0000, 0000, 0000, 0000
Aug 28 14:27:40 serv kernel: [ 1877.724495] ndiswrapper (wrapper_ioctl:814): Exit
Aug 28 14:27:40 serv kernel: [ 1877.724509] ndiswrapper (load_wrap_device:713): Exit
Aug 28 14:27:40 serv kernel: [ 1877.724516] ndiswrapper (wrap_pnp_start_pci_device:582): Exit
Aug 28 14:27:40 serv kernel: [ 1877.724521] ndiswrapper (wrapper_ioctl_release:819): Enter 
Aug 28 14:27:40 serv kernel: [ 1877.724611] ndiswrapper (wrap_pnp_start_usb_device:622): Enter 0b05, 17ab, 0000
Aug 28 14:27:40 serv kernel: [ 1877.724620] ndiswrapper (load_wrap_device:671): Enter 0b05, 17ab, 0000, 0000
Aug 28 14:27:40 serv kernel: [ 1877.724628] ndiswrapper (load_wrap_device:687): 0b05, 17ab, 0000, 0000, 000f
Aug 28 14:27:40 serv kernel: [ 1877.725947] ndiswrapper (wrapper_ioctl:753): Enter cmd: 1074359808
Aug 28 14:27:40 serv kernel: [ 1877.725955] ndiswrapper (wrapper_ioctl:764): 0000, 0000, 0000, 0000
Aug 28 14:27:40 serv kernel: [ 1877.725965] ndiswrapper (wrapper_ioctl:814): Exit
Aug 28 14:27:40 serv kernel: [ 1877.725979] ndiswrapper (load_wrap_device:713): Exit
Aug 28 14:27:40 serv kernel: [ 1877.725987] ndiswrapper (wrap_pnp_start_usb_device:641):           (null)
Aug 28 14:27:40 serv kernel: [ 1877.725992] ndiswrapper (wrapper_ioctl_release:819): Enter 
Aug 28 14:27:40 serv kernel: [ 1877.726001] ndiswrapper (wrap_pnp_start_usb_device:656): ret: -19
Aug 28 14:27:40 serv kernel: [ 1877.726006] ndiswrapper (wrap_pnp_start_usb_device:658): Exit
Aug 28 14:27:40 serv kernel: [ 1877.726060] usbcore: registered new interface driver ndiswrapper
Aug 28 14:27:40 serv kernel: [ 1877.726065] ndiswrapper (register_devices:639): Exit
Aug 28 14:27:40 serv kernel: [ 1877.726069] ndiswrapper (loader_init:853): Exit
Aug 28 14:27:40 serv kernel: [ 1877.726073] ndiswrapper (wrapper_init:101): Exit
Aug 28 14:29:17 serv kernel: [ 1975.033530] ndiswrapper (notifier_event:1761): Enter 0x9
Aug 28 14:29:17 serv kernel: [ 1975.036632] ndiswrapper (notifier_event:1761): Enter 0x2
Aug 28 14:29:17 serv kernel: [ 1975.037429] ndiswrapper (notifier_event:1761): Enter 0x6
Aug 28 14:29:17 serv kernel: [ 1975.037502] ndiswrapper (notifier_event:1761): Enter 0x11
Aug 28 14:29:18 serv kernel: [ 1976.116079] ndiswrapper (notifier_event:1761): Enter 0x6
```

---

### Post by chili555 on 2012-08-28
> Modules linked in: ndiswrapper(O+) pci_stub [COLOR="Red"]vboxpci[/COLOR](O) vboxnetadp(O) vboxnetfltAre you trying to get wireless networking going on a virtual machine? Did I miss something?

---

### Post by Lemons on 2012-08-28
Thats not what I was going for, but to be sure I disabled the startup of the virtualbox modules and get similar results (didn't have the debug version enabled this time):

```
Aug 28 16:35:13 serv kernel: [  306.581462] ndiswrapper version 1.58rc1 loaded (smp=yes, preempt=no)
Aug 28 16:35:13 serv kernel: [  306.627459] usbcore: registered new interface driver ndiswrapper
Aug 28 16:35:19 serv kernel: [  312.588195] usb 2-1: new high-speed USB device number 2 using ehci_hcd
Aug 28 16:35:19 serv mtp-probe: checking bus 2, device 2: "/sys/devices/pci0000:00/0000:00:13.2/usb2/2-1"
Aug 28 16:35:19 serv kernel: [  312.840136] usb 2-1: reset high-speed USB device number 2 using ehci_hcd
Aug 28 16:35:19 serv kernel: [  313.081206] ndiswrapper: driver netrtwlanu (Realtek Semiconductor Corp.,02/10/2012,1015.6.0210.2012) loaded
Aug 28 16:35:21 serv kernel: [  314.641688] wlan0: ethernet device c8:60:00:d4:9d:3d using NDIS driver: netrtwlanu, version: 0x1, NDIS version: 0x500, vendor: 'Realtek RTL8192C Wireless LAN USB NIC                                     ', 0B05:17AB.F.conf
Aug 28 16:35:21 serv kernel: [  314.641730] ndiswrapper (KeWaitForMultipleObjects:1119): attempt to wait with irql 2
Aug 28 16:35:21 serv kernel: [  314.641747] ndiswrapper (KeWaitForMultipleObjects:1119): attempt to wait with irql 2
Aug 28 16:35:21 serv kernel: [  314.641773] ndiswrapper (KeWaitForMultipleObjects:1119): attempt to wait with irql 2
Aug 28 16:35:21 serv kernel: [  314.641788] ndiswrapper (KeWaitForMultipleObjects:1119): attempt to wait with irql 2
Aug 28 16:35:21 serv kernel: [  314.641819] ndiswrapper (KeWaitForMultipleObjects:1119): attempt to wait with irql 2
Aug 28 16:35:21 serv kernel: [  314.641836] ndiswrapper (KeWaitForMultipleObjects:1119): attempt to wait with irql 2
Aug 28 16:35:21 serv kernel: [  314.641850] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2-PSK; AES/CCMP with WPA, WPA2, WPA2-PSK
Aug 28 16:35:21 serv kernel: [  314.641877] ndiswrapper (KeWaitForMultipleObjects:1119): attempt to wait with irql 2
Aug 28 16:35:21 serv kernel: [  314.641911] BUG: unable to handle kernel paging request at ffffffff00000000
Aug 28 16:35:21 serv kernel: [  314.641919] IP: [<ffffffff00000000>] 0xfffffffeffffffff
Aug 28 16:35:21 serv kernel: [  314.641930] PGD 1c07067 PUD 0 
Aug 28 16:35:21 serv kernel: [  314.641937] Oops: 0010 [#1] SMP 
Aug 28 16:35:21 serv kernel: [  314.641943] CPU 6 
Aug 28 16:35:21 serv kernel: [  314.641945] Modules linked in: ndiswrapper(O) ip6table_filter ip6_tables ebtable_nat ebtables ipt_MASQUERADE iptable_nat nf_nat nf_conntrack_ipv4 nf_defrag_ipv4 xt_state nf_conntrack ipt_REJECT xt_CHECKSUM iptable_mangle xt_tcpudp iptable_filter ip_tables x_tables bridge stp kvm_amd kvm rfcomm bnep bluetooth parport_pc ppdev dm_crypt binfmt_misc snd_hda_codec_realtek eeepc_wmi asus_wmi sparse_keymap nvidia(P) snd_hda_intel snd_hda_codec snd_hwdep snd_pcm snd_seq_midi cdc_acm snd_rawmidi snd_seq_midi_event snd_seq fam15h_power psmouse k10temp snd_timer serio_raw snd_seq_device edac_core edac_mce_amd snd sp5100_tco i2c_piix4 soundcore snd_page_alloc wmi mac_hid it87 hwmon_vid lp parport vesafb usbhid hid r8169 usb_storage
Aug 28 16:35:21 serv kernel: [  314.642036] 
Aug 28 16:35:21 serv kernel: [  314.642041] Pid: 47, comm: khubd Tainted: P           O 3.2.0-30-generic #48-Ubuntu To be filled by O.E.M. To be filled by O.E.M./M5A97
Aug 28 16:35:21 serv kernel: [  314.642052] RIP: 0010:[<ffffffff00000000>]  [<ffffffff00000000>] 0xfffffffeffffffff
Aug 28 16:35:21 serv kernel: [  314.642063] RSP: 0000:ffff88022fa450e0  EFLAGS: 00010282
Aug 28 16:35:21 serv kernel: [  314.642067] RAX: 0000000000000103 RBX: ffff88020b13e830 RCX: 0000000000000000
Aug 28 16:35:21 serv kernel: [  314.642072] RDX: 00000000bd404a80 RSI: ffff88020b13e830 RDI: ffffffffa0f2f4b0
Aug 28 16:35:21 serv kernel: [  314.642077] RBP: ffff88022fa450f0 R08: ffff8800bd404ba0 R09: 0000000000080e80
Aug 28 16:35:21 serv kernel: [  314.642081] R10: 00000000bd404a80 R11: 00000000ffffffff R12: ffff88020e1e3600
Aug 28 16:35:21 serv kernel: [  314.642086] R13: 0000000000000001 R14: ffff8801f921d3c0 R15: ffff88020e1e3600
Aug 28 16:35:21 serv kernel: [  314.642092] FS:  00007f5896e17700(0000) GS:ffff88023ed80000(0000) knlGS:00000000f77a2700
Aug 28 16:35:21 serv kernel: [  314.642097] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
Aug 28 16:35:21 serv kernel: [  314.642102] CR2: ffffffff00000000 CR3: 000000020664b000 CR4: 00000000000406e0
Aug 28 16:35:21 serv kernel: [  314.642107] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
Aug 28 16:35:21 serv kernel: [  314.642112] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
Aug 28 16:35:21 serv kernel: [  314.642117] Process khubd (pid: 47, threadinfo ffff88022fa44000, task ffff88022fa49700)
Aug 28 16:35:21 serv kernel: [  314.642121] Stack:
Aug 28 16:35:21 serv kernel: [  314.642124]  0000000000000001 000000012fa452a0 ffff88022fa45110 ffffffffa0f2f3c8
Aug 28 16:35:21 serv kernel: [  314.642135]  ffffc90014991000 ffffc90014991000 0000000000000000 ffffc90014810dc6
Aug 28 16:35:21 serv kernel: [  314.642144]  ffffc90014991000 ffffc90000000000 0000000000000001 0000000181162efd
Aug 28 16:35:21 serv kernel: [  314.642153] Call Trace:
Aug 28 16:35:21 serv kernel: [  314.642178]  [<ffffffffa0f2f3c8>] win2lin_IofCallDriver_2+0x18/0x20 [ndiswrapper]
Aug 28 16:35:21 serv kernel: [  314.642197]  [<ffffffff8165a6ae>] ? _raw_spin_lock_irqsave+0x2e/0x40
Aug 28 16:35:21 serv kernel: [  314.642217]  [<ffffffffa0f2fe92>] ? lin2win6+0x22/0x28 [ndiswrapper]
Aug 28 16:35:21 serv kernel: [  314.642227]  [<ffffffff81658f1d>] ? mutex_lock+0x1d/0x50
Aug 28 16:35:21 serv kernel: [  314.642254]  [<ffffffffa0f25f34>] ? mp_request+0x184/0x420 [ndiswrapper]
Aug 28 16:35:21 serv kernel: [  314.642273]  [<ffffffffa0f1079a>] ? set_iw_encr_mode+0x6a/0x100 [ndiswrapper]
Aug 28 16:35:21 serv kernel: [  314.642291]  [<ffffffffa0f11781>] ? set_default_iw_params+0x81/0x90 [ndiswrapper]
Aug 28 16:35:21 serv kernel: [  314.642319]  [<ffffffffa0f2955e>] ? NdisDispatchPnp+0xb6e/0xd90 [ndiswrapper]
Aug 28 16:35:21 serv kernel: [  314.642345]  [<ffffffffa0f1eb24>] ? IoInitializeIrp+0x34/0x70 [ndiswrapper]
Aug 28 16:35:21 serv kernel: [  314.642365]  [<ffffffffa0f2fb48>] ? win2lin_NdisDispatchPnp_2+0x18/0x20 [ndiswrapper]
Aug 28 16:35:21 serv kernel: [  314.642384]  [<ffffffffa0f2fb30>] ? win2lin_NdisDispatchDeviceControl_2+0x20/0x20 [ndiswrapper]
Aug 28 16:35:21 serv kernel: [  314.642402]  [<ffffffffa0f2fdfd>] ? lin2win2+0xd/0x20 [ndiswrapper]
Aug 28 16:35:21 serv kernel: [  314.642410]  [<ffffffff8165a529>] ? _raw_spin_unlock_bh+0x19/0x20
Aug 28 16:35:21 serv kernel: [  314.642434]  [<ffffffffa0f1f30e>] ? IofCallDriver+0x6e/0xc0 [ndiswrapper]
Aug 28 16:35:21 serv kernel: [  314.642460]  [<ffffffffa0f21177>] ? IoSendIrpTopDev+0xd7/0x120 [ndiswrapper]
Aug 28 16:35:21 serv kernel: [  314.642485]  [<ffffffffa0f213cc>] ? alloc_pdo+0x6c/0xf0 [ndiswrapper]
Aug 28 16:35:21 serv kernel: [  314.642512]  [<ffffffffa0f2155a>] ? wrap_pnp_start_device+0x10a/0x1e0 [ndiswrapper]
Aug 28 16:35:21 serv kernel: [  314.642539]  [<ffffffffa0f21f2f>] ? wrap_pnp_start_usb_device+0xef/0x120 [ndiswrapper]
Aug 28 16:35:21 serv kernel: [  314.642548]  [<ffffffff81400ba6>] ? __pm_runtime_set_status+0x146/0x230
Aug 28 16:35:21 serv kernel: [  314.642556]  [<ffffffff814009d9>] ? __pm_runtime_resume+0x69/0x90
Aug 28 16:35:21 serv kernel: [  314.642565]  [<ffffffff81498fa3>] ? usb_probe_interface+0xd3/0x1e0
Aug 28 16:35:21 serv kernel: [  314.642573]  [<ffffffff813f5a28>] ? really_probe+0x68/0x190
Aug 28 16:35:21 serv kernel: [  314.642580]  [<ffffffff813f5cb5>] ? driver_probe_device+0x45/0x70
Aug 28 16:35:21 serv kernel: [  314.642587]  [<ffffffff813f5de3>] ? __device_attach+0x53/0x60
Aug 28 16:35:21 serv kernel: [  314.642593]  [<ffffffff813f5d90>] ? __driver_attach+0xb0/0xb0
Aug 28 16:35:21 serv kernel: [  314.642599]  [<ffffffff813f479c>] ? bus_for_each_drv+0x5c/0x90
Aug 28 16:35:21 serv kernel: [  314.642606]  [<ffffffff813f5c27>] ? device_attach+0xa7/0xc0
Aug 28 16:35:21 serv kernel: [  314.642612]  [<ffffffff813f51cd>] ? bus_probe_device+0x2d/0x50
Aug 28 16:35:21 serv kernel: [  314.642620]  [<ffffffff813f329f>] ? device_add+0x2df/0x3e0
Aug 28 16:35:21 serv kernel: [  314.642628]  [<ffffffff814973d5>] ? usb_set_configuration+0x5a5/0x6e0
Aug 28 16:35:21 serv kernel: [  314.642637]  [<ffffffff814a0be3>] ? generic_probe+0x43/0xa0
Aug 28 16:35:21 serv kernel: [  314.642644]  [<ffffffff814990df>] ? usb_probe_device+0x2f/0x60
Aug 28 16:35:21 serv kernel: [  314.642651]  [<ffffffff813f5a28>] ? really_probe+0x68/0x190
Aug 28 16:35:21 serv kernel: [  314.642657]  [<ffffffff813f5cb5>] ? driver_probe_device+0x45/0x70
Aug 28 16:35:21 serv kernel: [  314.642664]  [<ffffffff813f5de3>] ? __device_attach+0x53/0x60
Aug 28 16:35:21 serv kernel: [  314.642670]  [<ffffffff813f5d90>] ? __driver_attach+0xb0/0xb0
Aug 28 16:35:21 serv kernel: [  314.642676]  [<ffffffff813f479c>] ? bus_for_each_drv+0x5c/0x90
Aug 28 16:35:21 serv kernel: [  314.642683]  [<ffffffff813f5c27>] ? device_attach+0xa7/0xc0
Aug 28 16:35:21 serv kernel: [  314.642689]  [<ffffffff813f51cd>] ? bus_probe_device+0x2d/0x50
Aug 28 16:35:21 serv kernel: [  314.642697]  [<ffffffff813f329f>] ? device_add+0x2df/0x3e0
Aug 28 16:35:21 serv kernel: [  314.642704]  [<ffffffff8148fa99>] ? usb_new_device+0x159/0x1a0
Aug 28 16:35:21 serv kernel: [  314.642711]  [<ffffffff81490688>] ? hub_port_connect_change+0x478/0x6e0
Aug 28 16:35:21 serv kernel: [  314.642719]  [<ffffffff81490da4>] ? hub_events+0x4b4/0x630
Aug 28 16:35:21 serv kernel: [  314.642727]  [<ffffffff81657ebc>] ? __schedule+0x3cc/0x6f0
Aug 28 16:35:21 serv kernel: [  314.642734]  [<ffffffff81490f55>] ? hub_thread+0x35/0x180
Aug 28 16:35:21 serv kernel: [  314.642742]  [<ffffffff8108aae0>] ? add_wait_queue+0x60/0x60
Aug 28 16:35:21 serv kernel: [  314.642749]  [<ffffffff81490f20>] ? hub_events+0x630/0x630
Aug 28 16:35:21 serv kernel: [  314.642755]  [<ffffffff8108a03c>] ? kthread+0x8c/0xa0
Aug 28 16:35:21 serv kernel: [  314.642763]  [<ffffffff81664b74>] ? kernel_thread_helper+0x4/0x10
Aug 28 16:35:21 serv kernel: [  314.642771]  [<ffffffff81089fb0>] ? flush_kthread_worker+0xa0/0xa0
Aug 28 16:35:21 serv kernel: [  314.642778]  [<ffffffff81664b70>] ? gs_change+0x13/0x13
Aug 28 16:35:21 serv kernel: [  314.642782] Code:  Bad RIP value.
Aug 28 16:35:21 serv kernel: [  314.642794] RIP  [<ffffffff00000000>] 0xfffffffeffffffff
Aug 28 16:35:21 serv kernel: [  314.642803]  RSP <ffff88022fa450e0>
Aug 28 16:35:21 serv kernel: [  314.642806] CR2: ffffffff00000000
Aug 28 16:35:21 serv kernel: [  314.642811] ---[ end trace 65bda04ead1caa36 ]---
```

---

### Post by chili555 on 2012-08-29
If you can establish that the cause of the kernel oops is indeed ndiswrapper, by removing it from /etc/modules and blacklisting it, then it's a genuine bug you can file against ndiswrapper.

I have no further suggestions aside from a different device,

---

### Post by Lemons on 2012-08-29
I'll work on coming up with a bug report. Thanks again for your help, really appreciated it.

---

