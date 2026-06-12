---
title: "ZyXel NWD2705 startup fails"
date: 2013-09-01
forum: Networking &amp; Wireless
---

### Post by flixer on 2013-09-01
I have a ZyXEL NWD2705 dual-band 450mbps wifi adapter and Lubuntu 13.10. I tried adding the lsusb of the adapter to rtusb_dev_id.c. but it didn't help. I used the [RT3573 USB]("http://www.mediatek.com/_en/07_downloads/01_windows.php?sn=501") driver from Mediatek. Any ideas what to do next?

/var/syslog:
```
Sep  1 19:41:12  kernel: [  127.440929] usb 1-1: USB disconnect, device number 2
Sep  1 19:41:13  kernel: [  127.796213] usb 1-1: new high-speed USB device number 5 using ehci-pci
Sep  1 19:41:13  kernel: [  127.932199] usb 1-1: New USB device found, idVendor=0586, idProduct=3421
Sep  1 19:41:13  kernel: [  127.932224] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
Sep  1 19:41:13  kernel: [  127.932245] usb 1-1: Product: NWD2705
Sep  1 19:41:13  kernel: [  127.932262] usb 1-1: Manufacturer: ZyXEL
Sep  1 19:41:13  kernel: [  127.932279] usb 1-1: SerialNumber: 1.0
Sep  1 19:41:13  mtp-probe: checking bus 1, device 5: "/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-1"
Sep  1 19:41:13  mtp-probe: bus: 1, device: 5 was not an MTP device
Sep  1 19:41:13  kernel: [  128.067076] rtusb init rt2870 --->
Sep  1 19:41:13  kernel: [  128.067922] 
Sep  1 19:41:13  kernel: [  128.067922] 
Sep  1 19:41:13  kernel: [  128.067922] === pAd = f9271000, size = 562656 ===
Sep  1 19:41:13  kernel: [  128.067922] 
Sep  1 19:41:13  kernel: [  128.068028] <-- RTMPAllocTxRxRingMemory, Status=0
Sep  1 19:41:13  kernel: [  128.068028] <-- RTMPAllocAdapterBlock, Status=0
Sep  1 19:41:13  kernel: [  128.069816] (Reassign Efuse for 3x7x/3x9x/53xx) Size=0x3c [3c0-3fb] 
Sep  1 19:41:13  kernel: [  128.076377] usbcore: registered new interface driver rt2870
Sep  1 19:41:13  NetworkManager[777]: <warn> failed to allocate link cache: (-10) Operation not supported
Sep  1 19:41:13  NetworkManager[777]: <info> (ra0): driver does not support SSID scans (scan_capa 0x00).
Sep  1 19:41:13  NetworkManager[777]: <info> (ra0): using WEXT for WiFi device control
Sep  1 19:41:13  NetworkManager[777]: <error> [1378053673.661751] [nm-device-wifi.c:2841] update_permanent_hw_address(): (ra0): unable to read permanent MAC address (error 0)
Sep  1 19:41:13  NetworkManager[777]: <info> (ra0): new 802.11 WiFi device (driver: 'usb' ifindex: 4)
Sep  1 19:41:13  NetworkManager[777]: <info> (ra0): exported as /org/freedesktop/NetworkManager/Devices/2
Sep  1 19:41:13  NetworkManager[777]: <info> (ra0): device state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
Sep  1 19:41:13  NetworkManager[777]: <info> (ra0): bringing up device.
Sep  1 19:41:13  kernel: [  128.252487] #
Sep  1 19:41:13  kernel: [  128.328391] #
Sep  1 19:41:13  kernel: [  128.404421] #
Sep  1 19:41:14  kernel: [  128.480589] #
Sep  1 19:41:14  kernel: [  128.556379] #
Sep  1 19:41:14  kernel: [  128.632427] #
Sep  1 19:41:14  kernel: [  128.708335] #
Sep  1 19:41:14  kernel: [  128.784496] #
Sep  1 19:41:14  kernel: [  128.860399] #
Sep  1 19:41:14  kernel: [  128.936449] #
Sep  1 19:41:14  kernel: [  128.940344] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=OUT, Req=0x2, Idx=0x3368,pAd->Flags=0x0
Sep  1 19:41:14  kernel: [  128.940344] 	Request Value=0x90aa!
Sep  1 19:41:14  kernel: [  129.012360] #
Sep  1 19:41:14  kernel: [  129.088401] #
Sep  1 19:41:14  kernel: [  129.164437] #
Sep  1 19:41:14  kernel: [  129.240356] #
Sep  1 19:41:14  kernel: [  129.318447] #
Sep  1 19:41:14  kernel: [  129.396441] #
Sep  1 19:41:15  kernel: [  129.472480] #
Sep  1 19:41:15  kernel: [  129.548585] #
Sep  1 19:41:15  kernel: [  129.624436] #
Sep  1 19:41:15  kernel: [  129.700463] #
Sep  1 19:41:15  kernel: [  129.704360] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=OUT, Req=0x2, Idx=0x336a,pAd->Flags=0x0
Sep  1 19:41:15  kernel: [  129.704360] 	Request Value=0x3670!]
```

