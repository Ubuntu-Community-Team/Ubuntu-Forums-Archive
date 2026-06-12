---
title: "Maverick (Elementary) and Netgear WNA3100"
date: 2011-06-01
forum: Networking &amp; Wireless
---

### Post by Shadow Player on 2011-06-01
Hi folks

I have been trying to install my USB wireless adapter (Netgear WNA3100) for two days now. I have read every thread about it on the internet and still haven't found a solution.

Here's the official WNA3100 page on the ndiswrapper wiki and a patch I successfully applied on ndiswrapper's source:
[http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Netgear_WNA3100](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Netgear_WNA3100)

Here's another patch I also had to apply to ndiswrapper's source to compile it on kernel v2.6.35:
[http://sourceforge.net/tracker/?func=detail&aid=3042172&group_id=93482&atid=604452](http://sourceforge.net/tracker/?func=detail&aid=3042172&group_id=93482&atid=604452)

Everything went smooth; make, make install, everything correct.

I also had to blacklist my notebook's internal wlan adapter in order for it to not interfere with ndiswrapper, this also worked correctly.

And I installed the right windows driver for my device in ndiswrapper successfully too.

So after doing all these steps I reboot and connect the WNA3100 to an USB port.

When I do:
```
ndiswrapper -l
```
I get a positive output, driver found and device detected.

so I do:

```
sudo modprobe ndiswrapper
```

and I get:

```
Killed
```

(whatever that means)

After that all things usb stop working: dmesg gives no further usb-related output (even if I disconnect some devices and reconnect them), lsusb won't return anything - it just hangs, ndiswrapper -l also hangs... nothing.



```

dmesg |grep ndis:

[ 5239.378001] ndiswrapper version 1.56 loaded (smp=yes, preempt=no)
[ 5239.655526] ndiswrapper (link_pe_images:565): fixing KI_USER_SHARED_DATA address in the driver
[ 5239.658716] ndiswrapper: driver bcmwlhigh5 (Netgear,11/05/2009, 5.60.180.11) loaded
[ 5239.661647] IP: [<ffffffffa05cac69>] USBD_InterfaceIsDeviceHighSpeed+0x9/0x20 [ndiswrapper]
[ 5239.661700] last sysfs file: /sys/bus/pci/drivers/ndiswrapper/uevent
[ 5239.661708] Modules linked in: ndiswrapper(+) cryptd aes_x86_64 aes_generic binfmt_misc vboxnetadp vboxnetflt vboxdrv parport_pc ppdev dm_crypt joydev snd_hda_codec_intelhdmi snd_hda_codec_idt snd_usb_audio snd_usbmidi_lib arc4 snd_hda_intel snd_hda_codec snd_hwdep uvcvideo snd_pcm videodev v4l1_compat v4l2_compat_ioctl32 snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_timer snd_seq_device hp_wmi snd psmouse serio_raw soundcore snd_page_alloc lp parport dm_raid45 xor btrfs zlib_deflate crc32c libcrc32c usbhid hid i915 drm_kms_helper drm r8169 i2c_algo_bit mii ahci libahci intel_agp video output ramzswap(C) lzo_compress [last unloaded: cfg80211]
[ 5239.661794] RIP: 0010:[<ffffffffa05cac69>]  [<ffffffffa05cac69>] USBD_InterfaceIsDeviceHighSpeed+0x9/0x20 [ndiswrapper]
[ 5239.661930]  [<ffffffffa05b835a>] ? NdisAllocateMemoryWithTag+0x1a/0x40 [ndiswrapper]
[ 5239.661962]  [<ffffffffa05cadf0>] ? USBD_InterfaceReference+0x0/0x30 [ndiswrapper]
[ 5239.661992]  [<ffffffffa05cadc0>] ? USBD_InterfaceDereference+0x0/0x30 [ndiswrapper]
[ 5239.662021]  [<ffffffffa05cac20>] ? USBD_InterfaceGetUSBDIVersion+0x0/0x40 [ndiswrapper]
[ 5239.662052]  [<ffffffffa05cb340>] ? USBD_InterfaceQueryBusTime+0x0/0x30 [ndiswrapper]
[ 5239.662082]  [<ffffffffa05cad90>] ? USBD_InterfaceSubmitIsoOutUrb+0x0/0x30 [ndiswrapper]
[ 5239.662111]  [<ffffffffa05cad60>] ? USBD_InterfaceQueryBusInformation+0x0/0x30 [ndiswrapper]
[ 5239.662141]  [<ffffffffa05cac60>] ? USBD_InterfaceIsDeviceHighSpeed+0x0/0x20 [ndiswrapper]
[ 5239.662171]  [<ffffffffa05bd8dc>] ? ExAllocatePoolWithTag+0x3c/0x80 [ndiswrapper]
[ 5239.662202]  [<ffffffffa05cc8bb>] ? win2lin3+0x11/0x14 [ndiswrapper]
[ 5239.662241]  [<ffffffffa05c8a5f>] ? mp_init+0x6f/0x210 [ndiswrapper]
[ 5239.662270]  [<ffffffffa05c2d92>] ? pdoDispatchPnp+0x42/0x100 [ndiswrapper]
[ 5239.662300]  [<ffffffffa05c9fcc>] ? ndis_start_device+0x2c/0x8c0 [ndiswrapper]
[ 5239.662329]  [<ffffffffa05bffbd>] ? IofCallDriver+0x6d/0xd0 [ndiswrapper]
[ 5239.662364]  [<ffffffffa05bff91>] ? IofCallDriver+0x41/0xd0 [ndiswrapper]
[ 5239.662393]  [<ffffffffa05c0576>] ? IoSyncForwardIrp+0x96/0xd0 [ndiswrapper]
[ 5239.662422]  [<ffffffffa05ca903>] ? NdisDispatchPnp+0xa3/0x150 [ndiswrapper]
[ 5239.662451]  [<ffffffffa05cc8a7>] ? win2lin2+0xe/0x11 [ndiswrapper]
[ 5239.662480]  [<ffffffffa05bff91>] ? IofCallDriver+0x41/0xd0 [ndiswrapper]
[ 5239.662507]  [<ffffffffa05bffbd>] ? IofCallDriver+0x6d/0xd0 [ndiswrapper]
[ 5239.662541]  [<ffffffffa05bff91>] ? IofCallDriver+0x41/0xd0 [ndiswrapper]
[ 5239.662569]  [<ffffffffa05c1e4d>] ? IoSendIrpTopDev+0xdd/0x130 [ndiswrapper]
[ 5239.662603]  [<ffffffffa05bfdd8>] ? IoAttachDeviceToDeviceStack+0x68/0x80 [ndiswrapper]
[ 5239.662632]  [<ffffffffa05c224c>] ? pnp_start_device+0x4c/0x90 [ndiswrapper]
[ 5239.662661]  [<ffffffffa05c2519>] ? wrap_pnp_start_device+0xf9/0x180 [ndiswrapper]
[ 5239.662689]  [<ffffffffa05c2691>] ? wrap_pnp_start_usb_device+0xf1/0x120 [ndiswrapper]
[ 5239.662785]  [<ffffffffa0580000>] ? wrapper_init+0x0/0xb0 [ndiswrapper]
[ 5239.662808]  [<ffffffffa05b3af0>] ? loader_init+0xd0/0x160 [ndiswrapper]
[ 5239.662828]  [<ffffffffa058007b>] ? wrapper_init+0x7b/0xb0 [ndiswrapper]
[ 5239.662911] RIP  [<ffffffffa05cac69>] USBD_InterfaceIsDeviceHighSpeed+0x9/0x20 [ndiswrapper]

```

Dear friends; what am I doing wrong?

Thanks in advance.

---

### Post by Shadow Player on 2011-06-02
*bump*

---

### Post by Shadow Player on 2011-06-02
Additional Information from my dmesg output:

```

[   80.704033] ndiswrapper (link_pe_images:565): fixing KI_USER_SHARED_DATA address in the driver
[   80.706130] ndiswrapper: driver bcmn43xx64 (,08/26/2009, 5.10.79.30) loaded
[COLOR="Red"][   80.708781] BUG: unable to handle kernel paging request at 00000000ffffffd0[/COLOR]
[   80.708787] IP: [<ffffffffa04f2a09>] USBD_InterfaceIsDeviceHighSpeed+0x9/0x20 [ndiswrapper]
[   80.708809] PGD 0 
[COLOR="red"][   80.708812] Oops: 0000 [#1] SMP[/COLOR] 
[   80.708815] last sysfs file: /sys/devices/pci0000:00/0000:00:1a.7/usb1/bDeviceClass


```

Please guys! Any idea will be helpful!

---

### Post by Shadow Player on 2011-06-02
*bump*

---

### Post by daveelton on 2011-08-14
I know its been a while since you posted, but in case it helps you or somebody else -

Locate usb.c from the ndiswrapper code, search for the function USBD_InterfaceIsDeviceHighSpeed, and comment the entire body out, leaving only this:

USBEXIT(return TRUE);

I admit it's a hack, but it worked for me.

---

