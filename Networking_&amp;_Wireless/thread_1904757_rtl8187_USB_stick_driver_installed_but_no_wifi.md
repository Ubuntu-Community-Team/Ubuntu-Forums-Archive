---
title: "rtl8187 USB stick driver installed but no wifi"
date: 2012-01-05
forum: Networking &amp; Wireless
---

### Post by Kyslosh on 2012-01-05
Hello all since I'm trying to get this work for 1 day I decide to write here for help.

I bought USB wireless stick for longer distances (WL-1600USB).

I installed driver (I hope sucessfuly) rtl8187 ([http://linuxwireless.org/](http://linuxwireless.org/))

My problem is that I do not see my device in either iwconfig or ifconfig (as I was expecting wlan1 or so...)

```

**lsusb**
Bus 002 Device 009: ID 1b75:8189 Ovislink Corp. 
Bus 002 Device 004: ID 1bcf:280c Sunplus Innovation Technology Inc. 
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 147e:1002 Upek 
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


**lsusb -v | grep -A 20 "Device 009"**
Bus 002 Device 009: ID 1b75:8189 Ovislink Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x1b75 Ovislink Corp.
  idProduct          0x8189 
  bcdDevice            2.00
  iManufacturer           1 Manufacturer_Realtek
  iProduct                2 AirLive WL1600USB
  iSerial                 3 00e04c000001
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           81
    bNumInterfaces          1

**lsmod | grep rtl8187**
rtl8187                53021  0 
eeprom_93cx6            1656  1 rtl8187
mac80211              309235  4 rtl8187,rtl8192ce,rtl8192c_common,rtlwifi
cfg80211              187835  3 rtl8187,rtlwifi,mac80211


```any advice to get my AirLive to work? (wlan1...)

---

### Post by chili555 on 2012-01-05
I love a mystery!

Let's be sure that rtl8187 is correct for your device (I doubt it). Please run and post:```
modinfo rtl8187 | grep 1B75
```> Bus 002 Device 009: ID [COLOR="Red"]1b75[/COLOR]:8189 Ovislink Corp. Where did you download the file you compiled? compat-wireless-2.6.tar.bz2?? I'd like to examine and build it myself.

---

### Post by chili555 on 2012-01-05
Here is what I have so far:> # modinfo drivers/net/wireless/rtl818x/rtl8187/rtl8187.ko | grep 1B75
alias:          usb:v[COLOR="Red"]1B75[/COLOR]p8187d*dc*dsc*dp*ic*isc*ip*
Notice 818[COLOR="Red"]9[/COLOR] is not listed.

------------
Note to chili: rtl8187/dev.c
RTL8187 or RTL8187B or neither??

---

### Post by Kyslosh on 2012-01-05
on this site: [http://linuxwireless.org/en/users/Drivers/rtl8187](http://linuxwireless.org/en/users/Drivers/rtl8187)
it says my device (chip) is supported
[rtl8187]("http://linuxwireless.org/en/users/Drivers/rtl8187")   AirLive   WL-1600USB   [COLOR=Red]0x1b75[/COLOR]   0x8187

I also have PCI wifi card from manufacturer that wifi works fine.
what I did is :)
downloaded latest "driver" pack from compact-wireless site and installed/built it as they have on page.

I have in my laptop rtl8189 as you say by default that wireless works fine (PCI). --WORKS

I need to run my wifi stick :) AirLive WL-1600USB rtl8187 chip.

I guess I just have problem to register my net_device or somewhat...

recently I installed AirDriver-ng to see if that can help, that program sees my USB device.

---

### Post by chili555 on 2012-01-05
> on this site: [http://linuxwireless.org/en/users/Drivers/rtl8187](http://linuxwireless.org/en/users/Drivers/rtl8187)
it says my device (chip) is supported
rtl8187 AirLive WL-1600USB 0x1b75 0x8187But that's NOT your device!> idVendor           0x[COLOR="Red"]1b75[/COLOR] Ovislink Corp.
  idProduct          0x[COLOR="Red"]818**9**[/COLOR] 
  bcdDevice            2.00
  iManufacturer           1 Manufacturer_Realtek
  iProduct                2 AirLive WL1600USB> I guess I just have problem to register my net_device or somewhat...Correct. The driver you built doesn't recognize the device you have. it recognizes 8187 but not what you have, 818[COLOR="Red"]9[/COLOR]. As an experiment, we can edit the dev.c file and see if we can trick it into working. There are two options and we can try both. Of course, there is a third option and that is that rtl8187 is not correct and some other driver is. Let's try to get the driver to work. Open a terminal and navigate to the compat wireless folder, for example:```
cd Desktop/compat-wireless-2012-01-04/
sudo su
./scripts/driver-select restore
make clean
gedit drivers/net/wireless/rtl818x/rtl8187/dev.c
```Add one line as I have highlighted here:```
{USB_DEVICE(0x13d1, 0xabe6), .driver_info = DEVICE_RTL8187},
	/* Qcom */
	{USB_DEVICE(0x18E8, 0x6232), .driver_info = DEVICE_RTL8187},
	/* AirLive */
	{USB_DEVICE(0x1b75, 0x8187), .driver_info = DEVICE_RTL8187},
	[COLOR="Blue"]/* Airlive */
        {USB_DEVICE(0x1b75, 0x8189), .driver_info = DEVICE_RTL8187},[/COLOR]
	/* Linksys */
	{USB_DEVICE(0x1737, 0x0073), .driver_info = DEVICE_RTL8187B},
	{}
```Do not change or remove any other text; just add the highlighted line. Spacing, indentation, etc. are crucial. Proofread carefully twice, save and close gedit. Notice there are RTL8187 and RTL8187B devices; we don't know which yours is so we may have to try again if this doesn't work correctly. Now do:```
./scripts/driver-select rtl818x
make
make install
```Now does it work?

---

### Post by Kyslosh on 2012-01-05
I did what you suggested
results are kinda funny but sad for me...

both my PCI wifi card && USB wifi card do not work 

I rebooted (ofc I unloaded all wireless drivers) and did not put any back on (modprobe cmd). While rebooting (I mean new start).
OS did not boot up saying (picture). (picture is no needed while dmesg works ;))
```

[   11.520024] [fglrx] ioport: bar 4, base 0x6000, size: 0x100
[   11.520032] pci 0000:01:00.0: enabling device (0004 -> 0007)
[   11.520039] pci 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   11.520044] pci 0000:01:00.0: setting latency timer to 64
[   11.520146] [fglrx] Kernel PAT support is enabled
[   11.520159] [fglrx] module loaded - fglrx 8.92.6 [Nov  9 2011] with 1 minors
[   11.631037] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   11.631104] HDA Intel 0000:00:1b.0: irq 44 for MSI/MSI-X
[   11.631133] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   11.737126] Synaptics Touchpad, model: 1, fw: 8.0, id: 0x1e2b1, caps: 0xd001a3/0x940300/0x120c00
[   11.737138] serio: Synaptics pass-through port at isa0060/serio1/input0
[   11.770484] rtl8192ce 0000:07:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   11.770497] rtl8192ce 0000:07:00.0: setting latency timer to 64
[   11.770528] ------------[ cut here ]------------
[   11.770555] kernel BUG at /root/compat-w/net/mac80211/main.c:618!
[   11.770584] invalid opcode: 0000 [#1] SMP 
[   11.770606] last sysfs file: /sys/devices/platform/thinkpad_acpi/input/input6/event6/uevent
[   11.770645] CPU 0 
[   11.770655] Modules linked in: rtl8192ce(+) rtl8192c_common snd_hda_intel(+) snd_hda_codec fglrx(P) rtlwifi snd_hwdep snd_pcm_oss snd_mixer_oss mac80211 snd_pcm thinkpad_acpi snd_seq_dummy cfg80211 snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event rfkill snd_seq uvcvideo snd_timer compat snd_seq_device lp parport mac_hid videodev snd snd_page_alloc psmouse soundcore sdhci_pci serio_raw sdhci v4l2_compat_ioctl32 wmi nvram i915 drm_kms_helper drm r8169 ahci libahci intel_agp i2c_algo_bit mii intel_gtt video
[   11.770912] 
[   11.770922] Pid: 369, comm: modprobe Tainted: P            2.6.39.4 #1 LENOVO 44012RG/44012RG
[   11.770966] RIP: 0010:[<ffffffffa030af3a>]  [<ffffffffa030af3a>] ieee80211_alloc_hw+0x48a/0x4a0 [mac80211]
[   11.771017] RSP: 0018:ffff8801350a3c08  EFLAGS: 00010246
[   11.771035] RAX: ffff88013572a540 RBX: ffff880135728d40 RCX: 0000000000000000
[   11.771058] RDX: 0000000000000078 RSI: ffffffffa028f4cc RDI: ffff8801357280c0
[   11.771081] RBP: ffff8801350a3c28 R08: 0000000000000000 R09: ffff880135ba7c00
[   11.771104] R10: 0000000000000001 R11: dead000000200200 R12: ffff8801357281e0
[   11.771127] R13: ffffffffa039c080 R14: ffff880138cbe1f8 R15: 00000000fffffff4
[   11.771151] FS:  00007f8d745a8700(0000) GS:ffff88013fa00000(0000) knlGS:0000000000000000
[   11.771177] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
[   11.771196] CR2: 00007f8d745a6000 CR3: 0000000136ab2000 CR4: 00000000000406f0
[   11.771219] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[   11.771242] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[   11.771265] Process modprobe (pid: 369, threadinfo ffff8801350a2000, task ffff880137ddc440)
[   11.771291] Stack:
[   11.771298]  ffff8801350a3c28 00000000ffffffff ffffffffa01b2220 ffff880138cbe000
[   11.771324]  ffff8801350a3d08 ffffffffa039a03b ffff8801350a3c68 ffffffff817da07f
[   11.771351]  ffff8801350a3c78 ffffffff811bc5a9 ffffffff81c69084 ffff880135668280
[   11.771377] Call Trace:
[   11.772306]  [<ffffffffa039a03b>] rtl_pci_probe+0x103/0x17b1 [rtlwifi]
[   11.773205]  [<ffffffff811bc5a9>] ? sysfs_find_dirent+0x49/0x70
[   11.774089]  [<ffffffff81034d89>] ? default_spin_lock_flags+0x9/0x10
[   11.774978]  [<ffffffff81034d89>] ? default_spin_lock_flags+0x9/0x10
[   11.775858]  [<ffffffff81309daf>] local_pci_probe+0x5f/0xd0
[   11.776735]  [<ffffffff8130b021>] pci_device_probe+0x101/0x120
[   11.777617]  [<ffffffff813baa7a>] ? driver_sysfs_add+0x7a/0xb0
[   11.778499]  [<ffffffff813babd6>] driver_probe_device+0x96/0x1c0
[   11.779380]  [<ffffffff813bad00>] ? driver_probe_device+0x1c0/0x1c0
[   11.780255]  [<ffffffff813bad9b>] __driver_attach+0x9b/0xa0
[   11.781117]  [<ffffffff813bad00>] ? driver_probe_device+0x1c0/0x1c0
[   11.781983]  [<ffffffff813b9ff8>] bus_for_each_dev+0x68/0x90
[   11.783054]  [<ffffffff813ba9fe>] driver_attach+0x1e/0x20
[   11.784263]  [<ffffffff813ba2dd>] bus_add_driver+0xcd/0x270
[   11.785471]  [<ffffffffa009e000>] ? 0xffffffffa009dfff
[   11.786670]  [<ffffffff813bb430>] driver_register+0x80/0x150
[   11.787875]  [<ffffffff810cc0d9>] ? tracepoint_module_notify+0x29/0x30
[   11.789062]  [<ffffffffa009e000>] ? 0xffffffffa009dfff
[   11.790237]  [<ffffffff8130b2a6>] __pci_register_driver+0x56/0xd0
[   11.791404]  [<ffffffffa009e023>] rtl92ce_module_init+0x23/0x59 [rtl8192ce]
[   11.792593]  [<ffffffff81002043>] do_one_initcall+0x43/0x190
[   11.793755]  [<ffffffff8109daab>] sys_init_module+0xbb/0x200
[   11.794904]  [<ffffffff815d5f82>] system_call_fastpath+0x16/0x1b
[   11.796042] Code: 5c 41 5d c9 c3 0f 1f 40 00 0d 68 01 00 00 41 89 84 24 34 08 00 00 e9 f6 fb ff ff 0f 0b eb fe 0f 0b eb fe 0f 0b eb fe 0f 0b eb fe <0f> 0b eb fe 0f 0b eb fe 0f 0b eb fe 66 2e 0f 1f 84 00 00 00 00 
[   11.798438] RIP  [<ffffffffa030af3a>] ieee80211_alloc_hw+0x48a/0x4a0 [mac80211]
[   11.799582]  RSP <ffff8801350a3c08>
[   11.800714] ---[ end trace b4a25d78114ddf04 ]---
[   11.855930] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input7
[   12.373632] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input8
[   12.546359] cfg80211: World regulatory domain updated:


```Had to go via recovery mode -> normal boot
and it did boot up but none of wireless cards working (I am on cable now :D)
I did modprobe rtl8192ce (my PCI card driver) but its "stuck" I mean for 5 minutes I can not do/post any commands via terminal (ofc I can create new terminal...)

why site says I get rtl8187L but my HW is actually rtl8189 I do not get this... I bought it because I was told (by the site) that drivers won't be problem...

tool airdriver
```

airdriver-ng detect


USB devices (generic detection):
Bus 002 Device 004: ID 1b75:8189 Ovislink Corp.

PCI devices (generic detection):
07:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)


```

---

### Post by chili555 on 2012-01-05
> why site says I get rtl8187L but my HW is actually rtl8189 I do not get this...Again, you do not have the device referred to on the site. You have 0x1b75, 0x818[COLOR="Red"]**9**[/COLOR] and not 0x1b75, 0x8187. Devices with the same name change chipsets as time goes by and technology improves. Here is an example: [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys#USB](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsLinksys#USB)

If you scroll down to WUSB54GC, you'll see that versions came out with RT2571, rt73usb, RT2070 and RTL8187B chipsets.

Your device is labeled an AirLive WL-1600USB, but it is not the version with the 8187 chipset; it has an 8189 chipset. I'm sure the site you referred to used the best information they had at the time. Information changes.

We could try to re-edit the dev.c file to now refer to an RTL8187B. We could conclude that there is currently no Linux driver for your device and try ndiswrapper. We could conclude that the ieee80211 and other elements that you built with compat-wireless don't work well with your other Realtek device. You could also return the device and buy another.

Whatever you decide, I'll be glad to help.

---

### Post by Kyslosh on 2012-01-05
Alrighty, I put CD in my CD-Rom searched and guess what :D
I found dirvers for all kinds of windozes and all of them are named (folders) as rtl8187.
(I understand what you wrote up there that by time chipsets r changing...) I tought same I just needed confirmation of my assumption.

Back to 8187 :D 

I guess I need to figure out how to boot my computer now (I mean at least my "old" wifi PCI card)
Stil its stuck while booting (normal boot without recovery mode). and no wifi (only cable). 

Any suggestions please?

-USB stick is there any way to change product ID? or that is completly bad idea?

---

### Post by Kyslosh on 2012-01-05
Oke now :) good news I am conected with my USB Stick
(didn't do a thing just tried boot up)
It did not work at first I mean it got stuck saying that OEM something is different than
```

[   10.953528] rtl8187: inconsistency between id with OEM info!

```
 driver rtl8187, so I powered off pop in recovery mode and put iwconfig in
there was device wlan1 (my default PCI was wlan0) so I figured that there is a change.
I did **ifconfig wlan1 up** and wifi stick started blinking like a hell.

BUT i do not have wlan0 (by that I mean my PCI card), **ifconfig wlan0 up** does not work
either does modprobe rtl8192ce (i guess because when I did lsmod | grep rtl8192ce i got following)
```

rtl8192ce              77963  1 
rtl8192c_common        59103  1 rtl8192ce
rtlwifi                85430  1 rtl8192ce
mac80211              309235  3 rtl8192ce,rtlwifi,rtl8187


```

and my boot does not work at all 

this is exactly where it stops loading/booting further more (I did wait about 2 minutes and powered off) (last timestamp)

```

