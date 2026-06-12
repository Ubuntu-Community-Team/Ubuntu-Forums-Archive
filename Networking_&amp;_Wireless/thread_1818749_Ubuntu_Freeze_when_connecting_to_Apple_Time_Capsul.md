---
title: "Ubuntu Freeze when connecting to Apple Time Capsule"
date: 2011-08-05
forum: Networking &amp; Wireless
---

### Post by nielsatha on 2011-08-05
Hello everyone,

I'm new to Ubuntu. I have the latest 11.04 installed.

I use a remote Apple Time Capsule as a File Server, that I connected in my fstab via
```

//172.16.1.1/Data   /media/Server   cifs   password=whatever,rw,iocharset=utf8,file_mode=0777,dir_mode=0777

```It works, but after a while of transferring files my computer just freezes and there is nothing I can do except hit the reset button. I checked my kern.log and the last lines say:

```

Aug  5 12:19:46 niels-ubuntu kernel: [   11.876575] type=1400 audit(1312539586.176:12): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=867 comm="apparmor_parser"
Aug  5 12:19:46 niels-ubuntu kernel: [   11.876927] type=1400 audit(1312539586.176:13): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=867 comm="apparmor_parser"
Aug  5 12:19:46 niels-ubuntu kernel: [   11.878305] type=1400 audit(1312539586.176:14): apparmor="STATUS" operation="profile_load" name="/usr/bin/evince" pid=868 comm="apparmor_parser"
Aug  5 12:19:46 niels-ubuntu kernel: [   11.994592] phy0 -> rt2800pci_mcu_status: Error - MCU request failed, no response from hardware
Aug  5 12:19:46 niels-ubuntu kernel: [   12.064495] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Aug  5 12:19:46 niels-ubuntu kernel: [   12.108780] fglrx_pci 0000:01:00.0: irq 61 for MSI/MSI-X
Aug  5 12:19:46 niels-ubuntu kernel: [   12.109341] [fglrx] Firegl kernel thread PID: 1160
Aug  5 12:19:46 niels-ubuntu kernel: [   12.109476] [fglrx] Firegl kernel thread PID: 1161
Aug  5 12:19:46 niels-ubuntu kernel: [   12.109648] [fglrx] Firegl kernel thread PID: 1162
Aug  5 12:19:46 niels-ubuntu kernel: [   12.109859] [fglrx] IRQ 61 Enabled
Aug  5 12:19:46 niels-ubuntu kernel: [   12.133665] EXT4-fs (sdb6): re-mounted. Opts: errors=remount-ro,commit=0
Aug  5 12:19:46 niels-ubuntu kernel: [   12.135151] EXT4-fs (sdb1): re-mounted. Opts: commit=0
Aug  5 12:19:46 niels-ubuntu kernel: [   12.160716] r8169 0000:05:00.0: eth0: unable to apply firmware patch
Aug  5 12:19:46 niels-ubuntu kernel: [   12.162512] r8169 0000:05:00.0: eth0: link down
Aug  5 12:19:46 niels-ubuntu kernel: [   12.162516] r8169 0000:05:00.0: eth0: link down
Aug  5 12:19:46 niels-ubuntu kernel: [   12.162932] ADDRCONF(NETDEV_UP): eth0: link is not ready
Aug  5 12:19:46 niels-ubuntu kernel: [   12.197790] EXT4-fs (sda1): re-mounted. Opts: user_xattr,commit=0
Aug  5 12:19:46 niels-ubuntu kernel: [   12.246104] [fglrx] Gart USWC size:1280 M.
Aug  5 12:19:46 niels-ubuntu kernel: [   12.246106] [fglrx] Gart cacheable size:508 M.
Aug  5 12:19:46 niels-ubuntu kernel: [   12.246109] [fglrx] Reserved FB block: Shared offset:0, size:1000000 
Aug  5 12:19:46 niels-ubuntu kernel: [   12.246111] [fglrx] Reserved FB block: Unshared offset:f8fd000, size:403000 
Aug  5 12:19:46 niels-ubuntu kernel: [   12.246112] [fglrx] Reserved FB block: Unshared offset:3fff4000, size:c000 
Aug  5 12:19:47 niels-ubuntu kernel: [   13.397480] EXT4-fs (sdb6): re-mounted. Opts: errors=remount-ro,commit=0
Aug  5 12:19:47 niels-ubuntu kernel: [   13.399425] EXT4-fs (sdb1): re-mounted. Opts: commit=0
Aug  5 12:19:47 niels-ubuntu kernel: [   13.400803] EXT4-fs (sda1): re-mounted. Opts: user_xattr,commit=0
Aug  5 12:19:48 niels-ubuntu kernel: [   14.322372] hda-intel: IRQ timing workaround is activated for card #2. Suggest a bigger bdl_pos_adj.
Aug  5 12:19:49 niels-ubuntu kernel: [   15.218801] r8169 0000:05:00.0: eth0: link up
Aug  5 12:19:49 niels-ubuntu kernel: [   15.219309] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Aug  5 12:19:53 niels-ubuntu kernel: [   19.546268] CIFS VFS: Autodisabling the use of server inode numbers on \\172.16.1.1\Data. This server doesn't seem to support them properly. Hardlinks will not be recognized on this mount. Consider mounting with the "noserverino" option to silence this message.
Aug  5 12:19:56 niels-ubuntu kernel: [   21.745610] CE: hpet4 increased min_delta_ns to 7500 nsec
Aug  5 12:19:56 niels-ubuntu kernel: [   21.745617] CE: hpet4 increased min_delta_ns to 11250 nsec
Aug  5 12:19:56 niels-ubuntu kernel: [   21.745621] hrtimer: interrupt took 2860 ns
Aug  5 12:20:00 niels-ubuntu kernel: [   26.172884] eth0: no IPv6 routers present
Aug  5 12:20:22 niels-ubuntu kernel: [   48.574685] CE: hpet2 increased min_delta_ns to 7500 nsec
Aug  5 12:20:22 niels-ubuntu kernel: [   48.574693] CE: hpet2 increased min_delta_ns to 11250 nsec
Aug  5 12:20:37 niels-ubuntu kernel: [   62.970103] CE: hpet3 increased min_delta_ns to 7500 nsec
Aug  5 12:20:37 niels-ubuntu kernel: [   62.970118] CE: hpet3 increased min_delta_ns to 11250 nsec

```So I assume it has something to do with the Time Capsule?!?

Can anyone help me here??


Regards, 

nielsatha

---

