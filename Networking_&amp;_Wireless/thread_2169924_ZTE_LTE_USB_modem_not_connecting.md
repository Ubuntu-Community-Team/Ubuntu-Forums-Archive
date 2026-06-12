---
title: "ZTE LTE USB modem not connecting"
date: 2013-08-24
forum: Networking &amp; Wireless
---

### Post by krishnaraj2 on 2013-08-24
I recently purchased an Airtel 4G LTE modem. Model is ZTE MF825A LTE usb card. It connects perfectly fine on windows. Although they have a setup for linux x86, I have a arm chromebook. Hence no setup!

1 thing surprised me. On windows, the usb modem creates an ethernet connection with ip 192.168.0.144 whenever its plugged in, whether connected to internet or not. Even after connecting to internet through Airtel 4G GUI this ip remains the same. What kind of connection is this?

Even on linux, this usb modem creates an eth0 connection with same ip, but no internet! :( I tried usb_modeswitch, no luck. Check below for log
> 
dmesg
[ 104.025283] usb 2-1: new high-speed USB device number 4 using s5p-ehci
[ 104.183421] usb 2-1: New USB device found, idVendor=19d2, idProduct=1225
[ 104.183498] usb 2-1: New USB device strings: Mfr=2, Product=3, SerialNumber=4
[ 104.183562] usb 2-1: Product: ZTE WCDMA Technologies MSM
[ 104.183616] usb 2-1: Manufacturer: ZTE,Incorporated
[ 104.183667] usb 2-1: SerialNumber: MF8250ZTED000000
[ 104.327876] usbcore: registered new interface driver libusual
[ 104.380155] Initializing USB Mass Storage driver...
[ 104.383780] scsi0 : usb-storage 2-1:1.0
[ 104.388458] usbcore: registered new interface driver usb-storage
[ 104.388518] USB Mass Storage support registered.
[ 105.395342] scsi 0:0:0:0: CD-ROM CWID USB SCSI CD-ROM 2.31 PQ: 0 ANSI: 2
[ 105.407270] scsi 0:0:0:1: Direct-Access ZTE MMC Storage 2.31 PQ: 0 ANSI: 2
[ 105.463160] sd 0:0:0:1: [sda] Attached SCSI removable disk
[ 105.553641] sr0: scsi-1 drive
[ 105.553668] cdrom: Uniform CD-ROM driver Revision: 3.20
[ 105.554806] sr 0:0:0:0: Attached scsi CD-ROM sr0
[ 110.415922] usb 2-1: USB disconnect, device number 4
[ 110.790178] usb 2-1: new high-speed USB device number 5 using s5p-ehci
[ 110.948539] usb 2-1: New USB device found, idVendor=19d2, idProduct=1408
[ 110.948614] usb 2-1: New USB device strings: Mfr=2, Product=3, SerialNumber=4
[ 110.948677] usb 2-1: Product: ZTE WCDMA Technologies MSM
[ 110.948730] usb 2-1: Manufacturer: ZTE,Incorporated
[ 110.948780] usb 2-1: SerialNumber: MF8250ZTED000000
[ 110.976822] scsi1 : usb-storage 2-1:1.2
[ 111.139335] cdc_ether 2-1:1.0: eth0: register 'cdc_ether' at usb-s5p-ehci-1, CDC Ethernet Device, 34:4b:50:b7:ef:4a
[ 111.141926] usbcore: registered new interface driver cdc_ether
[ 111.977805] scsi 1:0:0:0: CD-ROM CWID USB SCSI CD-ROM 2.31 PQ: 0 ANSI: 2
[ 111.991017] sr0: scsi-1 drive
[ 112.000746] sr 1:0:0:0: Attached scsi CD-ROM sr0
[ 112.004819] scsi 1:0:0:1: Direct-Access ZTE MMC Storage 2.31 PQ: 0 ANSI: 2
[ 112.032883] sd 1:0:0:1: [sda] Attached SCSI removable disk
[ 112.324082] ISO 9660 Extensions: Microsoft Joliet Level 1
[ 112.339758] ISOFS: changing to secondary root
[ 125.515006] eth0: no IPv6 routers present

kr@eternity:~$ lsusb
Bus 002 Device 005: ID 19d2:1408 ZTE WCDMA Technologies MSM 
Bus 002 Device 002: ID 0424:3503 Standard Microsystems Corp. 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 003: ID 2232:1037 

kr@eternity:~$ ifconfig 
eth0 Link encap:Ethernet HWaddr 34:4b:50:b7:ef:4a 
inet addr:192.168.0.144 Bcast:192.168.0.255 Mask:255.255.255.0
inet6 addr: fe80::364b:50ff:feb7:ef4a/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:79 errors:0 dropped:0 overruns:0 frame:0
TX packets:81 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:5358 (5.3 KB) TX bytes:6998 (6.9 KB)


lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:208 errors:0 dropped:0 overruns:0 frame:0
TX packets:208 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:15128 (15.1 KB) TX bytes:15128 (15.1 KB)

I just wonder what kind of connection is this!!

---