rtusb_dev_id.c
```
/* module table */
USB_DEVICE_ID rtusb_dev_id[] = {
#ifdef RT35xx
	{USB_DEVICE(0x148F,0x3572)}, /* Ralink 3573 */
	{USB_DEVICE(0x1740,0x9801)}, /* EnGenius 3572 */
	{USB_DEVICE(0x0DF6,0x0041)}, /* Sitecom 3572 */
	{USB_DEVICE(0x0DF6,0x0042)},
	{USB_DEVICE(0x04BB,0x0944)}, /* I-O DATA 3572 */
	{USB_DEVICE(0x1690,0x0740)}, /* 3572 */
	{USB_DEVICE(0x1690,0x0744)}, /* 3572 */
	{USB_DEVICE(0x5A57,0x0284)}, /* Zinwell 3572 */
	{USB_DEVICE(0x167B,0x4001)}, /* 3572 */
	{USB_DEVICE(0x1690,0x0764)}, /* 3572 */ 
	{USB_DEVICE(0x0930,0x0A07)}, /* TOSHIBA */
	{USB_DEVICE(0x1690,0x0761)}, /* Askey */
	{USB_DEVICE(0x13B1,0x002F)}, /* Cisco LinkSys AE1000 */
	{USB_DEVICE(0x1737,0x0079)}, /* Cisco LinkSys WUSB600N */
#endif /* RT35xx */
#ifdef RT3573
	{USB_DEVICE(0x148F,0x3573)}, /* Ralink 3573 */
	{USB_DEVICE(0x7392,0x7733)}, /* Edimax */
	{USB_DEVICE(0x0846,0x9012)}, /* Netgear WNDA4100 N900*/
	{USB_DEVICE(0x0586,0x3421)}, /* Zyxel */
#endif /* RT3573 */
	{ }/* Terminating entry */
}; 
```

---

### Post by praseodym on 2013-09-01
Please show:
```

modprobe -c | grep -i "0586.*3421" 
lsusb
lsmod
iwconfig
rfkill list
```

---

