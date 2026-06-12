---
title: "Modem MC8780 - authorization failed"
date: 2008-12-26
forum: Networking &amp; Wireless
---

### Post by rkarolek on 2008-12-26
Hello
I'm new in linux world ;)
I instaled Ubuntu 8.10 on my laptop Fujitsu-Siemens H250 with GSM modem MC8780 (Sierra Wireless)
Modem is correctly detected in system, and i can try connection but i can't input pin :(
I configure my connection by network manager aplet, all seems correct, but when i try connect, winndow with pin request appears, i typing pin and click OK, but window appaer again, and again, and again....
I don't know what is wrong, I think that problem is in right access to some files, but I don't know what i can do :(

Here are result lspic and usbpci:
```
robert@robert-laptop:~$ sudo lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:19.0 Ethernet controller: Intel Corporation 82566MM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HBM (ICH8M-E) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation Quadro FX 570M (rev a1)
14:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
1c:03.0 CardBus bridge: O2 Micro, Inc. OZ711SP1 Memory CardBus Controller (rev 01)
1c:03.1 CardBus bridge: O2 Micro, Inc. OZ711SP1 Memory CardBus Controller (rev 01)
1c:03.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02)
1c:03.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)
1c:03.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
```

```
robert@robert-laptop:~$ lsusb
Bus 003 Device 004: ID 046d:09b2 Logitech, Inc. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 004: ID 08ec:0015 M-Systems Flash Disk Pioneers Kingston DataTraveler ELITE
Bus 007 Device 002: ID 0781:540e SanDisk Corp. 
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 09da:000a A4 Tech Co., Ltd Port Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 1199:6832 Sierra Wireless, Inc. MC8780 Device
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0c24:000f Taiyo Yuden Bluetooth Driver (V2.0+EDR)
Bus 001 Device 002: ID 08ff:2580 AuthenTec, Inc. AES2501 Fingerprint Sensor
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

and changing in syslog when i try connect:
```
Dec 24 14:09:19 robert-laptop NetworkManager: <info>  Activation (ttyUSB0) starting connection 'iPlus' 
Dec 24 14:09:19 robert-laptop NetworkManager: <info>  (ttyUSB0): device state change: 3 -> 4 
Dec 24 14:09:19 robert-laptop NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) scheduled... 
Dec 24 14:09:19 robert-laptop NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) started... 
Dec 24 14:09:19 robert-laptop NetworkManager: <debug> [1230124159.441511] nm_serial_device_open(): (ttyUSB0) opening device... 
Dec 24 14:09:19 robert-laptop NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) complete. 
Dec 24 14:09:19 robert-laptop NetworkManager: <info>  (ttyUSB0): GSM pin secret required 
Dec 24 14:09:19 robert-laptop NetworkManager: <info>  (ttyUSB0): device state change: 4 -> 6 
Dec 24 14:09:19 robert-laptop NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) scheduled... 
Dec 24 14:09:19 robert-laptop NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) started... 
Dec 24 14:09:19 robert-laptop NetworkManager: <info>  (ttyUSB0): device state change: 6 -> 4 
Dec 24 14:09:19 robert-laptop NetworkManager: <debug> [1230124159.633732] nm_serial_device_open(): (ttyUSB0) opening device... 
Dec 24 14:09:19 robert-laptop NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) complete. 
Dec 24 14:09:19 robert-laptop NetworkManager: <WARN>  enter_pin_done(): Invalid secret 
Dec 24 14:09:19 robert-laptop NetworkManager: <info>  (ttyUSB0): GSM pin secret required 
Dec 24 14:09:19 robert-laptop NetworkManager: <info>  (ttyUSB0): device state change: 4 -> 6
```

now changing in syslog after appears window with pin request
```
Dec 24 14:10:03 robert-laptop NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) scheduled... 
Dec 24 14:10:03 robert-laptop NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) started... 
Dec 24 14:10:03 robert-laptop NetworkManager: <info>  (ttyUSB0): device state change: 6 -> 4 
Dec 24 14:10:03 robert-laptop NetworkManager: <debug> [1230124203.886897] nm_serial_device_open(): (ttyUSB0) opening device... 
Dec 24 14:10:03 robert-laptop NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) complete. 
Dec 24 14:10:04 robert-laptop NetworkManager: <WARN>  enter_pin_done(): Invalid secret 
Dec 24 14:10:04 robert-laptop NetworkManager: <info>  (ttyUSB0): GSM pin secret required 
Dec 24 14:10:04 robert-laptop NetworkManager: <info>  (ttyUSB0): device state change: 4 -> 6
```

and changing in syslog when i stop trying connection
```
Dec 24 14:10:41 robert-laptop NetworkManager: <WARN>  get_secrets_cb(): Couldn't get connection secrets: applet-device-gsm.c.636 (get_gsm_secrets_cb): canceled. 
Dec 24 14:10:42 robert-laptop NetworkManager: <info>  (ttyUSB0): device state change: 6 -> 9 
Dec 24 14:10:42 robert-laptop NetworkManager: <debug> [1230124241.762082] nm_serial_device_close(): Closing device 'ttyUSB0' 
Dec 24 14:10:42 robert-laptop NetworkManager: <info>  Marking connection 'iPlus' invalid. 
Dec 24 14:10:42 robert-laptop NetworkManager: <info>  Activation (ttyUSB0) failed. 
Dec 24 14:10:42 robert-laptop NetworkManager: <info>  (ttyUSB0): device state change: 9 -> 3 
Dec 24 14:10:42 robert-laptop NetworkManager: <info>  (ttyUSB0): deactivating device (reason: 0). 
Dec 24 14:10:42 robert-laptop NetworkManager: nm_system_device_flush_ip4_routes_with_iface: assertion `iface_idx >= 0' failed
Dec 24 14:10:42 robert-laptop NetworkManager: nm_system_device_flush_ip4_addresses_with_iface: assertion `iface_idx >= 0' failed
```


Please help me, i don't know what i'm doing wrong :(

And sorry for my english, but i think that you understand what i try tell and where is my problem ;)

Thank you in advance.

---

### Post by ieee488 on 2008-12-26
You don't have problems connecting in Windows; in other words, you know that the PIN you are using is the correct one?

---

### Post by rkarolek on 2008-12-26
> **ieee488 said:**
> You don't have problems connecting in Windows; in other words, you know that the PIN you are using is the correct one?

sure, i work everyday on this laptop, and connect with internet without any problems ;)

---

