---
title: "Network Manager Not Working with ZTE AC8700"
date: 2009-10-31
forum: Networking &amp; Wireless
---

### Post by kunalgautam on 2009-10-31
Hi There,

I'm having strange problem in using Ubuntu 9.10 with network manager !

Network manager was working fine in 9.04 but after upgrading or even new installation I'm unable to connect via Network Manager applet 

The Following LOG is generated while connecting to my Modem

```
Oct 31 22:46:10 Dhruv-Linux NetworkManager: <info>  Activation (ttyUSB0) starting connection 'Verizon connection 1'
Oct 31 22:46:10 Dhruv-Linux NetworkManager: <info>  (ttyUSB0): device state change: 3 -> 4 (reason 0)
Oct 31 22:46:10 Dhruv-Linux NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) scheduled...
Oct 31 22:46:10 Dhruv-Linux NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) started...
Oct 31 22:46:10 Dhruv-Linux NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) complete.
Oct 31 22:46:10 Dhruv-Linux modem-manager: (ttyUSB0) opening serial device...
Oct 31 22:46:10 Dhruv-Linux modem-manager: Got failure code 100: Unknown error
Oct 31 22:46:10 Dhruv-Linux modem-manager: Your CDMA modem does not support +CMEE command
Oct 31 22:47:11 Dhruv-Linux NetworkManager: <WARN>  stage1_prepare_done(): CDMA modem connection failed: No service
Oct 31 22:47:11 Dhruv-Linux NetworkManager: <info>  (ttyUSB0): device state change: 4 -> 9 (reason 0)
Oct 31 22:47:11 Dhruv-Linux NetworkManager: <info>  Marking connection 'Verizon connection 1' invalid.
Oct 31 22:47:11 Dhruv-Linux NetworkManager: <info>  Activation (ttyUSB0) failed.
Oct 31 22:47:11 Dhruv-Linux NetworkManager: <info>  (ttyUSB0): device state change: 9 -> 3 (reason 0)
Oct 31 22:47:11 Dhruv-Linux NetworkManager: <info>  (ttyUSB0): deactivating device (reason: 0).
Oct 31 22:47:11 Dhruv-Linux NetworkManager: flush_routes: assertion `iface_idx >= 0' failed
Oct 31 22:47:11 Dhruv-Linux NetworkManager: flush_addresses: assertion `iface_idx >= 0' failed
Oct 31 22:47:11 Dhruv-Linux modem-manager: (ttyUSB0) closing serial device...
```All i can know is that It is issuing Modem Initialization command as +CMEE (Instead of +AT or +ATZ )
BTW its working fine with wvdial

---

### Post by kunalgautam on 2009-11-01
Bump !

---

### Post by mr_amit on 2009-11-09
[https://bugs.launchpad.net/network-manager/+bug/461096](https://bugs.launchpad.net/network-manager/+bug/461096)

---

### Post by ravishakya on 2009-12-13
I also face same problem. I am *** to upgrade Network Manager and modemmanager to latest versions and if that does not help, will downgrade to the older version.
There are other apps like pidgin/empathy etc that check on connection thru network manager for their successful operation. I got to get this working!
So far I have been connecting using wvdial.

---