### Post by flixer on 2013-09-01
```
 modprobe -c | grep -i "0586.*3421" 
alias usb:v0586p3421d*dc*dsc*dp*ic*isc*ip*in* rt3573sta
 lsusb
Bus 001 Device 005: ID 0586:3421 ZyXEL Communications Corp. 
Bus 002 Device 002: ID 0e8f:0020 GreenAsia Inc. USB to PS/2 Adapter
Bus 003 Device 002: ID 046d:c016 Logitech, Inc. Optical Wheel Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 lsmod
Module                  Size  Used by
rt3573sta             663675  0 
nls_utf8               12493  0 
isofs                  39211  0 
lib80211_crypt_ccmp    12731  2 
rfcomm                 37420  0 
bnep                   17669  2 
bluetooth             202109  10 bnep,rfcomm
snd_intel8x0           33096  1 
snd_ac97_codec        105692  1 snd_intel8x0
ac97_bus               12670  1 snd_ac97_codec
snd_pcm                80890  2 snd_ac97_codec,snd_intel8x0
i915                  535544  2 
snd_page_alloc         14230  2 snd_intel8x0,snd_pcm
snd_seq_midi           13132  0 
pcmcia                 39544  0 
snd_seq_midi_event     14475  1 snd_seq_midi
ipw2200               140443  0 
libipw                 33172  1 ipw2200
snd_rawmidi            25114  1 snd_seq_midi
lib80211               14040  3 lib80211_crypt_ccmp,libipw,ipw2200
snd_seq                51280  2 snd_seq_midi_event,snd_seq_midi
drm_kms_helper         47545  1 i915
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
drm                   228489  3 i915,drm_kms_helper
snd_timer              24411  2 snd_pcm,snd_seq
cfg80211              469921  2 libipw,ipw2200
i2c_algo_bit           13197  1 i915
snd                    56485  9 snd_ac97_codec,snd_intel8x0,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_seq_device
yenta_socket           27095  0 
compat                 14155  5 cfg80211,lib80211_crypt_ccmp,libipw,lib80211,ipw2200
lpc_ich                16925  0 
tifm_7xx1              12905  0 
pcmcia_rsrc            18191  1 yenta_socket
amilo_rfkill           12819  0 
soundcore              12600  1 snd
microcode              18286  0 
joydev                 17097  0 
pcmcia_core            21505  3 pcmcia,pcmcia_rsrc,yenta_socket
psmouse                81065  0 
tifm_core              15068  1 tifm_7xx1
mac_hid                13037  0 
lp                     13299  0 
serio_raw              13031  0 
video                  18894  1 i915
parport                40753  1 lp
hid_generic            12484  0 
usbhid                 41805  0 
hid                    82666  2 hid_generic,usbhid
usb_storage            47684  0 
sdhci_pci              18158  0 
firewire_ohci          35292  0 
firewire_core          61718  1 firewire_ohci
b44                    31137  0 
ahci                   25507  2 
libahci                26108  1 ahci
sdhci                  31824  1 sdhci_pci
ssb                    50834  1 b44
crc_itu_t              12627  1 firewire_core
iwconfig
ra0       Ralink STA  
          Power Management:on
          
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11bg  ESSID:"Tractatus"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 24:DB:AC:72:5C:7A   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=90/100  Signal level=-39 dBm  Noise level=-90 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:1
rfkill list
0: amilo_rfkill: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

---

### Post by praseodym on 2013-09-01
You are currently connected via the internal Intel device. Try it without it:
```

sudo modprobe -rfv rt3573sta
sudo modprobe -rfv ipw2200
sudo modprobe -v rt3573sta
```
Check:```

iwconfig
dmesg | grep rt3
sudo iwlist scan
```

---

### Post by flixer on 2013-09-01
One interesting thing is that when I plugin the wireless adapter it is detected as a usb memory and when I unmount the usb memory the output of lsusb changes the output of lsusb is:
lsusb when plugged in
```
Bus 001 Device 008: ID 148f:2878 Ralink Technology, Corp. 
Bus 002 Device 002: ID 0e8f:0020 GreenAsia Inc. USB to PS/2 Adapter
Bus 003 Device 002: ID 046d:c016 Logitech, Inc. Optical Wheel Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```
and when I unmount:
```
Bus 001 Device 009: ID 0586:3421 ZyXEL Communications Corp. 
Bus 002 Device 002: ID 0e8f:0020 GreenAsia Inc. USB to PS/2 Adapter
Bus 003 Device 002: ID 046d:c016 Logitech, Inc. Optical Wheel Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

---

### Post by praseodym on 2013-09-01
Check in the storage mode:
```

sudo apt-get install usb-modeswitch
sudo usb_modeswitch -v 0x148f -p 0x2878 -w 100 -n -W -D
```
Fill a new file **/etc/usb_modeswitch.d/148f:2878** with this:
```

########################################################
# ZyXel NWD2705

DefaultVendor= 0x148f
DefaultProduct=0x2878

TargetVendor=  0x0586
TargetProduct= 0x3421

CheckSuccess=20

# MessageContent="55534243908ecd89000000000000061b000000020000000000000000000000"
```
and try again:
```
sudo usb_modeswitch -c /etc/usb_modeswitch.d/148f:2878
```

---