[   10.829263] ------------[ cut here ]------------
[   10.829281] kernel BUG at /root/compat-w/net/mac80211/main.c:618!
[   10.829302] invalid opcode: 0000 [#1] SMP 
[   10.829325] last sysfs file: /sys/devices/virtual/dmi/id/sys_vendor
[   10.829347] CPU 0 
[   10.829354] Modules linked in: rtl8192ce(+) rtl8192c_common rtlwifi snd_hwdep snd_pcm_oss rtl8187(+) thinkpad_acpi snd_mixer_oss snd_pcm snd_seq_dummy mac80211 snd_seq_oss cfg80211 snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device rfkill snd psmouse uvcvideo compat eeprom_93cx6 fglrx(P) serio_raw lp soundcore parport videodev sdhci_pci v4l2_compat_ioctl32 sdhci wmi mac_hid snd_page_alloc nvram i915 drm_kms_helper drm i2c_algo_bit video ahci libahci r8169 mii intel_agp intel_gtt
[   10.829598] 
[   10.829604] Pid: 366, comm: modprobe Tainted: P            2.6.39.4 #1 LENOVO 44012RG/44012RG
[   10.829632] RIP: 0010:[<ffffffffa066ff3a>]  [<ffffffffa066ff3a>] ieee80211_alloc_hw+0x48a/0x4a0 [mac80211]
[   10.829668] RSP: 0018:ffff880134811c08  EFLAGS: 00010246
[   10.829685] RAX: ffff880136182540 RBX: ffff880136180d40 RCX: 0000000000000000
[   10.829706] RDX: 0000000000000078 RSI: ffffffffa064d4cc RDI: ffff8801361800c0
[   10.829728] RBP: ffff880134811c28 R08: 0000000000000000 R09: ffff88013570b400
[   10.829749] R10: 0000000000000001 R11: dead000000200200 R12: ffff8801361801e0
[   10.829771] R13: ffffffffa07db080 R14: ffff880138cbe1f8 R15: 00000000fffffff4
[   10.829793] FS:  00007fdb3b4d7700(0000) GS:ffff88013fa00000(0000) knlGS:0000000000000000
[   10.829817] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
[   10.829835] CR2: 00007fdb3b414000 CR3: 0000000135ad7000 CR4: 00000000000406f0
[   10.829856] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[   10.829878] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[   10.829899] Process modprobe (pid: 366, threadinfo ffff880134810000, task ffff8801387fad80)
[   10.829923] Stack:
[   10.829930]  ffff880134811c28 00000000ffffffff ffffffffa080f220 ffff880138cbe000
[   10.829954]  ffff880134811d08 ffffffffa07d903b ffff880134811c68 ffffffff817da07f
[   10.829979]  ffff880134811c78 ffffffff811bc5a9 ffffffff81c69084 ffff8801353b8690
[   10.830838] Call Trace:
[   10.831690]  [<ffffffffa07d903b>] rtl_pci_probe+0x103/0x17b1 [rtlwifi]
[   10.832558]  [<ffffffff811bc5a9>] ? sysfs_find_dirent+0x49/0x70
[   10.833493]  [<ffffffff81034d89>] ? default_spin_lock_flags+0x9/0x10
[   10.834363]  [<ffffffff81034d89>] ? default_spin_lock_flags+0x9/0x10
[   10.835222]  [<ffffffff81309daf>] local_pci_probe+0x5f/0xd0
[   10.836087]  [<ffffffff8130b021>] pci_device_probe+0x101/0x120
[   10.836953]  [<ffffffff813baa7a>] ? driver_sysfs_add+0x7a/0xb0
[   10.837818]  [<ffffffff813babd6>] driver_probe_device+0x96/0x1c0
[   10.838671]  [<ffffffff813bad00>] ? driver_probe_device+0x1c0/0x1c0
[   10.839518]  [<ffffffff813bad9b>] __driver_attach+0x9b/0xa0
[   10.840360]  [<ffffffff813bad00>] ? driver_probe_device+0x1c0/0x1c0
[   10.841218]  [<ffffffff813b9ff8>] bus_for_each_dev+0x68/0x90
[   10.842077]  [<ffffffff813ba9fe>] driver_attach+0x1e/0x20
[   10.842958]  [<ffffffff813ba2dd>] bus_add_driver+0xcd/0x270
[   10.843811]  [<ffffffffa0813000>] ? 0xffffffffa0812fff
[   10.844658]  [<ffffffff813bb430>] driver_register+0x80/0x150
[   10.845496]  [<ffffffff810cc0d9>] ? tracepoint_module_notify+0x29/0x30
[   10.846330]  [<ffffffffa0813000>] ? 0xffffffffa0812fff
[   10.847156]  [<ffffffff8130b2a6>] __pci_register_driver+0x56/0xd0
[   10.847991]  [<ffffffffa0813023>] rtl92ce_module_init+0x23/0x59 [rtl8192ce]
[   10.848822]  [<ffffffff81002043>] do_one_initcall+0x43/0x190
[   10.849648]  [<ffffffff8109daab>] sys_init_module+0xbb/0x200
[   10.850471]  [<ffffffff815d5f82>] system_call_fastpath+0x16/0x1b
[   10.851288] Code: 5c 41 5d c9 c3 0f 1f 40 00 0d 68 01 00 00 41 89 84 24 34 08 00 00 e9 f6 fb ff ff 0f 0b eb fe 0f 0b eb fe 0f 0b eb fe 0f 0b eb fe <0f> 0b eb fe 0f 0b eb fe 0f 0b eb fe 66 2e 0f 1f 84 00 00 00 00 
[   10.853056] RIP  [<ffffffffa066ff3a>] ieee80211_alloc_hw+0x48a/0x4a0 [mac80211]
[   10.853900]  RSP <ffff880134811c08>
[   10.854768] ---[ end trace 483d75475a37a69c ]---
[   10.899206] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   10.900215] HDA Intel 0000:00:1b.0: irq 44 for MSI/MSI-X
[   10.901125] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   10.953528] rtl8187: inconsistency between id with OEM info!
[   10.954441] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   10.955283] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   10.956112] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   10.956960] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   10.957803] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   10.958661] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   10.959514] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   10.960383] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   10.961264] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   10.962173] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)
[   10.963084] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   **10.964017**] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (600 mBi, 2000 mBm)

```

any suggestions? :)

---

### Post by chili555 on 2012-01-06
> I found dirvers for all kinds of windozes and all of them are named (folders) as rtl8187.It would be very helpful to read the .inf file for the device to see if we need to tweak the compat-wireless install.> [   10.829281] kernel BUG at /root/compat-w/net/[COLOR="Red"]mac80211[/COLOR]/main.c:618!I am fearful that the mac80211 subsystem that compat-wireless installs to support the rtl8187 driver is incompatible with the stock built-in mac80211 subsystem that is needed to support rtl8192ce. I am afraid that the only way to proceed is to uninstall compat-wireless and try another way. I am confident your system will boot and the internal will work then.

There may be other ways to get your USB stick working. Why are you using two? Hacking, cracking and all that???

How would you like to proceed?

---

### Post by Kyslosh on 2012-01-06
> **chili555 said:**
> 
There may be other ways to get your USB stick working. Why are you using two? Hacking, cracking and all that???

I wish, I needed a usbstick for better "service" I mean signal... now all I do is either on cable or downstairs.

I want to be able go wireless upstairs :D 
Or all this could be because of my router... but since its from my internet provider for free I do not need to change it (while its modem also...).


> **chili555 said:**
> 
How would you like to proceed?


I would like to get my internal back on and mostly I need to boot up without "safe mode" boot.

I can get you all the infos u need from CD 
```

[87_Driver]
TitleName=AirLive WL1600USB Wireless LAN Driver
ProductGUID=876854B3-6F71-40EC-AD7C-A922C0B0EE0A
FileName= RTL8187.sys

InstallParameter[1] =/i /8187
InstallParameter[2] =/i /8187B
UnInstallParameter[1] =/u /8187
UnInstallParameter[2] =/u /8187B

ScanParameter =/8187
Driver_Path=Driver
Driver_Uninstall_Title=AirLive WL1600USB Wireless LAN Driver
;#####################################################################

```

```

;; Netrtuw.inf (For Win 7)
;;
;; Realtek RTL8187 Wireless 802.11g 54Mbps USB 2.0 Network Adapter
;;
;; Copyright (C) 2009 Realtek Semiconductor Corp.
;;
;; this release is primarily for WHQL test.
;;

[Version]
Signature    = "$Windows NT$"
Class        = Net
ClassGUID    = {4d36e972-e325-11ce-bfc1-08002be10318}
Provider    = %Realtek%
CatalogFile.NT    = netrtuw.cat        ;; for WHQL certified
DriverVer    = 12/09/2009,6.1316.1209.2009

[Manufacturer]
%Realtek% = Realtek,NTamd64.6.1

[ControlFlags]
ExcludeFromSelect = USB\VID_0BDA&PID_8187&REV_0100

;;****************************************************************************
;; IDs for X86
;;****************************************************************************
[Realtek.NTx86.6.1]
%RTL8187.DeviceDesc% = RTL8187.ndi, USB\VID_0BDA&PID_8187&REV_0100
%RTL8187.DeviceDesc% = RTL8187.ndi, USB\VID_13D1&PID_ABE6&REV_0100  
%RTL8187.DeviceDesc% = RTL8187.ndi, USB\VID_1371&PID_9401&REV_0100 
%RTL8187.DeviceDesc% = RTL8187.ndi, USB\VID_114B&PID_0150&REV_0100 
%RTL8187.DeviceDesc% = RTL8187.ndi, USB\VID_18E8&PID_6232&REV_0100 
%RTL8187.DeviceDesc% = RTL8187.ndi, USB\VID_0789&PID_010C&REV_0100
%RTL8187.DeviceDesc% = RTL8187.ndi, USB\VID_7392&PID_7612&REV_0100
%RTL8187.DeviceDesc% = RTL8187.ndi, USB\VID_145F&PID_0161&REV_0100
%RTL8187.DeviceDesc% = RTL8187.ndi, USB\VID_1B75&PID_8187&REV_0100

%RTL8187.DeviceDesc.Surecom% = RTL8187.ndi,USB\VID_0769&PID_11F2&REV_0100 
%RTL8187.DeviceDesc.Sitecom% = RTL8187.ndi,USB\VID_0DF6&PID_000D&REV_0100 

;;****************************************************************************
;; IDs for X64
;;****************************************************************************
[Realtek.NTamd64.6.1]
%RTL8187.DeviceDesc% = RTL8187.ndi, USB\VID_0BDA&PID_8187&REV_0100
%RTL8187.DeviceDesc% = RTL8187.ndi, USB\VID_13D1&PID_ABE6&REV_0100  
%RTL8187.DeviceDesc% = RTL8187.ndi, USB\VID_1371&PID_9401&REV_0100 
%RTL8187.DeviceDesc% = RTL8187.ndi, USB\VID_114B&PID_0150&REV_0100 
%RTL8187.DeviceDesc% = RTL8187.ndi, USB\VID_18E8&PID_6232&REV_0100 
%RTL8187.DeviceDesc% = RTL8187.ndi, USB\VID_0789&PID_010C&REV_0100
%RTL8187.DeviceDesc% = RTL8187.ndi, USB\VID_7392&PID_7612&REV_0100
%RTL8187.DeviceDesc% = RTL8187.ndi, USB\VID_145F&PID_0161&REV_0100
%RTL8187.DeviceDesc% = RTL8187.ndi, USB\VID_1B75&PID_8187&REV_0100

%RTL8187.DeviceDesc.Surecom% = RTL8187.ndi,USB\VID_0769&PID_11F2&REV_0100 
%RTL8187.DeviceDesc.Sitecom% = RTL8187.ndi,USB\VID_0DF6&PID_000D&REV_0100 

;;****************************************************************************
;; Windows 2000/XP
;;****************************************************************************
[RTL8187.ndi.NT]
AddReg            = RTL8187.common.reg, RTLWLAN.reg, RTL8187_os61.reg
Characteristics    = 0x84
BusType            = 15 
CopyFiles        = RTL8187.CopyFiles
*IfType            = 71            ; IF_TYPE_IEEE80211
*MediaType        = 16            ; NdisMediumNative802_11
*PhysicalMediaType    = 9          ; NdisPhysicalMediumNative802_11

[RTL8187.ndi.NT.Services]
AddService        = RTL8187, 2, RTL8187.nt61.Service, RTL8187.nt61.EventLog

[RTL8187.ndi.NT.HW]
AddReg = RTL8187_os61.vwifi.reg

;;****************************************************************************
;; register for both Win 7 x86 and x64                          **
;;****************************************************************************
[RTL8187_os61.reg]
HKR, Ndi,                Service,    0, "RTL8187"
HKR, Ndi\Interfaces,    UpperRange, 0, "ndis5,mdcwifi,wifipro"
HKR, Ndi\Interfaces,    LowerRange, 0, "wlan, ethernet,vwifi"

[RTL8187.nt61.Service]
DisplayName    = %RTL8187.DeviceDesc.DispName%
ServiceType    = 1        ; SERVICE_KERNEL_DRIVER
StartType      = 3        ; SERVICE_DEMAND_START
ErrorControl   = 1        ; SERVICE_ERROR_NORMAL
ServiceBinary  = %12%\rtl8187.sys
LoadOrderGroup = NDIS

[RTL8187.nt61.EventLog]
AddReg = RTL8187.nt61.AddEventLog.reg

[RTL8187.nt61.AddEventLog.reg]
HKR, , EventMessageFile, 0x00020000, "%%SystemRoot%%\System32\netevent.dll"
HKR, , TypesSupported  , 0x00010001, 7

;; Adds the VWiFi PNP filter
[RTL8187_os61.vwifi.reg]
HKR,,"UpperFilters",0x00010000,"vwifibus"


;*******************************************************************************
; RTL8187 common paramters
;*******************************************************************************
[RTL8187.common.reg]
HKR,Ndi\params\LedCtrl,        ParamDesc,  0, %LED_CONTROL_STR%
HKR,Ndi\params\LedCtrl,        type,       0, "enum"
HKR,Ndi\params\LedCtrl,        default,    0, "1"
HKR,Ndi\params\LedCtrl\enum,   "0",        0, %Disable_STR%
HKR,Ndi\params\LedCtrl\enum,   "1",        0, %ENABLE_STR%
HKR,defaults,LedCtrl,0,"1"
HKR,,LedCtrl,0,"1"

HKR,NDI\params\PowerSaveMode,      ParamDesc,  0, %POWER_SAVE_STR%
HKR,NDI\params\PowerSaveMode,      type,       0, "enum"
HKR,Ndi\params\PowerSaveMode,      default,    0, "0"
HKR,NDI\params\PowerSaveMode\enum, "0",        0, %CAM_STR%
HKR,NDI\params\PowerSaveMode\enum, "1",        0, %MAX_PSP_STR%
HKR,NDI\params\PowerSaveMode\enum, "2",        0, %FAST_PSP_STR%
HKR,defaults,PowerSaveMode,0,"0"
HKR,,PowerSaveMode,0,"0"

HKR,Ndi\params\WiFi11bIbss,        ParamDesc,  0, %WIFI_IBSS_STR%
HKR,Ndi\params\WiFi11bIbss,        type,       0, "enum"
HKR,Ndi\params\WiFi11bIbss,        default,    0, "0"
HKR,Ndi\params\WiFi11bIbss\enum,   "0",        0, %DISABLE_STR%
HKR,Ndi\params\WiFi11bIbss\enum,   "1",        0, %ENABLE_STR%
HKR,defaults,WiFi11bIbss,0,"0"
HKR,,WiFi11bIbss,0,"0"

HKR,Ndi\params\bRateAdaptive,        ParamDesc,  0, %RATE_ADAPTIVE_STR%
HKR,Ndi\params\bRateAdaptive,        type,       0, "enum"
HKR,Ndi\params\bRateAdaptive,        default,    0, "1"
HKR,Ndi\params\bRateAdaptive\enum,   "0",        0, %DISABLE_STR%
HKR,Ndi\params\bRateAdaptive\enum,   "1",        0, %ENABLE_STR%
HKR,defaults,bRateAdaptive,0,"1"
HKR,,bRateAdaptive,0,"1"

; IC specific
HKR,,QoS,0,"0"
HKR,,CcxRm,0,"0"


;;----------------------------------------------------------------------------
;; Realtek WLAN NIC parameters
;;----------------------------------------------------------------------------
[RTLWLAN.reg]
HKR,,SSID,0,""

HKR,Ndi\params\Channel,       ParamDesc,  0, %CHANNEL_STR%
HKR,Ndi\params\Channel,       type,       0, "int"
HKR,Ndi\params\Channel,       default,    0, "1"
HKR,Ndi\params\Channel,       Min,        0, "1"
HKR,Ndi\params\Channel,       Max,        0, "14"
HKR,Ndi\params\Channel,       Step,       0, "1"
HKR,Ndi\params\Channel,       Base,       0, "10"
HKR,defaults,Channel,0,"1"
HKR,,Channel,0,"1"

