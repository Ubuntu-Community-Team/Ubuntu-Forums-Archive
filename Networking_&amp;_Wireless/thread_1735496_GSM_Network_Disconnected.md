---
title: "GSM Network Disconnected"
date: 2011-04-21
forum: Networking &amp; Wireless
---

### Post by sknagesh on 2011-04-21
Hi All

Ubuntu 10.10


I have 3G Data Dard from model LW272 V1.0 connected to front USB port. Upon insertion for the first time it was detected correctly as GSM modem and upon selecting the country (India) carrier (BSNL) and APN (bsnlsouth) it connected successfully. I was able to use internet for about 2 mins. aster that it disconnected with message "GSM network disconnected. Now you are offline". Since then I am not able to connect no matter what I do. I have tried removing and reinserting, restarting computer etc, but still i am not able to connect.

here is the syslog.

Apr 21 20:38:41 raghu kernel: [ 1038.012067] usb 1-6: new high speed USB device using ehci_hcd and address 2
Apr 21 20:38:41 raghu kernel: [ 1038.281215] Initializing USB Mass Storage driver...
Apr 21 20:38:41 raghu kernel: [ 1038.281387] scsi4 : usb-storage 1-6:1.0
Apr 21 20:38:41 raghu kernel: [ 1038.281631] usbcore: registered new interface driver usb-storage
Apr 21 20:38:41 raghu kernel: [ 1038.281635] USB Mass Storage support registered.
Apr 21 20:38:42 raghu kernel: [ 1039.288908] scsi 4:0:0:0: CD-ROM            HSPA     USB SCSI CD-ROM  2.31 PQ: 0 ANSI: 2
Apr 21 20:38:42 raghu kernel: [ 1039.289507] scsi 4:0:0:1: Direct-Access     HSPA     MMC Storage      2.31 PQ: 0 ANSI: 2
Apr 21 20:38:42 raghu kernel: [ 1039.297001] sr1: scsi-1 drive
Apr 21 20:38:42 raghu kernel: [ 1039.297247] sr 4:0:0:0: Attached scsi CD-ROM sr1
Apr 21 20:38:42 raghu kernel: [ 1039.297381] sr 4:0:0:0: Attached scsi generic sg2 type 5
Apr 21 20:38:42 raghu kernel: [ 1039.297604] sd 4:0:0:1: Attached scsi generic sg3 type 0
Apr 21 20:38:42 raghu kernel: [ 1039.321427] sd 4:0:0:1: [sdb] Attached SCSI removable disk
Apr 21 20:38:42 raghu usb_modeswitch: switching 19d2:2000 (HSPA,Incorporated: HSPA WCDMA Technologies MSM)
Apr 21 20:38:42 raghu udevd-work[468]: inotify_add_watch(6, /dev/sdb, 10) failed: No such file or directory
Apr 21 20:38:43 raghu kernel: [ 1040.621034] usb 1-6: USB disconnect, address 2
Apr 21 20:38:51 raghu kernel: [ 1048.248023] usb 1-6: new high speed USB device using ehci_hcd and address 3
Apr 21 20:38:51 raghu kernel: [ 1048.409177] scsi5 : usb-storage 1-6:1.4
Apr 21 20:38:51 raghu kernel: [ 1048.492293] usbcore: registered new interface driver usbserial
Apr 21 20:38:51 raghu kernel: [ 1048.492335] USB Serial support registered for generic
Apr 21 20:38:51 raghu kernel: [ 1048.494347] usbcore: registered new interface driver usbserial_generic
Apr 21 20:38:51 raghu kernel: [ 1048.494353] usbserial: USB Serial Driver core
Apr 21 20:38:51 raghu kernel: [ 1048.521845] USB Serial support registered for GSM modem (1-port)
Apr 21 20:38:51 raghu kernel: [ 1048.523092] option 1-6:1.0: GSM modem (1-port) converter detected
Apr 21 20:38:51 raghu kernel: [ 1048.523382] usb 1-6: GSM modem (1-port) converter now attached to ttyUSB0
Apr 21 20:38:51 raghu kernel: [ 1048.523417] option 1-6:1.1: GSM modem (1-port) converter detected
Apr 21 20:38:51 raghu kernel: [ 1048.523589] usb 1-6: GSM modem (1-port) converter now attached to ttyUSB1
Apr 21 20:38:51 raghu kernel: [ 1048.523620] option 1-6:1.2: GSM modem (1-port) converter detected
Apr 21 20:38:51 raghu kernel: [ 1048.523790] usb 1-6: GSM modem (1-port) converter now attached to ttyUSB2
Apr 21 20:38:51 raghu kernel: [ 1048.523821] option 1-6:1.3: GSM modem (1-port) converter detected
Apr 21 20:38:51 raghu kernel: [ 1048.527143] usb 1-6: GSM modem (1-port) converter now attached to ttyUSB3
Apr 21 20:38:51 raghu kernel: [ 1048.528667] usbcore: registered new interface driver option
Apr 21 20:38:51 raghu kernel: [ 1048.528674] option: v0.7.2:USB Driver for GSM modems
Apr 21 20:38:51 raghu modem-manager: (ttyUSB0) opening serial device...
Apr 21 20:38:51 raghu modem-manager: (ttyUSB0): probe requested by plugin 'ZTE'
Apr 21 20:38:51 raghu modem-manager: (ttyUSB2) opening serial device...
Apr 21 20:38:51 raghu modem-manager: (ttyUSB2): probe requested by plugin 'ZTE'
Apr 21 20:38:51 raghu modem-manager: (ttyUSB3) opening serial device...
Apr 21 20:38:51 raghu modem-manager: (ttyUSB3): probe requested by plugin 'ZTE'
Apr 21 20:38:51 raghu modem-manager: (ttyUSB1) opening serial device...
Apr 21 20:38:51 raghu modem-manager: (ttyUSB1): probe requested by plugin 'ZTE'
Apr 21 20:38:51 raghu usb_modeswitch: switched to 19d2:0108 (HSPA,Incorporated: HSPA WCDMA Technologies MSM)
Apr 21 20:38:52 raghu kernel: [ 1049.413512] scsi 5:0:0:0: Direct-Access     HSPA     MMC Storage      2.31 PQ: 0 ANSI: 2
Apr 21 20:38:52 raghu kernel: [ 1049.416912] sd 5:0:0:0: Attached scsi generic sg2 type 0
Apr 21 20:38:52 raghu kernel: [ 1049.430124] sd 5:0:0:0: [sdb] Attached SCSI removable disk
Apr 21 20:38:56 raghu modem-manager: Got failure code 100: Unknown error
Apr 21 20:38:56 raghu modem-manager: Got failure code 14: SIM busy
Apr 21 20:38:59 raghu modem-manager: Got failure code 14: SIM busy
Apr 21 20:39:03 raghu modem-manager: (ttyUSB1) closing serial device...
Apr 21 20:39:04 raghu modem-manager: (ttyUSB1) opening serial device...
Apr 21 20:39:04 raghu modem-manager: (ZTE): GSM modem /sys/devices/pci0000:00/0000:00:10.4/usb1/1-6 claimed port ttyUSB1
Apr 21 20:39:04 raghu modem-manager: Added modem /sys/devices/pci0000:00/0000:00:10.4/usb1/1-6
Apr 21 20:39:04 raghu modem-manager: (tty/ttyUSB0): outstanding support task prevents export of /sys/devices/pci0000:00/0000:00:10.4/usb1/1-6
Apr 21 20:39:04 raghu modem-manager: (tty/ttyUSB0): outstanding support task prevents export of /sys/devices/pci0000:00/0000:00:10.4/usb1/1-6
Apr 21 20:39:04 raghu modem-manager: (ttyUSB3) closing serial device...
Apr 21 20:39:04 raghu modem-manager: (ZTE): GSM modem /sys/devices/pci0000:00/0000:00:10.4/usb1/1-6 claimed port ttyUSB3
Apr 21 20:39:04 raghu modem-manager: (tty/ttyUSB0): outstanding support task prevents export of /sys/devices/pci0000:00/0000:00:10.4/usb1/1-6
Apr 21 20:39:04 raghu modem-manager: (tty/ttyUSB0): outstanding support task prevents export of /sys/devices/pci0000:00/0000:00:10.4/usb1/1-6
Apr 21 20:39:04 raghu modem-manager: (ttyUSB1) closing serial device...
Apr 21 20:39:24 raghu modem-manager: (ttyUSB0) closing serial device...
Apr 21 20:39:24 raghu modem-manager: (ttyUSB0) opening serial device...
Apr 21 20:39:26 raghu modem-manager: (ttyUSB2) closing serial device...
Apr 21 20:39:26 raghu modem-manager: (ttyUSB2) opening serial device...
Apr 21 20:39:27 raghu modem-manager: (ttyUSB0) closing serial device...
Apr 21 20:39:27 raghu modem-manager: (ZTE): GSM modem /sys/devices/pci0000:00/0000:00:10.4/usb1/1-6 claimed port ttyUSB0
Apr 21 20:39:27 raghu modem-manager: (tty/ttyUSB2): outstanding support task prevents export of /sys/devices/pci0000:00/0000:00:10.4/usb1/1-6
Apr 21 20:39:32 raghu modem-manager: (ttyUSB2) closing serial device...
Apr 21 20:39:32 raghu modem-manager: (tty/ttyUSB2): ignoring port unsupported by physical modem's plugin
Apr 21 20:39:32 raghu modem-manager: Exported modem /sys/devices/pci0000:00/0000:00:10.4/usb1/1-6 as /org/freedesktop/ModemManager/Modems/0
Apr 21 20:39:32 raghu modem-manager: (/org/freedesktop/ModemManager/Modems/0): data port is ttyUSB1
Apr 21 20:39:32 raghu NetworkManager[775]: <warn> (ttyUSB1): failed to look up interface index
Apr 21 20:39:32 raghu NetworkManager[775]: <info> (ttyUSB1): new GSM device (driver: 'option1' ifindex: -1)
Apr 21 20:39:32 raghu NetworkManager[775]: <info> (ttyUSB1): exported as /org/freedesktop/NetworkManager/Devices/1
Apr 21 20:39:32 raghu NetworkManager[775]: <info> (ttyUSB1): now managed
Apr 21 20:39:32 raghu NetworkManager[775]: <info> (ttyUSB1): device state change: 1 -> 2 (reason 2)
Apr 21 20:39:32 raghu NetworkManager[775]: <info> (ttyUSB1): deactivating device (reason: 2).
Apr 21 20:39:32 raghu NetworkManager[775]: <info> (ttyUSB1): device state change: 2 -> 3 (reason 0)
Apr 21 20:42:33 raghu NetworkManager[775]: <info> Activation (ttyUSB1) starting connection 'BSNL/CellOne South Zone A (Karnatka, Andhra Pradesh, Chennai, Tamil Nadu, Kerala)'
Apr 21 20:42:33 raghu NetworkManager[775]: <info> (ttyUSB1): device state change: 3 -> 4 (reason 0)
Apr 21 20:42:33 raghu NetworkManager[775]: <info> Activation (ttyUSB1) Stage 1 of 5 (Device Prepare) scheduled...
Apr 21 20:42:33 raghu NetworkManager[775]: <info> Activation (ttyUSB1) Stage 1 of 5 (Device Prepare) started...
Apr 21 20:42:33 raghu NetworkManager[775]: <info> Activation (ttyUSB1) Stage 1 of 5 (Device Prepare) complete.
Apr 21 20:42:33 raghu modem-manager: (ttyUSB1) opening serial device...
Apr 21 20:42:33 raghu modem-manager: Modem /org/freedesktop/ModemManager/Modems/0: state changed (disabled -> enabling)
Apr 21 20:42:33 raghu modem-manager: (ttyUSB3) opening serial device...
Apr 21 20:42:33 raghu modem-manager: Modem /org/freedesktop/ModemManager/Modems/0: state changed (enabling -> enabled)
Apr 21 20:42:33 raghu modem-manager: CS registration state changed: 1
Apr 21 20:42:33 raghu modem-manager: Modem /org/freedesktop/ModemManager/Modems/0: state changed (enabled -> registered)
Apr 21 20:42:33 raghu modem-manager: PS registration state changed: 3
Apr 21 20:42:33 raghu modem-manager: CS registration state changed: 2
Apr 21 20:42:33 raghu modem-manager: Modem /org/freedesktop/ModemManager/Modems/0: state changed (registered -> searching)
Apr 21 20:42:33 raghu modem-manager: CS registration state changed: 1
Apr 21 20:42:33 raghu modem-manager: Modem /org/freedesktop/ModemManager/Modems/0: state changed (searching -> registered)
Apr 21 20:42:33 raghu modem-manager: CS registration state changed: 2
Apr 21 20:42:33 raghu modem-manager: Modem /org/freedesktop/ModemManager/Modems/0: state changed (registered -> searching)
Apr 21 20:42:33 raghu modem-manager: CS registration state changed: 1
Apr 21 20:42:33 raghu modem-manager: Modem /org/freedesktop/ModemManager/Modems/0: state changed (searching -> registered)
Apr 21 20:42:33 raghu modem-manager: Modem /org/freedesktop/ModemManager/Modems/0: state changed (registered -> connecting)
Apr 21 20:42:33 raghu kernel: [ 1270.617160] usb 1-6: USB disconnect, address 3
Apr 21 20:42:33 raghu kernel: [ 1270.617303] option: option_instat_callback: error -108
Apr 21 20:42:33 raghu kernel: [ 1270.617570] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
Apr 21 20:42:33 raghu kernel: [ 1270.617600] option 1-6:1.0: device disconnected
Apr 21 20:42:33 raghu kernel: [ 1270.617762] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
Apr 21 20:42:33 raghu kernel: [ 1270.617777] option 1-6:1.1: device disconnected
Apr 21 20:42:33 raghu kernel: [ 1270.617869] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
Apr 21 20:42:33 raghu kernel: [ 1270.617893] option 1-6:1.2: device disconnected
Apr 21 20:42:33 raghu kernel: [ 1270.618001] option1 ttyUSB3: GSM modem (1-port) converter now disconnected from ttyUSB3
Apr 21 20:42:33 raghu kernel: [ 1270.618016] option 1-6:1.3: device disconnected
Apr 21 20:42:33 raghu modem-manager: (ttyUSB1) closing serial device...
Apr 21 20:42:33 raghu modem-manager: Modem /org/freedesktop/ModemManager/Modems/0: state changed (connecting -> registered)
Apr 21 20:42:33 raghu modem-manager: (ttyUSB3) closing serial device...
Apr 21 20:42:33 raghu modem-manager: Modem /org/freedesktop/ModemManager/Modems/0: state changed (registered -> disabled)
Apr 21 20:42:33 raghu modem-manager: Removed modem /sys/devices/pci0000:00/0000:00:10.4/usb1/1-6
Apr 21 20:42:33 raghu NetworkManager[775]: <info> (ttyUSB1): now unmanaged
Apr 21 20:42:33 raghu NetworkManager[775]: <info> (ttyUSB1): device state change: 4 -> 1 (reason 36)
Apr 21 20:42:33 raghu NetworkManager[775]: <info> (ttyUSB1): deactivating device (reason: 36).
Apr 21 20:42:33 raghu modem-manager: mm_callback_info_schedule: assertion `info->pending_id == 0' failed
Apr 21 20:42:33 raghu NetworkManager[775]: <info> Policy set 'Auto eth0' (eth0) as default for IPv4 routing and DNS.
Apr 21 20:42:33 raghu NetworkManager[775]: <info> Policy set 'Auto eth0' (eth0) as default for IPv4 routing and DNS.
Apr 21 20:42:33 raghu NetworkManager[775]: <info> (ttyUSB1): cleaning up...
Apr 21 20:42:33 raghu NetworkManager[775]: <info> (ttyUSB1): taking down device.
Apr 21 20:42:36 raghu kernel: [ 1273.048027] usb 1-6: new high speed USB device using ehci_hcd and address 4
Apr 21 20:42:36 raghu kernel: [ 1273.185742] option 1-6:1.0: GSM modem (1-port) converter detected
Apr 21 20:42:36 raghu kernel: [ 1273.185892] usb 1-6: GSM modem (1-port) converter now attached to ttyUSB0
Apr 21 20:42:36 raghu modem-manager: (ttyUSB0) opening serial device...
Apr 21 20:42:36 raghu modem-manager: (ttyUSB0): probe requested by plugin 'ZTE'
Apr 21 20:43:05 raghu modem-manager: (ttyUSB0) closing serial device...
Apr 21 20:43:05 raghu modem-manager: (ttyUSB0) opening serial device...


Can some guide me in solving this. The data card works fine inder WinXP


TIA

SKN

---

### Post by GeorgeVita on 2011-04-21
Hi **sknagesh**,
your problem seems to be identical to my old one using a ZTE MF636 3G modem (bug#408555). My modem was identified at **lsusb** terminal command as 19d2:2000 (CD_ROM) and then changed to the 19d2:0031 (real modem state). A looping creation/disconnection of ttyUSB0-1-2 happened (as in your case).

This bug solved after a firmware update for the modem (downloaded from my local provider as some "localisation" is included). Can you check/ask your provider about the actual model of the modem and if they have any update?

There is also a method to connect by "stopping" modem-manager/network manager and then use wvdial to connect but this is the "hard-terminal way".

Regards,
George

---

### Post by sknagesh on 2011-04-22
My ISP will not even talk about linux as it is working on WinXP. But I did find a connection manager for this modem supplied by my ISP called "JoinAir" which was suppose to work on 9.04 . Using this also I am not able to connect. As it stops at "Initializing". I have also tried Sakis3G which also could not connect. Strange thing is once any of these programs including Network Manager tries to connect the modem light just turns off. There is no Red light or Green Ligth which were there before I tried to connect.

I dont know how to stop modem-manage or network manager. Can you guide me. I did find some scripts for use with wvdial. which i will try to use.

Regards
SKN

---

### Post by GeorgeVita on 2011-04-22
Hi SKN,
the 'firmware update' for the modem comes from the manufacturer and it is not for a specific O.S., it just fixes some small internal bugs. Most providers do no know/like to support these updates. If you can find the specific modem type (manufacturer should be ZTE) you can then search from the manufacturer's site. In any way it is better to get it from the provider (when available) as some warranty issues may occur.

Let' go back to terminal now!

Using terminal command **dmesg** you can see system activity. If you add parameter **-c** the "history" is cleared (full command is "sudo dmesg -c"). Next simple **dmesg** will show only the new system activity.

Try the following:
- boot without modem
- from terminal: **sudo dmesg -c**
- do not care about all data shown by this dmesg command
- attach your modem
- wait 15 seconds
- from terminal: **dmesg**

You can see the problematic creation/disconnection of the /dev/ttyUSBx ports (looping always).

Now you will repeat above without network-manager and modem-manager
- remove modem
- reboot without modem
- from terminal: 
```
sudo stop network-manager
sudo killall modem-manager
sudo dmesg -c
```
- do not care about all data shown by this dmesg command
- attach your modem
- wait 15 seconds
- from terminal: **dmesg**

You must see the creation of the /dev/ttyUSBx ports (usually 0-1-2) but now this is a STEADY condition!

Check above and confirm.
Is **wvdial** already installed? 
Check it with: **sudo apt-get install wvdial**
If not installed, do you have any other internet connection (WiFi or ethernet)?
What is your country/provider (to find some parameters).

Regards,
George

P.S. take a brief look at [bug#408555]("https://bugs.launchpad.net/bugs/408555")

---

### Post by sknagesh on 2011-04-22
Hi 

Thanks for the replay. The modem is from teracom. but I could not find any info on their website.

wvdial is already installed. I will stop NM and modem manager as you suggested and get back with results.

Thanks

SKN

---

### Post by sknagesh on 2011-04-22
Hi

Here is dmesg output with network-manager and modem-manager disabled.

raghu@raghu:~$ dmesg 
[  121.656049] usb 4-2: new full speed USB device using uhci_hcd and address 2
[  122.176019] usb 4-2: device not accepting address 2, error -71
[  122.288047] usb 4-2: new full speed USB device using uhci_hcd and address 3
[  122.816033] usb 4-2: device not accepting address 3, error -71
[  122.928024] usb 4-2: new full speed USB device using uhci_hcd and address 4
[  123.340116] usb 4-2: device not accepting address 4, error -71
[  123.452041] usb 4-2: new full speed USB device using uhci_hcd and address 5
[  123.860014] usb 4-2: device not accepting address 5, error -71
[  123.860031] hub 4-0:1.0: unable to enumerate USB device on port 2
[  151.952031] usb 4-2: new full speed USB device using uhci_hcd and address 6
[  152.072047] usb 4-2: device descriptor read/64, error -71
[  152.296045] usb 4-2: device descriptor read/64, error -71
[  152.512046] usb 4-2: new full speed USB device using uhci_hcd and address 7
[  152.632039] usb 4-2: device descriptor read/64, error -71
[  152.856019] usb 4-2: device descriptor read/64, error -71
[  153.072026] usb 4-2: new full speed USB device using uhci_hcd and address 8
[  153.480048] usb 4-2: device not accepting address 8, error -71
[  153.592017] usb 4-2: new full speed USB device using uhci_hcd and address 9
[  154.000066] usb 4-2: device not accepting address 9, error -71
[  154.000081] hub 4-0:1.0: unable to enumerate USB device on port 2


Looks like it is looking for a USB drive.

Thanks

SKN

---

### Post by GeorgeVita on 2011-04-22
... this is a strange behavior, I did not faced such case!
Searching for data for your modem, I did not found the specific (manufacturer) type. Can you check the output of:
```
usb-devices
lsusb
```
with the modem attached, just in case we got more info.
Give me also the output of:
```
uname -a
```
to check your ubuntu version.
G

---

### Post by sknagesh on 2011-04-22
Hi

This is the out out of usb-devices with NM and MM turned off.

raghu@raghu:~$ usb-devices 

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 8
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=02.06
S:  Manufacturer=Linux 2.6.35-22-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:10.4
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.35-22-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:10.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.35-22-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:10.1
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.35-22-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:10.2
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=05 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.35-22-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:10.3
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub




and out put of lsusb



Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


raghu@raghu:~$ uname -a
Linux raghu 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:34:50 UTC 2010 i686 GNU/Linux


HTH

Regards

SKN

---

### Post by GeorgeVita on 2011-04-22
I suppose your modem is attached but not shown to above output due to a problem. Try once more after fully shut down:
- remove modem
- shut down pc
- **boot without modem**
- wait for the system to fully load
- from terminal: sudo stop network-manager
>>> check that system responds "network-manager stop/waiting"
- from terminal: sudo killall modem-manager
>>> you can check that nothing is running with: **ps -A | grep -i manager**
- from terminal: sudo dmesg -c
- NOW attach modem and WAIT 30 seconds
- from terminal: dmesg
- from terminal: lsusb
>>> Check again terminal output to find the modem and /dev/**ttyUSBx** ports

If you cannot see the modem here, we have a new case and we need more ideas for help...
I am going to download your Ubuntu Version to check it in parallel with my ZTE modem.

G

---

### Post by sknagesh on 2011-04-22
Hi

here is the output


raghu@raghu:~$ dmesg 
[  186.752020] usb 4-2: new full speed USB device using uhci_hcd and address 2
[  186.872020] usb 4-2: device descriptor read/64, error -71
[  187.096015] usb 4-2: device descriptor read/64, error -71
[  187.312017] usb 4-2: new full speed USB device using uhci_hcd and address 3
[  187.432017] usb 4-2: device descriptor read/64, error -71
[  187.656015] usb 4-2: device descriptor read/64, error -71
[  187.872021] usb 4-2: new full speed USB device using uhci_hcd and address 4
[  188.280015] usb 4-2: device not accepting address 4, error -71
[  188.392034] usb 4-2: new full speed USB device using uhci_hcd and address 5
[  188.800015] usb 4-2: device not accepting address 5, error -71
[  188.800037] hub 4-0:1.0: unable to enumerate USB device on port 2
raghu@raghu:~$ lsusb 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
raghu@raghu:~$ 


Still it is not detected.

Thanks

SKN

---

### Post by GeorgeVita on 2011-04-22
... and if you try it without stopping NM & MM it is recognized?
G

---

### Post by sknagesh on 2011-04-22
Hi

with both managers running here is the output.

raghu@raghu:~$ lsusb 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 19d2:0108 ONDA Communication S.p.A. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


raghu@raghu:~$ usb-devices 

T:  Bus=01 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=480 MxCh= 8
D:  Ver= 2.00 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0002 Rev=02.06
S:  Manufacturer=Linux 2.6.35-22-generic ehci_hcd
S:  Product=EHCI Host Controller
S:  SerialNumber=0000:00:10.4
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=01 Lev=01 Prnt=01 Port=05 Cnt=01 Dev#=  3 Spd=480 MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=19d2 ProdID=0108 Rev=00.00
S:  Manufacturer=HSPA,Incorporated
S:  Product=HSPA WCDMA Technologies MSM
S:  SerialNumber=P679M1GEND010000
C:  #Ifs= 5 Cfg#= 1 Atr=e0 MxPwr=500mA
I:  If#= 0 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 1 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 2 Alt= 0 #EPs= 2 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 3 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=option
I:  If#= 4 Alt= 0 #EPs= 2 Cls=08(stor.) Sub=06 Prot=50 Driver=usb-storage

T:  Bus=02 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.35-22-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:10.0
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=03 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.35-22-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:10.1
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=04 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.35-22-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:10.2
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub

T:  Bus=05 Lev=00 Prnt=00 Port=00 Cnt=00 Dev#=  1 Spd=12  MxCh= 2
D:  Ver= 1.10 Cls=09(hub  ) Sub=00 Prot=00 MxPS=64 #Cfgs=  1
P:  Vendor=1d6b ProdID=0001 Rev=02.06
S:  Manufacturer=Linux 2.6.35-22-generic uhci_hcd
S:  Product=UHCI Host Controller
S:  SerialNumber=0000:00:10.3
C:  #Ifs= 1 Cfg#= 1 Atr=e0 MxPwr=0mA
I:  If#= 0 Alt= 0 #EPs= 1 Cls=09(hub  ) Sub=00 Prot=00 Driver=hub


Thanks

SKN

---

### Post by GeorgeVita on 2011-04-22
So the modem is listed as: **ID 19d2:0108 ONDA** Communication S.p.A.
 
Final try (from my "ideas") is to remove sim-pin check (if now using it) and try to recreate "mobile broadband connection". First delete all existing 'mobile broadband connections' (right click NM icon, Edit Connections, Mobile Broadband, click on existing, delete) and then create the new one with careful selection of the proper provider/APN (if you are not sure you can check what APN used by windows by enabling 'modem log' from advanced properties).
If you manage at least one connection (as in your 1st post) try to update (System>Administration>Update Manager).

G

---

### Post by sknagesh on 2011-04-22
hi

I have rechecked the APN from Windows. It is correct. Any way I deleted old connection and rebooted the system with out modem. Waited for about 5 mins and Inserted the modem. waited for about 1 min. Got new GSM broadband connection notice. Selected it to create a new connection. I have cross checked the connection details after creating it. They are correct. Once I select the connection it immediately says GSM Connection disconnected. Here is the log file

code:

raghu@raghu:~$ dmesg 
[  109.712040] usb 1-6: new high speed USB device using ehci_hcd and address 2
[  109.931199] Initializing USB Mass Storage driver...
[  109.931374] scsi4 : usb-storage 1-6:1.0
[  109.931630] usbcore: registered new interface driver usb-storage
[  109.931633] USB Mass Storage support registered.
[  112.062420] usb 1-6: USB disconnect, address 2
[  119.968026] usb 1-6: new high speed USB device using ehci_hcd and address 3
[  120.127575] scsi5 : usb-storage 1-6:1.4
[  120.183284] usbcore: registered new interface driver usbserial
[  120.183325] USB Serial support registered for generic
[  120.185904] usbcore: registered new interface driver usbserial_generic
[  120.185911] usbserial: USB Serial Driver core
[  120.226018] USB Serial support registered for GSM modem (1-port)
[  120.227275] option 1-6:1.0: GSM modem (1-port) converter detected
[  120.229839] usb 1-6: GSM modem (1-port) converter now attached to ttyUSB0
[  120.229891] option 1-6:1.1: GSM modem (1-port) converter detected
[  120.232578] usb 1-6: GSM modem (1-port) converter now attached to ttyUSB1
[  120.232641] option 1-6:1.2: GSM modem (1-port) converter detected
[  120.232931] usb 1-6: GSM modem (1-port) converter now attached to ttyUSB2
[  120.232964] option 1-6:1.3: GSM modem (1-port) converter detected
[  120.233149] usb 1-6: GSM modem (1-port) converter now attached to ttyUSB3
[  120.234424] usbcore: registered new interface driver option
[  120.234430] option: v0.7.2:USB Driver for GSM modems
[  121.133547] scsi 5:0:0:0: Direct-Access     HSPA     MMC Storage      2.31 PQ: 0 ANSI: 2
[  121.136931] sd 5:0:0:0: Attached scsi generic sg2 type 0
[  121.150526] sd 5:0:0:0: [sdb] Attached SCSI removable disk
[  200.705019] usb 1-6: USB disconnect, address 3
[  200.705160] option: option_instat_callback: error -108
[  200.705420] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0
[  200.705449] option 1-6:1.0: device disconnected
[  200.705578] option1 ttyUSB1: GSM modem (1-port) converter now disconnected from ttyUSB1
[  200.705594] option 1-6:1.1: device disconnected
[  200.705684] option1 ttyUSB2: GSM modem (1-port) converter now disconnected from ttyUSB2
[  200.705706] option 1-6:1.2: device disconnected
[  200.705813] option1 ttyUSB3: GSM modem (1-port) converter now disconnected from ttyUSB3
[  200.705827] option 1-6:1.3: device disconnected
[  203.120190] usb 1-6: new high speed USB device using ehci_hcd and address 4
[  203.257102] option 1-6:1.0: GSM modem (1-port) converter detected
[  203.257246] usb 1-6: GSM modem (1-port) converter now attached to ttyUSB0


After this there is no light on the modem.

One thing I tried in between is to use my friend's system running 10.04 LTS.There I was able to connect and browse once again for about  10 mins. But once I disconnected and tried to reconnect the result was same. Immediate disconnection.

Any way thank you very much for your help in trying to tackle this problem. I really appreciate it.

Thanks

SKN

---

### Post by dineshs on 2011-04-23
> **GeorgeVita said:**
> There is also a method to connect by "stopping" modem-manager/network manager and then use wvdial to connect but this is the "hard-terminal way".
I think you should try wvdial.

---

### Post by alexfish on 2011-04-24
Hi sknagesh

this device seems to have a storage problem + seem to dislike been probed on
certain ports 

> Apr 21 20:38:51 raghu usb_modeswitch: switched to 19d2:0108 (HSPA,Incorporated: HSPA WCDMA Technologies MSM)
Apr 21 20:38:52 raghu kernel: [ 1049.413512] scsi 5:0:0:0: Direct-Access HSPA MMC Storage 2.31 PQ: 0 ANSI: 2
Apr 21 20:38:52 raghu kernel: [ 1049.416912] sd 5:0:0:0: Attached scsi generic sg2 type 0
Apr 21 20:38:52 raghu kernel: [ 1049.430124] sd 5:0:0:0: [sdb] Attached SCSI removable disk
Apr 21 20:38:56 raghu modem-manager: Got failure code 100: Unknown error
Apr 21 20:38:56 raghu modem-manager: Got failure code 14: SIM busy
Apr 21 20:38:59 raghu modem-manager: Got failure code 14: SIM busy
Apr 21 20:39:03 raghu modem-manager: (ttyUSB1) closing serial device...
Apr 21 20:39:04 raghu modem-manager: (ttyUSB1) opening serial device...PLUS
> [ 120.233149] usb 1-6: GSM modem (1-port) converter now attached to ttyUSB3
[ 120.234424] usbcore: registered new interface driver option
[ 120.234430] option: v0.7.2:USB Driver for GSM modems
[ 121.133547] scsi 5:0:0:0: Direct-Access HSPA MMC Storage 2.31 PQ: 0 ANSI: 2
[ 121.136931] sd 5:0:0:0: Attached scsi generic sg2 type 0
[ 121.150526] sd 5:0:0:0: [sdb] Attached SCSI removable disk
[ 200.705019] usb 1-6: USB disconnect, address 3
[ 200.705160] option: option_instat_callback: error -108
[ 200.705420] option1 ttyUSB0: GSM modem (1-port) converter now disconnected from ttyUSB0can suggest to disable the switching

```
sudo gedit /etc/usb_modeswitch.conf
``` change the disable switching to
```
DisableSwitching=1
```save and exit
unplug the modem and reconnect
check with the lsusb command

```
lsusb
```if the device shows 19d2:2000

make a udev rule

```
sudu gedit /etc/udev/rules.d/zte-eject.rules
```add line
```
ATTRS{idVendor}=="19d2", ATTRS{idProduct}=="2000", RUN+="/usr/bin/eject %k", OPTIONS+="last_rule"
```save and exit

see what happens 

also can suggest using
Sakis3G - All-in-one script from
 **[*Sakis3G* - All-in-one script]("http://www.google.co.uk/url?sa=t&source=web&cd=1&ved=0CCAQFjAA&url=http%3A%2F%2Fwww.sakis3g.org%2F&rct=j&q=sakis3g%20-nostorage&ei=RAW0Tdb_Jcek8QPUw5SWDA&usg=AFQjCNFR0OA7GJQY3djYswddHkMjARyyDw&cad=rja")**

 if decide to use sakis3g , use from the terminal with nostorage option
```
sakis3g nostorage
```
there is a how to install sakis3g

[How To : Mobile Broadband Connections [ Ubuntu 10.10 : 10.04 : 9.10 ]]("http://ubuntuforums.org/showthread.php?t=1466490") 

alexfish

---

