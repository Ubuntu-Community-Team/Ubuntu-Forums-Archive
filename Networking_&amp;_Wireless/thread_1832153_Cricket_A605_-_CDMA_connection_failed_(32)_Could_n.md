---
title: "Cricket A605 - CDMA connection failed: (32) Could not parse Serving System results."
date: 2011-08-24
forum: Networking &amp; Wireless
---

### Post by Lee Roder on 2011-08-24
I have a Cricket A605 broadband modem that is being recognized by my xubuntu 11.04.  However, it is not connecting.  Here is a dump of the /var/log/syslog file (there are a few attempts to connect included).
Any assistance would be GREATLY appreciated.

Aug 24 09:16:21 APF2308 NetworkManager[531]: <info> Activation (ttyACM0) starting connection 'Cricket Communications connection 1'
Aug 24 09:16:21 APF2308 NetworkManager[531]: <info> (ttyACM0): device state change: 3 -> 4 (reason 0)
Aug 24 09:16:21 APF2308 NetworkManager[531]: <info> Activation (ttyACM0) Stage 1 of 5 (Device Prepare) scheduled...
Aug 24 09:16:21 APF2308 NetworkManager[531]: <info> Activation (ttyACM0) Stage 1 of 5 (Device Prepare) started...
Aug 24 09:16:21 APF2308 NetworkManager[531]: <info> Activation (ttyACM0) Stage 1 of 5 (Device Prepare) complete.
Aug 24 09:16:21 APF2308 NetworkManager[531]: <warn> CDMA connection failed: (32) Could not parse Serving System results.
Aug 24 09:16:21 APF2308 NetworkManager[531]: <info> (ttyACM0): device state change: 4 -> 9 (reason 0)
Aug 24 09:16:21 APF2308 NetworkManager[531]: <info> Marking connection 'Cricket Communications connection 1' invalid.
Aug 24 09:16:21 APF2308 NetworkManager[531]: <warn> Activation (ttyACM0) failed.
Aug 24 09:16:21 APF2308 NetworkManager[531]: <info> (ttyACM0): device state change: 9 -> 3 (reason 0)
Aug 24 09:16:21 APF2308 NetworkManager[531]: <info> (ttyACM0): deactivating device (reason: 0).
Aug 24 09:17:01 APF2308 CRON[1888]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Aug 24 09:18:39 APF2308 NetworkManager[531]: <info> Activation (ttyACM0) starting connection 'Cricket Communications connection 1'
Aug 24 09:18:39 APF2308 NetworkManager[531]: <info> (ttyACM0): device state change: 3 -> 4 (reason 0)
Aug 24 09:18:39 APF2308 NetworkManager[531]: <info> Activation (ttyACM0) Stage 1 of 5 (Device Prepare) scheduled...
Aug 24 09:18:39 APF2308 NetworkManager[531]: <info> Activation (ttyACM0) Stage 1 of 5 (Device Prepare) started...
Aug 24 09:18:39 APF2308 NetworkManager[531]: <info> Activation (ttyACM0) Stage 1 of 5 (Device Prepare) complete.
Aug 24 09:18:39 APF2308 NetworkManager[531]: <warn> CDMA connection failed: (32) Could not parse Serving System results.
Aug 24 09:18:39 APF2308 NetworkManager[531]: <info> (ttyACM0): device state change: 4 -> 9 (reason 0)
Aug 24 09:18:39 APF2308 NetworkManager[531]: <info> Marking connection 'Cricket Communications connection 1' invalid.
Aug 24 09:18:39 APF2308 NetworkManager[531]: <warn> Activation (ttyACM0) failed.
Aug 24 09:18:39 APF2308 NetworkManager[531]: <info> (ttyACM0): device state change: 9 -> 3 (reason 0)
Aug 24 09:18:39 APF2308 NetworkManager[531]: <info> (ttyACM0): deactivating device (reason: 0).
Aug 24 09:18:40 APF2308 NetworkManager[531]:    keyfile: updating /etc/NetworkManager/system-connections/Cricket Communications connection 1
Aug 24 09:18:43 APF2308 NetworkManager[531]: <info> Activation (ttyACM0) starting connection 'Cricket Communications connection 1'
Aug 24 09:18:43 APF2308 NetworkManager[531]: <info> (ttyACM0): device state change: 3 -> 4 (reason 0)
Aug 24 09:18:43 APF2308 NetworkManager[531]: <info> Activation (ttyACM0) Stage 1 of 5 (Device Prepare) scheduled...
Aug 24 09:18:43 APF2308 NetworkManager[531]: <info> Activation (ttyACM0) Stage 1 of 5 (Device Prepare) started...
Aug 24 09:18:43 APF2308 NetworkManager[531]: <info> Activation (ttyACM0) Stage 1 of 5 (Device Prepare) complete.
Aug 24 09:18:43 APF2308 NetworkManager[531]: <warn> CDMA connection failed: (32) Could not parse Serving System results.
Aug 24 09:18:43 APF2308 NetworkManager[531]: <info> (ttyACM0): device state change: 4 -> 9 (reason 0)
Aug 24 09:18:43 APF2308 NetworkManager[531]: <info> Marking connection 'Cricket Communications connection 1' invalid.
Aug 24 09:18:43 APF2308 NetworkManager[531]: <warn> Activation (ttyACM0) failed.
Aug 24 09:18:43 APF2308 NetworkManager[531]: <info> (ttyACM0): device state change: 9 -> 3 (reason 0)
Aug 24 09:18:43 APF2308 NetworkManager[531]: <info> (ttyACM0): deactivating device (reason: 0).
Aug 24 09:18:50 APF2308 kernel: [ 1680.616170] usb 2-1: USB disconnect, address 3
Aug 24 09:18:50 APF2308 modem-manager[554]: <info>  (ttyACM0) closing serial port...
Aug 24 09:18:50 APF2308 modem-manager[554]: <info>  (ttyACM0) serial port closed
Aug 24 09:18:50 APF2308 modem-manager[554]: <info>  (tty/ttyACM0): released by modem /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1
Aug 24 09:18:50 APF2308 modem-manager[554]: <info>  Modem /org/freedesktop/ModemManager/Modems/0: state changed (enabled -> disabled)
Aug 24 09:18:50 APF2308 NetworkManager[531]: <info> (ttyACM0): now unmanaged
Aug 24 09:18:50 APF2308 NetworkManager[531]: <info> (ttyACM0): device state change: 3 -> 1 (reason 36)
Aug 24 09:18:50 APF2308 NetworkManager[531]: <info> (ttyACM0): cleaning up...
Aug 24 09:18:50 APF2308 NetworkManager[531]: <info> (ttyACM0): taking down device.
Aug 24 09:18:50 APF2308 NetworkManager[531]: <info> Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
Aug 24 09:18:50 APF2308 NetworkManager[531]: <info> Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889))
Aug 24 09:35:57 APF2308 kernel: [ 2707.732077] usb 2-2: new full speed USB device using uhci_hcd and address 4
Aug 24 09:35:58 APF2308 kernel: [ 2707.895838] scsi7 : usb-storage 2-2:1.0
Aug 24 09:35:58 APF2308 usb_modeswitch: switching 19d2:ffe6 (ACTScom  Co.  Limited : USB Micro SD Storage)
Aug 24 09:35:59 APF2308 kernel: [ 2709.816207] usb 2-2: USB disconnect, address 4
Aug 24 09:36:06 APF2308 kernel: [ 2716.144113] usb 2-2: new full speed USB device using uhci_hcd and address 5
Aug 24 09:36:06 APF2308 kernel: [ 2716.310737] cdc_acm 2-2:1.0: ttyACM0: USB ACM device
Aug 24 09:36:06 APF2308 kernel: [ 2716.343395] scsi8 : usb-storage 2-2:1.6
Aug 24 09:36:06 APF2308 usb_modeswitch: switched to 19d2:ffe5 (ACTScom  Co.  Limited : ACTScom  CDMA USB Modem A605  )
Aug 24 09:36:06 APF2308 modem-manager[554]: <info>  (ttyACM0) opening serial port...
Aug 24 09:36:07 APF2308 kernel: [ 2717.352575] scsi 8:0:0:0: Direct-Access     ACTScom  T-Flash Disk     2.31 PQ: 0 ANSI: 2
Aug 24 09:36:07 APF2308 kernel: [ 2717.355572] sd 8:0:0:0: Attached scsi generic sg2 type 0
Aug 24 09:36:07 APF2308 kernel: [ 2717.372555] sd 8:0:0:0: [sdc] Attached SCSI removable disk
Aug 24 09:36:14 APF2308 modem-manager[554]: <info>  (ttyACM0) closing serial port...
Aug 24 09:36:14 APF2308 modem-manager[554]: <info>  (ttyACM0) serial port closed
Aug 24 09:36:14 APF2308 modem-manager[554]: <info>  (ttyACM0) opening serial port...
Aug 24 09:36:14 APF2308 modem-manager[554]: <info>  (ZTE): CDMA modem /sys/devices/pci0000:00/0000:00:1d.0/usb2/2-2 claimed port ttyACM0
Aug 24 09:36:14 APF2308 modem-manager[554]: <info>  (ttyACM0) closing serial port...
Aug 24 09:36:14 APF2308 modem-manager[554]: <info>  (ttyACM0) serial port closed
Aug 24 09:36:14 APF2308 NetworkManager[531]: <warn> (ttyACM0): failed to look up interface index
Aug 24 09:36:14 APF2308 NetworkManager[531]: <info> WWAN now disabled by management service
Aug 24 09:36:14 APF2308 NetworkManager[531]: <info> (ttyACM0): new CDMA device (driver: 'cdc_acm' ifindex: -1)
Aug 24 09:36:14 APF2308 NetworkManager[531]: <info> (ttyACM0): exported as /org/freedesktop/NetworkManager/Devices/3
Aug 24 09:36:14 APF2308 NetworkManager[531]: <info> (ttyACM0): now managed
Aug 24 09:36:14 APF2308 NetworkManager[531]: <info> (ttyACM0): device state change: 1 -> 2 (reason 2)
Aug 24 09:36:14 APF2308 NetworkManager[531]: <info> (ttyACM0): deactivating device (reason: 2).
Aug 24 09:36:14 APF2308 NetworkManager[531]: <info> (ttyACM0): device state change: 2 -> 3 (reason 0)
Aug 24 09:36:18 APF2308 NetworkManager[531]: <info> Activation (ttyACM0) starting connection 'Cricket Communications connection 1'
Aug 24 09:36:18 APF2308 NetworkManager[531]: <info> (ttyACM0): device state change: 3 -> 4 (reason 0)
Aug 24 09:36:18 APF2308 NetworkManager[531]: <info> Activation (ttyACM0) Stage 1 of 5 (Device Prepare) scheduled...
Aug 24 09:36:18 APF2308 NetworkManager[531]: <info> Activation (ttyACM0) Stage 1 of 5 (Device Prepare) started...
Aug 24 09:36:18 APF2308 NetworkManager[531]: <info> Activation (ttyACM0) Stage 1 of 5 (Device Prepare) complete.
Aug 24 09:36:18 APF2308 modem-manager[554]: <info>  (ttyACM0) opening serial port...
Aug 24 09:36:18 APF2308 modem-manager[554]: <info>  Modem /org/freedesktop/ModemManager/Modems/1: state changed (disabled -> enabling)
Aug 24 09:36:18 APF2308 modem-manager[554]: <info>  Modem /org/freedesktop/ModemManager/Modems/1: state changed (enabling -> enabled)
Aug 24 09:36:18 APF2308 NetworkManager[531]: <info> WWAN now enabled by management service
Aug 24 09:36:19 APF2308 NetworkManager[531]: <warn> CDMA connection failed: (32) Could not parse Serving System results.
Aug 24 09:36:19 APF2308 NetworkManager[531]: <info> (ttyACM0): device state change: 4 -> 9 (reason 0)
Aug 24 09:36:19 APF2308 NetworkManager[531]: <info> Marking connection 'Cricket Communications connection 1' invalid.
Aug 24 09:36:19 APF2308 NetworkManager[531]: <warn> Activation (ttyACM0) failed.
Aug 24 09:36:19 APF2308 NetworkManager[531]: <info> (ttyACM0): device state change: 9 -> 3 (reason 0)
Aug 24 09:36:19 APF2308 NetworkManager[531]: <info> (ttyACM0): deactivating device (reason: 0).
Aug 24 09:36:53 APF2308 NetworkManager[531]: <info> Activation (ttyACM0) starting connection 'Cricket Communications connection 1'
Aug 24 09:36:53 APF2308 NetworkManager[531]: <info> (ttyACM0): device state change: 3 -> 4 (reason 0)
Aug 24 09:36:53 APF2308 NetworkManager[531]: <info> Activation (ttyACM0) Stage 1 of 5 (Device Prepare) scheduled...
Aug 24 09:36:53 APF2308 NetworkManager[531]: <info> Activation (ttyACM0) Stage 1 of 5 (Device Prepare) started...
Aug 24 09:36:53 APF2308 NetworkManager[531]: <info> Activation (ttyACM0) Stage 1 of 5 (Device Prepare) complete.
Aug 24 09:36:53 APF2308 NetworkManager[531]: <warn> CDMA connection failed: (32) Could not parse Serving System results.
Aug 24 09:36:53 APF2308 NetworkManager[531]: <info> (ttyACM0): device state change: 4 -> 9 (reason 0)
Aug 24 09:36:53 APF2308 NetworkManager[531]: <info> Marking connection 'Cricket Communications connection 1' invalid.
Aug 24 09:36:53 APF2308 NetworkManager[531]: <warn> Activation (ttyACM0) failed.
Aug 24 09:36:53 APF2308 NetworkManager[531]: <info> (ttyACM0): device state change: 9 -> 3 (reason 0)
Aug 24 09:36:53 APF2308 NetworkManager[531]: <info> (ttyACM0): deactivating device (reason: 0).
Aug 24 09:36:54 APF2308 NetworkManager[531]:    keyfile: updating /etc/NetworkManager/system-connections/Cricket Communications connection 1
Aug 24 09:36:57 APF2308 NetworkManager[531]: <info> Activation (ttyACM0) starting connection 'Cricket Communications connection 1'
Aug 24 09:36:57 APF2308 NetworkManager[531]: <info> (ttyACM0): device state change: 3 -> 4 (reason 0)
Aug 24 09:36:57 APF2308 NetworkManager[531]: <info> Activation (ttyACM0) Stage 1 of 5 (Device Prepare) scheduled...
Aug 24 09:36:57 APF2308 NetworkManager[531]: <info> Activation (ttyACM0) Stage 1 of 5 (Device Prepare) started...
Aug 24 09:36:57 APF2308 NetworkManager[531]: <info> Activation (ttyACM0) Stage 1 of 5 (Device Prepare) complete.
Aug 24 09:36:57 APF2308 NetworkManager[531]: <warn> CDMA connection failed: (32) Could not parse Serving System results.
Aug 24 09:36:57 APF2308 NetworkManager[531]: <info> (ttyACM0): device state change: 4 -> 9 (reason 0)
Aug 24 09:36:57 APF2308 NetworkManager[531]: <info> Marking connection 'Cricket Communications connection 1' invalid.
Aug 24 09:36:57 APF2308 NetworkManager[531]: <warn> Activation (ttyACM0) failed.
Aug 24 09:36:57 APF2308 NetworkManager[531]: <info> (ttyACM0): device state change: 9 -> 3 (reason 0)
Aug 24 09:36:57 APF2308 NetworkManager[531]: <info> (ttyACM0): deactivating device (reason: 0).
Aug 24 09:41:17 APF2308 NetworkManager[531]: <info> Activation (ttyACM0) starting connection 'Cricket Communications connection 1'
Aug 24 09:41:17 APF2308 NetworkManager[531]: <info> (ttyACM0): device state change: 3 -> 4 (reason 0)
Aug 24 09:41:17 APF2308 NetworkManager[531]: <info> Activation (ttyACM0) Stage 1 of 5 (Device Prepare) scheduled...
Aug 24 09:41:17 APF2308 NetworkManager[531]: <info> Activation (ttyACM0) Stage 1 of 5 (Device Prepare) started...
Aug 24 09:41:17 APF2308 NetworkManager[531]: <info> Activation (ttyACM0) Stage 1 of 5 (Device Prepare) complete.
Aug 24 09:41:18 APF2308 NetworkManager[531]: <warn> CDMA connection failed: (32) Could not parse Serving System results.
Aug 24 09:41:18 APF2308 NetworkManager[531]: <info> (ttyACM0): device state change: 4 -> 9 (reason 0)
Aug 24 09:41:18 APF2308 NetworkManager[531]: <info> Marking connection 'Cricket Communications connection 1' invalid.
Aug 24 09:41:18 APF2308 NetworkManager[531]: <warn> Activation (ttyACM0) failed.
Aug 24 09:41:18 APF2308 NetworkManager[531]: <info> (ttyACM0): device state change: 9 -> 3 (reason 0)
Aug 24 09:41:18 APF2308 NetworkManager[531]: <info> (ttyACM0): deactivating device (reason: 0).
Aug 24 09:41:27 APF2308 NetworkManager[531]: <info> Activation (ttyACM0) starting connection 'Cricket Communications connection 1'
Aug 24 09:41:27 APF2308 NetworkManager[531]: <info> (ttyACM0): device state change: 3 -> 4 (reason 0)
Aug 24 09:41:27 APF2308 NetworkManager[531]: <info> Activation (ttyACM0) Stage 1 of 5 (Device Prepare) scheduled...
Aug 24 09:41:27 APF2308 NetworkManager[531]: <info> Activation (ttyACM0) Stage 1 of 5 (Device Prepare) started...
Aug 24 09:41:27 APF2308 NetworkManager[531]: <info> Activation (ttyACM0) Stage 1 of 5 (Device Prepare) complete.
Aug 24 09:41:27 APF2308 NetworkManager[531]: <warn> CDMA connection failed: (32) Could not parse Serving System results.
Aug 24 09:41:27 APF2308 NetworkManager[531]: <info> (ttyACM0): device state change: 4 -> 9 (reason 0)
Aug 24 09:41:27 APF2308 NetworkManager[531]: <info> Marking connection 'Cricket Communications connection 1' invalid.
Aug 24 09:41:27 APF2308 NetworkManager[531]: <warn> Activation (ttyACM0) failed.
Aug 24 09:41:27 APF2308 NetworkManager[531]: <info> (ttyACM0): device state change: 9 -> 3 (reason 0)
Aug 24 09:41:27 APF2308 NetworkManager[531]: <info> (ttyACM0): deactivating device (reason: 0).

---

