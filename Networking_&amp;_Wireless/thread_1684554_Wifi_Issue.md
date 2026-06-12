---
title: "Wifi Issue"
date: 2011-02-09
forum: Networking &amp; Wireless
---

### Post by lombartm on 2011-02-09
Im 99% sure this is an issue with my schools network and not ubuntu but if anyone has any ideas as to what is happening Id appreciate it. After I log onto my schools wifi Im disconnected after about 15 minutes and I have to logon again. Any ideas why this is happening. Here is a copy of my log file.

Feb  9 09:33:23 Latitude-D630 kernel: [  381.987831] sr 4:0:0:1: Attached scsi generic sg3 type 5
Feb  9 09:33:26 Latitude-D630 kernel: [  384.794030] sd 4:0:0:0: [sdb] 31116288 512-byte logical blocks: (15.9 GB/14.8 GiB)
Feb  9 09:33:26 Latitude-D630 kernel: [  384.796746]  sdb: sdb1
Feb  9 09:33:28 Latitude-D630 kernel: [  387.033925] iwl3945 0000:0c:00.0: Card state received: HW:Kill SW:On
Feb  9 09:33:28 Latitude-D630 kernel: [  387.034126] iwl3945 0000:0c:00.0: Not sending command - RF KILL
Feb  9 09:33:28 Latitude-D630 kernel: [  387.034149] iwl3945 0000:0c:00.0: Not sending command - RF KILL
Feb  9 09:33:28 Latitude-D630 kernel: [  387.034169] iwl3945 0000:0c:00.0: Not sending command - RF KILL
Feb  9 09:33:28 Latitude-D630 kernel: [  387.034190] iwl3945 0000:0c:00.0: Not sending command - RF KILL
Feb  9 09:33:28 Latitude-D630 kernel: [  387.041071] iwl3945 0000:0c:00.0: Not sending command - RF KILL
Feb  9 09:33:28 Latitude-D630 kernel: [  387.049144] usb 3-2: USB disconnect, address 2
Feb  9 09:33:28 Latitude-D630 kernel: [  387.109183] cfg80211: Calling CRDA to update world regulatory domain
Feb  9 09:33:28 Latitude-D630 kernel: [  387.113317] cfg80211: World regulatory domain updated:
Feb  9 09:33:28 Latitude-D630 kernel: [  387.113320]     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Feb  9 09:33:28 Latitude-D630 kernel: [  387.113323]     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Feb  9 09:33:28 Latitude-D630 kernel: [  387.113325]     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Feb  9 09:33:28 Latitude-D630 kernel: [  387.113328]     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Feb  9 09:33:28 Latitude-D630 kernel: [  387.113330]     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Feb  9 09:33:28 Latitude-D630 kernel: [  387.113333]     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Feb  9 09:33:32 Latitude-D630 kernel: [  390.744803] usb 3-2: new full speed USB device using uhci_hcd and address 3
Feb  9 09:33:32 Latitude-D630 kernel: [  391.193146] ADDRCONF(NETDEV_UP): wlan0: link is not ready
Feb  9 09:33:34 Latitude-D630 kernel: [  392.815714] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

---

### Post by herdwick on 2011-02-09
Feb 9 09:33:28 Latitude-D630 kernel: [ 387.033925] iwl3945 0000:0c:00.0: Card state received: HW:Kill SW:On

searching for "Card state received: HW:Kill SW:On" throws up plenty of reading - hardware switch ? Fn Key press ? power saving turning device off ?

---