HKR,Ndi\params\NetworkType,        ParamDesc,  0, %NETWORK_TYPE_STR%
HKR,Ndi\params\NetworkType,        type,       0, "enum"
HKR,Ndi\params\NetworkType,        default,    0, "1"
HKR,Ndi\params\NetworkType\enum,   "0",        0, %AD_HOC_STR%
HKR,Ndi\params\NetworkType\enum,   "1",        0, %INFRA_STR%
HKR,Ndi\params\NetworkType\enum,   "2",        0, %AUTO_SELECT_STR%
HKR,defaults,NetworkType,0,"1"
HKR,,NetworkType,0,"1"

HKR,Ndi\params\ChannelPlan, ParamDesc, 0, %CHANNEL_PLAN_STR%
HKR,Ndi\params\ChannelPlan, type, 0, "enum"
HKR,Ndi\params\ChannelPlan, default, 0, "15"
HKR,Ndi\params\ChannelPlan\enum, "0", 0, "FCC"
HKR,Ndi\params\ChannelPlan\enum, "1", 0, "IC"
HKR,Ndi\params\ChannelPlan\enum, "2", 0, "ETSI"
HKR,Ndi\params\ChannelPlan\enum, "3", 0, "Spain"
HKR,Ndi\params\ChannelPlan\enum, "4", 0, "France"
HKR,Ndi\params\ChannelPlan\enum, "5", 0, "MKK"
HKR,Ndi\params\ChannelPlan\enum, "6", 0, "MKK1"
HKR,Ndi\params\ChannelPlan\enum, "7", 0, "Israel"
HKR,Ndi\params\ChannelPlan\enum, "8", 0, "TELEC"
HKR,Ndi\params\ChannelPlan\enum, "15", 0, "DOMAIN_FROM_EEPROM"
HKR,defaults,ChannelPlan, 0, "15"
HKR,,ChannelPlan, 0, "15"

; Wireless Mode, 2006.11.30, by shien chang.
HKR,Ndi\params\WirelessMode, ParamDesc, 0, %WL_MODE_STR%
HKR,Ndi\params\WirelessMode, type, 0, "enum"
HKR,Ndi\params\WirelessMode, default, 0, "8"
;HKR,Ndi\params\WirelessMode\enum, "1", 0, "IEEE 802.11a"
HKR,Ndi\params\WirelessMode\enum, "2", 0, "IEEE 802.11b"
HKR,Ndi\params\WirelessMode\enum, "4", 0, "IEEE 802.11b/g"
;HKR,Ndi\params\WirelessMode\enum, "8", 0, "Auto"
HKR,defaults,WirelessMode, 0, "4"
HKR,,WirelessMode, 0, "4"

; For PSP XLink mode, 2006.09.04, by shien chang.
;HKR,Ndi\params\PSPXlinkMode,        ParamDesc,  0, %PSP_XLINK_STR%
;HKR,Ndi\params\PSPXlinkMode,        type,       0, "enum"
;HKR,Ndi\params\PSPXlinkMode,        default,    0, "0"
;HKR,Ndi\params\PSPXlinkMode\enum,   "0",        0, "Disable"
;HKR,Ndi\params\PSPXlinkMode\enum,   "1",        0, "Enable"
;HKR,defaults,PSPXlinkMode,0,"0"
;HKR,,PSPXlinkMode,0,"0"

; Preamble mode, 2006.11.30, by shien chang.
HKR,Ndi\params\PreambleMode, ParamDesc, 0, %PREAMBLE_MODE_STR%
HKR,Ndi\params\PreambleMode, type, 0, "enum"
HKR,Ndi\params\PreambleMode, default, 0, "2"
HKR,Ndi\params\PreambleMode\enum, "1", 0, "Long Preamble"
HKR,Ndi\params\PreambleMode\enum, "2", 0, "Auto"
HKR,Ndi\params\PreambleMode\enum, "3", 0, "Short Preamble"
HKR,defaults,PreambleMode, 0, "2"
HKR,,PreambleMode, 0, "2"

HKR,,DefaultKeyID,,"0"
HKR,,DefaultKey0,,""
HKR,,DefaultKey1,,""
HKR,,DefaultKey2,,""
HKR,,DefaultKey3,,""


;*******************************************************************************
; Destination Directory
;*******************************************************************************
[RTL8187.CopyFiles]
RTL8187.sys,,,2

[DestinationDirs]
DefaultDestDir     = 11
RTL8187.CopyFiles        = 12

;;****************************************************************************
;; Source Files
;;****************************************************************************
[SourceDisksFiles]
RTL8187.sys = 1

[SourceDisksNames]
1=%DISKNAME%,,,

;*******************************************************************************
; Strings
;*******************************************************************************
[Strings]
Realtek                 = "Ovislink Corp."
SSID_STR                = "SSID"
CHANNEL_STR                = "Channel"
NETWORK_TYPE_STR        = "Network Type"
LED_CONTROL_STR            = "LED Control" 
POWER_SAVE_STR            = "Power Save Mode"
WIFI_IBSS_STR            = "IBSS Default 11b Mode"
RATE_ADAPTIVE_STR        = "Rate Adaptive"
QOS_STR                    = "QoS"
TransmitBuffers                  = "Transmit Buffers"
ReceiveBuffers                   = "Receive Buffers"
FORCE_PRIORITY_STR        = "Forced Priority"
HW_PARA_STR                = "Init from HwParaFile"
THREE_WIRE_MODE_STR        = "Three Wire Programming Mode"
BOARD_TYPE_STR            = "Board Type"
PROTECTION_MODE_STR        = "Protection Mode"
TPC_STR                    = "Transmit Power Control"
TPC_POLARITY_STR        = "TPC Polarity Select"
HIGH_POWER_STR            = "High Power Mechanism"
INIT_GAIN_STR            = "Initial Gain State"
CW_MAX_MIN_STR            = "Contention Window"
PSP_XLINK_STR            = "PSP XLink Mode"
ANTENNA_DIVERSITY_STR        = "SW Antenna Diversity"
INACTIVE_POWER_SAVE        = "Inactive Power Save"
B_MODE_INIT_GAIN_STR        = "B Mode Initial Gain"
WL_MODE_STR            = "Wireless Mode"
PREAMBLE_MODE_STR        = "Preamble Mode"
FRAGTHRESH_STR            = "Fragmentation Threshold"
RTSTHRESH_STR            = "RTS Threshold"
DOT11_ENABLE_STR        = "802.11d"
CHANNEL_PLAN_STR        = "Channel Plan"
CAM_STR                                    ="CAM"
MAX_PSP_STR                            ="MAX_PSP"
FAST_PSP_STR                        ="Fast_PSP"
DISABLE_STR                            ="Disable"
ENABLE_STR                            ="Enable"
AD_HOC_STR                            ="Ad Hoc"
INFRA_STR                                ="Infrastructure"
AUTO_SELECT_STR                    ="Auto select"
11A_STR                                    ="IEEE 802.11 a"
11B_STR                                    ="IEEE 802.11 b"
11BG_STR                                ="IEEE 802.11 b/g"
LONG_PREAMBLE_STR                ="Long Preamble"
SHORT_PREAMBLE_STR            ="Short Preamble"
AUTO_STR                                ="Auto"

;; Source disk name
DISKNAME            = "AirLive WL1600USB"
RTL8187.DeviceDesc        = "AirLive WL1600USB"
RTL8187.DeviceDesc.DispName    = "AirLive WL1600USB"
RTL8187.DeviceDesc.Surecom    = "SURECOM EP-9001-g 802.11g 54M WLAN USB Adapter"
RTL8187.DeviceDesc.Sitecom    = "SITECOM WL-168 Wireless Network USB Adapter 54g"


```


I do not know what exactly should I look for in CD.

---

### Post by chili555 on 2012-01-06
> I would like to get my internal back on and mostly I need to boot up without "safe mode" boot.Then please do this:```
cd Desktop/compat-wireless-version-whatever
```^^^Susbstitute the location you downloaded the compat wireless package. Next do:```
sudo su
make uninstall
make clean
./scripts/driver-select restore
exit
```Reboot and give us your report.> I can get you all the infos u need from CDWhat I don't see is your usb.id idVendor 0x1b75; idProduct 0x8189. I'm not quite sure how or even if this device is going to work with that .inf file.

There are probably other things we could try if you have any patience left. I don't have your device so I can't guarantee anything except I'll be happy to work with you.

---

### Post by Kyslosh on 2012-01-06
Oke I am bootet up (via recovery mode), I'll try as you suggest uninstall compat and try my internal ;)


If you are asking my patience, well I am willing to use all your knowledge to get my USB stick work ;).

//did uninstall let me reboot

---

### Post by Kyslosh on 2012-01-06
my internal (wlan0) rtl8192ce works perfectly as before ;) (iw wlan0 scan)

what are my next steps with my USB stick ? :)

is there any possible way to change USB stick ProductID?

here is file 
/media/WL-1600USB-2/Driver/Driver/WinXP/net8187b.inf
```

;; net8187b.inf 
;;
;; Realtek RTL8187B Wireless 802.11g 54Mbps USB 2.0 Network Adapter
;;
;; Copyright (C) 2010 Realtek Semiconductor Corp.
;;
;; this release is primarily for WHQL test.
;;

[Version]
Signature    = "$Chicago$"
Compatible    = 1
Class        = Net
ClassGUID    = {4d36e972-e325-11ce-bfc1-08002be10318}
Provider    = %Realtek%
CatalogFile.NT    = net8187b.cat        ;; for WHQL certified
DriverVer    = 03/31/2010,6.1163.0331.2010

[Manufacturer]
%Realtek% = Realtek,NTx86

[ControlFlags]
ExcludeFromSelect = USB\VID_0BDA&PID_8187&REV_0200

;;****************************************************************************
;; IDs for X64
;;****************************************************************************
[Realtek.NTamd64]
%RTL8187B.DeviceDesc% = RTL8187B.ndi, USB\VID_0BDA&PID_8187&REV_0200
%RTL8187B.DeviceDesc% = RTL8187B.ndi, USB\VID_0BDA&PID_8189&REV_0200
%RTL8187B.DeviceDesc% = RTL8187B.ndi, USB\VID_1B75&PID_8187&REV_0200
%RTL8187B.DeviceDesc% = RTL8187B.ndi, USB\VID_1B75&PID_8189&REV_0200

;;****************************************************************************
;; IDs for 2K/XP
;;****************************************************************************
[Realtek.NTx86]
%RTL8187B.DeviceDesc% = RTL8187B.ndi, USB\VID_0BDA&PID_8187&REV_0200
%RTL8187B.DeviceDesc% = RTL8187B.ndi, USB\VID_0BDA&PID_8189&REV_0200
%RTL8187B.DeviceDesc% = RTL8187B.ndi, USB\VID_1B75&PID_8187&REV_0200
%RTL8187B.DeviceDesc% = RTL8187B.ndi, USB\VID_1B75&PID_8189&REV_0200

;;****************************************************************************
;; IDs for 98SE/ME
;;****************************************************************************
[Realtek]
%RTL8187B.DeviceDesc% = RTL8187B.ndi, USB\VID_0BDA&PID_8187&REV_0200
%RTL8187B.DeviceDesc% = RTL8187B.ndi, USB\VID_0BDA&PID_8189&REV_0200
%RTL8187B.DeviceDesc% = RTL8187B.ndi, USB\VID_1B75&PID_8187&REV_0200
%RTL8187B.DeviceDesc% = RTL8187B.ndi, USB\VID_1B75&PID_8189&REV_0200

;;****************************************************************************
;; Windows 98SE/ME
;;****************************************************************************
[RTL8187B.ndi]
DriverVer        = 03/29/2010,1163
AddReg            = RTL8187B.win.reg, RTL8187B.common.reg, RTLWLAN.reg
CopyFiles        = RTL8187B.CopyFiles98

;;****************************************************************************
;; Windows 2000/XP
;;****************************************************************************
[RTL8187B.ndi.NT]
AddReg            = RTL8187B.nt5.reg, RTL8187B.common.reg, RTLWLAN.reg
Characteristics    = 0x84
BusType            = 15 
CopyFiles        = RTL8187B.CopyFiles

[RTL8187B.ndi.NT.Services]
AddService        = RTL8187B, 2, RTL8187B.nt5.Service, RTL8187B.nt5.EventLog


;;----------------------------------------------------------------------------
;; RTL8187B Parameters
;;----------------------------------------------------------------------------
;;***************************************************************************
;; Windows 98SE/ME Parameters
;;***************************************************************************
[RTL8187B.win.reg]
HKR, Ndi, DeviceID, 0, USB\VID_0BDA&PID_8187&REV_0200

HKR,Ndi,CardType,,"PNP"

HKR, , DriverDesc, 0, "Realtek RTL8187B Wireless 802.11g 54Mbps USB 2.0 Network Adapter"
HKR, , DevLoader,,*ndis,*ntkern,*ndis
HKR, , DeviceVxDs,,RTL8187B.sys
HKR, , EnumPropPages, 0, netdi.dll, EnumPropPages

; NDIS Info
HKR,NDIS,MajorNdisVersion,1,03
HKR,NDIS,MinorNdisVersion,1,0a
HKR,NDIS,LogDriverName,,RTL8187B

; Interfaces
HKR,Ndi\Interfaces,DefLower,,"ethernet"
HKR,Ndi\Interfaces,LowerRange,,"ethernet"
HKR,Ndi\Interfaces,DefUpper,,"ndis3"
HKR,Ndi\Interfaces,UpperRange,,"ndis3"

;;****************************************************************************
;; Windows 2000/XP parameters
;;****************************************************************************
[RTL8187B.nt5.reg]
HKR, Ndi\Interfaces,    UpperRange, 0, "ndis5,mdcwifi,wifipro"
HKR, Ndi\Interfaces,    LowerRange, 0, "ethernet"
HKR, Ndi,                Service,    0, "RTL8187B"

[RTL8187B.nt5.Service]
DisplayName    = %RTL8187B.DeviceDesc.DispName%
ServiceType    = 1        ; %SERVICE_KERNEL_DRIVER%
StartType      = 3        ; %SERRVICE_DEMAND_START%
ErrorControl   = 1        ; %SERRVICE_ERROR_NORMAL%
ServiceBinary  = %12%\RTL8187B.sys
LoadOrderGroup = NDIS

[RTL8187B.nt5.EventLog]
AddReg = RTL8187B.nt5.AddEventLog.reg

[RTL8187B.nt5.AddEventLog.reg]
HKR, , EventMessageFile, 0x00020000, "%%SystemRoot%%\System32\netevent.dll"
HKR, , TypesSupported  , 0x00010001, 7

;*******************************************************************************
; RTL8187B common paramters
;*******************************************************************************
[RTL8187B.common.reg]
HKR,Ndi\params\LedCtrl,        ParamDesc,  0, %LED_CONTROL_STR%
HKR,Ndi\params\LedCtrl,        type,       0, "enum"
HKR,Ndi\params\LedCtrl,        default,    0, "1"
HKR,Ndi\params\LedCtrl\enum,   "0",        0, %DISABLE_STR%
HKR,Ndi\params\LedCtrl\enum,   "1",        0, %ENABLE_STR%
HKR,defaults,LedCtrl,0,"1"
HKR,,LedCtrl,0,"1"

HKR,NDI\params\PowerSaveMode,      ParamDesc,  0, %POWER_SAVE_STR%
HKR,NDI\params\PowerSaveMode,      type,       0, "enum"
HKR,Ndi\params\PowerSaveMode,      default,    0, "0"
HKR,NDI\params\PowerSaveMode\enum, "0",        0, %CAM_STR%
HKR,NDI\params\PowerSaveMode\enum, "1",        0, %MAX_PSP_STR%
HKR,NDI\params\PowerSaveMode\enum, "2",        0, %FAST_PSP_STR%
HKR,defaults,PowerSaveMode,0,"0"
HKR,,PowerSaveMode,0,"0"

HKR,Ndi\params\WiFi11bIbss,        ParamDesc,  0, %WIFI_IBSS_STR%
HKR,Ndi\params\WiFi11bIbss,        type,       0, "enum"
HKR,Ndi\params\WiFi11bIbss,        default,    0, "0"
HKR,Ndi\params\WiFi11bIbss\enum,   "0",        0, %DISABLE_STR%
HKR,Ndi\params\WiFi11bIbss\enum,   "1",        0, %ENABLE_STR%
HKR,defaults,WiFi11bIbss,0,"0"
HKR,,WiFi11bIbss,0,"0"

