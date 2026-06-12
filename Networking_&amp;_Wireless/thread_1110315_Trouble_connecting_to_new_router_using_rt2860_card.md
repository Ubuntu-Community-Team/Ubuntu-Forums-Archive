---
title: "Trouble connecting to new router using rt2860 card and packaged DKMS driver"
date: 2009-03-29
forum: Networking &amp; Wireless
---

### Post by acreda on 2009-03-29
Hi All

Ive been using a Wifi N card with the Ralink rt2860 chipset. I have been using a packaged driver from Stéphane Graber ([https://launchpad.net/~stgraber/+archive/ppa](https://launchpad.net/~stgraber/+archive/ppa)) which is a ubuntu package for the current 1.8.0 driver from Ralink

It has been working fine on a standard 802.11G router with no drop offs at 54Mbs, working absoulutley fine:-

Changed my router to go 802.11n (2.0) and it seems to get stuck during handshaking with the wpasubaplicant

need to restart my browser but will continue soon............

Right back now, here is the deamon log listing what Network Manager is outputing...

Mar 29 22:05:40 Linux-CM690 NetworkManager: <info>  Activation (ra0) starting connection 'Auto Belkin_N+_437CDD' 
Mar 29 22:05:40 Linux-CM690 NetworkManager: <info>  (ra0): device state change: 3 -> 4 
Mar 29 22:05:40 Linux-CM690 NetworkManager: <info>  Activation (ra0) Stage 1 of 5 (Device Prepare) scheduled... 
Mar 29 22:05:40 Linux-CM690 NetworkManager: <info>  Activation (ra0) Stage 1 of 5 (Device Prepare) started... 
Mar 29 22:05:40 Linux-CM690 NetworkManager: <info>  Activation (ra0) Stage 2 of 5 (Device Configure) scheduled... 
Mar 29 22:05:40 Linux-CM690 NetworkManager: <info>  Activation (ra0) Stage 1 of 5 (Device Prepare) complete. 
Mar 29 22:05:40 Linux-CM690 NetworkManager: <info>  Activation (ra0) Stage 2 of 5 (Device Configure) starting... 
Mar 29 22:05:40 Linux-CM690 NetworkManager: <info>  (ra0): device state change: 4 -> 5 
Mar 29 22:05:40 Linux-CM690 NetworkManager: <info>  Activation (ra0/wireless): connection 'Auto Belkin_N+_437CDD' requires no security.  No secrets needed. 
Mar 29 22:05:40 Linux-CM690 NetworkManager: <info>  Config: added 'ssid' value 'Belkin_N+_437CDD' 
Mar 29 22:05:40 Linux-CM690 NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
Mar 29 22:05:40 Linux-CM690 NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE' 
Mar 29 22:05:40 Linux-CM690 NetworkManager: <info>  Activation (ra0) Stage 2 of 5 (Device Configure) complete. 
Mar 29 22:05:40 Linux-CM690 NetworkManager: <info>  Config: set interface ap_scan to 1 
Mar 29 22:05:40 Linux-CM690 NetworkManager: <info>  (ra0): supplicant connection state change: 1 -> 2 
Mar 29 22:05:45 Linux-CM690 NetworkManager: <info>  (ra0): supplicant connection state change: 2 -> 3 
Mar 29 22:05:55 Linux-CM690 NetworkManager: <info>  (ra0): supplicant connection state change: 3 -> 0 
Mar 29 22:05:55 Linux-CM690 NetworkManager: <info>  (ra0): supplicant connection state change: 0 -> 2 
Mar 29 22:06:01 Linux-CM690 NetworkManager: <info>  (ra0): supplicant connection state change: 2 -> 3 
Mar 29 22:06:10 Linux-CM690 NetworkManager: <info>  ra0: link timed out. 
Mar 29 22:06:11 Linux-CM690 NetworkManager: <info>  (ra0): supplicant connection state change: 3 -> 0 
Mar 29 22:06:11 Linux-CM690 NetworkManager: <info>  (ra0): supplicant connection state change: 0 -> 2 
Mar 29 22:06:16 Linux-CM690 NetworkManager: <info>  (ra0): supplicant connection state change: 2 -> 3 
Mar 29 22:06:26 Linux-CM690 NetworkManager: <info>  ra0: link timed out. 
Mar 29 22:06:26 Linux-CM690 NetworkManager: <info>  (ra0): supplicant connection state change: 3 -> 0 
Mar 29 22:06:26 Linux-CM690 NetworkManager: <info>  (ra0): supplicant connection state change: 0 -> 2 
Mar 29 22:06:31 Linux-CM690 NetworkManager: <info>  (ra0): supplicant connection state change: 2 -> 3 
Mar 29 22:06:40 Linux-CM690 NetworkManager: <info>  Activation (ra0/wireless): association took too long, failing activation. 
Mar 29 22:06:40 Linux-CM690 NetworkManager: <info>  (ra0): device state change: 5 -> 9 
Mar 29 22:06:40 Linux-CM690 NetworkManager: <info>  Activation (ra0) failed for access point (Belkin_N+_437CDD) 
Mar 29 22:06:40 Linux-CM690 NetworkManager: <info>  Marking connection 'Auto Belkin_N+_437CDD' invalid. 
Mar 29 22:06:40 Linux-CM690 NetworkManager: <info>  Activation (ra0) failed. 
Mar 29 22:06:40 Linux-CM690 NetworkManager: <info>  (ra0): device state change: 9 -> 3 
Mar 29 22:06:40 Linux-CM690 NetworkManager: <info>  (ra0): deactivating device (reason: 0).

---

### Post by surfed on 2009-03-29
Try setting your router to 801.11n only.

---

### Post by acreda on 2009-05-01
finally got to the end of the problem

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/339891](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/339891)

---