### Post by flixer on 2013-09-01
```
sudo usb_modeswitch -v 0x148f -p 0x2878 -w 100 -n -W -D
Taking all parameters from the command line


 * usb_modeswitch: handle USB devices with multiple modes
 * Version 1.2.5 (C) Josua Dietze 2012
 * Based on libusb0 (0.1.12 and above)

 ! PLEASE REPORT NEW CONFIGURATIONS !

DefaultVendor=  0x148f
DefaultProduct= 0x2878
TargetVendor=   not set
TargetProduct=  not set
TargetClass=    not set
TargetProductList=""

DetachStorageOnly=0
HuaweiMode=0
SierraMode=0
SonyMode=0
QisdaMode=0
GCTMode=0
KobilMode=0
SequansMode=0
MobileActionMode=0
CiscoMode=0
MessageEndpoint=  not set
MessageContent=""
NeedResponse=1
ResponseEndpoint= not set

InquireDevice disabled
Success check disabled
System integration mode enabled


usb_set_debug: Setting debugging level to 15 (on)
usb_os_find_busses: Found 005
usb_os_find_busses: Found 004
usb_os_find_busses: Found 003
usb_os_find_busses: Found 002
usb_os_find_busses: Found 001
usb_os_find_devices: Found 001 on 005
usb_os_find_devices: Found 001 on 004
usb_os_find_devices: Found 002 on 003
skipped 1 class/vendor specific interface descriptors
usb_os_find_devices: Found 001 on 003
error obtaining child information: Inappropriate ioctl for device
usb_os_find_devices: Found 002 on 002
skipped 1 class/vendor specific interface descriptors
skipped 1 class/vendor specific interface descriptors
usb_os_find_devices: Found 001 on 002
error obtaining child information: Inappropriate ioctl for device
usb_os_find_devices: Found 004 on 001
usb_os_find_devices: Found 001 on 001
error obtaining child information: Inappropriate ioctl for device
Looking for default devices ...
  searching devices, found USB ID 1d6b:0001
  searching devices, found USB ID 1d6b:0001
  searching devices, found USB ID 046d:c016
  searching devices, found USB ID 1d6b:0001
  searching devices, found USB ID 0e8f:0020
  searching devices, found USB ID 1d6b:0001
  searching devices, found USB ID 148f:2878
   found matching vendor ID
   found matching product ID
   adding device
  searching devices, found USB ID 1d6b:0002
 Found device in default mode, class or configuration (1)
Accessing device 004 on bus 001 ...
Getting the current device configuration ...
 OK, got current device configuration (1)
Using interface number 0

USB description data (for identification)
-------------------------
Manufacturer: ZyXEL
     Product: NWD2705
  Serial No.: not provided
-------------------------
Warning: no switching method given.
-> Run lsusb to note any changes. Bye.

sudo usb_modeswitch -v 0x148f -p 0x2878 -w 100 -n -W -D
Taking all parameters from the command line


 * usb_modeswitch: handle USB devices with multiple modes
 * Version 1.2.5 (C) Josua Dietze 2012
 * Based on libusb0 (0.1.12 and above)

 ! PLEASE REPORT NEW CONFIGURATIONS !

DefaultVendor=  0x148f
DefaultProduct= 0x2878
TargetVendor=   not set
TargetProduct=  not set
TargetClass=    not set
TargetProductList=""

DetachStorageOnly=0
HuaweiMode=0
SierraMode=0
SonyMode=0
QisdaMode=0
GCTMode=0
KobilMode=0
SequansMode=0
MobileActionMode=0
CiscoMode=0
MessageEndpoint=  not set
MessageContent=""
NeedResponse=1
ResponseEndpoint= not set

InquireDevice disabled
Success check disabled
System integration mode enabled


usb_set_debug: Setting debugging level to 15 (on)
usb_os_find_busses: Found 005
usb_os_find_busses: Found 004
usb_os_find_busses: Found 003
usb_os_find_busses: Found 002
usb_os_find_busses: Found 001
usb_os_find_devices: Found 001 on 005
usb_os_find_devices: Found 001 on 004
usb_os_find_devices: Found 002 on 003
skipped 1 class/vendor specific interface descriptors
usb_os_find_devices: Found 001 on 003
error obtaining child information: Inappropriate ioctl for device
usb_os_find_devices: Found 002 on 002
skipped 1 class/vendor specific interface descriptors
skipped 1 class/vendor specific interface descriptors
usb_os_find_devices: Found 001 on 002
error obtaining child information: Inappropriate ioctl for device
usb_os_find_devices: Found 005 on 001
usb_os_find_devices: Found 001 on 001
error obtaining child information: Inappropriate ioctl for device
Looking for default devices ...
  searching devices, found USB ID 1d6b:0001
  searching devices, found USB ID 1d6b:0001
  searching devices, found USB ID 046d:c016
  searching devices, found USB ID 1d6b:0001
  searching devices, found USB ID 0e8f:0020
  searching devices, found USB ID 1d6b:0001
  searching devices, found USB ID 148f:2878
   found matching vendor ID
   found matching product ID
   adding device
  searching devices, found USB ID 1d6b:0002
 Found device in default mode, class or configuration (1)
Accessing device 005 on bus 001 ...
Getting the current device configuration ...
 OK, got current device configuration (1)
Using interface number 0

USB description data (for identification)
-------------------------
Manufacturer: ZyXEL
     Product: NWD2705
  Serial No.: not provided
-------------------------
Warning: no switching method given.
-> Run lsusb to note any changes. Bye.
```