HKR,Ndi\params\bRateAdaptive,        ParamDesc,  0, %RATE_ADAPTIVE_STR%
HKR,Ndi\params\bRateAdaptive,        type,       0, "enum"
HKR,Ndi\params\bRateAdaptive,        default,    0, "1"
HKR,Ndi\params\bRateAdaptive\enum,   "0",        0, %DISABLE_STR%
HKR,Ndi\params\bRateAdaptive\enum,   "1",        0, %ENABLE_STR%
HKR,defaults,bRateAdaptive,0,"1"
HKR,,bRateAdaptive,0,"1"

HKR,Ndi\params\QoS,        ParamDesc,  0, %QOS_STR%
HKR,Ndi\params\QoS,        type,       0, "enum"
HKR,Ndi\params\QoS,        default,    0, "0"
HKR,Ndi\params\QoS\enum,   "0",        0, %DISABLE_STR%
HKR,Ndi\params\QoS\enum,   "1",        0, %ENABLE_STR%
HKR,defaults,QoS,0,"0"
HKR,,QoS,0,"0"

HKR,Ndi\params\CcxRm,        ParamDesc,  0, %CCX_RM_STR%
HKR,Ndi\params\CcxRm,        type,       0, "enum"
HKR,Ndi\params\CcxRm,        default,    0, "1"
HKR,Ndi\params\CcxRm\enum,   "0",        0, %DISABLE_STR%
HKR,Ndi\params\CcxRm\enum,   "1",        0, %ENABLE_STR%
HKR,defaults,CcxRm,0,"1"
HKR,,CcxRm,0,"1"

HKR,Ndi\params\CcxOffLineDurUpLimit,        ParamDesc,  0, %CCX_OFF_LINE_DUR_UP_LIMIT_STR%
HKR,Ndi\params\CcxOffLineDurUpLimit,        type,       0, "word"
HKR,Ndi\params\CcxOffLineDurUpLimit,        default,    0, "0"
HKR,Ndi\params\CcxOffLineDurUpLimit,        min,        0, "0"
HKR,Ndi\params\CcxOffLineDurUpLimit,        max,        0, "65535"
HKR,Ndi\params\CcxOffLineDurUpLimit,        step,       0, "1"
HKR,Ndi\params\CcxOffLineDurUpLimit,        base,       0, "10"
HKR,defaults,CcxOffLineDurUpLimit,0,"0"
HKR,,CcxOffLineDurUpLimit,0,"0"

;;----------------------------------------------------------------------------
;; Realtek WLAN NIC parameters
;;----------------------------------------------------------------------------
[RTLWLAN.reg]
HKR,Ndi\params\SSID,             ParamDesc,  0, %SSID_STR%
HKR,Ndi\params\SSID,             type,       0, "edit"
HKR,Ndi\params\SSID,             default,    0, "ANY"
HKR,Ndi\params\SSID,             LimitText,  0, "32"
HKR,defaults,SSID,0,"ANY"
HKR,,SSID,0,"ANY"

HKR,Ndi\params\Channel,       ParamDesc,  0, %CHANNEL_STR%
HKR,Ndi\params\Channel,       type,       0, "int"
HKR,Ndi\params\Channel,       default,    0, "1"
HKR,Ndi\params\Channel,       Min,        0, "1"
HKR,Ndi\params\Channel,       Max,        0, "14"
HKR,Ndi\params\Channel,       Step,       0, "1"
HKR,Ndi\params\Channel,       Base,       0, "10"
HKR,defaults,Channel,0,"1"
HKR,,Channel,0,"1"

HKR,Ndi\params\NetworkType,        ParamDesc,  0, %NETWORK_TYPE_STR%
HKR,Ndi\params\NetworkType,        type,       0, "enum"
HKR,Ndi\params\NetworkType,        default,    0, "1"
HKR,Ndi\params\NetworkType\enum,   "0",        0, %AD_HOC_STR%
HKR,Ndi\params\NetworkType\enum,   "1",        0, %INFRASTRUCTURE_STR%
HKR,Ndi\params\NetworkType\enum,   "2",        0, %AUTO_SELECT_STR%
HKR,defaults,NetworkType,0,"1"
HKR,,NetworkType,0,"1"

HKR,Ndi\params\StaUapsd,        ParamDesc,  0, %WMM_APSD%
HKR,Ndi\params\StaUapsd,        type,       0, "enum"
HKR,Ndi\params\StaUapsd,        default,    0, "0"
HKR,Ndi\params\StaUapsd\enum,   "0",        0, %DISABLE_STR%
HKR,Ndi\params\StaUapsd\enum,   "7",        0, %ENABLE_STR%
HKR,defaults,StaUapsd,0,"0"
HKR,,StaUapsd,0,"0"

HKR,Ndi\params\ChannelPlan, ParamDesc, 0, %CHANNEL_PLAN_STR%
HKR,Ndi\params\ChannelPlan, type, 0, "enum"
HKR,Ndi\params\ChannelPlan, default, 0, "15"
HKR,Ndi\params\ChannelPlan\enum, "0", 0, %FCC_STR%
HKR,Ndi\params\ChannelPlan\enum, "1", 0, %IC_STR%
HKR,Ndi\params\ChannelPlan\enum, "2", 0, %ETSI_STR%
HKR,Ndi\params\ChannelPlan\enum, "3", 0, %SPAIN_STR%
HKR,Ndi\params\ChannelPlan\enum, "4", 0, %FRANCE_STR%
HKR,Ndi\params\ChannelPlan\enum, "5", 0, %MKK_STR%
HKR,Ndi\params\ChannelPlan\enum, "6", 0, %MKK1_STR%
HKR,Ndi\params\ChannelPlan\enum, "7", 0, %ISRAEL_STR%
HKR,Ndi\params\ChannelPlan\enum, "8", 0, %TELEC_STR%
HKR,Ndi\params\ChannelPlan\enum, "15", 0, %DOMAIN_FROM_EEPROM_STR%
HKR,defaults,ChannelPlan, 0, "15"
HKR,,ChannelPlan, 0, "15"

; Wireless Mode, 2006.11.30, by shien chang.
HKR,Ndi\params\WirelessMode, ParamDesc, 0, %WL_MODE_STR%
HKR,Ndi\params\WirelessMode, type, 0, "enum"
HKR,Ndi\params\WirelessMode, default, 0, "8"
;HKR,Ndi\params\WirelessMode\enum, "1", 0, %IEEE_802_11A_STR%
HKR,Ndi\params\WirelessMode\enum, "2", 0, %IEEE_802_11B_STR%
HKR,Ndi\params\WirelessMode\enum, "4", 0, %IEEE_802_11BG_STR%
;HKR,Ndi\params\WirelessMode\enum, "8", 0, %AUTO_STR%
HKR,defaults,WirelessMode, 0, "4"
HKR,,WirelessMode, 0, "4"

; Preamble mode, 2006.11.30, by shien chang.
HKR,Ndi\params\PreambleMode, ParamDesc, 0, %PREAMBLE_MODE_STR%
HKR,Ndi\params\PreambleMode, type, 0, "enum"
HKR,Ndi\params\PreambleMode, default, 0, "2"
HKR,Ndi\params\PreambleMode\enum, "1", 0, %LONG_PREAMBLE_STR%
HKR,Ndi\params\PreambleMode\enum, "2", 0, %AUTO_STR%
HKR,Ndi\params\PreambleMode\enum, "3", 0, %SHORT_PREAMBLE_STR%
HKR,defaults,PreambleMode, 0, "2"
HKR,,PreambleMode, 0, "2"

; For PSP XLink mode, 2006.09.04, by shien chang.
HKR,Ndi\params\PSPXlinkMode,        ParamDesc,  0, %PSP_XLINK_STR%
HKR,Ndi\params\PSPXlinkMode,        type,       0, "enum"
HKR,Ndi\params\PSPXlinkMode,        default,    0, "0"
HKR,Ndi\params\PSPXlinkMode\enum,   "0",        0, %DISABLE_STR%
HKR,Ndi\params\PSPXlinkMode\enum,   "1",        0, %ENABLE_STR%
HKR,defaults,PSPXlinkMode,0,"0"
HKR,,PSPXlinkMode,0,"0"

HKR,Ndi\params\FragThresh, ParamDesc, 0, %FRAGTHRESH_STR%
HKR,Ndi\params\FragThresh, default, 0, "2346"
HKR,Ndi\params\FragThresh, type, 0, "int"
HKR,Ndi\params\FragThresh, min, 0, "256"
HKR,Ndi\params\FragThresh, max, 0, "2346"
HKR,Ndi\params\FragThresh, step, 0, "1"
HKR,defaults,FragThresh, 0, "2346"
HKR,,FragThresh, 0, "2346"

HKR,Ndi\params\RTSThresh, ParamDesc, 0, %RTSTHRESH_STR%
HKR,Ndi\params\RTSThresh, default, 0, "2347"
HKR,Ndi\params\RTSThresh, type, 0, "int"
HKR,Ndi\params\RTSThresh, min, 0, "0"
HKR,Ndi\params\RTSThresh, max, 0, "2347"
HKR,Ndi\params\RTSThresh, step, 0, "1"
HKR,defaults,RTSThresh, 0, "2347"
HKR,,RTSThresh, 0, "2347"

HKR,Ndi\params\Dot11dEnable,        ParamDesc,  0, %DOT11_ENABLE_STR%
HKR,Ndi\params\Dot11dEnable,        type,       0, "enum"
HKR,Ndi\params\Dot11dEnable,        default,    0, "0"
HKR,Ndi\params\Dot11dEnable\enum,   "0",        0, %DISABLE_STR%
HKR,Ndi\params\Dot11dEnable\enum,   "1",        0, %ENABLE_STR%
HKR,defaults,Dot11dEnable,0,"0"
HKR,,Dot11dEnable,0,"0"

;Inactive Power Save
HKR,,bInactivePs,0,"1"

HKR,,DefaultKeyID,,"0"
HKR,,DefaultKey0,,""
HKR,,DefaultKey1,,""
HKR,,DefaultKey2,,""
HKR,,DefaultKey3,,""


;*******************************************************************************
; Destination Directory
;*******************************************************************************
[RTL8187B.CopyFiles]
RTL8187B.sys,,,2

[RTL8187B.CopyFiles98]
RTL8187B.sys,,,2

[DestinationDirs]
RTL8187B.CopyFiles98    = 11
RTL8187B.CopyFiles        = 12

;;****************************************************************************
;; Source Files
;;****************************************************************************
[SourceDisksFiles]
RTL8187B.sys = 1

[SourceDisksNames]
1=%DISKNAME%,,,

;*******************************************************************************
; Strings
;*******************************************************************************
[Strings]
Realtek                 = "Realtek Semiconductor Corp."
SSID_STR                = "SSID"
CHANNEL_STR                = "Channel"
NETWORK_TYPE_STR        = "Network Type"
LED_CONTROL_STR            = "LED Control" 
POWER_SAVE_STR            = "Power Save Mode"
WIFI_IBSS_STR            = "IBSS Default 11b Mode"
RATE_ADAPTIVE_STR        = "Rate Adaptive"
QOS_STR                    = "QoS"
WMM_APSD            = "WMM APSD"
CCX_RM_STR                = "CCX Radio Measurement"
CCX_OFF_LINE_DUR_UP_LIMIT_STR    = "CCX Max Off-Line Measurement (0: unlimited)"
FORCE_PRIORITY_STR        = "Forced Priority"
HW_PARA_STR                = "Init from HwParaFile"
THREE_WIRE_MODE_STR        = "Three Wire Programming Mode"
BOARD_TYPE_STR            = "Board Type"
PROTECTION_MODE_STR        = "Protection Mode"
TPC_STR                    = "Transmit Power Control"
TPC_POLARITY_STR        = "TPC Polarity Select"
HIGH_POWER_STR            = "High Power Mechanism"
INIT_GAIN_STR            = "Initial Gain State"
CW_MAX_MIN_STR            = "Contention Window"
PSP_XLINK_STR            = "PSP XLink Mode"
CHANNEL_PLAN_STR        = "Channel Plan"
WL_MODE_STR                = "Wireless Mode"
PREAMBLE_MODE_STR        = "Preamble Mode"
FRAGTHRESH_STR            = "Fragmentation Threshold"
RTSTHRESH_STR            = "RTS Threshold"
DOT11_ENABLE_STR        = "802.11d"

DISABLE_STR             = "Disable"
ENABLE_STR             = "Enable"
CAM_STR             = "CAM"
MAX_PSP_STR             = "MAX_PSP"
FAST_PSP_STR             = "Fast_PSP"
AD_HOC_STR             = "Ad Hoc"
INFRASTRUCTURE_STR         = "Infrastructure"
AUTO_SELECT_STR         = "Auto select"
DOMAIN_FROM_EEPROM_STR         = "DOMAIN_FROM_EEPROM"
AUTO_STR             = "Auto"
LONG_PREAMBLE_STR         = "Long Preamble"
SHORT_PREAMBLE_STR         = "Short Preamble"

FCC_STR             = "FCC"
IC_STR                 = "IC"
ETSI_STR             = "ETSI"
SPAIN_STR             = "Spain"
FRANCE_STR             = "France"
MKK_STR             = "MKK"
MKK1_STR             = "MKK1"
ISRAEL_STR             = "Israel"
TELEC_STR             = "TELEC"

IEEE_802_11A_STR         = "IEEE 802.11a"
IEEE_802_11B_STR         = "IEEE 802.11b"
IEEE_802_11BG_STR         = "IEEE 802.11 b/g"

;; Source disk name
DISKNAME            = "AirLive WL1600USB Wireless 802.11b/g 54Mbps USB 2.0 Network Adapters Driver Disk"
RTL8187B.DeviceDesc         = "AirLive WL1600USB Wireless 802.11b/g 54Mbps USB 2.0 Network Adapters"
RTL8187B.DeviceDesc.DispName    = "AirLive WL1600USB Wireless 802.11b/g 54Mbps USB 2.0 Network Adapters"



```

---

### Post by chili555 on 2012-01-06
> %RTL8187B.DeviceDesc% = RTL8187[COLOR="Red"]B[/COLOR].ndi, USB\VID_[COLOR="Red"]1B75[/COLOR]&PID_[COLOR="Red"]8189[/COLOR]&REV_0200Ahhh! Now we see your device and we know it's an RTL8187[COLOR="Red"]B[/COLOR].First, remove the USB stick. Let's stop your internal from loading and evidently conflicting.```
sudo su
echo "blacklist rtl8192ce" >> /etc/modprobe.d/blacklist.conf
modprobe -r rtl8192ce
```Now, we'll tweak the dev.c file:```
cd ~/Desktop/compat-wireless-2012-01-04/
gedit drivers/net/wireless/rtl818x/rtl8187/dev.c
```Add the B as I have shown here. Remember, we are not removing any lines from the file or changing anything but the line we previously added:```
{USB_DEVICE(0x13d1, 0xabe6), .driver_info = DEVICE_RTL8187},
	/* Qcom */
{USB_DEVICE(0x18E8, 0x6232), .driver_info = DEVICE_RTL8187},
	/* AirLive */
{USB_DEVICE(0x1b75, 0x8187), .driver_info = DEVICE_RTL8187},
	/* Airlive */
{USB_DEVICE(0x1b75, 0x8189), .driver_info = DEVICE_RTL8187[COLOR="Red"]**B**[/COLOR]},
	/* Linksys */
{USB_DEVICE(0x1737, 0x0073), .driver_info = DEVICE_RTL8187B},
	{}
```Proofread carefully twice. Remember spacing, punctuation, indentation, etc. are crucial. Save and close gedit. Now let's build again:```
./scripts/driver-select rtl818x
make
make install
exit
```Insert the stick and let me have your report.

---

### Post by Kyslosh on 2012-01-06
install [OK]
boot [OK]
USB stick works (after ifconfig wlan1 down/up) -> not right after start but I can manage via bash script later

what are my next steps to get my internal work? :)

---

### Post by chili555 on 2012-01-06
> what are my next steps to get my internal work?With the conflict in the 80211 subsystems, they are probably *not* going to work at the same time. I thought you wanted the USB because it offers greater range the internal does not.

Pick one, not both.

---

### Post by frncz on 2012-01-06
chili555 - this is pretty amazing hand-holding!
It is wonderful that there are people like you on this forum

---

### Post by Kyslosh on 2012-01-06
yea Chili is great guy !

Yep I've picked ;) USB stick ;)

but one Question so if I want to use internal (if I forget my stick home etcetera) I need to uninstall compat?

(I mean is it possible to switch between? on fly? or at least on reboot?)

---

### Post by chili555 on 2012-01-06
> but one Question so if I want to use internal (if I forget my stick home etcetera) I need to uninstall compat?Sorry but yes. You'd also need to re-load the driver for your internal:```
sudo modprobe rtl8192ce
```Thanks for the kind comments. The dev.c file is pretty intricate stuff!

---

### Post by Kyslosh on 2012-01-06
All this invoke one another question.
Is there any way how to actually compile both driver "sets" and in GRUB (boot) would ask which I want to use/boot up with?

---

### Post by chili555 on 2012-01-06
> Is there any way how to actually compile both driver "sets" Probably.> and in GRUB (boot) would ask which I want to use/boot up with? Not in grub; however, you could probably come up with a shell script to "Start Internal Wireless" that modprobed the previously blacklisted driver and upped the interface; likewise "Start USB Wireless."

I'm pretty weak on shell scripts but we can compile a compat-wireless rtl8192ce if you'd like another grueling adventure.

---

### Post by Kyslosh on 2012-01-06
> **chili555 said:**
> 
Not in grub; however, you could probably come up with a shell script to  "Start Internal Wireless" that modprobed the previously blacklisted  driver and upped the interface; likewise "Start USB Wireless."

I won't mind modprobing manualy... eventuelly I would come up with bash script ;)

u mean something like
```

