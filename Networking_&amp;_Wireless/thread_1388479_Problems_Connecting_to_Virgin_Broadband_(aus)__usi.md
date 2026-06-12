---
title: "Problems Connecting to Virgin Broadband (aus)  using Huawei E160e"
date: 2010-01-23
forum: Networking &amp; Wireless
---

### Post by damien_d on 2010-01-23
Hello all,

I am attempting to connect to Virgin Broadband (Australia) pre-paid using a Huawei E160e modem in Ubuntu 9.10 UNR.

I have setup the connection as per [http://ubuntuforums.org/showthread.php?t=1014221](http://ubuntuforums.org/showthread.php?t=1014221), including disabling CHAP and changing the APN as required in the thread.

However, when I try to connect using the network manager, it disconnects straight away with the message "GSM Network disconnected".

When examining the logs /var/log/daemon.log, I get the following information:

```

Jan 23 21:26:09 janet-laptop NetworkManager: <info>  Activation (ttyUSB0) starting connection 'Virgin Mobile'
Jan 23 21:26:09 janet-laptop NetworkManager: <info>  (ttyUSB0): device state change: 3 -> 4 (reason 0)
Jan 23 21:26:09 janet-laptop NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) scheduled...
Jan 23 21:26:09 janet-laptop NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) started...
Jan 23 21:26:09 janet-laptop NetworkManager: <info>  (ttyUSB0): device state change: 4 -> 6 (reason 0)
Jan 23 21:26:09 janet-laptop NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) complete.
Jan 23 21:26:09 janet-laptop NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) scheduled...
Jan 23 21:26:09 janet-laptop NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) started...
Jan 23 21:26:09 janet-laptop NetworkManager: <info>  (ttyUSB0): device state change: 6 -> 4 (reason 0)
Jan 23 21:26:09 janet-laptop NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) complete.
Jan 23 21:26:09 janet-laptop modem-manager: (ttyUSB0) opening serial device...
Jan 23 21:26:12 janet-laptop NetworkManager: <WARN>  stage1_prepare_done(): GSM modem connection failed: Serial command timed out
Jan 23 21:26:12 janet-laptop NetworkManager: <info>  (ttyUSB0): device state change: 4 -> 9 (reason 1)
Jan 23 21:26:12 janet-laptop NetworkManager: <info>  Marking connection 'Virgin Mobile' invalid.
Jan 23 21:26:12 janet-laptop NetworkManager: <info>  Activation (ttyUSB0) failed.
Jan 23 21:26:12 janet-laptop NetworkManager: <info>  (ttyUSB0): device state change: 9 -> 3 (reason 0)
Jan 23 21:26:12 janet-laptop NetworkManager: <info>  (ttyUSB0): deactivating device (reason: 0).
Jan 23 21:26:12 janet-laptop NetworkManager: flush_routes: assertion `iface_idx >= 0' failed
Jan 23 21:26:12 janet-laptop NetworkManager: flush_addresses: assertion `iface_idx >= 0' failed
Jan 23 21:26:12 janet-laptop modem-manager: (ttyUSB0) closing serial device...
Jan 23 21:27:54 janet-laptop wpa_supplicant[921]: CTRL-EVENT-SCAN-RESULTS 
Jan 23 21:29:54 janet-laptop wpa_supplicant[921]: CTRL-EVENT-SCAN-RESULTS

```

And attempting again:

```
 
Jan 23 21:31:31 janet-laptop NetworkManager: <info>  Activation (ttyUSB0) starting connection 'Virgin Mobile'
Jan 23 21:31:31 janet-laptop NetworkManager: <info>  (ttyUSB0): device state change: 3 -> 4 (reason 0)
Jan 23 21:31:31 janet-laptop NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) scheduled...
Jan 23 21:31:31 janet-laptop NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) started...
Jan 23 21:31:31 janet-laptop NetworkManager: <info>  (ttyUSB0): device state change: 4 -> 6 (reason 0)
Jan 23 21:31:31 janet-laptop NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) complete.
Jan 23 21:31:31 janet-laptop NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) scheduled...
Jan 23 21:31:31 janet-laptop NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) started...
Jan 23 21:31:31 janet-laptop NetworkManager: <info>  (ttyUSB0): device state change: 6 -> 4 (reason 0)
Jan 23 21:31:31 janet-laptop NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) complete.
Jan 23 21:31:31 janet-laptop modem-manager: (ttyUSB0) opening serial device...
Jan 23 21:31:32 janet-laptop modem-manager: Got failure code 100: Unknown error
Jan 23 21:31:32 janet-laptop NetworkManager: <WARN>  stage1_prepare_done(): GSM modem connection failed: Unknown error
Jan 23 21:31:32 janet-laptop NetworkManager: <info>  (ttyUSB0): device state change: 4 -> 9 (reason 1)
Jan 23 21:31:32 janet-laptop NetworkManager: <info>  Marking connection 'Virgin Mobile' invalid.
Jan 23 21:31:32 janet-laptop NetworkManager: <info>  Activation (ttyUSB0) failed.
Jan 23 21:31:32 janet-laptop NetworkManager: <info>  (ttyUSB0): device state change: 9 -> 3 (reason 0)
Jan 23 21:31:32 janet-laptop NetworkManager: <info>  (ttyUSB0): deactivating device (reason: 0).
Jan 23 21:31:32 janet-laptop NetworkManager: flush_routes: assertion `iface_idx >= 0' failed
Jan 23 21:31:32 janet-laptop NetworkManager: flush_addresses: assertion `iface_idx >= 0' failed
Jan 23 21:31:32 janet-laptop modem-manager: (ttyUSB0) closing serial device...

```

Since the error message changed, I attempted a third time:
```

Jan 23 21:40:07 janet-laptop NetworkManager: <info>  Activation (ttyUSB0) starting connection 'Virgin Mobile'
Jan 23 21:40:07 janet-laptop NetworkManager: <info>  (ttyUSB0): device state change: 3 -> 4 (reason 0)
Jan 23 21:40:07 janet-laptop NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) scheduled...
Jan 23 21:40:07 janet-laptop NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) started...
Jan 23 21:40:07 janet-laptop NetworkManager: <info>  (ttyUSB0): device state change: 4 -> 6 (reason 0)
Jan 23 21:40:07 janet-laptop NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) complete.
Jan 23 21:40:07 janet-laptop NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) scheduled...
Jan 23 21:40:07 janet-laptop NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) started...
Jan 23 21:40:07 janet-laptop NetworkManager: <info>  (ttyUSB0): device state change: 6 -> 4 (reason 0)
Jan 23 21:40:07 janet-laptop NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) complete.
Jan 23 21:40:07 janet-laptop modem-manager: (ttyUSB0) opening serial device...
Jan 23 21:40:10 janet-laptop NetworkManager: <WARN>  stage1_prepare_done(): GSM modem connection failed: Serial command timed out
Jan 23 21:40:10 janet-laptop NetworkManager: <info>  (ttyUSB0): device state change: 4 -> 9 (reason 1)
Jan 23 21:40:10 janet-laptop NetworkManager: <info>  Marking connection 'Virgin Mobile' invalid.
Jan 23 21:40:10 janet-laptop NetworkManager: <info>  Activation (ttyUSB0) failed.
Jan 23 21:40:10 janet-laptop NetworkManager: <info>  (ttyUSB0): device state change: 9 -> 3 (reason 0)
Jan 23 21:40:10 janet-laptop NetworkManager: <info>  (ttyUSB0): deactivating device (reason: 0).
Jan 23 21:40:10 janet-laptop NetworkManager: flush_routes: assertion `iface_idx >= 0' failed
Jan 23 21:40:10 janet-laptop NetworkManager: flush_addresses: assertion `iface_idx >= 0' failed
Jan 23 21:40:10 janet-laptop modem-manager: (ttyUSB0) closing serial device...

```

It seems to be having problems communicating on the virtual serial port... ?

If it at all helps, the modem doesn't quite come up with the model expected:
```

Bus 001 Device 008: ID 12d1:1003 Huawei Technologies Co., Ltd. E220 HSDPA Modem / E270 HSDPA/HSUPA Modem

```

I have connected the device before on a Netgear 3G router, and I have some vague recollection that I tested on another Ubuntu laptop, but don't quote me on the latter.

Yes, I have credit remaining on the network, and the blue light is flashing once every couple of seconds.

I am using kernel:

```

janet@janet-laptop:~$ uname -r
2.6.31-17-generic
janet@janet-laptop:~$ uname -a
Linux janet-laptop 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 16:20:31 UTC 2009 i686 GNU/Linux

```

The device appears to have registered itself properly with the kernel.
```

[ 2079.952205] usb 1-2: new high speed USB device using ehci_hcd and address 7
[ 2080.095807] usb 1-2: configuration #1 chosen from 1 choice
[ 2080.110922] scsi11 : SCSI emulation for USB Mass Storage devices
[ 2080.112999] usb 1-2: USB disconnect, address 7
[ 2080.112999] usb-storage: device found at 7
[ 2080.112999] usb-storage: waiting for device to settle before scanning
[ 2086.696123] usb 1-2: new high speed USB device using ehci_hcd and address 8
[ 2086.839805] usb 1-2: configuration #1 chosen from 1 choice
[ 2086.855039] option 1-2:1.0: GSM modem (1-port) converter detected
[ 2086.855273] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB0
[ 2086.855622] option 1-2:1.1: GSM modem (1-port) converter detected
[ 2086.855782] usb 1-2: GSM modem (1-port) converter now attached to ttyUSB1
[ 2086.869864] scsi14 : SCSI emulation for USB Mass Storage devices
[ 2086.872306] usb-storage: device found at 8
[ 2086.872314] usb-storage: waiting for device to settle before scanning
[ 2086.880654] scsi15 : SCSI emulation for USB Mass Storage devices
[ 2086.880973] usb-storage: device found at 8
[ 2086.880973] usb-storage: waiting for device to settle before scanning
[ 2091.869712] usb-storage: device scan complete
[ 2091.871641] scsi 14:0:0:0: CD-ROM            HUAWEI   Mass Storage     2.31 PQ: 0 ANSI: 2
[ 2091.882758] usb-storage: device scan complete
[ 2091.884910] scsi 15:0:0:0: Direct-Access     HUAWEI   MMC Storage      2.31 PQ: 0 ANSI: 2
[ 2091.900328] sr0: scsi-1 drive
[ 2091.900578] sr 14:0:0:0: Attached scsi CD-ROM sr0
[ 2091.900735] sr 14:0:0:0: Attached scsi generic sg1 type 5
[ 2091.901399] sd 15:0:0:0: Attached scsi generic sg2 type 0
[ 2091.920461] sd 15:0:0:0: [sdb] Attached SCSI removable disk
[ 2104.968852] ISO 9660 Extensions: Microsoft Joliet Level 1
[ 2104.971872] ISOFS: changing to secondary root

```


Any tips to what I should do next?

---

### Post by d3v1150m471c on 2010-01-23
right-click the network applet on your panel. edit connections, navigate to the mobile broadband tab. follow your nose and set it to automatically connect. unplug the device and plug it back in. It should work.

---

### Post by damien_d on 2010-01-23
> **d3v1150m471c said:**
> right-click the network applet on your panel. edit connections, navigate to the mobile broadband tab. follow your nose and set it to automatically connect. unplug the device and plug it back in. It should work.

Unfortunately not.  I also attempted to do so again after a reboot, but no such luck.

However, the errors this time are much more interesting...

```

Jan 23 22:26:38 janet-laptop modem-manager: (Huawei): (ttyUSB1) deferring support check
Jan 23 22:26:38 janet-laptop modem-manager: (ttyUSB0) opening serial device...
Jan 23 22:26:38 janet-laptop modem-manager: (ttyUSB0): probe requested by plugin 'Huawei'
Jan 23 22:26:39 janet-laptop modem-manager: (ttyUSB0) closing serial device...
Jan 23 22:26:39 janet-laptop modem-manager: (Huawei): GSM modem /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-2 claimed port ttyUSB0
Jan 23 22:26:39 janet-laptop modem-manager: Added modem /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-2
Jan 23 22:26:39 janet-laptop modem-manager: Exported modem /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-2 as /org/freedesktop/ModemManager/Modems/0
Jan 23 22:26:39 janet-laptop NetworkManager: <info>  (ttyUSB0): new GSM device (driver: 'option1')
Jan 23 22:26:39 janet-laptop NetworkManager: <info>  (ttyUSB0): exported as /org/freedesktop/NetworkManager/Devices/2
Jan 23 22:26:39 janet-laptop NetworkManager: <info>  (ttyUSB0): now managed
Jan 23 22:26:39 janet-laptop NetworkManager: <info>  (ttyUSB0): device state change: 1 -> 2 (reason 2)
Jan 23 22:26:39 janet-laptop NetworkManager: <info>  (ttyUSB0): deactivating device (reason: 2).
Jan 23 22:26:39 janet-laptop NetworkManager: flush_routes: assertion `iface_idx >= 0' failed
Jan 23 22:26:39 janet-laptop NetworkManager: flush_addresses: assertion `iface_idx >= 0' failed
Jan 23 22:26:39 janet-laptop NetworkManager: <info>  (ttyUSB0): device state change: 2 -> 3 (reason 0)
Jan 23 22:26:39 janet-laptop NetworkManager: <info>  Activation (ttyUSB0) starting connection 'Virgin Mobile'
Jan 23 22:26:39 janet-laptop NetworkManager: <info>  (ttyUSB0): device state change: 3 -> 4 (reason 0)
Jan 23 22:26:39 janet-laptop NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) scheduled...
Jan 23 22:26:39 janet-laptop NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) started...
Jan 23 22:26:39 janet-laptop NetworkManager: <info>  (ttyUSB0): device state change: 4 -> 6 (reason 0)
Jan 23 22:26:39 janet-laptop NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) complete.
Jan 23 22:26:39 janet-laptop NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) scheduled...
Jan 23 22:26:39 janet-laptop NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) started...
Jan 23 22:26:39 janet-laptop NetworkManager: <info>  (ttyUSB0): device state change: 6 -> 4 (reason 0)
Jan 23 22:26:39 janet-laptop NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) complete.
Jan 23 22:26:39 janet-laptop modem-manager: (ttyUSB0) opening serial device...
Jan 23 22:26:40 janet-laptop wpa_supplicant[864]: CTRL-EVENT-SCAN-RESULTS 
Jan 23 22:26:41 janet-laptop modem-manager: Registration state changed: 2
Jan 23 22:26:41 janet-laptop modem-manager: (ttyUSB1): re-checking support...
Jan 23 22:26:41 janet-laptop modem-manager: (ttyUSB1) opening serial device...
Jan 23 22:26:41 janet-laptop modem-manager: (ttyUSB1) closing serial device...
Jan 23 22:26:41 janet-laptop modem-manager: (Huawei): GSM modem /sys/devices/pci0000:00/0000:00:1d.7/usb1/1-2 claimed port ttyUSB1
Jan 23 22:26:42 janet-laptop modem-manager: Registration state changed: 1
Jan 23 22:26:42 janet-laptop NetworkManager: <info>  Activation (ttyUSB0) Stage 2 of 5 (Device Configure) scheduled...
Jan 23 22:26:42 janet-laptop NetworkManager: <info>  Activation (ttyUSB0) Stage 2 of 5 (Device Configure) starting...
Jan 23 22:26:42 janet-laptop NetworkManager: <info>  (ttyUSB0): device state change: 4 -> 5 (reason 0)
Jan 23 22:26:42 janet-laptop NetworkManager: <info>  Activation (ttyUSB0) Stage 2 of 5 (Device Configure) successful.
Jan 23 22:26:42 janet-laptop NetworkManager: <info>  Activation (ttyUSB0) Stage 3 of 5 (IP Configure Start) scheduled.
Jan 23 22:26:42 janet-laptop NetworkManager: <info>  Activation (ttyUSB0) Stage 2 of 5 (Device Configure) complete.
Jan 23 22:26:42 janet-laptop NetworkManager: <info>  Activation (ttyUSB0) Stage 3 of 5 (IP Configure Start) started...
Jan 23 22:26:42 janet-laptop NetworkManager: <info>  (ttyUSB0): device state change: 5 -> 7 (reason 0)
Jan 23 22:26:42 janet-laptop NetworkManager: <info>  Starting pppd connection
Jan 23 22:26:42 janet-laptop NetworkManager: <debug> [1264249602.184115] nm_ppp_manager_start(): Command line: /usr/sbin/pppd nodetach lock nodefaultroute user blank ttyUSB0 noipdefault noauth refuse-chap refuse-mschap refuse-mschap-v2 usepeerdns lcp-echo-failure 0 lcp-echo-interval 0 ipparam /org/freedesktop/NetworkManager/PPP/0 plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so
Jan 23 22:26:42 janet-laptop NetworkManager: <debug> [1264249602.194194] nm_ppp_manager_start(): ppp started with pid 1977
Jan 23 22:26:42 janet-laptop NetworkManager: <info>  Activation (ttyUSB0) Stage 4 of 5 (IP6 Configure Get) scheduled...
Jan 23 22:26:42 janet-laptop NetworkManager: <info>  Activation (ttyUSB0) Stage 3 of 5 (IP Configure Start) complete.
Jan 23 22:26:42 janet-laptop NetworkManager: <info>  Activation (ttyUSB0) Stage 4 of 5 (IP6 Configure Get) started...
Jan 23 22:26:42 janet-laptop NetworkManager: <info>  Activation (ttyUSB0) Stage 4 of 5 (IP6 Configure Get) complete.
Jan 23 22:26:42 janet-laptop NetworkManager: <WARN>  ppp_exit_code(): ppp pid 1977 exited with error: pppd options error
Jan 23 22:26:42 janet-laptop NetworkManager: <debug> [1264249602.221765] ppp_watch_cb(): ppp pid 1977 cleaned up
Jan 23 22:26:42 janet-laptop NetworkManager: <info>  (ttyUSB0): device state change: 7 -> 9 (reason 14)
Jan 23 22:26:42 janet-laptop NetworkManager: <info>  Marking connection 'Virgin Mobile' invalid.
Jan 23 22:26:42 janet-laptop NetworkManager: <info>  Activation (ttyUSB0) failed.
Jan 23 22:26:42 janet-laptop NetworkManager: <info>  (ttyUSB0): device state change: 9 -> 3 (reason 0)
Jan 23 22:26:42 janet-laptop NetworkManager: <info>  (ttyUSB0): deactivating device (reason: 0).
Jan 23 22:26:42 janet-laptop NetworkManager: flush_routes: assertion `iface_idx >= 0' failed
Jan 23 22:26:42 janet-laptop NetworkManager: flush_addresses: assertion `iface_idx >= 0' failed
Jan 23 22:26:43 janet-laptop modem-manager: (ttyUSB0) closing serial device...

```

Looks like ppp is complaining this time.

---

### Post by Holmen on 2010-01-26
I got the same problem, but with a Huawei E182E and the '3' operator.

---

### Post by pdc on 2010-01-27
hi damien_d;

sorry to hear of your issues with Virgin Australia;

see post #14 here; 

[http://ubuntuforums.org/showthread.php?t=1354619&page=2](http://ubuntuforums.org/showthread.php?t=1354619&page=2)

mjneil reported success with Ubuntu 9.04; and Virgin Oz

maybe if you check each step he detailed; he does seem to continue to follow the forums, so may be help you

you might even have to contemplate installing 9.04 on a small partition on your system to access the internet: it is less than 1G install 

sorry; this may be identical to what you followed

my only other suggestion would be to use wvdial; 

I use that with a ZTE modem and find it very reliable; 

I don't use network manager for the ZTE: wvdial is very fast to connect

---

### Post by damien_d on 2010-04-11
Today I did a clean install of 9.10 on the machine in question and it worked right away after the VirginInternet -> VirginBroadband change and the uncheck CHAP change.

No idea why it was broken before the re-install...


  -- Damien

---

### Post by pdc on 2010-04-11
well done; glad to hear it is working well; enjoy!

---