Second usb-modeswitch command:

```
sudo usb_modeswitch -c /etc/usb_modeswitch.d/148f:2878
Looking for target devices ...
 No devices in target mode or class found
Looking for default devices ...
   found matching product ID
   adding device
 Found device in default mode, class or configuration (1)
Accessing device 005 on bus 001 ...
Getting the current device configuration ...
 OK, got current device configuration (1)
Using interface number 0
Using endpoints 0x01 (out) and 0x81 (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
 OK, driver found ("usb-storage")
 OK, driver "usb-storage" detached

SCSI inquiry data (for identification)
-------------------------
  Vendor String: NWD2705 
   Model String: Autorun         
Revision String: 0.01
-------------------------

USB description data (for identification)
-------------------------
Manufacturer: ZyXEL
     Product: NWD2705
  Serial No.: not provided
-------------------------
Warning: no switching method given.

Checking for mode switch (max. 20 times, once per second) ...
 Searching for target devices ...
 Searching for target devices ...
 Searching for target devices ...
 Searching for target devices ...
 Searching for target devices ...
 Searching for target devices ...
 Searching for target devices ...
 Searching for target devices ...
 Searching for target devices ...
 Searching for target devices ...
 Searching for target devices ...
 Searching for target devices ...
 Searching for target devices ...
 Searching for target devices ...
 Searching for target devices ...
 Searching for target devices ...
 Searching for target devices ...
 Searching for target devices ...
 Searching for target devices ...
 Searching for target devices ...
 No new devices in target mode or class found

Mode switch has failed. Bye.
```


Dmesg when plugged in before the usb-modeswitch instructions you gave:

```

[ 1385.656184] usb 1-1: new high-speed USB device number 5 using ehci-pci
[ 1385.791296] usb 1-1: New USB device found, idVendor=148f, idProduct=2878
[ 1385.791321] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 1385.791341] usb 1-1: Product: NWD2705
[ 1385.791359] usb 1-1: Manufacturer: ZyXEL
[ 1385.800020] scsi7 : usb-storage 1-1:1.0
[ 1386.797445] scsi 7:0:0:0: CD-ROM            NWD2705  Autorun          0.01 PQ: 0 ANSI: 0 CCS
[ 1386.804692] sr1: scsi3-mmc drive: 52x/52x cd/rw xa/form2 cdda tray
[ 1386.805435] sr 7:0:0:0: Attached scsi CD-ROM sr1
[ 1386.807170] sr 7:0:0:0: Attached scsi generic sg2 type 5
[ 1387.270291] ISO 9660 Extensions: Microsoft Joliet Level 1
[ 1387.280020] ISOFS: changing to secondary root
```

---

### Post by praseodym on 2013-09-02
Please try to swap Target and Product/Vendor IDs in the file and run it again

---

### Post by flixer on 2013-09-03
If I change swap their places I get an error where DefaultVendor or TargetVendor is not found.
I took the comment out of the MessageContent line.
I still get the same errors in dmesg plus modeswitch errors.
```
########################################################
# ZyXel NWD2705

DefaultVendor= 0x148f
DefaultProduct=0x2878

TargetVendor=  0x0586
TargetProduct= 0x3421

CheckSuccess=20
MessageContent="55534243908ecd89000000000000061b000000020000000000000000000000"

```