if USBSTICK is plugged -> modprobe rtl8187 
else -> modprobe rtl8192ce

```that will be easy to do if I can get to work both internal and usb devices without reinstalling/compiling.

> **chili555 said:**
> 
I'm pretty weak on shell scripts but we can compile a compat-wireless rtl8192ce if you'd like another grueling adventure.

I like your idea :) and I would like to continue compiling stuff as far as its educating+working.

So where do we start with compiling rtl8192ce? 
I already downloaded rtl8192ce driver 
92ce_se_de_linux_mac80211_0005.1230.2011.tar.gz
//edit: I guess I won't need it because u mentioned compat-w so no need for drivers which I dled

(my lspci report: 07:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01))
but driver should be 8192ce as it worked fine (but signal strength indicator was "broken")

---

### Post by chili555 on 2012-01-06
> u mean something like
Code:

if USBSTICK is plugged -> modprobe rtl8187 
else -> modprobe rtl8192ce

No, I envision a launcher on your desktop with a hover that says, "Start internal wireless" for which the executable is like modprobe rtl8192ce && ifconfig wlan0 up. Another for USB is something like modprobe rtl8187 && ifconfig wlan1 up. A person more clever than me could probably figure out a script that grepped 8189 in lsusb and then started rtl8187; otherwise rtl8192ce.

OK, let's go:```
cd Desktop/compat-wireless-whatever
sudo su
./scripts/driver-select restore
make clean
./scripts/driver-select rtlwifi
make
make install
exit
```Now test by removing the USB device and do:```
sudo modprobe rtl8192ce
sudo ifconfig wlan0 up
```Any errors or warnings or Safe Modes?

---

### Post by Kyslosh on 2012-01-06
> **chili555 said:**
> 

```

**sudo modprobe rtl8192ce**
sudo ifconfig wlan0 up
```Any errors or warnings or Safe Modes?

shouldn't I modprobe -r rtl8187 first? (before modprobing internal)


[U][B]
!! and it works !![/B][/U]
(I unloaded rtl8187 first tho)


this is awesome :)

I'll make bash script for this first thing morning (its 3:18 am here) central europe.

---

### Post by chili555 on 2012-01-06
> **Kyslosh said:**
> shouldn't I modprobe -r rtl8187 first? (before modprobing internal)If the 80211 subsystems are now identical and therefor compatible, it shouldn't matter, but why mess with gasoline and matches. Go ahead.

We probably will still have a tweak or two to make after we see your result.

---

### Post by Kyslosh on 2012-01-06
Ok I modprobed both drivers but it seems that rtl8187 does not work I mean after
modprobe rtl8187 (no error)
nothing happens I mean ifconfig does not show my wlan1 (USB)
neither does iw command

I also tried 
```

modprobe -r rtl8192ce
modprobe rtl8187

```same results as before (nothing shows up in ifconfig)

//trying reboot

after reboot same results USB stick does not work

```

**modprobe rtl8187**
**ifconfig wlan1 up**
wlan1: ERROR while getting interface flags: No such device
**iw wlan1**
nl80211 not found.
**ifconfig wlan0 up**
wlan0: ERROR while getting interface flags: No such device
**iw wlan0**
nl80211 not found.


**lsmod | grep rtl**
rtl8187                52861  0 
mac80211              309235  1 rtl8187
cfg80211              187835  2 rtl8187,mac80211
eeprom_93cx6            1656  1 rtl8187
**modprobe rtl8192ce**
**lsmod | grep rtl**
rtl8192ce              74903  0 
rtl8192c_common        64046  1 rtl8192ce
rtlwifi               100040  1 rtl8192ce
rtl8187                52861  0 
mac80211              309235  4 rtl8192ce,rtl8192c_common,rtlwifi,rtl8187
cfg80211              187835  3 rtlwifi,rtl8187,mac80211
eeprom_93cx6            1656  1 rtl8187
**ifconfig | grep wlan**
wlan0     Link encap:Ethernet  HWaddr 88:9f:fa:ff:c0:41
 




```//USB sticks MAC-> 00:4F:78:01:dB:3D (I know its not helpful info but its here)
//after modprobing rtl8192ce wlan0 (internal does work)
//offline now need 2 sleep ;)

---

### Post by chili555 on 2012-01-07
Let's see if there are kernel messages that help us:```
sudo modprobe rtl8187
dmesg | grep 818
```Thanks.

---

### Post by Kyslosh on 2012-01-07
Ok so ;)
I get collision
I restored drivers and I started all over again I mean I uninstalled all compat and start in different order
first I installed rtl8192ce
(all running)
then I installed rtl8187
```

make wlunload
modprobe rtl8187
ifconfig wlan1 up [OK]
modprobe rtl8192ce  <---- caused collision

```[B]
(no reboot yet!)[/B]

```
[B]
lsmod | grep rtl[/B]
rtl8192ce              77963  1 
rtl8192c_common        59103  1 rtl8192ce
rtlwifi                85430  1 rtl8192ce
rtl8187                53053  0 
mac80211              309235  3 rtl8192ce,rtlwifi,rtl8187
cfg80211              187867  3 rtlwifi,rtl8187,mac80211
eeprom_93cx6            1656  1 rtl8187


```USBstick is working right now internal does not

```

**ifconfig | grep wlan**
wlan1     Link encap:Ethernet  HWaddr 00:4f:78:01:db:3d 
**ifconfig wlan0 up**
wlan0: ERROR while getting interface flags: No such device

```**after reboot**
I did following
```

lsmod | grep rtl

```
no rtl module was loaded (modprobed)
note: my USB stick was **unplugged**

so I did
```

modprobe -r rtl8187 (just to make sure)
modprobe rtl8192ce <---------- caused collision
_Segmentation fault_


**lsmod | grep rtl**
rtl8192ce              77963  1 
rtl8192c_common        59103  1 rtl8192ce
rtlwifi                85430  1 rtl8192ce
mac80211              309235  2 rtl8192ce,rtlwifi
cfg80211              187867  2 rtlwifi,mac80211


```

---

### Post by chili555 on 2012-01-07
I will say this again and, hopefully for the last time. It is doubtful that you will ever get both running at the same time. Why on earth would you want to?

I suggest you blacklist *BOTH* drivers. Reboot the computer and stick in the USB stick. Run:```
sudo modprobe rtl8187
sudo ifconfig wlan1 up
```Does it work? Great!

Now let's try the internal. Remove the USB stick and run:```
sudo modprobe -r rtl8187
sudo modprobe rtl8192ce
sudo ifconfig wlan0 up
```Does it work? Great!

You have suggested that you want to use one *OR* the other. Let's stick to that.

---

### Post by Kyslosh on 2012-01-07
> **chili555 said:**
> I will say this again and, hopefully for the last time. It is doubtful that you will ever get both running at the same time. Why on earth would you want to?


I did run both on same time but that was a mistake please read "after boot edit" ;) (If I am right modprobe -r stops device running so I can run another device) in my case I stop USB stick to run internal, and I stop internal to run USB stick

I unplugged + modprobe -r rtl8187 (even in my lsmod rtl8187 is not present!)
modprobe rtl8192ce makes collision!!!

both devices are in blacklist
**clean start**
lsmod | grep rtl
(nthing here)
modprobe rtl8192ce <-- collision
_Segmentation fault_

```

dmesg | grep rtl
[   86.380870] rtl8192ce 0000:07:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   86.380882] rtl8192ce 0000:07:00.0: setting latency timer to 64
[   86.380985] Modules linked in: rtl8192ce(+) rtl8192c_common rtlwifi mac80211 cfg80211 compat dm_crypt joydev snd_hda_codec_hdmi snd_hda_codec_conexant snd_hda_intel snd_hda_codec snd_hwdep snd_pcm_oss snd_mixer_oss thinkpad_acpi snd_pcm rfkill snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device fglrx(P) uvcvideo snd videodev psmouse snd_page_alloc soundcore serio_raw sdhci_pci v4l2_compat_ioctl32 nvram lp sdhci wmi parport mac_hid i915 drm_kms_helper drm ahci libahci r8169 mii i2c_algo_bit intel_agp intel_gtt video
[   86.381608]  [<ffffffffa053903b>] rtl_pci_probe+0x103/0x17b1 [rtlwifi]
[   86.383620]  [<ffffffffa0086023>] rtl92ce_module_init+0x23/0x59 [rtl8192ce]


```

note to all my todays posts
I did new install of compat-wireless but in different order first I installed rtl8192ce and as second I installed rtl8187 
yesterday (it was first 8187 and as second 8192ce) -> there was no collision but 8187 did not work after modprobe -r rtl8192ce, modprobe rtl8187.
[U][B]
I guess compat-wireless installs even different mac80211[/B][/U] with different drivers

---

### Post by chili555 on 2012-01-07
> even in my lsmod rtl8187 is not present!How about all of rtl8187's dependencies/henchmen?```
filename:       drivers/net/wireless/rtl818x/rtl8187/rtl8187.ko
license:        GPL
description:    RTL8187/RTL8187B USB wireless driver
author:         Larry Finger <Larry.Finger@lwfinger.net>
author:         Hin-Tak Leung <htl10@users.sourceforge.net>
author:         Herton Ronaldo Krzesinski <herton@mandriva.com.br>
author:         Andrea Merello <andreamrl@tiscali.it>
author:         Michael Wu <flamingice@sourmilk.net>
srcversion:     DEECA9F5638D0907B4C8D78
<snip>
[COLOR="Red"]depends:        mac80211,eeprom_93cx6,cfg80211[/COLOR]
vermagic:       3.0.0-14-generic SMP mod_unload modversions 686
```Please be sure they are removed as well and then try rtl8192ce.

---

### Post by Kyslosh on 2012-01-07
> **chili555 said:**
> How about all of rtl8187's dependencies/henchmen?```

srcversion:     DEECA9F5638D0907B4C8D78
<snip>
[COLOR=Red]depends:        mac80211,eeprom_93cx6,cfg80211[/COLOR]
vermagic:       3.0.0-14-generic SMP mod_unload modversions 686
```Please be sure they are removed as well and then try rtl8192ce.

I am sorry my editing makes things confusing

clean start (both devices in blacklist) USB device unplugged

```

**lsmod**
Module                  Size  Used by
dm_crypt               16476  0 
joydev                 10865  0 
snd_hda_codec_hdmi     24590  1 
snd_hda_codec_conexant    46388  1 
snd_hda_intel          25382  4 
snd_hda_codec          89862  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep               6666  1 snd_hda_codec
snd_pcm_oss            39737  0 
snd_mixer_oss          15609  1 snd_pcm_oss
snd_pcm                83135  5 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            29952  0 
snd_seq_midi            5676  0 
snd_rawmidi            21765  1 snd_seq_midi
snd_seq_midi_event      6708  2 snd_seq_oss,snd_seq_midi
uvcvideo               63292  0 
thinkpad_acpi          75592  0 
snd_seq                54693  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
videodev               81991  1 uvcvideo
snd_timer              21958  3 snd_pcm,snd_seq
rfkill                 18476  1 thinkpad_acpi
snd_seq_device          6265  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
psmouse                60384  0 
snd                    65738  20 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,thinkpad_acpi,snd_seq,snd_timer,snd_seq_device
v4l2_compat_ioctl32     8184  1 videodev
serio_raw               4784  0 
fglrx                3121822  193 
soundcore               7240  1 snd
mac_hid                 3869  0 
snd_page_alloc          8149  2 snd_hda_intel,snd_pcm
lp                      9893  0 
nvram                   7223  1 thinkpad_acpi
sdhci_pci               9136  0 
sdhci                  18564  1 sdhci_pci
wmi                     9944  0 
parport                34080  1 lp
i915                  522208  2                                                                            
drm_kms_helper         32921  1 i915                                                                       
drm                   211510  3 i915,drm_kms_helper                                                        
ahci                   21622  2                                                                            
libahci                22318  1 ahci
i2c_algo_bit            5628  1 i915
r8169                  42945  0 
intel_agp              11862  1 i915
mii                     4807  1 r8169
intel_gtt              16156  3 i915,intel_agp
video                  12530  1 i915


```

---

### Post by chili555 on 2012-01-07
> clean start (both devices in blacklist) USB device unplugged
Good. Now if you modprobe rtl8192ce, does it cause a collision or work as expected?

---

### Post by Kyslosh on 2012-01-07
> **chili555 said:**
> Good. Now if you modprobe rtl8192ce, does it cause a collision or work as expected?

it makes collision :/
```

**modprobe rtl8192ce**
Segmentation fault

