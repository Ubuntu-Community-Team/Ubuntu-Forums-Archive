---
title: "Sierra MC7710: Warning on dmesg"
date: 2013-01-30
forum: Networking &amp; Wireless
---

### Post by themaxxx on 2013-01-30
Hi guys, we have a problem with de Modem Sierra MC7710.

Ubuntu 10.04.
Driver: v1.7.12_kernel-2.6.31.serial.tar

When I can register the modem with the operator, in dmesg I see the following:

```

Jan 30 09:17:07 localhost kernel: [ 1466.432949] ------------[ cut here ]------------
Jan 30 09:17:07 localhost kernel: [ 1466.442424] WARNING: at /build/buildd/linux-2.6.32/drivers/usb/serial/usb-serial.c:454 serial_ioctl+0x9d/0xb0 [usbserial]()
Jan 30 09:17:07 localhost kernel: [ 1466.461732] Hardware name:  
Jan 30 09:17:07 localhost kernel: [ 1466.471278] Modules linked in: kpci9030 kpex8311 fbcon tileblit font bitblit softcursor ks_userport ks_softswitch vga16fb vgastate usbclient cp210x kstreamer yenta_socket sierra usbserial i2c_viapro serio_raw rsrc_nonstatic pcmcia_core via_agp shpchp agpgart lp parport usbhid hid usb_storage 8139too pata_via sata_via 8139cp mii
Jan 30 09:17:07 localhost kernel: [ 1466.527851] Pid: 2061, comm: minicom Tainted: G      D W  2.6.32-34-generic-pae #77-Ubuntu
Jan 30 09:17:07 localhost kernel: [ 1466.550379] Call Trace:
Jan 30 09:17:07 localhost kernel: [ 1466.561668]  [<c0154dd2>] warn_slowpath_common+0x72/0xa0
Jan 30 09:17:07 localhost kernel: [ 1466.573023]  [<f827c70d>] ? serial_ioctl+0x9d/0xb0 [usbserial]
Jan 30 09:17:07 localhost kernel: [ 1466.584275]  [<f827c70d>] ? serial_ioctl+0x9d/0xb0 [usbserial]
Jan 30 09:17:07 localhost kernel: [ 1466.595207]  [<c0154e1a>] warn_slowpath_null+0x1a/0x20
Jan 30 09:17:07 localhost kernel: [ 1466.606075]  [<f827c70d>] serial_ioctl+0x9d/0xb0 [usbserial]
Jan 30 09:17:07 localhost kernel: [ 1466.617015]  [<c01310a8>] ? default_spin_lock_flags+0x8/0x10
Jan 30 09:17:07 localhost kernel: [ 1466.628010]  [<f827c670>] ? serial_ioctl+0x0/0xb0 [usbserial]
Jan 30 09:17:07 localhost kernel: [ 1466.639076]  [<c03ca7ce>] tty_ioctl+0x7e/0x650
Jan 30 09:17:07 localhost kernel: [ 1466.650509]  [<c03d08a5>] ? put_ldisc+0x55/0xb0
Jan 30 09:17:07 localhost kernel: [ 1466.661727]  [<c03d099d>] ? tty_ldisc_deref+0xd/0x10
Jan 30 09:17:07 localhost kernel: [ 1466.672940]  [<c03cb938>] ? tty_write+0x1b8/0x210
Jan 30 09:17:07 localhost kernel: [ 1466.684352]  [<c03ca750>] ? tty_ioctl+0x0/0x650
Jan 30 09:17:07 localhost kernel: [ 1466.695819]  [<c0222651>] vfs_ioctl+0x21/0x90
Jan 30 09:17:07 localhost kernel: [ 1466.707232]  [<c0222939>] do_vfs_ioctl+0x79/0x310
Jan 30 09:17:07 localhost kernel: [ 1466.718576]  [<c03cb780>] ? tty_write+0x0/0x210
Jan 30 09:17:07 localhost kernel: [ 1466.729933]  [<c0222c37>] sys_ioctl+0x67/0x80
Jan 30 09:17:07 localhost kernel: [ 1466.741255]  [<c01096c3>] sysenter_do_call+0x12/0x28
Jan 30 09:17:07 localhost kernel: [ 1466.752824] ---[ end trace 883f2603e92fee1e ]---
Jan 30 09:17:07 localhost kernel: [ 1466.807127] ------------[ cut here ]------------
Jan 30 09:17:07 localhost kernel: [ 1466.815970] WARNING: at /build/buildd/linux-2.6.32/drivers/usb/serial/usb-serial.c:454 serial_ioctl+0x9d/0xb0 [usbserial]()
Jan 30 09:17:07 localhost kernel: [ 1466.833398] Hardware name:  
Jan 30 09:17:07 localhost kernel: [ 1466.841725] Modules linked in: kpci9030 kpex8311 fbcon tileblit font bitblit softcursor ks_userport ks_softswitch vga16fb vgastate usbclient cp210x kstreamer yenta_socket sierra usbserial i2c_viapro serio_raw rsrc_nonstatic pcmcia_core via_agp shpchp agpgart lp parport usbhid hid usb_storage 8139too pata_via sata_via 8139cp mii
Jan 30 09:17:07 localhost kernel: [ 1466.888792] Pid: 2061, comm: minicom Tainted: G      D W  2.6.32-34-generic-pae #77-Ubuntu
Jan 30 09:17:07 localhost kernel: [ 1466.905624] Call Trace:
Jan 30 09:17:07 localhost kernel: [ 1466.914247]  [<c0154dd2>] warn_slowpath_common+0x72/0xa0
Jan 30 09:17:07 localhost kernel: [ 1466.922904]  [<f827c70d>] ? serial_ioctl+0x9d/0xb0 [usbserial]
Jan 30 09:17:07 localhost kernel: [ 1466.931756]  [<f827c70d>] ? serial_ioctl+0x9d/0xb0 [usbserial]
Jan 30 09:17:07 localhost kernel: [ 1466.940474]  [<c0154e1a>] warn_slowpath_null+0x1a/0x20
Jan 30 09:17:07 localhost kernel: [ 1466.949034]  [<f827c70d>] serial_ioctl+0x9d/0xb0 [usbserial]
Jan 30 09:17:07 localhost kernel: [ 1466.957624]  [<c03d08a5>] ? put_ldisc+0x55/0xb0
Jan 30 09:17:07 localhost kernel: [ 1466.966092]  [<f827c670>] ? serial_ioctl+0x0/0xb0 [usbserial]
Jan 30 09:17:07 localhost kernel: [ 1466.974527]  [<c03ca7ce>] tty_ioctl+0x7e/0x650
Jan 30 09:17:07 localhost kernel: [ 1466.983059]  [<c03d08a5>] ? put_ldisc+0x55/0xb0
Jan 30 09:17:07 localhost kernel: [ 1466.991546]  [<c03d099d>] ? tty_ldisc_deref+0xd/0x10
Jan 30 09:17:07 localhost kernel: [ 1466.999899]  [<c03cb938>] ? tty_write+0x1b8/0x210
Jan 30 09:17:07 localhost kernel: [ 1467.008349]  [<c03ca750>] ? tty_ioctl+0x0/0x650
Jan 30 09:17:07 localhost kernel: [ 1467.016879]  [<c0222651>] vfs_ioctl+0x21/0x90
Jan 30 09:17:07 localhost kernel: [ 1467.025400]  [<c0222939>] do_vfs_ioctl+0x79/0x310
Jan 30 09:17:07 localhost kernel: [ 1467.033968]  [<c03cb780>] ? tty_write+0x0/0x210
Jan 30 09:17:07 localhost kernel: [ 1467.042653]  [<c0222c37>] sys_ioctl+0x67/0x80
Jan 30 09:17:07 localhost kernel: [ 1467.051227]  [<c01096c3>] sysenter_do_call+0x12/0x28
Jan 30 09:17:07 localhost kernel: [ 1467.059822] ---[ end trace 883f2603e92fee1f ]---
Jan 30 09:17:07 localhost kernel: [ 1467.078786] ------------[ cut here ]------------
Jan 30 09:17:07 localhost kernel: [ 1467.087543] WARNING: at /build/buildd/linux-2.6.32/drivers/usb/serial/usb-serial.c:454 serial_ioctl+0x9d/0xb0 [usbserial]()
Jan 30 09:17:07 localhost kernel: [ 1467.104637] Hardware name:  
Jan 30 09:17:07 localhost kernel: [ 1467.112804] Modules linked in: kpci9030 kpex8311 fbcon tileblit font bitblit softcursor ks_userport ks_softswitch vga16fb vgastate usbclient cp210x kstreamer yenta_socket sierra usbserial i2c_viapro serio_raw rsrc_nonstatic pcmcia_core via_agp shpchp agpgart lp parport usbhid hid usb_storage 8139too pata_via sata_via 8139cp mii
Jan 30 09:17:07 localhost kernel: [ 1467.159449] Pid: 2061, comm: minicom Tainted: G      D W  2.6.32-34-generic-pae #77-Ubuntu
Jan 30 09:17:07 localhost kernel: [ 1467.176117] Call Trace:
Jan 30 09:17:07 localhost kernel: [ 1467.184721]  [<c0154dd2>] warn_slowpath_common+0x72/0xa0
Jan 30 09:17:07 localhost kernel: [ 1467.193385]  [<f827c70d>] ? serial_ioctl+0x9d/0xb0 [usbserial]
Jan 30 09:17:07 localhost kernel: [ 1467.202205]  [<f827c70d>] ? serial_ioctl+0x9d/0xb0 [usbserial]
Jan 30 09:17:07 localhost kernel: [ 1467.210862]  [<c0154e1a>] warn_slowpath_null+0x1a/0x20
Jan 30 09:17:07 localhost kernel: [ 1467.219466]  [<f827c70d>] serial_ioctl+0x9d/0xb0 [usbserial]
Jan 30 09:17:07 localhost kernel: [ 1467.228133]  [<c03d08a5>] ? put_ldisc+0x55/0xb0
Jan 30 09:17:07 localhost kernel: [ 1467.236731]  [<f827c670>] ? serial_ioctl+0x0/0xb0 [usbserial]
Jan 30 09:17:07 localhost kernel: [ 1467.245440]  [<c03ca7ce>] tty_ioctl+0x7e/0x650
Jan 30 09:17:07 localhost kernel: [ 1467.254190]  [<c03d08a5>] ? put_ldisc+0x55/0xb0
Jan 30 09:17:07 localhost kernel: [ 1467.262901]  [<c03d099d>] ? tty_ldisc_deref+0xd/0x10
Jan 30 09:17:07 localhost kernel: [ 1467.271522]  [<c03cb938>] ? tty_write+0x1b8/0x210
Jan 30 09:17:07 localhost kernel: [ 1467.280136]  [<c03ca750>] ? tty_ioctl+0x0/0x650
Jan 30 09:17:07 localhost kernel: [ 1467.288801]  [<c0222651>] vfs_ioctl+0x21/0x90
Jan 30 09:17:07 localhost kernel: [ 1467.297463]  [<c0222939>] do_vfs_ioctl+0x79/0x310
Jan 30 09:17:07 localhost kernel: [ 1467.306174]  [<c03cb780>] ? tty_write+0x0/0x210
Jan 30 09:17:07 localhost kernel: [ 1467.314879]  [<c0222c37>] sys_ioctl+0x67/0x80
Jan 30 09:17:07 localhost kernel: [ 1467.323634]  [<c01096c3>] sysenter_do_call+0x12/0x28
Jan 30 09:17:07 localhost kernel: [ 1467.332376] ---[ end trace 883f2603e92fee20 ]---
Jan 30 09:17:08 localhost kernel: [ 1467.348581] ------------[ cut here ]------------
Jan 30 09:17:08 localhost kernel: [ 1467.357391] WARNING: at /build/buildd/linux-2.6.32/drivers/usb/serial/usb-serial.c:470 serial_set_termios+0x76/0xb0 [usbserial]()
Jan 30 09:17:08 localhost kernel: [ 1467.374783] Hardware name:  
Jan 30 09:17:08 localhost kernel: [ 1467.383141] Modules linked in: kpci9030 kpex8311 fbcon tileblit font bitblit softcursor ks_userport ks_softswitch vga16fb vgastate usbclient cp210x kstreamer yenta_socket sierra usbserial i2c_viapro serio_raw rsrc_nonstatic pcmcia_core via_agp shpchp agpgart lp parport usbhid hid usb_storage 8139too pata_via sata_via 8139cp mii
Jan 30 09:17:08 localhost kernel: [ 1467.430648] Pid: 2061, comm: minicom Tainted: G      D W  2.6.32-34-generic-pae #77-Ubuntu
Jan 30 09:17:08 localhost kernel: [ 1467.447648] Call Trace:
Jan 30 09:17:08 localhost kernel: [ 1467.456369]  [<c0154dd2>] warn_slowpath_common+0x72/0xa0
Jan 30 09:17:08 localhost kernel: [ 1467.465118]  [<f827cb36>] ? serial_set_termios+0x76/0xb0 [usbserial]
Jan 30 09:17:08 localhost kernel: [ 1467.474318]  [<f827cb36>] ? serial_set_termios+0x76/0xb0 [usbserial]
Jan 30 09:17:08 localhost kernel: [ 1467.483352]  [<c0154e1a>] warn_slowpath_null+0x1a/0x20
Jan 30 09:17:08 localhost kernel: [ 1467.492434]  [<f827cb36>] serial_set_termios+0x76/0xb0 [usbserial]
Jan 30 09:17:08 localhost kernel: [ 1467.501726]  [<c05b0eab>] ? schedule+0x46b/0x870
Jan 30 09:17:08 localhost kernel: [ 1467.510902]  [<c03cf879>] change_termios+0x169/0x2c0
Jan 30 09:17:08 localhost kernel: [ 1467.520016]  [<c03cfbd0>] set_termios+0xe0/0x220
Jan 30 09:17:08 localhost kernel: [ 1467.529316]  [<c03d00b7>] tty_mode_ioctl+0x2d7/0x450
Jan 30 09:17:08 localhost kernel: [ 1467.538721]  [<c05b0859>] ? printk+0x1d/0x24
Jan 30 09:17:08 localhost kernel: [ 1467.548081]  [<c0154b9f>] ? print_oops_end_marker+0x2f/0x40
Jan 30 09:17:08 localhost kernel: [ 1467.557344]  [<c0154de1>] ? warn_slowpath_common+0x81/0xa0
Jan 30 09:17:08 localhost kernel: [ 1467.566670]  [<c01310a8>] ? default_spin_lock_flags+0x8/0x10
Jan 30 09:17:08 localhost kernel: [ 1467.576023]  [<c05b2fbf>] ? _spin_lock_irqsave+0x2f/0x50
Jan 30 09:17:08 localhost kernel: [ 1467.585469]  [<c03d026d>] n_tty_ioctl_helper+0x3d/0x190
Jan 30 09:17:08 localhost kernel: [ 1467.594861]  [<c03cd1c0>] ? n_tty_ioctl+0x0/0xe0
Jan 30 09:17:08 localhost kernel: [ 1467.604297]  [<c03cd1f3>] n_tty_ioctl+0x33/0xe0
Jan 30 09:17:08 localhost kernel: [ 1467.613791]  [<c03cd1c0>] ? n_tty_ioctl+0x0/0xe0
Jan 30 09:17:08 localhost kernel: [ 1467.623389]  [<c03ca801>] tty_ioctl+0xb1/0x650
Jan 30 09:17:08 localhost kernel: [ 1467.633028]  [<c03d08a5>] ? put_ldisc+0x55/0xb0
Jan 30 09:17:08 localhost kernel: [ 1467.642731]  [<c03d099d>] ? tty_ldisc_deref+0xd/0x10
Jan 30 09:17:08 localhost kernel: [ 1467.652534]  [<c03cb938>] ? tty_write+0x1b8/0x210
Jan 30 09:17:08 localhost kernel: [ 1467.662164]  [<c03ca750>] ? tty_ioctl+0x0/0x650
Jan 30 09:17:08 localhost kernel: [ 1467.671853]  [<c0222651>] vfs_ioctl+0x21/0x90
Jan 30 09:17:08 localhost kernel: [ 1467.681505]  [<c0222939>] do_vfs_ioctl+0x79/0x310
Jan 30 09:17:08 localhost kernel: [ 1467.691114]  [<c03cb780>] ? tty_write+0x0/0x210
Jan 30 09:17:08 localhost kernel: [ 1467.700391]  [<c0222c37>] sys_ioctl+0x67/0x80
Jan 30 09:17:08 localhost kernel: [ 1467.709230]  [<c01096c3>] sysenter_do_call+0x12/0x28
Jan 30 09:17:08 localhost kernel: [ 1467.717662] ---[ end trace 883f2603e92fee21 ]---
Jan 30 09:17:08 localhost kernel: [ 1467.736014] *pdpt = 00000000359d6001 *pde = 0000000000000000 
Jan 30 09:17:08 localhost kernel: [ 1467.736014] Modules linked in: kpci9030 kpex8311 fbcon tileblit font bitblit softcursor ks_userport ks_softswitch vga16fb vgastate usbclient cp210x kstreamer yenta_socket sierra usbserial i2c_viapro serio_raw rsrc_nonstatic pcmcia_core via_agp shpchp agpgart lp parport usbhid hid usb_storage 8139too pata_via sata_via 8139cp mii
Jan 30 09:17:08 localhost kernel: [ 1467.736014] 
Jan 30 09:17:08 localhost kernel: [ 1467.736014] Pid: 2061, comm: minicom Tainted: G      D W  (2.6.32-34-generic-pae #77-Ubuntu)  
Jan 30 09:17:08 localhost kernel: [ 1467.736014] EIP: 0060:[<f82a73d4>] EFLAGS: 00010246 CPU: 0
Jan 30 09:17:08 localhost kernel: [ 1467.736014] EIP is at sierra_send_setup+0xb4/0x110 [sierra]
Jan 30 09:17:08 localhost kernel: [ 1467.736014] EAX: 00000000 EBX: ec775680 ECX: 00000000 EDX: 00002580
Jan 30 09:17:08 localhost kernel: [ 1467.736014] ESI: ec7d8780 EDI: 00000000 EBP: f4ce3d74 ESP: f4ce3d50
Jan 30 09:17:08 localhost kernel: [ 1467.736014]  DS: 007b ES: 007b FS: 00d8 GS: 00e0 SS: 0068
Jan 30 09:17:08 localhost kernel: [ 1467.736014]  c0154de1 c06e7fc7 c0940034 000001d6 f827cb36 f827cb36 f596f800 f4c9e800
Jan 30 09:17:08 localhost kernel: [ 1467.736014] <0> f82a7520 f4ce3d80 f82a753c f596f800 f4ce3da8 f827cb04 c05b0eab ec71c000
Jan 30 09:17:08 localhost kernel: [ 1467.736014] <0> 0ddbf590 00000000 f4ce3db8 f4c9e800 ec6e902c f4ce3db8 f4ce3df4 c03cf879
Jan 30 09:17:08 localhost kernel: [ 1467.736014]  [<c0154de1>] ? warn_slowpath_common+0x81/0xa0
Jan 30 09:17:08 localhost kernel: [ 1467.736014]  [<f827cb36>] ? serial_set_termios+0x76/0xb0 [usbserial]
Jan 30 09:17:08 localhost kernel: [ 1467.736014]  [<f827cb36>] ? serial_set_termios+0x76/0xb0 [usbserial]
Jan 30 09:17:08 localhost kernel: [ 1467.736014]  [<f82a7520>] ? sierra_set_termios+0x0/0x20 [sierra]
Jan 30 09:17:08 localhost kernel: [ 1467.736014]  [<f82a753c>] ? sierra_set_termios+0x1c/0x20 [sierra]
Jan 30 09:17:08 localhost kernel: [ 1467.736014]  [<f827cb04>] ? serial_set_termios+0x44/0xb0 [usbserial]
Jan 30 09:17:08 localhost kernel: [ 1467.736014]  [<c05b0eab>] ? schedule+0x46b/0x870
Jan 30 09:17:08 localhost kernel: [ 1467.736014]  [<c03cf879>] ? change_termios+0x169/0x2c0
Jan 30 09:17:08 localhost kernel: [ 1467.736014]  [<c03cfbd0>] ? set_termios+0xe0/0x220
Jan 30 09:17:08 localhost kernel: [ 1467.736014]  [<c03d00b7>] ? tty_mode_ioctl+0x2d7/0x450
Jan 30 09:17:08 localhost kernel: [ 1467.736014]  [<c05b0859>] ? printk+0x1d/0x24
Jan 30 09:17:08 localhost kernel: [ 1467.736014]  [<c0154b9f>] ? print_oops_end_marker+0x2f/0x40
Jan 30 09:17:08 localhost kernel: [ 1467.736014]  [<c0154de1>] ? warn_slowpath_common+0x81/0xa0
Jan 30 09:17:08 localhost kernel: [ 1467.736014]  [<c01310a8>] ? default_spin_lock_flags+0x8/0x10
Jan 30 09:17:08 localhost kernel: [ 1467.736014]  [<c05b2fbf>] ? _spin_lock_irqsave+0x2f/0x50
Jan 30 09:17:08 localhost kernel: [ 1467.736014]  [<c03d026d>] ? n_tty_ioctl_helper+0x3d/0x190
Jan 30 09:17:08 localhost kernel: [ 1467.736014]  [<c03cd1c0>] ? n_tty_ioctl+0x0/0xe0
Jan 30 09:17:08 localhost kernel: [ 1467.736014]  [<c03cd1f3>] ? n_tty_ioctl+0x33/0xe0
Jan 30 09:17:08 localhost kernel: [ 1467.736014]  [<c03cd1c0>] ? n_tty_ioctl+0x0/0xe0
Jan 30 09:17:08 localhost kernel: [ 1467.736014]  [<c03ca801>] ? tty_ioctl+0xb1/0x650
Jan 30 09:17:08 localhost kernel: [ 1467.736014]  [<c03d08a5>] ? put_ldisc+0x55/0xb0
Jan 30 09:17:08 localhost kernel: [ 1467.736014]  [<c03d099d>] ? tty_ldisc_deref+0xd/0x10
Jan 30 09:17:08 localhost kernel: [ 1467.736014]  [<c03cb938>] ? tty_write+0x1b8/0x210
Jan 30 09:17:08 localhost kernel: [ 1467.736014]  [<c03ca750>] ? tty_ioctl+0x0/0x650
Jan 30 09:17:08 localhost kernel: [ 1467.736014]  [<c0222651>] ? vfs_ioctl+0x21/0x90
Jan 30 09:17:08 localhost kernel: [ 1467.736014]  [<c0222939>] ? do_vfs_ioctl+0x79/0x310
Jan 30 09:17:08 localhost kernel: [ 1467.736014]  [<c03cb780>] ? tty_write+0x0/0x210
Jan 30 09:17:08 localhost kernel: [ 1467.736014]  [<c0222c37>] ? sys_ioctl+0x67/0x80
Jan 30 09:17:08 localhost kernel: [ 1467.736014]  [<c01096c3>] ? sysenter_do_call+0x12/0x28
Jan 30 09:17:08 localhost kernel: [ 1468.347600] ---[ end trace 883f2603e92fee22 ]---
```