```
sudo usb_modeswitch -c /etc/usb_modeswitch.d/148f:2878
Looking for target devices ...
 No devices in target mode or class found
Looking for default devices ...
   found matching product ID
   adding device
 Found device in default mode, class or configuration (1)
Accessing device 009 on bus 001 ...
Getting the current device configuration ...
 OK, got current device configuration (1)
Using interface number 0
Using endpoints 0x01 (out) and 0x81 (in)
Inquiring device details; driver will be detached ...
Looking for active driver ...
 No driver found. Either detached before or never attached

SCSI inquiry data (for identification)
-------------------------
  Vendor String: NWD2705 
   Model String: Autorun         
Revision String: 0.01
-------------------------

USB description data (for identification)
-------------------------
Manufacturer: ZyXEL
     Product: NWD2705
  Serial No.: not provided
-------------------------
Setting up communication with interface 0
Using endpoint 0x01 for message sending ...
Trying to send message 1 to endpoint 0x01 ...
 Device seems to have vanished right after sending. Good.
 Device is gone, skipping any further commands

Checking for mode switch (max. 20 times, once per second) ...
 Searching for target devices ...
   found matching product ID
   adding device

Found target device, now opening
Error: could not get description string "manufacturer"
Error: could not get description string "product"
Error: could not get description string "serial number"
 Found correct target device

Mode switch succeeded. Bye.
```

```
[ 9434.940023] usb 1-1: usbfs: process 4282 (usb_modeswitch) did not claim interface 0 before use
[ 9434.940660] usb 1-1: USB disconnect, device number 11
[ 9435.292190] usb 1-1: new high-speed USB device number 12 using ehci-pci
[ 9435.427974] usb 1-1: New USB device found, idVendor=0586, idProduct=3421
[ 9435.427999] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 9435.428019] usb 1-1: Product: NWD2705
[ 9435.428036] usb 1-1: Manufacturer: ZyXEL
[ 9435.428053] usb 1-1: SerialNumber: 1.0
[ 9435.439523] 
[ 9435.439523] 
[ 9435.439523] === pAd = f953f000, size = 562656 ===
[ 9435.439523] 
[ 9435.440018] <-- RTMPAllocTxRxRingMemory, Status=0
[ 9435.440018] <-- RTMPAllocAdapterBlock, Status=0
[ 9435.440018] (Reassign Efuse for 3x7x/3x9x/53xx) Size=0x3c [3c0-3fb] 
[ 9435.604464] #
[ 9435.680464] #
[ 9435.756336] #
[ 9435.832338] #
[ 9435.908338] #
[ 9435.984352] #
[ 9436.060346] #
[ 9436.136340] #
[ 9436.212336] #
[ 9436.288340] #
[ 9436.292243] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=OUT, Req=0x2, Idx=0x334a,pAd->Flags=0x0
[ 9436.292243] 	Request Value=0xf008!
[ 9436.364342] #
[ 9436.440342] #
[ 9436.516346] #
[ 9436.592343] #
[ 9436.668344] #
[ 9436.744345] #
[ 9436.820347] #
[ 9436.896348] #
[ 9436.972349] #
[ 9437.000620] usb 1-1: usbfs: USBDEVFS_CONTROL failed cmd usb_modeswitch rqt 128 rq 6 len 255 ret -110
[ 9437.048361] #
[ 9437.052253] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=OUT, Req=0x2, Idx=0x334c,pAd->Flags=0x0
[ 9437.052253] 	Request Value=0x3b75!
[ 9437.124359] #
[ 9437.200351] #
[ 9437.276356] #
[ 9437.352352] #
[ 9437.428352] #
[ 9437.504356] #
[ 9437.580434] #
[ 9437.656364] #
[ 9437.732357] #
[ 9437.808358] #
[ 9437.812262] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=OUT, Req=0x2, Idx=0x334e,pAd->Flags=0x0
[ 9437.812262] 	Request Value=0xe418!
[ 9437.884361] #
[ 9437.960360] #
[ 9438.000625] usb 1-1: usbfs: USBDEVFS_CONTROL failed cmd usb_modeswitch rqt 128 rq 6 len 255 ret -110
[ 9438.036368] #
[ 9438.112365] #
[ 9438.188366] #
[ 9438.264366] #
[ 9438.340365] #
[ 9438.416364] #
[ 9438.492373] #
[ 9438.568370] #
[ 9438.572273] RTUSB_VendorRequest failed(-110),TxFlags=0x0, ReqType=OUT, Req=0x2, Idx=0x3350,pAd->Flags=0x0
[ 9438.572273] 	Request Value=0x26f5!
[ 9438.644372] #
[ 9438.720370] #
[ 9438.796359] #
[ 9438.872375] #
[ 9438.948372] #
[ 9439.000528] usb 1-1: usbfs: USBDEVFS_CONTROL failed cmd usb_modeswitch rqt 128 rq 6 len 255 ret -110
```

---

