---
title: "Network Problem"
date: 2013-01-18
forum: Networking &amp; Wireless
---

### Post by Shastru on 2013-01-18
Hello everyone , i have a problem that really sucks and i would need help to solve it as soon as possible.
Everyi night at 2 AM the internet from ubuntu stops working and i have to reboot to get the connection again.
I have ubuntu installed in virtual box 2gb rams.
Anyone could please tell me how to make it stop doing that?
because im hosting a game..and its hard to stay up every night till 2 AM

---

### Post by dpurgert on 2013-01-18
since you're running it virtualized, is there anything happening to the host system around then?

---

### Post by Shastru on 2013-01-18
> **dpurgert said:**
> since you're running it virtualized, is there anything happening to the host system around then?

nope :(

---

### Post by dpurgert on 2013-01-18
well, that makes things difficult.  

What are you re-booting at 0200?  is it the virtual box, or the entire host machine?

---

### Post by elgordodude on 2013-01-18
How about a look at the logs?

cat /var/log/syslog | grep eth0

or whatever your interface is

or

cat /var/log/syslog | grep 02:00

if it is happening at exactly 2 AM, which is a weird thing to happen, might have the answer in black and white

---

### Post by Shastru on 2013-01-19
> **dpurgert said:**
> well, that makes things difficult.  

What are you re-booting at 0200?  is it the virtual box, or the entire host machine?

the host

---

### Post by Shastru on 2013-01-19
> **elgordodude said:**
> How about a look at the logs?

cat /var/log/syslog | grep eth0

or whatever your interface is

or

cat /var/log/syslog | grep 02:00

if it is happening at exactly 2 AM, which is a weird thing to happen, might have the answer in black and white

     CD-ROM           1.0  PQ: 0 ANSI: 5
Jan 13 02:00:47 blue kernel: [    6.016769] sr0: scsi3-mmc drive: 32x/32x xa/for                                                                                        m2 tray
Jan 13 02:00:47 blue kernel: [    6.016769] Uniform CD-ROM driver Revision: 3.20
Jan 13 02:00:47 blue kernel: [    6.016769] sr 1:0:0:0: Attached scsi CD-ROM sr0
Jan 13 02:00:47 blue kernel: [    6.113525] sr 1:0:0:0: Attached scsi generic sg                                                                                        0 type 5
Jan 13 02:00:47 blue kernel: [    6.124221] usb 1-1: configuration #1 chosen fro                                                                                        m 1 choice
Jan 13 02:00:47 blue kernel: [    6.480073] serio: i8042 KBD port at 0x60,0x64 i                                                                                        rq 1
Jan 13 02:00:47 blue kernel: [    6.480073] serio: i8042 AUX port at 0x60,0x64 i                                                                                        rq 12
Jan 13 02:00:47 blue kernel: [    6.480073] mice: PS/2 mouse device common for a                                                                                        ll mice
Jan 13 02:00:47 blue kernel: [    6.490303] rtc_cmos rtc_cmos: rtc core: registe                                                                                        red rtc_cmos as rtc0
Jan 13 02:00:47 blue kernel: [    6.496789] rtc0: alarms up to one day, 114 byte                                                                                        s nvram
Jan 13 02:00:47 blue kernel: [    6.496789] device-mapper: uevent: version 1.0.3
Jan 13 02:00:47 blue kernel: [    6.537191] input: AT Translated Set 2 keyboard                                                                                         as /devices/platform/i8042/serio0/input/input3
Jan 13 02:00:47 blue kernel: [    6.537191] device-mapper: ioctl: 4.15.0-ioctl (                                                                                        2009-04-01) initialised: [email]dm-devel@redhat.com[/email]
Jan 13 02:00:47 blue kernel: [    6.537191] device-mapper: multipath: version 1.                                                                                        1.0 loaded
Jan 13 02:00:47 blue kernel: [    6.537191] device-mapper: multipath round-robin                                                                                        : version 1.0.0 loaded
Jan 13 02:00:47 blue kernel: [    6.541191] EISA: Probing bus 0 at eisa.0
Jan 13 02:00:47 blue kernel: [    6.541191] Cannot allocate resource for EISA sl                                                                                        ot 4
Jan 13 02:00:47 blue kernel: [    6.541191] EISA: Detected 0 cards.
Jan 13 02:00:47 blue kernel: [    6.541191] cpuidle: using governor ladder
Jan 13 02:00:47 blue kernel: [    6.541191] cpuidle: using governor menu
Jan 13 02:00:47 blue kernel: [    6.544222] TCP cubic registered
Jan 13 02:00:47 blue kernel: [    6.544222] NET: Registered protocol family 10
Jan 13 02:00:47 blue kernel: [    6.550007] NET: Registered protocol family 17
Jan 13 02:00:47 blue kernel: [    6.652823] Using IPI No-Shortcut mode
Jan 13 02:00:47 blue kernel: [    6.652823] PM: Resume from disk failed.
Jan 13 02:00:47 blue kernel: [    6.652823] registered taskstats version 1
Jan 13 02:00:47 blue kernel: [    6.652823]   Magic number: 13:752:1009
Jan 13 02:00:47 blue kernel: [    6.652823] rtc_cmos rtc_cmos: setting system cl                                                                                        ock to 2013-01-13 00:00:02 UTC (1358035202)
Jan 13 02:00:47 blue kernel: [    6.652823] BIOS EDD facility v0.16 2004-Jun-25,                                                                                         0 devices found
Jan 13 02:00:47 blue kernel: [    6.652823] EDD information not available.
Jan 13 02:00:47 blue kernel: [    6.716221] Freeing initrd memory: 9743k freed
Jan 13 02:00:47 blue kernel: [    6.764882] Freeing unused kernel memory: 684k f                                                                                        reed
Jan 13 02:00:47 blue kernel: [    6.776482] Write protecting the kernel text: 48                                                                                        32k
Jan 13 02:00:47 blue kernel: [    6.776482] Write protecting the kernel read-onl                                                                                        y data: 1884k
Jan 13 02:00:47 blue kernel: [    7.607536] udev: starting version 151
Jan 13 02:00:47 blue kernel: [    9.328396] ahci 0000:00:0d.0: version 3.0
Jan 13 02:00:47 blue kernel: [    9.484191] ACPI: PCI Interrupt Link [LNKA] enab                                                                                        led at IRQ 5
Jan 13 02:00:47 blue kernel: [    9.484191] PCI: setting IRQ 5 as level-triggere                                                                                        d
Jan 13 02:00:47 blue kernel: [    9.484191] ahci 0000:00:0d.0: PCI INT A -> Link                                                                                        [LNKA] -> GSI 5 (level, low) -> IRQ 5
Jan 13 02:00:47 blue kernel: [    9.484191] ahci: SSS flag set, parallel bus sca                                                                                        n disabled
Jan 13 02:00:47 blue kernel: [    9.484191] ahci 0000:00:0d.0: AHCI 0001.0100 32                                                                                         slots 1 ports 3 Gbps 0x1 impl SATA mode
Jan 13 02:00:47 blue kernel: [    9.484191] ahci 0000:00:0d.0: flags: 64bit ncq                                                                                         stag only ccc
Jan 13 02:00:47 blue kernel: [    9.484191] ahci 0000:00:0d.0: setting latency t                                                                                        imer to 64
Jan 13 02:00:47 blue kernel: [    9.605265] scsi2 : ahci
Jan 13 02:00:47 blue kernel: [    9.605265] ata3: SATA max UDMA/133 abar m8192@0                                                                                        xf0806000 port 0xf0806100 irq 5
Jan 13 02:00:47 blue kernel: [    9.997013] ata3: SATA link up 3.0 Gbps (SStatus                                                                                         123 SControl 300)
Jan 13 02:00:47 blue kernel: [   10.012194] ata3.00: ATA-6: VBOX HARDDISK, 1.0,                                                                                         max UDMA/133
Jan 13 02:00:47 blue kernel: [   10.012194] ata3.00: 33554432 sectors, multi 128                                                                                        : LBA48 NCQ (depth 31/32)
Jan 13 02:00:47 blue kernel: [   10.016223] ata3.00: configured for UDMA/133
Jan 13 02:00:47 blue kernel: [   10.039162] scsi 2:0:0:0: Direct-Access     ATA                                                                                              VBOX HARDDISK    1.0  PQ: 0 ANSI: 5
Jan 13 02:00:47 blue kernel: [   10.160244] sd 2:0:0:0: Attached scsi generic sg                                                                                        1 type 0
Jan 13 02:00:47 blue kernel: [   10.236309] sd 2:0:0:0: [sda] 33554432 512-byte                                                                                         logical blocks: (17.1 GB/16.0 GiB)
Jan 13 02:00:47 blue kernel: [   10.240204] sd 2:0:0:0: [sda] Write Protect is o                                                                                        ff
Jan 13 02:00:47 blue kernel: [   10.240204] sd 2:0:0:0: [sda] Mode Sense: 00 3a                                                                                         00 00
Jan 13 02:00:47 blue kernel: [   10.240204] sd 2:0:0:0: [sda] Write cache: enabl                                                                                        ed, read cache: enabled, doesn't support DPO or FUA
Jan 13 02:00:47 blue kernel: [   10.267584]  sda: sda1 sda2 < sda5 >
Jan 13 02:00:47 blue kernel: [   10.427226] sd 2:0:0:0: [sda] Attached SCSI disk
Jan 13 02:00:47 blue kernel: [   10.428207] vga16fb: initializing
Jan 13 02:00:47 blue kernel: [   10.428207] vga16fb: mapped to 0xc00a0000
Jan 13 02:00:47 blue kernel: [   10.428207] fb0: VGA16 VGA frame buffer device
Jan 13 02:00:47 blue kernel: [   11.377412] usbcore: registered new interface dr                                                                                        iver hiddev
Jan 13 02:00:47 blue kernel: [   11.384466] Intel(R) PRO/1000 Network Driver - v                                                                                        ersion 7.3.21-k5-NAPI
Jan 13 02:00:47 blue kernel: [   11.384466] Copyright (c) 1999-2006 Intel Corpor                                                                                        ation.
Jan 13 02:00:47 blue kernel: [   11.384466] ACPI: PCI Interrupt Link [LNKC] enab                                                                                        led at IRQ 10
Jan 13 02:00:47 blue kernel: [   11.384466] PCI: setting IRQ 10 as level-trigger                                                                                        ed
Jan 13 02:00:47 blue kernel: [   11.384466] e1000 0000:00:03.0: PCI INT A -> Lin                                                                                        k[LNKC] -> GSI 10 (level, low) -> IRQ 10
Jan 13 02:00:47 blue kernel: [   11.384466] e1000 0000:00:03.0: setting latency                                                                                         timer to 64
Jan 13 02:00:47 blue kernel: [   11.434285] input: VirtualBox USB Tablet as /dev                                                                                        ices/pci0000:00/0000:00:06.0/usb1/1-1/1-1:1.0/input/input4
Jan 13 02:00:47 blue kernel: [   11.440278] generic-usb 0003:80EE:0021.0001: inp                                                                                        ut,hidraw0: USB HID v1.10 Mouse [VirtualBox USB Tablet] on usb-0000:00:06.0-1/in                                                                                        put0
Jan 13 02:00:47 blue kernel: [   11.440278] usbcore: registered new interface dr                                                                                        iver usbhid
Jan 13 02:00:47 blue kernel: [   11.462052] usbhid: v2.6:USB HID core driver
Jan 13 02:00:47 blue kernel: [   12.124576] e1000: 0000:00:03.0: e1000_probe: (P                                                                                        CI:33MHz:32-bit) 08:00:27:34:7e:50
Jan 13 02:00:47 blue kernel: [   12.540402] Console: switching to colour frame b                                                                                        uffer device 80x30
Jan 13 02:00:47 blue kernel: [   12.936607] e1000: eth0: e1000_probe: Intel(R) P                                                                                        RO/1000 Network Connection
Jan 13 02:00:47 blue kernel: [   19.846356] EXT4-fs (sda1): INFO: recovery requi                                                                                        red on readonly filesystem
Jan 13 02:00:47 blue kernel: [   19.846356] EXT4-fs (sda1): write access will be                                                                                         enabled during recovery
Jan 13 02:00:47 blue kernel: [   28.739150] EXT4-fs (sda1): orphan cleanup on re                                                                                        adonly fs
Jan 13 02:00:47 blue kernel: [   28.739150] EXT4-fs (sda1): ext4_orphan_cleanup:                                                                                         deleting unreferenced inode 429169
Jan 13 02:00:47 blue kernel: [   28.739150] EXT4-fs (sda1): ext4_orphan_cleanup:                                                                                         deleting unreferenced inode 7939
Jan 13 02:00:47 blue kernel: [   28.739150] EXT4-fs (sda1): ext4_orphan_cleanup:                                                                                         deleting unreferenced inode 7938
Jan 13 02:00:47 blue kernel: [   28.739150] EXT4-fs (sda1): ext4_orphan_cleanup:                                                                                         deleting unreferenced inode 7937
Jan 13 02:00:47 blue kernel: [   28.739150] EXT4-fs (sda1): ext4_orphan_cleanup:                                                                                         deleting unreferenced inode 7936
Jan 13 02:00:47 blue kernel: [   28.739150] EXT4-fs (sda1): ext4_orphan_cleanup:                                                                                         deleting unreferenced inode 7905
Jan 13 02:00:47 blue kernel: [   28.739150] EXT4-fs (sda1): 6 orphan inodes dele                                                                                        ted
Jan 13 02:00:47 blue kernel: [   28.739150] EXT4-fs (sda1): recovery complete
Jan 13 02:00:47 blue kernel: [   29.148067] EXT4-fs (sda1): mounted filesystem w                                                                                        ith ordered data mode
Jan 13 02:00:47 blue kernel: [   38.716190] udev: starting version 151
Jan 13 02:00:47 blue kernel: [   40.041767] Intel ICH 0000:00:05.0: PCI INT A ->                                                                                         Link[LNKA] -> GSI 5 (level, low) -> IRQ 5
Jan 13 02:00:47 blue kernel: [   40.041767] Intel ICH 0000:00:05.0: setting late                                                                                        ncy timer to 64
Jan 13 02:00:47 blue kernel: [   40.880374] psmouse serio1: ID: 10 00 64
Jan 13 02:00:47 blue kernel: [   40.884203] input: ImExPS/2 Generic Explorer Mou                                                                                        se as /devices/platform/i8042/serio1/input/input5
Jan 13 02:00:47 blue kernel: [   41.092193] ip_tables: (C) 2000-2006 Netfilter C                                                                                        ore Team
Jan 13 02:00:47 blue kernel: [   44.988368] lp: driver loaded but no devices fou                                                                                        nd
Jan 13 02:00:47 blue kernel: [   45.868199] type=1505 audit(1358035241.712:2):                                                                                          operation="profile_load" pid=337 name="/sbin/dhclient3"
Jan 13 02:00:47 blue kernel: [   45.868199] type=1505 audit(1358035241.712:3):                                                                                          operation="profile_load" pid=337 name="/usr/lib/NetworkManager/nm-dhcp-client.ac                                                                                        tion"
Jan 13 02:00:47 blue kernel: [   45.868199] type=1505 audit(1358035241.712:4):                                                                                          operation="profile_load" pid=337 name="/usr/lib/connman/scripts/dhclient-script"
Jan 13 02:00:47 blue kernel: [   46.097824] parport_pc 00:04: reported by Plug a                                                                                        nd Play ACPI
Jan 13 02:00:47 blue kernel: [   47.221124] nf_conntrack version 0.5.0 (13821 bu                                                                                        ckets, 55284 max)
Jan 13 02:00:47 blue kernel: [   47.225124] CONFIG_NF_CT_ACCT is deprecated and                                                                                         will be removed soon. Please use
Jan 13 02:00:47 blue kernel: [   47.225124] nf_conntrack.acct=1 kernel parameter                                                                                        , acct=1 nf_conntrack module option or
Jan 13 02:00:47 blue kernel: [   47.225124] sysctl net.netfilter.nf_conntrack_ac                                                                                        ct=1 to enable it.
Jan 13 02:00:47 blue kernel: [   47.336276] ppdev: user-space parallel port driv                                                                                        er
Jan 13 02:00:47 blue kernel: [   48.168242] ip6_tables: (C) 2000-2006 Netfilter                                                                                         Core Team
Jan 13 02:00:47 blue kernel: [   49.097084] intel8x0_measure_ac97_clock: measure                                                                                        d 7218496 usecs (326676 samples)
Jan 13 02:00:47 blue kernel: [   49.097084] intel8x0: clocking to 50911
Jan 13 02:00:47 blue kernel: [   49.100240] piix4_smbus 0000:00:07.0: SMBus base                                                                                         address uninitialized - upgrade BIOS or use force_addr=0xaddr
Jan 13 02:00:48 blue dhclient: Internet Systems Consortium DHCP Client V3.1.3
Jan 13 02:00:48 blue dhclient: Copyright 2004-2009 Internet Systems Consortium.
Jan 13 02:00:48 blue dhclient: All rights reserved.
Jan 13 02:00:48 blue dhclient: For info, please visit [https://www.isc.org/softwa](https://www.isc.org/softwa)                                                                                        re/dhcp/
Jan 13 02:00:48 blue dhclient:
Jan 13 02:00:49 blue kernel: [   53.576855] e1000: eth0 NIC Link is Up 1000 Mbps                                                                                         Full Duplex, Flow Control: RX
Jan 13 02:00:49 blue kernel: [   53.748188] type=1505 audit(1358035249.592:5):                                                                                          operation="profile_replace" pid=635 name="/sbin/dhclient3"
Jan 13 02:00:49 blue kernel: [   53.748188] type=1505 audit(1358035249.592:6):                                                                                          operation="profile_replace" pid=635 name="/usr/lib/NetworkManager/nm-dhcp-client                                                                                        .action"
Jan 13 02:00:49 blue kernel: [   53.748188] type=1505 audit(1358035249.592:7):                                                                                          operation="profile_replace" pid=635 name="/usr/lib/connman/scripts/dhclient-scri                                                                                        pt"
Jan 13 02:00:49 blue dhclient: Listening on LPF/eth0/08:00:27:34:7e:50
Jan 13 02:00:49 blue dhclient: Sending on   LPF/eth0/08:00:27:34:7e:50
Jan 13 02:00:49 blue dhclient: Sending on   Socket/fallback
Jan 13 02:00:50 blue kernel: [   54.164625] type=1505 audit(1358035250.008:8):                                                                                          operation="profile_load" pid=637 name="/usr/sbin/tcpdump"
Jan 13 02:00:51 blue dhclient: DHCPREQUEST of 192.168.1.5 on eth0 to 255.255.255                                                                                        .255 port 67
Jan 13 02:00:51 blue dhclient: DHCPACK of 192.168.1.5 from 192.168.1.1
Jan 13 02:00:51 blue kernel: [   55.798494] padlock: VIA PadLock not detected.
Jan 13 02:00:52 blue init: apport pre-start process (695) terminated with status                                                                                         1
Jan 13 02:00:52 blue init: apport post-stop process (721) terminated with status                                                                                         1
Jan 13 02:00:53 blue dhclient: bound to 192.168.1.5 -- renewal in 38845 seconds.
Jan 13 02:00:53 blue cron[715]: (CRON) INFO (pidfile fd = 3)
Jan 13 02:00:53 blue cron[738]: (CRON) STARTUP (fork ok)
Jan 13 02:00:53 blue cron[738]: (CRON) INFO (Running @reboot jobs)
Jan 13 02:00:53 blue kernel: [   57.492221] padlock: VIA PadLock Hash Engine not                                                                                         detected.
Jan 13 02:00:53 blue modprobe: FATAL: Error inserting padlock_sha (/lib/modules/                                                                                        2.6.32-33-generic-pae/kernel/drivers/crypto/padlock-sha.ko): No such device
Jan 14 17:02:00 blue logservice[3835]: TcpManager OnAddSession

---

### Post by elgordodude on 2013-01-20
> **Shastru said:**
> 
Jan 13 02:00:48 blue dhclient: Internet Systems Consortium DHCP Client V3.1.3
Jan 13 02:00:48 blue dhclient: Copyright 2004-2009 Internet Systems Consortium.
Jan 13 02:00:48 blue dhclient: All rights reserved.
Jan 13 02:00:48 blue dhclient: For info, please visit [https://www.isc.org/softwa](https://www.isc.org/softwa)                                                                                        re/dhcp/
Jan 13 02:00:48 blue dhclient:
Jan 13 02:00:49 blue kernel: [   53.576855] e1000: eth0 NIC Link is Up 1000 Mbps                                                                                         Full Duplex, Flow Control: RX
Jan 13 02:00:49 blue kernel: [   53.748188] type=1505 audit(1358035249.592:5):                                                                                          operation="profile_replace" pid=635 name="/sbin/dhclient3"
Jan 13 02:00:49 blue kernel: [   53.748188] type=1505 audit(1358035249.592:6):                                                                                          operation="profile_replace" pid=635 name="/usr/lib/NetworkManager/nm-dhcp-client                                                                                        .action"
Jan 13 02:00:49 blue kernel: [   53.748188] type=1505 audit(1358035249.592:7):                                                                                          operation="profile_replace" pid=635 name="/usr/lib/connman/scripts/dhclient-scri                                                                                        pt"
Jan 13 02:00:49 blue dhclient: Listening on LPF/eth0/08:00:27:34:7e:50
Jan 13 02:00:49 blue dhclient: Sending on   LPF/eth0/08:00:27:34:7e:50
Jan 13 02:00:49 blue dhclient: Sending on   Socket/fallback
Jan 13 02:00:50 blue kernel: [   54.164625] type=1505 audit(1358035250.008:8):                                                                                          operation="profile_load" pid=637 name="/usr/sbin/tcpdump"
Jan 13 02:00:51 blue dhclient: DHCPREQUEST of 192.168.1.5 on eth0 to 255.255.255                                                                                        .255 port 67
Jan 13 02:00:51 blue dhclient: DHCPACK of 192.168.1.5 from 192.168.1.1
Jan 13 02:00:51 blue kernel: [   55.798494] padlock: VIA PadLock not detected.
Jan 13 02:00:52 blue init: apport pre-start process (695) terminated with status                                                                                         1
Jan 13 02:00:52 blue init: apport post-stop process (721) terminated with status                                                                                         1
Jan 13 02:00:53 blue dhclient: bound to 192.168.1.5 -- renewal in 38845 seconds.


Well, you're going through a dhcp renewal, and apport says it crashed. DHCP renewals aren't generally a big deal so I'd guess it's a combination of the virtual machine, gaming, and your router.

I'd either assign a static ip on your machine, a static ip for the machine on your router, or extend dhcp on the router so far into the future that it wasn't an issue.

See here for assigning a static ip:

[http://www.howtoforge.com/linux-basics-set-a-static-ip-on-ubuntu](http://www.howtoforge.com/linux-basics-set-a-static-ip-on-ubuntu)

---

