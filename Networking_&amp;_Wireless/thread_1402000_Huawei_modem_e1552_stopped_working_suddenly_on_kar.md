---
title: "Huawei modem e1552 stopped working suddenly on karmic"
date: 2010-02-08
forum: Networking &amp; Wireless
---

### Post by albertoguevara on 2010-02-08
Hi, i'm running Kubuntu karmic and i've been using a 3G Huawei E1552 modem to connect to the internet, everything was going well when suddenly my modem stopped working. I've tried reconfiguring everything, i even reinstalled kubuntu from scratch with no success.

Here's a part of my /var/log/debug

[HTML]Feb  8 17:14:01 alberto-laptop kernel: [ 1532.099883] usb-storage: device found at 7
Feb  8 17:14:01 alberto-laptop kernel: [ 1532.099888] usb-storage: waiting for device to settle before scanning
Feb  8 17:14:01 alberto-laptop kernel: [ 1532.101067] usb-storage: device found at 7
Feb  8 17:14:01 alberto-laptop kernel: [ 1532.101072] usb-storage: waiting for device to settle before scanning
Feb  8 17:14:06 alberto-laptop kernel: [ 1537.091478] usb-storage: device scan complete
Feb  8 17:14:14 alberto-laptop kernel: [ 1544.770255] usb-storage: device found at 8
Feb  8 17:14:14 alberto-laptop kernel: [ 1544.770260] usb-storage: waiting for device to settle before scanning
Feb  8 17:14:14 alberto-laptop kernel: [ 1544.771936] usb-storage: device found at 8
Feb  8 17:14:14 alberto-laptop kernel: [ 1544.771942] usb-storage: waiting for device to settle before scanning
Feb  8 17:14:14 alberto-laptop modem-manager: (Huawei): (ttyUSB1) deferring support check
Feb  8 17:14:14 alberto-laptop modem-manager: (ttyUSB0): probe requested by plugin 'Huawei'
Feb  8 17:14:14 alberto-laptop modem-manager: (Huawei): (ttyUSB2) deferring support check
Feb  8 17:14:15 alberto-laptop modem-manager: Added modem /sys/devices/pci0000:00/0000:00:1d.7/usb2/2-3
Feb  8 17:14:15 alberto-laptop modem-manager: Exported modem /sys/devices/pci0000:00/0000:00:1d.7/usb2/2-3 as /org/freedesktop/ModemManager/Modems/1
Feb  8 17:14:17 alberto-laptop modem-manager: (ttyUSB1): re-checking support...
Feb  8 17:14:17 alberto-laptop modem-manager: (ttyUSB2): re-checking support...
Feb  8 17:14:19 alberto-laptop kernel: [ 1549.771671] usb-storage: device scan complete
Feb  8 17:14:19 alberto-laptop kernel: [ 1549.773619] usb-storage: device scan complete
Feb  8 17:14:19 alberto-laptop kernel: [ 1549.797135] sr 19:0:0:0: Attached scsi CD-ROM sr2
Feb  8 17:14:22 alberto-laptop modem-manager: (ttyUSB1): probe requested by plugin 'Generic'
Feb  8 17:14:23 alberto-laptop modem-manager: Registration state changed: 2[/HTML]

Here's my /var/log/syslog