Thanks for your time & support.

---

### Post by themaxxx on 2013-01-31
Hey guys, do you have news?? 

Thanks in advance

---

### Post by varunendra on 2013-02-01
Hi!

First off, unless you have any specific reason to keep using 10.04, please upgrade to 12.04 to take advantage of newer kernel. It may natively support your modem (which seems to be a USB 3G one), thus eliminating the need for a third party driver. Besides, 10.04 is going to reach its EOL ([End of Life]("https://wiki.ubuntu.com/Releases")) in April this year - meaning there will be no more active support for it and you won't get any updates for it afterwards.

If however, you really need to keep your 10.04, please explain in detail the problem you are having, along with the outputs of the following (while the modem is plugged-in)-
```
uname -mr
lsusb
usb-devices
lsmod
dmesg | tail -20
cat /var/log/syslog | tail -20
```

We may need more info later depending upon the above outputs and the nature of problem you are having.

But I would once again suggest to try 12.04.1 from a live cd, and see if the modem works any better on it. You should have at least 1GB RAM to use the live cd of 12.04.

If you do decide to try 12.04, I'd suggest to download the ISO via torrent (64 bit, if your system supports it). It ensures the integrity of the downloaded data and is usually faster. Here's the link for torrents : [http://www.ubuntu.com/download/desktop/alternative-downloads](http://www.ubuntu.com/download/desktop/alternative-downloads)
(choose the LTS one. "Desktop" version is live cd, others are intall-only)

---

### Post by themaxxx on 2013-02-19
> **varunendra said:**
> Hi!

First off, unless you have any specific reason to keep using 10.04, please upgrade to 12.04 to take advantage of newer kernel. It may natively support your modem (which seems to be a USB 3G one), thus eliminating the need for a third party driver. Besides, 10.04 is going to reach its EOL ([End of Life]("https://wiki.ubuntu.com/Releases")) in April this year - meaning there will be no more active support for it and you won't get any updates for it afterwards.

If however, you really need to keep your 10.04, please explain in detail the problem you are having, along with the outputs of the following (while the modem is plugged-in)-
```
uname -mr
lsusb
usb-devices
lsmod
dmesg | tail -20
cat /var/log/syslog | tail -20
```

We may need more info later depending upon the above outputs and the nature of problem you are having.

But I would once again suggest to try 12.04.1 from a live cd, and see if the modem works any better on it. You should have at least 1GB RAM to use the live cd of 12.04.

If you do decide to try 12.04, I'd suggest to download the ISO via torrent (64 bit, if your system supports it). It ensures the integrity of the downloaded data and is usually faster. Here's the link for torrents : [http://www.ubuntu.com/download/desktop/alternative-downloads](http://www.ubuntu.com/download/desktop/alternative-downloads)
(choose the LTS one. "Desktop" version is live cd, others are intall-only)

Hi varunendra, thanks for your reply.

I understand that we should move to the latest version. But take this as a last option because they are remote servers in production.

I leave here the output of commands:


**uname -mr:**

```
2.6.32-34-generic-pae i686
```

**lsusb:**

```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 011: ID 22b8:2d91 Motorola PCS 
Bus 001 Device 010: ID 0451:5430 Texas Instruments, Inc. 
Bus 001 Device 009: ID 0451:5430 Texas Instruments, Inc. 
Bus 001 Device 008: ID 0424:2517 Standard Microsystems Corp. 
Bus 001 Device 007: ID 0451:5430 Texas Instruments, Inc. 
Bus 001 Device 006: ID 0451:5430 Texas Instruments, Inc. 
Bus 001 Device 005: ID 0451:5430 Texas Instruments, Inc. 
Bus 001 Device 004: ID 10c4:ea60 Cygnal Integrated Products, Inc. CP210x Composite Device
Bus 001 Device 003: ID 0424:2517 Standard Microsystems Corp. 
Bus 001 Device 002: ID 0424:2514 Standard Microsystems Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

**usb-devices:**

```
T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 8
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=02.06
S:  Manufacturer=Linux 2.6.32-34-generic-pae ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:10.4
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=480 MxCh= 4
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=02 MxPS=64 #Cfgs=  1
P:  Vendor=0424 ProdID=2514 Rev=00.00
S:  Manufacturer=Zoitron S.A.
S:  Product=HUB 2.0 ADECEF
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=2mA
I:  If#= 0 Alt= 1 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=02 Driver=hub

T:  Bus=01 Lev=02 Prnt=02 Port=00 Cnt=01 Dev#=  4 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=10c4 ProdID=ea60 Rev=01.00
S:  Manufacturer=Silicon Labs
S:  Product=CP2102 USB to UART Bridge Controller
S:  SerialNumber=0001
C:  #Ifs= 1 Cfg#= 1 Atr=80 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=00 Prot=00 Driver=cp210x

T:  Bus=01 Lev=02 Prnt=02 Port=01 Cnt=02 Dev#= 19 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1199 ProdID=68a3 Rev=00.06
S:  Manufacturer=Sierra Wireless, Incorporated
S:  Product=MC7710
S:  SerialNumber=358178040548937
C:  #Ifs= 6 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=sierra
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=sierra
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=sierra
I:  If#= 3 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=sierra
I:  If#= 4 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=sierra
I:  If#= 7 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)

T:  Bus=01 Lev=02 Prnt=02 Port=02 Cnt=03 Dev#=  5 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=ff(vend.) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=0451 ProdID=5430 Rev=02.0a
S:  Manufacturer=implementa gmbh, germany
S:  Product=USB SIM Adapter
S:  SerialNumber=SN#0000146D1343
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=00 Prot=00 Driver=simclient

T:  Bus=01 Lev=01 Prnt=01 Port=06 Cnt=02 Dev#=  3 Spd=480 MxCh= 7
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=02 MxPS=64 #Cfgs=  1
P:  Vendor=0424 ProdID=2517 Rev=00.02
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=2mA
I:  If#= 0 Alt= 1 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=02 Driver=hub

T:  Bus=01 Lev=02 Prnt=03 Port=00 Cnt=01 Dev#=  6 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=ff(vend.) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=0451 ProdID=5430 Rev=02.0a
S:  Manufacturer=implementa gmbh, germany
S:  Product=USB SIM Adapter
S:  SerialNumber=SN#0000151ED041
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=00 Prot=00 Driver=simclient

T:  Bus=01 Lev=02 Prnt=03 Port=02 Cnt=02 Dev#=  7 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=ff(vend.) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=0451 ProdID=5430 Rev=02.0a
S:  Manufacturer=implementa gmbh, germany
S:  Product=USB SIM Adapter
S:  SerialNumber=SN#0000151FD308
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=00 Prot=00 Driver=simclient

T:  Bus=01 Lev=02 Prnt=03 Port=03 Cnt=03 Dev#= 11 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=ff(vend.) Sub=ff Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=22b8 ProdID=2d91 Rev=00.02
S:  Manufacturer=Motorola, Inc.
S:  Product=Motorola Phone (H24)
C:  #Ifs= 2 Cfg#= 1 Atr=e0 MxPwr=20mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=02(commc) Sub=02 Prot=01 Driver=cdc_acm
I:  If#= 1 Alt= 0 #EPs= 2 Cls=0a(data ) Sub=00 Prot=00 Driver=cdc_acm

T:  Bus=01 Lev=02 Prnt=03 Port=04 Cnt=04 Dev#=  8 Spd=480 MxCh= 7
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=02 MxPS=64 #Cfgs=  1
P:  Vendor=0424 ProdID=2517 Rev=00.02
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=2mA
I:  If#= 0 Alt= 1 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=02 Driver=hub

T:  Bus=01 Lev=03 Prnt=08 Port=00 Cnt=01 Dev#=  9 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=ff(vend.) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=0451 ProdID=5430 Rev=02.0a
S:  Manufacturer=implementa gmbh, germany
S:  Product=USB SIM Adapter
S:  SerialNumber=SN#0000151F090D
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=00 Prot=00 Driver=simclient

T:  Bus=01 Lev=03 Prnt=08 Port=02 Cnt=02 Dev#= 10 Spd=12  MxCh= 0
D:  Ver= 1.10 Cls=ff(vend.) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=0451 ProdID=5430 Rev=02.0a
S:  Manufacturer=implementa gmbh, germany
S:  Product=USB SIM Adapter
S:  SerialNumber=SN#0000151FD12A
C:  #Ifs= 1 Cfg#= 1 Atr=a0 MxPwr=100mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=00 Prot=00 Driver=simclient

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.32-34-generic-pae uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:10.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.32-34-generic-pae uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:10.1
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.32-34-generic-pae uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:10.2
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=05 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.32-34-generic-pae uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:10.3
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub
```

**lsmod:** 

```
root@portugal:~# lsmod
Module                  Size  Used by
sierra                 11034  0 
cdc_acm                13758  0 
kpex8311               15816  0 
snd_via82xx            20122  0 
gameport                9089  1 snd_via82xx
snd_ac97_codec        100646  1 snd_via82xx
ac97_bus                1002  1 snd_ac97_codec
snd_pcm                70918  2 snd_via82xx,snd_ac97_codec
snd_timer              19098  1 snd_pcm
snd_page_alloc          7172  2 snd_via82xx,snd_pcm
fbcon                  35102  71 
tileblit                1999  1 fbcon
snd_mpu401_uart         5649  1 snd_via82xx
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
snd_rawmidi            19056  1 snd_mpu401_uart
vga16fb                11385  1 
snd_seq_device          5700  1 snd_rawmidi
vgsm2                  28520  11 
vgastate                8961  1 vga16fb
ks_userport             6893  0 
cp210x                 11924  0 
snd                    54244  7 snd_via82xx,snd_ac97_codec,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
ks_softswitch           2248  2 vgsm2,ks_userport
usbclient               3520  5 
usbserial              33694  13 sierra,cp210x,usbclient
serio_raw               3978  0 
i2c_viapro              5637  0 
soundcore               6620  1 snd
kstreamer              34329  4 vgsm2,ks_userport,ks_softswitch
kpci9030               12680  2 
shpchp                 28899  0 
via_agp                 5310  1 
agpgart                31788  1 via_agp
lp                      7028  0 
parport                32635  1 lp
8139too                18673  0 
pata_via                7272  1 
8139cp                 16602  0 
sata_via                7172  0 
mii                     4381  2 8139too,8139cp
```

**dmesg | tail -20**

```
[ 2749.914632] sierra 1-1.2:1.4: device disconnected
[ 2753.924219] usb 1-1.2: new high speed USB device using ehci_hcd and address 20
[ 2754.017756] usb 1-1.2: config 1 has an invalid interface number: 7 but max is 5
[ 2754.017772] usb 1-1.2: config 1 has no interface number 5
[ 2754.021642] usb 1-1.2: configuration #1 chosen from 1 choice
[ 2754.023888] sierra 1-1.2:1.0: Sierra USB modem converter detected
[ 2754.025811] usb 1-1.2: APM supported, enabling autosuspend.
[ 2754.026162] usb 1-1.2: Sierra USB modem converter now attached to ttyUSB6
[ 2754.026424] sierra 1-1.2:1.1: Sierra USB modem converter detected
[ 2754.027400] usb 1-1.2: APM supported, enabling autosuspend.
[ 2754.029400] usb 1-1.2: Sierra USB modem converter now attached to ttyUSB7
[ 2754.029946] sierra 1-1.2:1.2: Sierra USB modem converter detected
[ 2754.030786] usb 1-1.2: APM supported, enabling autosuspend.
[ 2754.031992] usb 1-1.2: Sierra USB modem converter now attached to ttyUSB8
[ 2754.033779] sierra 1-1.2:1.3: Sierra USB modem converter detected
[ 2754.047651] usb 1-1.2: APM supported, enabling autosuspend.
[ 2754.050126] usb 1-1.2: Sierra USB modem converter now attached to ttyUSB9
[ 2754.051250] sierra 1-1.2:1.4: Sierra USB modem converter detected
[ 2754.052921] usb 1-1.2: APM supported, enabling autosuspend.
[ 2754.054010] usb 1-1.2: Sierra USB modem converter now attached to ttyUSB10
```

**cat /var/log/syslog | tail -20 **

```
Feb 19 14:05:30 localhost kernel: [ 2753.924219] usb 1-1.2: new high speed USB device using ehci_hcd and address 20
Feb 19 14:05:30 localhost kernel: [ 2754.017756] usb 1-1.2: config 1 has an invalid interface number: 7 but max is 5
Feb 19 14:05:30 localhost kernel: [ 2754.017772] usb 1-1.2: config 1 has no interface number 5
Feb 19 14:05:30 localhost kernel: [ 2754.021642] usb 1-1.2: configuration #1 chosen from 1 choice
Feb 19 14:05:30 localhost kernel: [ 2754.023888] sierra 1-1.2:1.0: Sierra USB modem converter detected
Feb 19 14:05:30 localhost kernel: [ 2754.025811] usb 1-1.2: APM supported, enabling autosuspend.
Feb 19 14:05:30 localhost kernel: [ 2754.026162] usb 1-1.2: Sierra USB modem converter now attached to ttyUSB6
Feb 19 14:05:30 localhost kernel: [ 2754.026424] sierra 1-1.2:1.1: Sierra USB modem converter detected
Feb 19 14:05:30 localhost kernel: [ 2754.027400] usb 1-1.2: APM supported, enabling autosuspend.
Feb 19 14:05:30 localhost kernel: [ 2754.029400] usb 1-1.2: Sierra USB modem converter now attached to ttyUSB7
Feb 19 14:05:30 localhost kernel: [ 2754.029946] sierra 1-1.2:1.2: Sierra USB modem converter detected
Feb 19 14:05:30 localhost kernel: [ 2754.030786] usb 1-1.2: APM supported, enabling autosuspend.
Feb 19 14:05:30 localhost kernel: [ 2754.031992] usb 1-1.2: Sierra USB modem converter now attached to ttyUSB8
Feb 19 14:05:30 localhost kernel: [ 2754.033779] sierra 1-1.2:1.3: Sierra USB modem converter detected
Feb 19 14:05:30 localhost kernel: [ 2754.047651] usb 1-1.2: APM supported, enabling autosuspend.
Feb 19 14:05:30 localhost kernel: [ 2754.050126] usb 1-1.2: Sierra USB modem converter now attached to ttyUSB9
Feb 19 14:05:30 localhost kernel: [ 2754.051250] sierra 1-1.2:1.4: Sierra USB modem converter detected
Feb 19 14:05:30 localhost kernel: [ 2754.052921] usb 1-1.2: APM supported, enabling autosuspend.
Feb 19 14:05:30 localhost kernel: [ 2754.054010] usb 1-1.2: Sierra USB modem converter now attached to ttyUSB10
```

---

### Post by varunendra on 2013-02-19
I wrapped your outputs in 'Code' tags. Please always use them when posting terminal commands or codes *(follow the 'Code tags example' link in my signature to see how)*.

I see nothing wrong in the outputs. What is the problem you are having?

If it is only the warning messages you are worried about, most often they are not serious like 'errors', and can be safely ignored *(frankly, I can not conclude anything from the warning snippets you are getting in dmesg, but they don't seem serious to me)*.

---

