---
title: "lirc stops working..."
date: 2010-11-16
forum: Multimedia Software
---

### Post by Termo on 2010-11-16
Recently suddenly my remote stops working after a while (I have still not found what trickers it)

Anyway I can see that when the case is I have not only the /dev/lirc0 but now a new /dev/lirc1. When I looked in my syslog I see:

```

Nov 16 11:35:19 Antec kernel: [ 1921.513987] imon usb_rx_callback_intf0: status(-75): ignored
Nov 16 11:35:19 Antec kernel: [ 1921.537981] imon usb_rx_callback_intf0: status(-84): ignored
Nov 16 11:35:19 Antec kernel: [ 1921.537994] lirc_imon: send_packet: packet tx failed (-71)
Nov 16 11:35:19 Antec kernel: [ 1921.537999] lirc_imon: vfd_write: send packet failed for packet #1
Nov 16 11:35:19 Antec kernel: [ 1921.561980] imon usb_rx_callback_intf0: status(-84): ignored
Nov 16 11:35:19 Antec kernel: [ 1921.585977] imon usb_rx_callback_intf0: status(-84): ignored
Nov 16 11:35:19 Antec kernel: [ 1921.609975] imon usb_rx_callback_intf0: status(-84): ignored
Nov 16 11:35:19 Antec kernel: [ 1921.633972] imon usb_rx_callback_intf0: status(-84): ignored
Nov 16 11:35:19 Antec kernel: [ 1921.649976] lirc_imon: send_packet: packet tx failed (-71)
Nov 16 11:35:19 Antec kernel: [ 1921.649981] lirc_imon: vfd_write: send packet failed for packet #0
Nov 16 11:35:19 Antec kernel: [ 1921.657969] imon usb_rx_callback_intf0: status(-84): ignored
Nov 16 11:35:19 Antec kernel: [ 1921.672061] hub 8-0:1.0: port 1 disabled by hub (EMI?), re-enabling...
Nov 16 11:35:19 Antec kernel: [ 1921.672067] usb 8-1: USB disconnect, address 2
Nov 16 11:35:19 Antec kernel: [ 1921.673968] imon usb_rx_callback_intf0: status(-108): ignored
Nov 16 11:35:19 Antec kernel: [ 1921.696297] imon_disconnect: iMON device (intf0) disconnected
Nov 16 11:35:19 Antec kernel: [ 1921.754654] lirc_imon: vfd_write: no iMON device present
Nov 16 11:35:19 Antec kernel: [ 1921.879685] lirc_imon: vfd_write: no iMON device present
Nov 16 11:35:20 Antec kernel: [ 1921.936022] usb 8-1: new low speed USB device using uhci_hcd and address 3
Nov 16 11:35:20 Antec kernel: [ 1922.004617] lirc_imon: vfd_write: no iMON device present
Nov 16 11:35:20 Antec kernel: [ 1922.092078] usb 8-1: configuration #1 chosen from 1 choice
Nov 16 11:35:20 Antec kernel: [ 1922.094992] lirc_dev: lirc_register_driver: sample_rate: 0
Nov 16 11:35:20 Antec kernel: [ 1922.095040] lirc_imon: Registered iMON driver (lirc minor: 1)
Nov 16 11:35:20 Antec kernel: [ 1922.095104] input: iMON PAD IR Mouse (15c2:ffdc) as /devices/pci0000:00/0000:00:1d.2/usb8/8-$
Nov 16 11:35:20 Antec kernel: [ 1922.106196] imon_set_ir_protocol: MCE IR protocol not supported on this device, using iMON p$
Nov 16 11:35:20 Antec kernel: [ 1922.106202] lirc_imon: iMON device (15c2:ffdc, intf0) on usb<8:3> initialized
Nov 16 11:35:20 Antec lircd-0.8.6[1664]: caught signal
Nov 16 11:35:20 Antec kernel: [ 1922.110458] lirc_imon: IR port closed
Nov 16 11:39:18 Antec kernel: [ 2160.308042] INFO: task LCDd:1157 blocked for more than 120 seconds.
Nov 16 11:39:18 Antec kernel: [ 2160.308046] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Nov 16 11:39:18 Antec kernel: [ 2160.308050] LCDd          D 000015b6     0  1157      1 0x00000000
Nov 16 11:39:18 Antec kernel: [ 2160.308057]  eb67deec 00000086 c012a578 000015b6 00000000 c0848760 eb6228ec c0848760
Nov 16 11:39:18 Antec kernel: [ 2160.308066]  87d8d95d 000001bf c0848760 c0848760 eb6228ec c0848760 c0848760 eeb4ce00
Nov 16 11:39:18 Antec kernel: [ 2160.308076]  87d89602 000001bf eb622640 eebe9820 eebe9824 ffffffff eb67df18 c058c1f6
Nov 16 11:39:18 Antec kernel: [ 2160.308085] Call Trace:
Nov 16 11:39:18 Antec kernel: [ 2160.308095]  [<c012a578>] ? default_spin_lock_flags+0x8/0x10
Nov 16 11:39:18 Antec kernel: [ 2160.308101]  [<c058c1f6>] __mutex_lock_slowpath+0xd6/0x140
Nov 16 11:39:18 Antec kernel: [ 2160.308106]  [<c058c5e7>] ? do_nanosleep+0x97/0xc0
Nov 16 11:39:18 Antec kernel: [ 2160.308110]  [<c058c105>] mutex_lock+0x25/0x40
Nov 16 11:39:18 Antec kernel: [ 2160.308122]  [<f8863ed5>] vfd_write+0x45/0x1f0 [lirc_imon]
Nov 16 11:39:18 Antec kernel: [ 2160.308128]  [<c02f5914>] ? security_file_permission+0x14/0x20
Nov 16 11:39:18 Antec kernel: [ 2160.308135]  [<c0208942>] vfs_write+0xa2/0x1a0
Nov 16 11:39:18 Antec kernel: [ 2160.308141]  [<f8863e90>] ? vfd_write+0x0/0x1f0 [lirc_imon]
Nov 16 11:39:18 Antec kernel: [ 2160.308146]  [<c0354699>] ? copy_to_user+0x39/0x130
Nov 16 11:39:18 Antec kernel: [ 2160.308151]  [<c0209262>] sys_write+0x42/0x70
Nov 16 11:39:18 Antec kernel: [ 2160.308155]  [<c01033ec>] syscall_call+0x7/0xb
Nov 16 11:39:18 Antec kernel: [ 2160.308171] INFO: task lircd:1664 blocked for more than 120 seconds.
Nov 16 11:39:18 Antec kernel: [ 2160.308174] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Nov 16 11:39:18 Antec kernel: [ 2160.308177] lircd         D 000027c2     0  1664      1 0x00000000
Nov 16 11:39:18 Antec kernel: [ 2160.308182]  ddab9e98 00000082 d78a6000 000027c2 00000000 c0848760 e8a0756c c0848760
Nov 16 11:39:18 Antec kernel: [ 2160.308191]  86de9fde 000001bf c0848760 c0848760 e8a0756c c0848760 c0848760 e8a80540
Nov 16 11:39:18 Antec kernel: [ 2160.308200]  00000000 000001bf e8a072c0 f8850ca8 f8850cac ffffffff ddab9ec4 c058c1f6

```

Any ideas to what is going on and where to look?

*sudo service lirc restart* does not change anything. Also I can not *modprobe -r lirc_imon* as module is in use...

I have also tried to restart usb by modproble -r uhci_hcd or ehci_hcd but that just gives me a:

```
FATAL: Module ehci_hcd is builtin

```

Finally when trying lsusb after lirc stops working gives me just a blinking cursor and a terminal I can not ^C out of?!? So something hangs with the usb module...

I'm running Ubuntu 10.04

---

### Post by Termo on 2011-01-29
By changing the physical usb port the display is connected to seems to have solved the problem... Maybe a faulty internal usb connector on the mb.

---