[HTML]Feb  8 17:18:29 alberto-laptop NetworkManager: <info>  Activation (ttyUSB0) starting connection 'BAM 3G'
Feb  8 17:18:29 alberto-laptop NetworkManager: <info>  (ttyUSB0): device state change: 3 -> 4 (reason 0)
Feb  8 17:18:29 alberto-laptop NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) scheduled...
Feb  8 17:18:29 alberto-laptop NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) started...
Feb  8 17:18:29 alberto-laptop NetworkManager: <info>  (ttyUSB0): device state change: 4 -> 6 (reason 0)
Feb  8 17:18:29 alberto-laptop NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) complete.
Feb  8 17:18:29 alberto-laptop NetworkManager: <WARN>  secrets_update_setting(): Failed to update connection secrets: 1 ipv4
Feb  8 17:18:29 alberto-laptop NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) scheduled...
Feb  8 17:18:29 alberto-laptop NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) started...
Feb  8 17:18:29 alberto-laptop NetworkManager: <info>  (ttyUSB0): device state change: 6 -> 4 (reason 0)
Feb  8 17:18:29 alberto-laptop NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) complete.
Feb  8 17:18:29 alberto-laptop modem-manager: (ttyUSB0) opening serial device...
Feb  8 17:18:30 alberto-laptop modem-manager: Registration state changed: 2
Feb  8 17:18:33 alberto-laptop modem-manager: Registration state changed: 1
Feb  8 17:18:33 alberto-laptop NetworkManager: <info>  Activation (ttyUSB0) Stage 2 of 5 (Device Configure) scheduled...
Feb  8 17:18:33 alberto-laptop NetworkManager: <info>  Activation (ttyUSB0) Stage 2 of 5 (Device Configure) starting...
Feb  8 17:18:33 alberto-laptop NetworkManager: <info>  (ttyUSB0): device state change: 4 -> 5 (reason 0)
Feb  8 17:18:33 alberto-laptop NetworkManager: <info>  Activation (ttyUSB0) Stage 2 of 5 (Device Configure) successful.
Feb  8 17:18:33 alberto-laptop NetworkManager: <info>  Activation (ttyUSB0) Stage 3 of 5 (IP Configure Start) scheduled.
Feb  8 17:18:33 alberto-laptop NetworkManager: <info>  Activation (ttyUSB0) Stage 2 of 5 (Device Configure) complete.
Feb  8 17:18:33 alberto-laptop NetworkManager: <info>  Activation (ttyUSB0) Stage 3 of 5 (IP Configure Start) started...
Feb  8 17:18:33 alberto-laptop NetworkManager: <info>  (ttyUSB0): device state change: 5 -> 7 (reason 0)
Feb  8 17:18:33 alberto-laptop NetworkManager: <info>  Starting pppd connection
Feb  8 17:18:33 alberto-laptop NetworkManager: <debug> [1265665713.178033] nm_ppp_manager_start(): Command line: /usr/sbin/pppd nodetach lock nodefaultroute user Digitel ttyUSB0 noipdefault noauth usepeerdns lcp-echo-failure 0 lcp-echo-interval 0 ipparam /org/freedesktop/NetworkManager/PPP/1 plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so
Feb  8 17:18:33 alberto-laptop pppd[2736]: Plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so loaded.
Feb  8 17:18:33 alberto-laptop NetworkManager: <debug> [1265665713.194415] nm_ppp_manager_start(): ppp started with pid 2736
Feb  8 17:18:33 alberto-laptop NetworkManager: <info>  Activation (ttyUSB0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Feb  8 17:18:33 alberto-laptop NetworkManager: <info>  Activation (ttyUSB0) Stage 3 of 5 (IP Configure Start) complete.
Feb  8 17:18:33 alberto-laptop NetworkManager: <info>  Activation (ttyUSB0) Stage 4 of 5 (IP6 Configure Get) started...
Feb  8 17:18:33 alberto-laptop NetworkManager: <info>  Activation (ttyUSB0) Stage 4 of 5 (IP6 Configure Get) complete.
Feb  8 17:18:33 alberto-laptop pppd[2736]: pppd 2.4.5 started by root, uid 0
Feb  8 17:18:33 alberto-laptop pppd[2736]: Using interface ppp0
Feb  8 17:18:33 alberto-laptop pppd[2736]: Connect: ppp0 <--> /dev/ttyUSB0
Feb  8 17:18:33 alberto-laptop NetworkManager:    SCPlugin-Ifupdown: devices added (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Feb  8 17:18:33 alberto-laptop NetworkManager:    SCPlugin-Ifupdown: device added (path: /sys/devices/virtual/net/ppp0, iface: ppp0): no ifupdown configuration found.
Feb  8 17:18:33 alberto-laptop NetworkManager: <WARN>  secrets_update_setting(): Failed to update connection secrets: 1 ipv4
Feb  8 17:18:33 alberto-laptop pppd[2736]: CHAP authentication succeeded
Feb  8 17:18:33 alberto-laptop pppd[2736]: CHAP authentication succeeded
Feb  8 17:18:53 alberto-laptop NetworkManager: <WARN>  pppd_timed_out(): Looks like pppd didn't initialize our dbus module
Feb  8 17:18:53 alberto-laptop NetworkManager: <info>  (ttyUSB0): device state change: 7 -> 9 (reason 14)
Feb  8 17:18:53 alberto-laptop NetworkManager: <info>  Marking connection 'BAM 3G' invalid.
Feb  8 17:18:53 alberto-laptop NetworkManager: <info>  Activation (ttyUSB0) failed.
Feb  8 17:18:53 alberto-laptop NetworkManager: <info>  (ttyUSB0): device state change: 9 -> 3 (reason 0)
Feb  8 17:18:53 alberto-laptop NetworkManager: <info>  (ttyUSB0): deactivating device (reason: 0).
Feb  8 17:18:53 alberto-laptop NetworkManager: flush_routes: assertion `iface_idx >= 0' failed
Feb  8 17:18:53 alberto-laptop NetworkManager: flush_addresses: assertion `iface_idx >= 0' failed
Feb  8 17:18:53 alberto-laptop pppd[2736]: Terminating on signal 15
Feb  8 17:18:53 alberto-laptop NetworkManager: <info>  Policy set 'Sala de Lectura IQ 2 WPA' (wlan0) as default for routing and DNS.
Feb  8 17:18:53 alberto-laptop pppd[2736]: Connection terminated.
Feb  8 17:18:53 alberto-laptop NetworkManager:    SCPlugin-Ifupdown: devices removed (path: /sys/devices/virtual/net/ppp0, iface: ppp0)
Feb  8 17:18:53 alberto-laptop modem-manager: Got failure code 3: No carrier
Feb  8 17:18:54 alberto-laptop modem-manager: (ttyUSB0) closing serial device...
Feb  8 17:18:54 alberto-laptop pppd[2736]: Exit.
Feb  8 17:18:55 alberto-laptop NetworkManager: <debug> [1265665735.001191] ensure_killed(): waiting for ppp pid 2736 to exit
Feb  8 17:18:55 alberto-laptop NetworkManager: <debug> [1265665735.001394] ensure_killed(): ppp pid 2736 cleaned up
Feb  8 17:18:57 alberto-laptop wpa_supplicant[1102]: CTRL-EVENT-SCAN-RESULTS [/HTML]

Here's my /var/log/messages

[HTML]Feb  8 17:03:13 alberto-laptop kernel: [  883.785311] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
Feb  8 17:03:13 alberto-laptop kernel: [  883.785361] option 2-3:1.0: device disconnected
Feb  8 17:03:13 alberto-laptop kernel: [  883.785654] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
Feb  8 17:03:13 alberto-laptop kernel: [  883.785694] option 2-3:1.1: device disconnected
Feb  8 17:03:13 alberto-laptop kernel: [  883.785973] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
Feb  8 17:03:13 alberto-laptop kernel: [  883.786016] option 2-3:1.2: device disconnected
Feb  8 17:14:01 alberto-laptop kernel: [ 1531.930579] usb 2-3: new high speed USB device using ehci_hcd and address 7
Feb  8 17:14:01 alberto-laptop kernel: [ 1532.091664] usb 2-3: configuration #1 chosen from 1 choice
Feb  8 17:14:01 alberto-laptop kernel: [ 1532.099269] scsi14 : SCSI emulation for USB Mass Storage devices
Feb  8 17:14:01 alberto-laptop kernel: [ 1532.099646] scsi15 : SCSI emulation for USB Mass Storage devices
Feb  8 17:14:06 alberto-laptop kernel: [ 1537.093652] scsi 15:0:0:0: Direct-Access     HUAWEI   MMC Storage      2.31 PQ: 0 ANSI: 2
Feb  8 17:14:06 alberto-laptop kernel: [ 1537.094565] sd 15:0:0:0: Attached scsi generic sg4 type 0
Feb  8 17:14:06 alberto-laptop kernel: [ 1537.104729] sd 15:0:0:0: [sdc] Attached SCSI removable disk
Feb  8 17:14:07 alberto-laptop kernel: [ 1538.364164] usb 2-3: USB disconnect, address 7
Feb  8 17:14:14 alberto-laptop kernel: [ 1544.601419] usb 2-3: new high speed USB device using ehci_hcd and address 8
Feb  8 17:14:14 alberto-laptop kernel: [ 1544.763010] usb 2-3: configuration #1 chosen from 1 choice
Feb  8 17:14:14 alberto-laptop kernel: [ 1544.767583] option 2-3:1.0: GSM modem (1-port) converter detected
Feb  8 17:14:14 alberto-laptop kernel: [ 1544.767784] usb 2-3: GSM modem (1-port) converter now attached to ttyUSB0
Feb  8 17:14:14 alberto-laptop kernel: [ 1544.768254] option 2-3:1.1: GSM modem (1-port) converter detected
Feb  8 17:14:14 alberto-laptop kernel: [ 1544.768375] usb 2-3: GSM modem (1-port) converter now attached to ttyUSB1
Feb  8 17:14:14 alberto-laptop kernel: [ 1544.768730] option 2-3:1.2: GSM modem (1-port) converter detected
Feb  8 17:14:14 alberto-laptop kernel: [ 1544.768859] usb 2-3: GSM modem (1-port) converter now attached to ttyUSB2
Feb  8 17:14:14 alberto-laptop kernel: [ 1544.769618] scsi19 : SCSI emulation for USB Mass Storage devices
Feb  8 17:14:14 alberto-laptop kernel: [ 1544.771620] scsi20 : SCSI emulation for USB Mass Storage devices
Feb  8 17:14:19 alberto-laptop kernel: [ 1549.773891] scsi 19:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
Feb  8 17:14:19 alberto-laptop kernel: [ 1549.776663] scsi 20:0:0:0: Direct-Access     HUAWEI   MMC Storage      2.31 PQ: 0 ANSI: 2
Feb  8 17:14:19 alberto-laptop kernel: [ 1549.796867] sr2: scsi-1 drive
Feb  8 17:14:19 alberto-laptop kernel: [ 1549.797297] sr 19:0:0:0: Attached scsi generic sg4 type 5
Feb  8 17:14:19 alberto-laptop kernel: [ 1549.797644] sd 20:0:0:0: Attached scsi generic sg5 type 0
Feb  8 17:14:19 alberto-laptop kernel: [ 1549.811840] sd 20:0:0:0: [sdc] Attached SCSI removable disk
Feb  8 17:18:33 alberto-laptop pppd[2736]: Plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so loaded.
Feb  8 17:18:33 alberto-laptop pppd[2736]: pppd 2.4.5 started by root, uid 0
Feb  8 17:18:33 alberto-laptop pppd[2736]: Using interface ppp0
Feb  8 17:18:33 alberto-laptop pppd[2736]: Connect: ppp0 <--> /dev/ttyUSB0
Feb  8 17:18:33 alberto-laptop pppd[2736]: CHAP authentication succeeded
Feb  8 17:18:33 alberto-laptop pppd[2736]: CHAP authentication succeeded
Feb  8 17:18:53 alberto-laptop pppd[2736]: Terminating on signal 15
Feb  8 17:18:53 alberto-laptop pppd[2736]: Connection terminated.
Feb  8 17:18:54 alberto-laptop pppd[2736]: Exit.[/HTML]

And here's the huawei modem part of my /var/log/udev

[HTML]UDEV  [1265663933.266733] add      /devices/pci0000:00/0000:00:1d.7/usb2/2-3/2-3:1.1/host8/target8:0:0/8:0:0:0/block/sdc (block)
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:1d.7/usb2/2-3/2-3:1.1/host8/target8:0:0/8:0:0:0/block/sdc
SUBSYSTEM=block
DEVNAME=/dev/sdc
DEVTYPE=disk
SEQNUM=1354
ID_VENDOR=HUAWEI
ID_VENDOR_ENC=HUAWEI\x20\x20
ID_VENDOR_ID=12d1
ID_MODEL=MMC_Storage
ID_MODEL_ENC=MMC\x20Storage\x20\x20\x20\x20\x20
ID_MODEL_ID=1446
ID_REVISION=2.31
ID_SERIAL=HUAWEI_MMC_Storage-0:0
ID_TYPE=disk
ID_INSTANCE=0:0
ID_BUS=usb
ID_USB_INTERFACES=:080650:
ID_USB_INTERFACE_NUM=01
ID_USB_DRIVER=usb-storage
ID_PATH=pci-0000:00:1d.7-usb-0:3:1.1-scsi-0:0:0:0
DKD_MEDIA_AVAILABLE=0
DKD_PRESENTATION_NOPOLICY=0
MAJOR=8
MINOR=32
DEVLINKS=/dev/block/8:32 /dev/disk/by-id/usb-HUAWEI_MMC_Storage-0:0 /dev/disk/by-path/pci-0000:00:1d.7-usb-0:3:1.1-scsi-0:0:0:0[/HTML]

Can somebody help me with this? Thanks in advance.

---

### Post by nejode on 2010-02-15
albertoguevara: same thing happened to me and have not been able to fix it... it must be a change in the authentication protocol of DIGITEL...

---

### Post by Sylslay on 2010-02-16
My huaweii e180 stop work. Signal lost (only green led blinking, no steady blue - 7.2mb). Not possible to connect.
They change for new, in shop. But had always problem with booting up system while not in use SD card storege in that modem.
Since than I use old e220. No problem working always perfect in Meteor. (modem form 3g, unlocked , flsahed with latest  o2 frimware) . And speed is ok. Not much slower than e180.
And new e180 "is on holidays", due waiting for kernel upgrade? or my BIOS malfunction?
And most funny, e180 modem always was seen as e220/e270 in system, acording to lsusb..:o
e270 was best 3g modem I used so far. Left at my parents home.

---

### Post by NiksaVel on 2010-04-01
Hi guys, 

just thought I'd add my experience with my Huawei E620 in Karmic...   a bit disappointing really...  especially as it worked flawlessly in Jaunty.

I am using Karmic, fully updated to this day, on Acer Aspire One in the netbook-remix version.

As of the clean install it did not work due to the regression....  with subsequent kernel updates it started working okay, and the 2.6.31-17-generic is the last kernel version where it work perfect.

The -19 update makes it able to connect only once before having to reboot (and there is no traffic going on) and the -20 update does not see the modem in network-manager at all.  Seems like a regression back to the vanilla karmic install.  I can only see the "cd storage"


Anyone has any ideas whats up with this?

---

### Post by pdc on 2010-04-02
the crunchbang distro has gone to using debian;

VMC (vodafone mobile connect) has gone to using debian;

being a shooting star can have its drawbacks

---

