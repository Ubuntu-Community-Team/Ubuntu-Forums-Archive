---
title: "Reliance ZTE EVDO USB dongle"
date: 2012-11-24
forum: Networking &amp; Wireless
---

### Post by vset on 2012-11-24
I configured the EVDO datacard on ubuntu 12.10, it worked like magic the first time. After restart the error I get is

(1) Creating object for path '/org/freedesktop/NetworkManager/ActiveConnection/1' failed in libnm-glib.

Need Help to correct it.
the lsusb output is
Bus 002 Device 002: ID 064e:e201 Suyin Corp. Lenovo Integrated Webcam
Bus 006 Device 003: ID 19d2:fff1 ZTE WCDMA Technologies MSM 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bput us 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

The dmesg output
lt5@lt2:~$ dmesg | tail -n 100
[ 1448.370412] type=1701 audit(1353762736.780:199): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=3587 comm="chrome" reason="seccomp" sig=0 syscall=2 compat=0 ip=0x7f8e83f326b0 code=0x50000
[ 1448.372928] type=1701 audit(1353762736.784:200): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=3593 comm="chrome" reason="seccomp" sig=0 syscall=59 compat=0 ip=0x7f8e83f0bc27 code=0x50000
[ 1489.655225] wlan0: deauthenticating from 80:a1:d7:c0:fa:27 by local choice (reason=3)
[ 1489.677647] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 1489.677657] cfg80211: Restoring regulatory settings
[ 1489.677665] cfg80211: Calling CRDA to update world regulatory domain
[ 1489.961732] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[ 1489.961738] cfg80211: World regulatory domain updated:
[ 1489.961741] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1489.961744] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1489.961748] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1489.961751] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1489.961754] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1489.961757] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1499.564821] wlan0: authenticate with 80:a1:d7:c0:fa:27
[ 1499.592148] wlan0: send auth to 80:a1:d7:c0:fa:27 (try 1/3)
[ 1499.594822] wlan0: authenticated
[ 1499.608042] wlan0: associate with 80:a1:d7:c0:fa:27 (try 1/3)
[ 1499.610124] wlan0: RX AssocResp from 80:a1:d7:c0:fa:27 (capab=0x421 status=0 aid=1)
[ 1499.611137] wlan0: associated
[ 1499.611981] cfg80211: Calling CRDA for country: IN
[ 1499.618560] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[ 1499.618567] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1499.618571] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[ 1499.618575] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1499.618578] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[ 1499.618582] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1499.618585] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[ 1499.618589] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1499.618592] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[ 1499.618596] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1499.618599] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[ 1499.618603] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1499.618606] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[ 1499.618610] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1499.618613] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[ 1499.618617] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1499.618620] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[ 1499.618624] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1499.618627] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[ 1499.618631] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1499.618634] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[ 1499.618637] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1499.618640] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[ 1499.618644] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1499.618647] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[ 1499.618651] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 1499.618654] cfg80211: Disabling freq 2484 MHz
[ 1499.618661] cfg80211: Regulatory domain changed to country: IN
[ 1499.618663] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1499.618667] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 1499.618671] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 1499.618674] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 1499.618677] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 1500.224282] usb 6-2: new full-speed USB device number 5 using uhci_hcd
[ 1500.445133] usb 6-2: New USB device found, idVendor=19d2, idProduct=fff5
[ 1500.445144] usb 6-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 1500.445151] usb 6-2: Product: USB Storage
[ 1500.445158] usb 6-2: Manufacturer: ZTE, Incorporated
[ 1500.445163] usb 6-2: SerialNumber: 000000000002
[ 1500.448917] scsi10 : usb-storage 6-2:1.0
[ 1501.453180] scsi 10:0:0:0: CD-ROM            ZTE      USB Storage FFF1 2.31 PQ: 0 ANSI: 2
[ 1501.456221] scsi 10:0:0:1: Direct-Access     ZTE      USB Storage FFF1 2.31 PQ: 0 ANSI: 2
[ 1501.475174] sr0: scsi-1 drive
[ 1501.475704] sr 10:0:0:0: Attached scsi CD-ROM sr0
[ 1501.478216] sr 10:0:0:0: Attached scsi generic sg1 type 5
[ 1501.479019] sd 10:0:0:1: Attached scsi generic sg2 type 0
[ 1501.502142] sd 10:0:0:1: [sdb] Attached SCSI removable disk
[ 1502.784214] usb 6-2: USB disconnect, device number 5
[ 1504.264158] usb 6-2: new full-speed USB device number 6 using uhci_hcd
[ 1504.427112] usb 6-2: New USB device found, idVendor=19d2, idProduct=fff1
[ 1504.427120] usb 6-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 1504.427124] usb 6-2: Product: ZTE CDMA Tech
[ 1504.427128] usb 6-2: Manufacturer: ZTE, Incorporated
[ 1504.433210] option 6-2:1.0: GSM modem (1-port) converter detected
[ 1504.433348] usb 6-2: GSM modem (1-port) converter now attached to ttyUSB0
[ 1504.435179] option 6-2:1.1: GSM modem (1-port) converter detected
[ 1504.435282] usb 6-2: GSM modem (1-port) converter now attached to ttyUSB1
[ 1504.437182] option 6-2:1.2: GSM modem (1-port) converter detected
[ 1504.437282] usb 6-2: GSM modem (1-port) converter now attached to ttyUSB2
[ 1504.439176] option 6-2:1.3: GSM modem (1-port) converter detected
[ 1504.439285] usb 6-2: GSM modem (1-port) converter now attached to ttyUSB3
[ 1504.441175] option 6-2:1.4: GSM modem (1-port) converter detected
[ 1504.441283] usb 6-2: GSM modem (1-port) converter now attached to ttyUSB4
[ 1504.441521] scsi11 : usb-storage 6-2:1.5
[ 1505.444129] scsi 11:0:0:0: Direct-Access     ZTE      USB Storage FFF1 2.31 PQ: 0 ANSI: 2
[ 1505.447500] sd 11:0:0:0: Attached scsi generic sg1 type 0
[ 1505.462120] sd 11:0:0:0: [sdb] Attached SCSI removable disk
[ 1576.206623] wlan0: deauthenticating from 80:a1:d7:c0:fa:27 by local choice (reason=3)
[ 1576.231905] cfg80211: All devices are disconnected, going to restore regulatory settings
[ 1576.231918] cfg80211: Restoring regulatory settings
[ 1576.231926] cfg80211: Calling CRDA to update world regulatory domain
[ 1576.240386] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[ 1576.240392] cfg80211: World regulatory domain updated:
[ 1576.240395] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 1576.240399] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1576.240402] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1576.240406] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 1576.240409] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 1576.240412] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)

---