**dmesg**
[  316.393067] kernel BUG at /root/compat-w/net/mac80211/main.c:618!
[  316.393106] invalid opcode: 0000 [#1] SMP 
[  316.393129] last sysfs file: /sys/module/rfkill/initstate
[  316.393156] CPU 2 
[  316.393167] Modules linked in: rtl8192ce(+) rtl8192c_common rtlwifi mac80211 cfg80211 compat dm_crypt joydev snd_hda_codec_hdmi snd_hda_codec_conexant snd_hda_intel snd_hda_codec snd_hwdep snd_pcm_oss snd_mixer_oss snd_pcm snd_seq_dummy snd_seq_oss snd_seq_midi snd_rawmidi snd_seq_midi_event uvcvideo thinkpad_acpi snd_seq videodev snd_timer rfkill snd_seq_device psmouse snd v4l2_compat_ioctl32 serio_raw fglrx(P) soundcore mac_hid snd_page_alloc lp nvram sdhci_pci sdhci wmi parport i915 drm_kms_helper drm ahci libahci i2c_algo_bit r8169 intel_agp mii intel_gtt video
[  316.393372] 
[  316.393378] Pid: 1758, comm: modprobe Tainted: P            2.6.39.4 #1 LENOVO 44012RG/44012RG
[  316.393407] RIP: 0010:[<ffffffffa0637f3a>]  [<ffffffffa0637f3a>] ieee80211_alloc_hw+0x48a/0x4a0 [mac80211]
[  316.393442] RSP: 0018:ffff880139339c08  EFLAGS: 00010246
[  316.393459] RAX: ffff880103212540 RBX: ffff880103210d40 RCX: 0000000000000000
[  316.393480] RDX: 0000000000000078 RSI: ffffffffa04804ec RDI: ffff8801032100c0
[  316.393502] RBP: ffff880139339c28 R08: 0000000000000000 R09: ffff880115084c00
[  316.393523] R10: 0000000000000001 R11: dead000000200200 R12: ffff8801032101e0
[  316.393544] R13: ffffffffa0694080 R14: ffff880138cbe1f8 R15: 00000000fffffff4
[  316.393565] FS:  00007f23370b4700(0000) GS:ffff88013fa80000(0000) knlGS:0000000000000000
[  316.393590] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
[  316.393607] CR2: 00007f23370b2000 CR3: 000000010331b000 CR4: 00000000000406e0
[  316.393628] DR0: 0000000000000000 DR1: 0000000000000000 DR2: 0000000000000000
[  316.393649] DR3: 0000000000000000 DR6: 00000000ffff0ff0 DR7: 0000000000000400
[  316.393671] Process modprobe (pid: 1758, threadinfo ffff880139338000, task ffff880111be4440)
[  316.393696] Stack:
[  316.393702]  ffff880139339c28 00000000ffffffff ffffffffa06ab220 ffff880138cbe000
[  316.393727]  ffff880139339d08 ffffffffa069203b ffff880139339c68 ffffffff817da07f
[  316.393751]  ffff880139339c78 ffffffff811bc5a9 ffffffff81c69084 ffff88013501a960
[  316.393776] Call Trace:
[  316.393787]  [<ffffffffa069203b>] rtl_pci_probe+0x103/0x17b1 [rtlwifi]
[  316.393809]  [<ffffffff811bc5a9>] ? sysfs_find_dirent+0x49/0x70
[  316.393829]  [<ffffffff81034d89>] ? default_spin_lock_flags+0x9/0x10
[  316.393849]  [<ffffffff81034d89>] ? default_spin_lock_flags+0x9/0x10
[  316.393870]  [<ffffffff81309daf>] local_pci_probe+0x5f/0xd0
[  316.393888]  [<ffffffff8130b021>] pci_device_probe+0x101/0x120
[  316.393908]  [<ffffffff813baa7a>] ? driver_sysfs_add+0x7a/0xb0
[  316.393926]  [<ffffffff813babd6>] driver_probe_device+0x96/0x1c0
[  316.393945]  [<ffffffff813bad00>] ? driver_probe_device+0x1c0/0x1c0
[  316.393964]  [<ffffffff813bad9b>] __driver_attach+0x9b/0xa0
[  316.393982]  [<ffffffff813bad00>] ? driver_probe_device+0x1c0/0x1c0
[  316.394002]  [<ffffffff813b9ff8>] bus_for_each_dev+0x68/0x90
[  316.394020]  [<ffffffff813ba9fe>] driver_attach+0x1e/0x20
[  316.394037]  [<ffffffff813ba2dd>] bus_add_driver+0xcd/0x270
[  316.394055]  [<ffffffffa04c3000>] ? 0xffffffffa04c2fff
[  316.394071]  [<ffffffff813bb430>] driver_register+0x80/0x150
[  316.394090]  [<ffffffff810cc0d9>] ? tracepoint_module_notify+0x29/0x30
[  316.394110]  [<ffffffffa04c3000>] ? 0xffffffffa04c2fff
[  316.394952]  [<ffffffff8130b2a6>] __pci_register_driver+0x56/0xd0
[  316.395793]  [<ffffffffa04c3023>] rtl92ce_module_init+0x23/0x59 [rtl8192ce]
[  316.396667]  [<ffffffff81002043>] do_one_initcall+0x43/0x190
[  316.397506]  [<ffffffff8109daab>] sys_init_module+0xbb/0x200
[  316.398346]  [<ffffffff815d5f82>] system_call_fastpath+0x16/0x1b
[  316.399180] Code: 5c 41 5d c9 c3 0f 1f 40 00 0d 68 01 00 00 41 89 84 24 34 08 00 00 e9 f6 fb ff ff 0f 0b eb fe 0f 0b eb fe 0f 0b eb fe 0f 0b eb fe <0f> 0b eb fe 0f 0b eb fe 0f 0b eb fe 66 2e 0f 1f 84 00 00 00 00 
[  316.400953] RIP  [<ffffffffa0637f3a>] ieee80211_alloc_hw+0x48a/0x4a0 [mac80211]
[  316.401814]  RSP <ffff880139339c08>
[  316.406685] ---[ end trace 026fa63296fe683c ]---



```


note to all my todays posts
I did new install of compat-wireless but in different order first I installed rtl8192ce and as second I installed rtl8187 
yesterday (it was first 8187 and as second 8192ce) -> there was no  collision but 8187 did not work after modprobe -r rtl8192ce, modprobe  rtl8187.
[U][B]
I guess compat-wireless installs even different mac80211[/B][/U] with different drivers

---

### Post by chili555 on 2012-01-07
I think the answer to this question:> Is there any way how to actually compile both driver "sets" Is, evidently not. I think you now have three options; first, uninstall compat-wireless and live with the internal. Second, blacklist the internal and use the USB permanently. Third, press forward with further experiments and hope for the best with no guarantees. I have another idea. It's crazy but may work.

It is, however, perfectly fine to conclude that you have a working solution with the USB and stop now.

---

### Post by Kyslosh on 2012-01-07
> **chili555 said:**
> I think the answer to this question:Is, evidently not. I think you now have three options; first, uninstall compat-wireless and live with the internal. Second, blacklist the internal and use the USB permanently. Third, press forward with further experiments and hope for the best with no guarantees. I have another idea. It's crazy but may work.

It is, however, perfectly fine to conclude that you have a working solution with the USB and stop now.
:) thanks for all help you provided I am glad people like you even exist. (tons of patience, knowledge...)

anyway I am going to try one another thing since yesterdays "set" we may call it (I mean first install compat rtl8187, and right after install compat rtl8192ce)
and see what will happend ;) 
I am sure result will be deff. different I assume there will be no collision but rtl8187 won't work and we may solve this unworking problem.

---

### Post by Kyslosh on 2012-01-07
> **chili555 said:**
> Let's see if there are kernel messages that help us:```
sudo modprobe rtl8187
dmesg | grep 818
```Thanks.

```

dmesg | grep 818
[    0.010000] Detected 2294.818 MHz processor.
[    0.000002] Calibrating delay loop (skipped), value calculated using timer frequency.. 4589.63 BogoMIPS (lpj=22948180)
[    1.838181] pci 0000:00:02.0: reg 18: [mem 0xd0000000-0xdfffffff 64bit pref]
[    1.838186] pci 0000:00:02.0: reg 20: [io  0x7000-0x703f]
[    1.845212] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[  922.240626] usbcore: registered new interface driver rtl8187

```


there is definitely difference when I install drivers compat-wireless in different order as I am mentioning above.

---

### Post by chili555 on 2012-01-07
> there is definitely difference when I install drivers compat-wireless in different order And does it allow you to select either to run correctly? Or are you ready to go all USB? Or are you ready to try other, more drastic measures???

---

### Post by Kyslosh on 2012-01-07
> **chili555 said:**
> And does it allow you to select either to run correctly? Or are you ready to go all USB? Or are you ready to try other, more drastic measures???

Yes if I 
```
[B]probemode -r rtl8187
probmode rtl8192ce[/B]

```wlan0 (internal does work)

right after

```

[B]probmode -r rtl8192ce
probmode rtl8187[/B]

```wlan1 does not seem to work
```

**ifconfig wlan1 up**
wlan1: ERROR while getting interface flags: No such device

```
and yea I'm ready to whatever it takes :)

////I won't be able to reply ASAP,  need to do something - 2 hours.

---

### Post by chili555 on 2012-01-07
> yea I'm ready to whatever it takesI like your attitude! Let's rock.

First run:```
cd Desktop/compat-wireless-whatever
sudo su
modprobe -r rtl8187
modprobe -r rtl8192ce
make uninstall
gedit /etc/udev/rules.d/network_drivers.rules
```Add one long line:```

ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="1b75", ATTR{idProduct}=="8189", RUN+="/sbin/modprobe -qba rtl8187"
```Caps, brackets, punctuation, etc. are crucial. Proofread twice, save and close gedit.```
sudo gedit /etc/modprobe.d/network_drivers.conf
```Add one long single line:```

install rtl8187 /sbin/modprobe --ignore-install rtl8187 $CMDLINE_OPTS; /bin/echo "1b75 8189" > /sys/bus/usb/drivers/rtl8187/new_id
```
Proofread twice, save and close gedit. Insert the device. If it doesn't start immediately, you might have to do:```
sudo modprobe rtl8187
```Now do both work based on the original, built-in drivers and 80211 subsystem?

---

### Post by Kyslosh on 2012-01-07
It works!!!
everything works ;) I can even run both (worthless but no conflict!)

you are the man! (:

Thank you so much!

---

### Post by chili555 on 2012-01-07
> **Kyslosh said:**
> It works!!!
everything works ;) I can even run both (worthless but no conflict!)

you are the man! (:

Thank you so much!Awesome! Glad it's working.

It only took a lightning fast 43 posts!

---

### Post by bwajbii on 2012-06-08
Hi Chili,

Thanks for these posts. I'm running a similar custom module on Ubuntu & trying to get the Netgear WNA1000M working via a powered USB hub. I tried your compat-wireless method to the T & it never brought up the wlan0 at all & kept giving this error:
```

root@arago:~# ifconfig wlan0 up
ifconfig: SIOCGIFFLAGS: No such device

```lsmod output:
```

root@arago:~# lsmod
Module                  Size  Used by    Not tainted
ti81xxhdmi             14478  0
ti81xxfb               21771  0
vpss                   72346  2 ti81xxhdmi,ti81xxfb
ipv6                  209855 10
syslink              1108491  0
rtl8192cu              86535  0
rtl8192c_common        52988  1 rtl8192cu
rtlwifi                85477  1 rtl8192cu
mac80211              150543  3 rtl8192cu,rtl8192c_common,rtlwifi
cfg80211              122145  2 rtlwifi,mac80211

```Here's the output of the dmesg as well:
```

root@arago:~# dmesg
 SATA max UDMA/133 mmio [mem 0x4a140000-0x4a150fff] port 0x100 irq 16
ata2: SATA max UDMA/133 mmio [mem 0x4a140000-0x4a150fff] port 0x180 irq 16
omap2-nand driver initializing
ONFI flash detected
NAND device: Manufacturer ID: 0xad, Chip ID: 0xda (Hynix ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ)
Scanning device for bad blocks
Creating 7 MTD partitions on "omap2-nand.0":
0x000000000000-0x000000120000 : "U-Boot"
0x000000120000-0x000000240000 : "U-Boot Update"
0x000000240000-0x000000260000 : "U-Boot Env Update"
0x000000260000-0x000000280000 : "U-Boot Env"
0x000000280000-0x0000006c0000 : "Kernel"
0x0000006c0000-0x00000cee0000 : "File System"
0x00000cee0000-0x000010000000 : "Reserved"
davinci_mdio davinci_mdio.0: davinci mdio revision 1.6
davinci_mdio davinci_mdio.0: detected phy mask fffffffc
davinci_mdio.0: probed
davinci_mdio davinci_mdio.0: phy[0]: device 0:00, driver unknown
davinci_mdio davinci_mdio.0: phy[1]: device 0:01, driver unknown
usbcore: registered new interface driver cdc_ether
usbcore: registered new interface driver dm9601
Initializing USB Mass Storage driver...
usbcore: registered new interface driver usb-storage
USB Mass Storage support registered.
mice: PS/2 mouse device common for all mice
omap_rtc omap_rtc: rtc core: registered omap_rtc as rtc0
i2c /dev entries driver
Linux video capture interface: v2.00
Software Watchdog Timer: 0.07 initialized. soft_noboot=0 soft_margin=60 sec (nowayout= 1)
usbcore: registered new interface driver usbhid
usbhid: USB HID core driver
notify_init : notify drivercreated  for  remote proc id 2 at physical Address 0xbf900000
asoc: tlv320aic3x-hifi <-> davinci-mcasp.2 mapping ok
asoc: HDMI-DAI-CODEC <-> hdmi-dai mapping ok
ALSA device list:
  #0: TI81XX EVM
TCP cubic registered
NET: Registered protocol family 17
VFP support v0.3: implementor 41 architecture 3 part 30 variant c rev 3
omap_voltage_late_init: Voltage driver support not added
Power Management for TI81XX.
smartreflex smartreflex: Driver initialized
omap_rtc omap_rtc: setting system clock to 2000-01-01 00:00:00 UTC (946684800)
usb 1-1: new high speed USB device using musb-hdrc and address 2
usb 1-1: New USB device found, idVendor=2001, idProduct=f103
usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
hub 1-1:1.0: USB hub found
hub 1-1:1.0: 7 ports detected
davinci_mdio davinci_mdio.0: resetting idled controller
net eth0: attached PHY driver [Generic PHY] (mii_bus:phy_addr=0:01, id=1cc914)
usb 1-1.1: new high speed USB device using musb-hdrc and address 3
usb 1-1.1: New USB device found, idVendor=0846, idProduct=9041
usb 1-1.1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
usb 1-1.1: Product: 802.11n WLAN Adapter
usb 1-1.1: Manufacturer: Realtek
usb 1-1.1: SerialNumber: 00e04c000001
IP-Config: Complete:
     device=eth0, addr=10.0.3.2, mask=255.255.0.0, gw=10.0.1.129,
     host=Z3-Netra, domain=, nis-domain=(none),
     bootserver=10.0.2.5, rootserver=10.0.2.5, rootpath=
Waiting 4sec before mounting root device...
ata1: SATA link down (SStatus 0 SControl 300)
ata2: SATA link down (SStatus 0 SControl 300)
PHY: 0:01 - Link is Up - 1000/Full
VFS: Mounted root (nfs filesystem) on device 0:14.
devtmpfs: mounted
Freeing init memory: 200K
udevd (67): /proc/67/oom_adj is deprecated, please use /proc/67/oom_score_adj instead.
udev: starting version 141
cfg80211: Calling CRDA to update world regulatory domain
rtl8192cu: MAC address: c4:3d:c7:78:33:79
rtl8192cu: Board Type 0
rtl8192cu:rtl92cu_init_sw_vars():<0-0> Failed to request firmware!
rtlwifi:rtl_usb_probe():<0-0> Can't init_sw_vars.
usbcore: registered new interface driver rtl8192cu
SysLink version : 2.00.05.85
SysLink module created on Date:May 21 2012 Time:11:30:28
NET: Registered protocol family 10
VPSS_CORE : core init
VPSS_CORE : cpu version 0x81600281
VPSS_SHRBUF: sbuf init
VPSS_SHRBUF: map 0xbfb00000 to 0xd2400000 with size 2097152
VPSS_FVID2: fvid2 init
VPSS_SHRBUF: FOUND 0xbfb00000, end 0xbfd00000, map vir 0xd2400000 size 8192
VPSS_FVID2: Handshake...
VPSS_SHRBUF: FOUND 0xbfb02000, end 0xbfd00000, map vir 0xd2402000 size 4096
VPSS_SHRBUF: free mem paddr 0xbfb02000 vaddr 0xd2402000 size 4096
VPSS_FVID2: get firmware version 0x01000133.
VPSS_SYSTEM: enter system init
VPSS_SHRBUF: FOUND 0xbfb02000, end 0xbfd00000, map vir 0xd2402000 size 4096
VPSS_FVID2: Fvid2 handle 0x9f3cc458 with notifyno 10 within 0 ms
VPSS_FVID2: send control with cmd 0x10080002
VPSS_FVID2: control event 0x10080002 return 0 within 1 ms.
VPSS_DCTRL: dctrl init
VPSS_SHRBUF: FOUND 0xbfb03000, end 0xbfd00000, map vir 0xd2403000 size 4096
VPSS_FVID2: Fvid2 handle 0x9f3cc478 with notifyno 11 within 0 ms
VPSS_DCTRL: mode hdmi:1080p-60
VPSS_FVID2: send control with cmd 0x10040003
VPSS_FVID2: control event 0x10040003 return 0 within 0 ms.
VPSS_FVID2: send control with cmd 0x10040003
VPSS_FVID2: control event 0x10040003 return 0 within 0 ms.
VPSS_FVID2: send control with cmd 0x10040003
VPSS_FVID2: control event 0x10040003 return 0 within 0 ms.
VPSS_FVID2: send control with cmd 0x10040003
VPSS_FVID2: control event 0x10040003 return 0 within 0 ms.
VPSS_FVID2: send control with cmd 0x1004001c
VPSS_FVID2: control event 0x1004001c return 0 within 0 ms.
VPSS_FVID2: send control with cmd 0x1004001c
VPSS_FVID2: control event 0x1004001c return 0 within 0 ms.
VPSS_FVID2: send control with cmd 0x1004001c
VPSS_FVID2: control event 0x1004001c return 0 within 0 ms.
VPSS_SYSTEM: enter set pll 148500KHz for VENC 1
VPSS_FVID2: send control with cmd 0x10080000
VPSS_FVID2: control event 0x10080000 return 0 within 0 ms.
VPSS_SYSTEM: enter set pll 148500KHz for VENC 1
VPSS_FVID2: send control with cmd 0x10080000
VPSS_FVID2: control event 0x10080000 return 0 within 0 ms.
VPSS_SYSTEM: enter set pll 216000KHz for VENC 0
VPSS_FVID2: send control with cmd 0x10080000
VPSS_FVID2: control event 0x10080000 return 0 within 0 ms.
VPSS_SYSTEM: enter set pll 74250KHz for VENC 2
VPSS_FVID2: send control with cmd 0x10080000
VPSS_FVID2: control event 0x10080000 return 0 within 1 ms.
VPSS_FVID2: send control with cmd 0x1004001a
VPSS_FVID2: control event 0x1004001a return 0 within 0 ms.
VPSS_FVID2: send control with cmd 0x10040019
VPSS_FVID2: control event 0x10040019 return 0 within 0 ms.
VPSS_FVID2: send control with cmd 0x10040019
VPSS_FVID2: control event 0x10040019 return 0 within 0 ms.
VPSS_FVID2: send control with cmd 0x10040019
VPSS_FVID2: control event 0x10040019 return 0 within 0 ms.
VPSS_FVID2: send control with cmd 0x10040019
VPSS_FVID2: control event 0x10040019 return 0 within 0 ms.
VPSS_GRPX : grpx init
VPSS_SHRBUF: FOUND 0xbfb04000, end 0xbfd00000, map vir 0xd2404000 size 4096
VPSS_VIDEO: video init
VPSS_SHRBUF: FOUND 0xbfb05000, end 0xbfd00000, map vir 0xd2405000 size 8192
VPSS_CAPTURE: cap init
VPSS_SHRBUF: FOUND 0xbfb07000, end 0xbfd00000, map vir 0xd2407000 size 49152
VPSS_SHRBUF: sharing buffer used 77824 byte, left 2019328 bytes
VPSS_GRPX : (0)- get resolution.
VPSS_DCTRL: enter get output format
VPSS_FVID2: send control with cmd 0x1004001a
VPSS_FVID2: control event 0x1004001a return 0 within 0 ms.
VPSS_GRPX : (1)- get resolution.
VPSS_DCTRL: enter get output format
VPSS_FVID2: send control with cmd 0x1004001a
VPSS_FVID2: control event 0x1004001a return 0 within 0 ms.
VPSS_GRPX : (2)- get resolution.
VPSS_DCTRL: enter get output format
VPSS_FVID2: send control with cmd 0x1004001a
VPSS_FVID2: control event 0x1004001a return 0 within 1 ms.
VPSS_GRPX : (0)- get resolution.
VPSS_DCTRL: enter get output format
VPSS_FVID2: send control with cmd 0x1004001a
VPSS_FVID2: control event 0x1004001a return 0 within 0 ms.
VPSS_GRPX : (0)- get region params.
VPSS_GRPX : (0)- get sc params.
VPSS_GRPX : (0)- get resolution.
VPSS_DCTRL: enter get output format
VPSS_FVID2: send control with cmd 0x1004001a
VPSS_FVID2: control event 0x1004001a return 0 within 0 ms.
VPSS_GRPX : (0) - get timing
VPSS_GRPX : (1)- get resolution.
VPSS_DCTRL: enter get output format
VPSS_FVID2: send control with cmd 0x1004001a
VPSS_FVID2: control event 0x1004001a return 0 within 0 ms.
VPSS_GRPX : (1)- get region params.
VPSS_GRPX : (1)- get sc params.
VPSS_GRPX : (1)- get resolution.
VPSS_DCTRL: enter get output format
VPSS_FVID2: send control with cmd 0x1004001a
VPSS_FVID2: control event 0x1004001a return 0 within 0 ms.
VPSS_GRPX : (1) - get timing
VPSS_GRPX : (2)- get resolution.
VPSS_DCTRL: enter get output format
VPSS_FVID2: send control with cmd 0x1004001a
VPSS_FVID2: control event 0x1004001a return 0 within 0 ms.
VPSS_GRPX : (2)- get region params.
VPSS_GRPX : (2)- get sc params.
VPSS_GRPX : (2)- get resolution.
VPSS_DCTRL: enter get output format
VPSS_FVID2: send control with cmd 0x1004001a
VPSS_FVID2: control event 0x1004001a return 0 within 0 ms.
VPSS_GRPX : (2) - get timing
VPSS_GRPX : (0)- apply changes into FVID2_FRAME.
VPSS_GRPX : (0)- set format bpp 32 df 4104, pitch 7680.
VPSS_GRPX : (0)- get region params.
VPSS_GRPX : (0)- set region params.
VPSS_GRPX : (0)- add buffer 0x87e00000
VPSS_GRPX : (0)- apply changes into FVID2_FRAME.
VPSS_GRPX : (1)- apply changes into FVID2_FRAME.
VPSS_GRPX : (1)- set format bpp 32 df 4104, pitch 7680.
VPSS_GRPX : (1)- get region params.
VPSS_GRPX : (1)- set region params.
VPSS_GRPX : (1)- add buffer 0x89600000
VPSS_GRPX : (1)- apply changes into FVID2_FRAME.
VPSS_GRPX : (2)- apply changes into FVID2_FRAME.
VPSS_GRPX : (2)- set format bpp 32 df 4104, pitch 2880.
VPSS_GRPX : (2)- get region params.
VPSS_GRPX : (2)- set region params.
VPSS_GRPX : (2)- add buffer 0x8a600000
VPSS_GRPX : (2)- apply changes into FVID2_FRAME.
VPSS_DCTRL: enter venc disable
VPSS_FVID2: send control with cmd 0x1004001a
VPSS_FVID2: control event 0x1004001a return 0 within 0 ms.
VPSS_FVID2: send control with cmd 0x1004001b
VPSS_FVID2: control event 0x1004001b return 0 within 0 ms.
VPSS_FVID2: send control with cmd 0x1004001a
VPSS_FVID2: control event 0x1004001a return 0 within 0 ms.
VPSS_FVID2: send control with cmd 0x10040004
VPSS_FVID2: control event 0x10040004 return 0 within 0 ms.
VPSS_FVID2: send control with cmd 0x10040003
VPSS_FVID2: control event 0x10040003 return 0 within 0 ms.
VPSS_FVID2: send control with cmd 0x1004001a
VPSS_FVID2: control event 0x1004001a return 0 within 0 ms.
VPSS_FVID2: send control with cmd 0x10040019
VPSS_FVID2: control event 0x10040019 return 0 within 2 ms.
VPSS_GRPX : create grpx0
VPSS_DCTRL: enter set node
VPSS_FVID2: send control with cmd 0x10040018
VPSS_FVID2: control event 0x10040018 return 0 within 0 ms.
VPSS_FVID2: send control with cmd 0x10040017
VPSS_FVID2: control event 0x10040017 return 0 within 0 ms.
VPSS_FVID2: Fvid2 handle 0x9f3cc498 with notifyno 12 within 0 ms
VPSS_GRPX : (0)- add buffer 0x87e00000
VPSS_GRPX : start grpx0
VPSS_GRPX : (0)- get resolution.
VPSS_DCTRL: enter get output format
VPSS_FVID2: send control with cmd 0x1004001a
VPSS_FVID2: control event 0x1004001a return 0 within 0 ms.
VPSS_FVID2: send control with cmd 0x00000003
VPSS_FVID2: control event 0x3 return 0 within 0 ms.
VPSS_FVID2: send control with cmd 0x10000002
VPSS_FVID2: control event 0x10000002 return 0 within 0 ms.
VPSS_FVID2: queue event return 0 within 0 ms.
VPSS_FVID2: send control with cmd 0x00000005
VPSS_FVID2: control event 0x5 return 0 within 44 ms.
VPSS_GRPX : stop grpx0
VPSS_FVID2: send control with cmd 0x00000006
VPSS_FVID2: control event 0x6 return 0 within 66 ms.
VPSS_GRPX : delete GRPX0
VPSS_FVID2: enter delete.
VPSS_FVID2: delete event return 0 within 0 ms
VPSS_DCTRL: enter set node
VPSS_FVID2: send control with cmd 0x10040018
VPSS_FVID2: control event 0x10040018 return 0 within 0 ms.
VPSS_FVID2: send control with cmd 0x10040017
VPSS_FVID2: control event 0x10040017 return 0 within 0 ms.
VPSS_GRPX : create grpx0
VPSS_DCTRL: enter set node
VPSS_FVID2: send control with cmd 0x10040018
VPSS_FVID2: control event 0x10040018 return 0 within 0 ms.
VPSS_FVID2: send control with cmd 0x10040017
VPSS_FVID2: control event 0x10040017 return 0 within 0 ms.
VPSS_FVID2: Fvid2 handle 0x9f3cc498 with notifyno 12 within 0 ms
VPSS_GRPX : (0)- add buffer 0x87e00000
VPSS_GRPX : start grpx0
VPSS_GRPX : (0)- get resolution.
VPSS_DCTRL: enter get output format
VPSS_FVID2: send control with cmd 0x1004001a
VPSS_FVID2: control event 0x1004001a return 0 within 0 ms.
VPSS_FVID2: send control with cmd 0x00000003
VPSS_FVID2: control event 0x3 return 0 within 0 ms.
VPSS_FVID2: send control with cmd 0x10000002
VPSS_FVID2: control event 0x10000002 return 0 within 0 ms.
VPSS_FVID2: queue event return 0 within 0 ms.
VPSS_FVID2: send control with cmd 0x00000005
VPSS_FVID2: control event 0x5 return 0 within 63 ms.
VPSS_GRPX : stop grpx0
VPSS_FVID2: send control with cmd 0x00000006
VPSS_FVID2: control event 0x6 return 0 within 61 ms.
VPSS_GRPX : delete GRPX0
VPSS_FVID2: enter delete.
VPSS_FVID2: delete event return 0 within 0 ms
VPSS_DCTRL: enter set node
VPSS_FVID2: send control with cmd 0x10040018
VPSS_FVID2: control event 0x10040018 return 0 within 0 ms.
VPSS_FVID2: send control with cmd 0x10040017
VPSS_FVID2: control event 0x10040017 return 0 within 0 ms.
VPSS_GRPX : create grpx1
VPSS_DCTRL: enter set node
VPSS_FVID2: send control with cmd 0x10040018
VPSS_FVID2: control event 0x10040018 return 0 within 0 ms.
VPSS_FVID2: send control with cmd 0x10040017
VPSS_FVID2: control event 0x10040017 return 0 within 0 ms.
VPSS_FVID2: Fvid2 handle 0x9f3cc498 with notifyno 12 within 0 ms
VPSS_GRPX : (1)- add buffer 0x89600000
VPSS_GRPX : start grpx1
VPSS_GRPX : (1)- get resolution.
VPSS_DCTRL: enter get output format
VPSS_FVID2: send control with cmd 0x1004001a
VPSS_FVID2: control event 0x1004001a return 0 within 0 ms.
VPSS_FVID2: send control with cmd 0x00000003
VPSS_FVID2: control event 0x3 return 0 within 0 ms.
VPSS_FVID2: send control with cmd 0x10000002
VPSS_FVID2: control event 0x10000002 return 0 within 0 ms.
VPSS_FVID2: queue event return 0 within 0 ms.
VPSS_FVID2: send control with cmd 0x00000005
VPSS_FVID2: control event 0x5 return 0 within 36 ms.
VPSS_GRPX : stop grpx1
VPSS_FVID2: send control with cmd 0x00000006
VPSS_FVID2: control event 0x6 return 0 within 57 ms.
VPSS_GRPX : delete GRPX1
VPSS_FVID2: enter delete.
VPSS_FVID2: delete event return 0 within 0 ms
VPSS_DCTRL: enter set node
VPSS_FVID2: send control with cmd 0x10040018
VPSS_FVID2: control event 0x10040018 return 0 within 0 ms.
VPSS_FVID2: send control with cmd 0x10040017
VPSS_FVID2: control event 0x10040017 return 0 within 0 ms.
HDMI W1 rev 2.0
VPSS_FVID2: send control with cmd 0x1004001a
VPSS_FVID2: control event 0x1004001a return 0 within 1 ms.
VPSS_FVID2: send control with cmd 0x10040004
VPSS_FVID2: control event 0x10040004 return 0 within 0 ms.
Timing Info:
  pixel_clk = 148500
  x_res  = 1920
  y_res  = 1080
  hfp      = 88
  hsw      = 44
  hbp      = 148
  vfp      = 4
  vsw      = 5
  vbp      = 36
hdmi: Enter HDMI_W1_StopVideoFrame()
hdmi: Enter HDMI_W1_GlobalInitVars()
hdmi: Enter HDMI_Core_GlobalInitVars()
hdmi: Enter HDMI_W1_ConfigVideoInterface()
hdmi: HDMI_WP_AUDIO_CFG = 0x1030006
hdmi: HDMI_WP_AUDIO_CFG2 = 0x20c0
hdmi: HDMI_WP_AUDIO_CTRL = 0x20
hdmi: Enter DSS_HDMI_CORE_SW_RESET_ASSERT ()
hdmi: Enter DSS_HDMI_CORE_POWER_DOWN_DISABLE()
hdmi: Enter DSS_HDMI_CORE_SW_RESET_RELEASE()
hdmi: Enter HDMI_W1_StartVideoFrame  ()
eth0: no IPv6 routers present

```I was searching around for a solution & then this seemed to work partially:
[http://ubuntuforums.org/showthread.php?t=1806839&page=4](http://ubuntuforums.org/showthread.php?t=1806839&page=4)

I followed it to the T & was able to see the wlan0 come up. Here's the boot output from that:
```

U-Boot 2010.06 (Jan 16 2012 - 16:32:01)

TI8168-GP rev 1.2

ARM clk: 987MHz
DDR clk: 675MHz

I2C:   ready
DRAM:  1 GiB
NAND:  256 MiB
Net:   Detected MACID:40:5f:c2:6a:13:2c
Ethernet PHY: GENERIC (x001cc914) @ 0x01
DaVinci EMAC
Press SPACE to abort autoboot in 10 seconds
Z3-DM8168-MOD# run brajan-boot-nfs
Boot from TFTP and NFS...
Set powerlevel to 5
Using DaVinci EMAC device
TFTP from server 10.0.2.5; our IP address is 10.0.3.2
Filename 'brajanboot/uImage'.
Load address: 0x81800000
Loading: #################################################################
         #################################################################
         #################################################################
         #################################################################
         #################################################################
         #################################################################
         #################################################################
         ##############################
done
Bytes transferred = 2479812 (25d6c4 hex)
## Booting kernel from Legacy Image at 81800000 ...
   Image Name:   Linux-2.6.37
   Image Type:   ARM Linux Kernel Image (uncompressed)
   Data Size:    2479748 Bytes = 2.4 MiB
   Load Address: 80008000
   Entry Point:  80008000
   Verifying Checksum ... OK
   Loading Kernel Image ... OK
OK

Starting kernel ...

Uncompressing Linux... done, booting the kernel.
Linux version 2.6.37 (brajan@shadowfax) (gcc version 4.3.3 (Sourcery G++ Lite 2009q1-203) ) #7 Thu Jun 7 13:45:58 MST 2012
CPU: ARMv7 Processor [413fc082] revision 2 (ARMv7), cr=10c53c7f
CPU: VIPT nonaliasing data cache, VIPT aliasing instruction cache
Machine: ti8168evm
vram size = 52428800 at 0x0
bootconsole [earlycon0] enabled
reserved size = 52428800 at 0x0
FB: Reserving 52428800 bytes SDRAM for VRAM
Memory policy: ECC disabled, Data cache writeback
OMAP chip is TI8168 2.0
Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 31904
Kernel command line: console=ttyO2,115200 mem=176M vram=50M earlyprintk z3dram=1024M notifyk.vpssm3_sva=0xBF900000 noinitrd root=/dev/nfs nfsroot=10.0.2.5:/home/brajan/work/z3/filesys/fs,nolock,udp rw rootdelay=4 ip=10.0.3.2:10.0.2.5:10.0.1.129:255.255.0.0:Z3-Netra::off
PID hash table entries: 512 (order: -1, 2048 bytes)
Dentry cache hash table entries: 16384 (order: 4, 65536 bytes)
Inode-cache hash table entries: 8192 (order: 3, 32768 bytes)
Memory: 126MB = 126MB total
Memory: 122148k/122148k available, 58076k reserved, 0K highmem
Virtual kernel memory layout:
    vector  : 0xffff0000 - 0xffff1000   (   4 kB)
    fixmap  : 0xfff00000 - 0xfffe0000   ( 896 kB)
    DMA     : 0xffc00000 - 0xffe00000   (   2 MB)
    vmalloc : 0xcb800000 - 0xf8000000   ( 712 MB)
    lowmem  : 0xc0000000 - 0xcb000000   ( 176 MB)
    pkmap   : 0xbfe00000 - 0xc0000000   (   2 MB)
    modules : 0xbf000000 - 0xbfe00000   (  14 MB)
      .init : 0xc0008000 - 0xc003a000   ( 200 kB)
      .text : 0xc003a000 - 0xc04b6000   (4592 kB)
      .data : 0xc04b6000 - 0xc04fa0c0   ( 273 kB)
SLUB: Genslabs=11, HWalign=64, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
NR_IRQS:407
IRQ: Found an INTC at 0xfa200000 (revision 5.0) with 128 interrupts
Total of 128 interrupts on 1 active controller
GPMC revision 6.0
Trying to install interrupt handler for IRQ400
Trying to install interrupt handler for IRQ401
Trying to install interrupt handler for IRQ402
Trying to install interrupt handler for IRQ403
Trying to install interrupt handler for IRQ404
Trying to install interrupt handler for IRQ405
Trying to install interrupt handler for IRQ406
Trying to install type control for IRQ407
Trying to set irq flags for IRQ407
OMAP clockevent source: GPTIMER1 at 27000000 Hz
Console: colour dummy device 80x30
Calibrating delay loop... 986.31 BogoMIPS (lpj=4931584)
pid_max: default: 32768 minimum: 301
Security Framework initialized
Mount-cache hash table entries: 512
CPU: Testing write buffer coherency: ok
devtmpfs: initialized
omap_voltage_early_init: voltage driver support not added
regulator: core version 0.5
regulator: dummy:
NET: Registered protocol family 16
OMAP GPIO hardware version 0.1
OMAP GPIO hardware version 0.1
evm_init_begin
omap_mux_init: Add partition: #1: core, flags: 0
_omap_mux_get_by_name: Could not find signal i2c2_scl.i2c2_scl
_omap_mux_get_by_name: Could not find signal i2c2_sda.i2c2_sda
registered ti816x_vpss device
error setting wl12xx data
registered ti816x_gpio_vr device
registered TI816x on-chip HDMI device
registered ti816x_sr device
registered ti81xx_vidout device
pm_dbg_init: only OMAP3 supported
ti81xx_pcie: Invoking PCI BIOS...
ti81xx_pcie: Setting up Host Controller...
ti81xx_pcie: Register base mapped @0xcb838000
ti81xx_pcie: Starting PCI scan...
PCI: bus0: Fast back to back transfers enabled
bio: create slab <bio-0> at 0
regulator: VFB: 858 <--> 1397 mV at 1103 mV
vgaarb: loaded
SCSI subsystem initialized
usbcore: registered new interface driver usbfs
usbcore: registered new interface driver hub
usbcore: registered new device driver usb
registerd cppi-dma Intr @ IRQ 17
Cppi41 Init Done
omap_i2c omap_i2c.1: bus 1 rev4.0 at 100 kHz
omap_i2c omap_i2c.2: bus 2 rev4.0 at 100 kHz
Advanced Linux Sound Architecture Driver Version 1.0.23.
Switching to clocksource gp timer
musb-hdrc: version 6.0, host, debug=0
musb-hdrc musb-hdrc.0: dma type: dma-cppi41
musb-hdrc musb-hdrc.0: MUSB HDRC host driver
musb-hdrc musb-hdrc.0: new USB bus registered, assigned bus number 1
usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
usb usb1: Product: MUSB HDRC host driver
usb usb1: Manufacturer: Linux 2.6.37 musb-hcd
usb usb1: SerialNumber: musb-hdrc.0
hub 1-0:1.0: USB hub found
hub 1-0:1.0: 1 port detected
musb-hdrc musb-hdrc.0: USB Host mode controller at cb81e000 using DMA, IRQ 18
musb-hdrc musb-hdrc.1: dma type: dma-cppi41
musb-hdrc musb-hdrc.1: MUSB HDRC host driver
musb-hdrc musb-hdrc.1: new USB bus registered, assigned bus number 2
usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
usb usb2: Product: MUSB HDRC host driver
usb usb2: Manufacturer: Linux 2.6.37 musb-hcd
usb usb2: SerialNumber: musb-hdrc.1
hub 2-0:1.0: USB hub found
hub 2-0:1.0: 1 port detected
musb-hdrc musb-hdrc.1: USB Host mode controller at cb832800 using DMA, IRQ 19
NET: Registered protocol family 2
IP route cache hash table entries: 1024 (order: 0, 4096 bytes)
TCP established hash table entries: 4096 (order: 3, 32768 bytes)
TCP bind hash table entries: 4096 (order: 2, 16384 bytes)
TCP: Hash tables configured (established 4096 bind 4096)
TCP reno registered
UDP hash table entries: 256 (order: 0, 4096 bytes)
UDP-Lite hash table entries: 256 (order: 0, 4096 bytes)
NET: Registered protocol family 1
RPC: Registered udp transport module.
RPC: Registered tcp transport module.
RPC: Registered tcp NFSv4.1 backchannel transport module.
NetWinder Floating Point Emulator V0.97 (double precision)
PMU: registered new PMU device of type 0
omap-iommu omap-iommu.0: ducati registered
omap-iommu omap-iommu.1: sys registered
squashfs: version 4.0 (2009/01/31) Phillip Lougher
JFFS2 version 2.2. (NAND) © 2001-2006 Red Hat, Inc.
msgmni has been set to 238
io scheduler noop registered
io scheduler deadline registered
io scheduler cfq registered (default)
Serial: 8250/16550 driver, 4 ports, IRQ sharing enabled
omap_uart.0: ttyO0 at MMIO 0x48020000 (irq = 72) is a OMAP UART0
omap_uart.1: ttyO1 at MMIO 0x48022000 (irq = 73) is a OMAP UART1
omap_uart.2: ttyO2 at MMIO 0x48024000 (irq = 74) is a OMAP UART2
console [ttyO2] enabled, bootconsole disabled
console [ttyO2] enabled, bootconsole disabled
brd: module loaded
loop: module loaded
ahci ahci.0: forcing PORTS_IMPL to 0x3
ahci ahci.0: AHCI 0001.0100 32 slots 2 ports 3 Gbps 0x3 impl platform mode
ahci ahci.0: flags: ncq sntf pm led clo only pmp pio slum part ccc
scsi0 : ahci_platform
scsi1 : ahci_platform
ata1: SATA max UDMA/133 mmio [mem 0x4a140000-0x4a150fff] port 0x100 irq 16
ata2: SATA max UDMA/133 mmio [mem 0x4a140000-0x4a150fff] port 0x180 irq 16
omap2-nand driver initializing
ONFI flash detected
NAND device: Manufacturer ID: 0xad, Chip ID: 0xda (Hynix ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ ÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿÿ)
Scanning device for bad blocks
Creating 7 MTD partitions on "omap2-nand.0":
0x000000000000-0x000000120000 : "U-Boot"
0x000000120000-0x000000240000 : "U-Boot Update"
0x000000240000-0x000000260000 : "U-Boot Env Update"
0x000000260000-0x000000280000 : "U-Boot Env"
0x000000280000-0x0000006c0000 : "Kernel"
0x0000006c0000-0x00000cee0000 : "File System"
0x00000cee0000-0x000010000000 : "Reserved"
davinci_mdio davinci_mdio.0: davinci mdio revision 1.6
davinci_mdio davinci_mdio.0: detected phy mask fffffffc
davinci_mdio.0: probed
davinci_mdio davinci_mdio.0: phy[0]: device 0:00, driver unknown
davinci_mdio davinci_mdio.0: phy[1]: device 0:01, driver unknown
usbcore: registered new interface driver cdc_ether
usbcore: registered new interface driver dm9601
Initializing USB Mass Storage driver...
usbcore: registered new interface driver usb-storage
USB Mass Storage support registered.
mice: PS/2 mouse device common for all mice
omap_rtc omap_rtc: rtc core: registered omap_rtc as rtc0
i2c /dev entries driver
Linux video capture interface: v2.00
Software Watchdog Timer: 0.07 initialized. soft_noboot=0 soft_margin=60 sec (nowayout= 1)
usbcore: registered new interface driver usbhid
usbhid: USB HID core driver
notify_init : notify drivercreated  for  remote proc id 2 at physical Address 0xbf900000
asoc: tlv320aic3x-hifi <-> davinci-mcasp.2 mapping ok
asoc: HDMI-DAI-CODEC <-> hdmi-dai mapping ok
ALSA device list:
  #0: TI81XX EVM
TCP cubic registered
NET: Registered protocol family 17
VFP support v0.3: implementor 41 architecture 3 part 30 variant c rev 3
omap_voltage_late_init: Voltage driver support not added
Power Management for TI81XX.
smartreflex smartreflex: Driver initialized
omap_rtc omap_rtc: setting system clock to 2000-01-01 00:00:00 UTC (946684800)
usb 1-1: new high speed USB device using musb-hdrc and address 2
usb 1-1: New USB device found, idVendor=2001, idProduct=f103
usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
hub 1-1:1.0: USB hub found
hub 1-1:1.0: 7 ports detected
davinci_mdio davinci_mdio.0: resetting idled controller
net eth0: attached PHY driver [Generic PHY] (mii_bus:phy_addr=0:01, id=1cc914)
usb 1-1.2: new high speed USB device using musb-hdrc and address 3
usb 1-1.2: New USB device found, idVendor=0846, idProduct=9041
usb 1-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
usb 1-1.2: Product: 802.11n WLAN Adapter
usb 1-1.2: Manufacturer: Realtek
usb 1-1.2: SerialNumber: 00e04c000001
IP-Config: Complete:
     device=eth0, addr=10.0.3.2, mask=255.255.0.0, gw=10.0.1.129,
     host=Z3-Netra, domain=, nis-domain=(none),
     bootserver=10.0.2.5, rootserver=10.0.2.5, rootpath=
Waiting 4sec before mounting root device...
ata1: SATA link down (SStatus 0 SControl 300)
ata2: SATA link down (SStatus 0 SControl 300)
PHY: 0:01 - Link is Up - 1000/Full
VFS: Mounted root (nfs filesystem) on device 0:14.
devtmpfs: mounted
Freeing init memory: 200K
init started: BusyBox v1.15.0.svn (2012-02-28 14:19:22 MST)
starting pid 45, tty '': '/etc/init.d/rcS'
Please wait: booting...
Starting udev
udevd (67): /proc/67/oom_adj is deprecated, please use /proc/67/oom_score_adj instead.
udev: starting version 141
Root filesystem already rw, not remounting
rtw driver version=v3.4.2_3727.20120404
Build at: Jun  8 2012 11:45:28
register rtw_netdev_ops to netdev_ops
CHIP TYPE: RTL8188C_8192C

usb_endpoint_descriptor(0):
bLength=7
bDescriptorType=5
bEndpointAddress=81
wMaxPacketSize=200
bInterval=0
RT_usb_endpoint_is_bulk_in = 1

usb_endpoint_descriptor(1):
bLength=7
bDescriptorType=5
bEndpointAddress=2
wMaxPacketSize=200
bInterval=0
RT_usb_endpoint_is_bulk_out = 2

usb_endpoint_descriptor(2):
bLength=7
bDescriptorType=5
bEndpointAddress=3
wMaxPacketSize=200
bInterval=0
RT_usb_endpoint_is_bulk_out = 3

usb_endpoint_descriptor(3):
bLength=7
bDescriptorType=5
bEndpointAddress=84
wMaxPacketSize=40
bInterval=1
RT_usb_endpoint_is_int_in = 4, Interval = 1
nr_endpoint=4, in_num=2, out_num=2

USB_SPEED_HIGH
Chip Version ID: VERSION_NORMAL_TSMC_CHIP_88C.
RF_Type is 3!!
EEPROM type is E-FUSE
====> ReadAdapterInfo8192C
Boot from EFUSE, Autoload OK !
EEPROMVID = 0x0846
EEPROMPID = 0x9041
EEPROMCustomerID : 0x00
EEPROMSubCustomerID: 0x00
RT_CustomerID: 0x00
_ReadMACAddress MAC Address from EFUSE = c4:3d:c7:78:33:79
EEPROMRegulatory = 0x3
_ReadBoardType(0)
BT Coexistance = disable
RT_ChannelPlan: 0x02
_ReadPSSetting...bHWPwrPindetect(0)-bHWPowerdown(0) ,bSupportRemoteWakeup(1)
### PS params=>  power_mgnt(1),usbss_enable(0) ###
### AntDivCfg(0)
readAdapterInfo_8192CU(): REPLACEMENT = 1
<==== ReadAdapterInfo8192C in 100 ms

  padapter->pwrctrlpriv.bSupportRemoteWakeup~~~~~~

  padapter->pwrctrlpriv.bSupportRemoteWakeup~~~[0]~~~
rtw_macaddr_cfg MAC Address  = c4:3d:c7:78:33:79
MAC Address from pnetdev->dev_addr= c4:3d:c7:78:33:79
bDriverStopped:1, bSurpriseRemoved:0, bup:0, hw_init_completed:0
usbcore: registered new interface driver rtl8192cu
root: mount: mounting rootfs on / failed: No such file or directory
Setting up IP spoofing protection: rp_filter.
Configuring network interfaces... done.
Wed Dec  2 18:59:00 UTC 2009
Loading HDVICP2 Firmware
SysLink version : 2.00.05.85
SysLink module created on Date:May 21 2012 Time:11:30:28
udev: renamed network interface wlan0 to wlan1
FIRMWARE: Memory map bin file not passed
Usage : firmware_loader <Processor Id> <Location of Firmware> <start|stop> [Location of Mem map bin file]
FIRMWARE: Default memory configuration is used
MemCfg: DCMM (Dynamically Configurable Memory Map) Version :  2.1.1.1
FIRMWARE: Memory Configuration status : In Progress
FIRMWARE: 1 start Successful
Starting telnet daemon.
NET: Registered protocol family 10
Loading HDVPSS Firmware
FIRMWARE: Memory map bin file not passed
Usage : firmware_loader <Processor Id> <Location of Firmware> <start|stop> [Location of Mem map bin file]
FIRMWARE: Default memory configuration is used
MemCfg: DCMM (Dynamically Configurable Memory Map) Version :  2.1.1.1
FIRMWARE: Memory Configuration status : In Progress
FIRMWARE: 2 start Successful
HDMI W1 rev 2.0
Timing Info:
  pixel_clk = 148500
  x_res  = 1920
  y_res  = 1080
  hfp      = 88
  hsw      = 44
  hbp      = 148
  vfp      = 4
  vsw      = 5
  vbp      = 36
Loading DSP Firmware
FIRMWARE: Memory map bin file not passed
Usage : firmware_loader <Processor Id> <Location of Firmware> <start|stop> [Location of Mem map bin file]
FIRMWARE: Default memory configuration is used
MemCfg: DCMM (Dynamically Configurable Memory Map) Version :  2.1.1.1
FIRMWARE: Memory Configuration status : In Progress
FIRMWARE: 0 start Successful
Starting syslogd/klogd: done
BoardID=0
starting pid 975, tty '/dev/ttyO2': '/sbin/getty 115200 ttyO2 vt100'

 _____                    _____           _         _
|  _  |___ ___ ___ ___   |  _  |___ ___  |_|___ ___| |_
|     |  _| .'| . | . |  |   __|  _| . | | | -_|  _|  _|
|__|__|_| |__,|_  |___|  |__|  |_| |___|_| |___|___|_|
              |___|                    |___|

Arago Project http://arago-project.org arago ttyO2

Arago 2009.11 arago ttyO2

arago login: root

```After this, I'm able to see my WNA1000M wireless device:
```

root@arago:~# ifconfig -a
eth0      Link encap:Ethernet  HWaddr 40:5F:C2:6A:13:2C
          inet addr:10.0.3.2  Bcast:10.0.255.255  Mask:255.255.0.0
          inet6 addr: fe80::425f:c2ff:fe6a:132c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21357 errors:0 dropped:25 overruns:0 frame:0
          TX packets:7766 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:21932548 (20.9 MiB)  TX bytes:1178488 (1.1 MiB)
          Interrupt:40

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr C4:3D:C7:78:33:79
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```After this, I'm trying to set it up as an access point & am going back & forth on failures:
```

root@arago:~# hostapd /etc/hostapd.conf
Configuration file: /etc/hostapd.conf
nl80211: 'nl80211' generic netlink not found
nl80211 driver initialization failed.
rmdir[ctrl_interface]: No such file or directory

root@arago:~# iw dev wlan0 scan
command failed: No such device (-19)

root@arago:~# lsmod
Module                  Size  Used by    Not tainted
hostap                 89192  0
lib80211                3312  1 hostap
mac80211              150543  0
cfg80211              122145  1 mac80211
adv7604                38618  0
ti81xxhdmi             14478  0
ti81xxfb               21771  0
vpss                   72346  2 ti81xxhdmi,ti81xxfb
ipv6                  209855 10
syslink              1108491  0
wlan                  500354  0

```Since its a custom TI-8168EVM board for video decoders, I don't have the luxury of traditional lsusb, iwconfig, iwlist etc. commands like in Linux.

My question is HOW TO GET this WNA1000M WORKING on my board & SET IT UP AS AN ACCESS POINT?  I'm looking for a solution for the past 5 days non-stop & any help would be greatly appreciated!! Thanks.

Bharadwaj

---

