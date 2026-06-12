---
title: "compact-wireless driver issue | tl-wn722n | atheros chipset - 9271"
date: 2012-02-18
forum: Networking &amp; Wireless
---

### Post by floorripper on 2012-02-18
Hello,

After installation my original wifi driver **iwl3945** become disabled and I cannot modprobe it back!


majo@laptop:~/tl-wn722n$ sudo modprobe iwl3945
[sudo] password for majo: 
[SIZE=2][COLOR=DarkRed]FATAL: Error inserting iwl3945  (/lib/modules/2.6.32-38-generic/kernel/drivers/net/wireless/iwlwifi/iwl3945.ko):  Unknown symbol in module, or unknown parameter (see dmesg)
[/COLOR][/SIZE] 
I bought a new TP-link usb wifi adapter. tl-wn722n.
I had several issues during installation. But then installed it.
followed this page:
[http://dwiel.net/blog/tp-link-tl-wn7...-ubuntu-10-04/]("http://dwiel.net/blog/tp-link-tl-wn722n-on-ubuntu-10-04/")

I have downloaded and installed
[B]compat-wireless-2.6.38.2-2.tar.bz2
[/B]

my current kernel is:
[COLOR=Sienna]2.6.32-38-generic
Ubuntu 10.04.4 LTS \n \l[/COLOR]

I am attaching some show commands and DMESG file.
Please help.

root@laptop:/home/majo/airtest# lsusb 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0b05:1712 ASUSTek Computer, Inc. BT-183 Bluetooth 2.0+EDR adapter
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 0cf3:9271 Atheros Communications, Inc. 
Bus 001 Device 004: ID 174f:a311 Syntek 1.3MPixel Web Cam - Asus A3A, A6J, A6K, A6M, A6R, A6T, A6V, A7T, A7sv, A7U
Bus 001 Device 002: ID 1e3d:2092  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

-------------------------------------------------------------------------
root@laptop:/home/majo/airtest# hwinfo --wlan
16: PCI 300.0: 0282 WLAN controller                             
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_8086_4222
  Unique ID: svHJ.voNJAxCYCzB
  Parent ID: Z7uZ.f4r+Yl3RyX5
  SysFS ID: /devices/pci0000:00/0000:00:1c.3/0000:03:00.0
  SysFS BusID: 0000:03:00.0
  Hardware Class: network
  Model: "Intel PRO/Wireless 3945ABG Network Connection"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x4222 "PRO/Wireless 3945ABG [Golan] Network Connection"
  SubVendor: pci 0x8086 "Intel Corporation"
  SubDevice: pci 0x1001 "PRO/Wireless 3945ABG Network Connection"
  Revision: 0x02
  Features: WLAN
  Memory Range: 0xfe1ff000-0xfe1fffff (rw,non-prefetchable)
  IRQ: 3 (no events)
  Module Alias: "pci:v00008086d00004222sv00008086sd00001001bc02sc80i00"
  Driver Info #0:
    Driver Status: iwl3945 is not active
    Driver Activation Cmd: "modprobe iwl3945"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #5 (PCI bridge)
----------------------------------------------------------------------
hwinfo --usb
16: USB 00.0: 0000 Unclassified device
  [Created at usb.122]
  UDI: /org/freedesktop/Hal/devices/usb_device_cf3_9271_12345_if0
  Unique ID: Uc5H.7OI4S6n4RF2
  Parent ID: k4bc.9T1GDCLyFd9
  SysFS ID: /devices/pci0000:00/0000:00:1d.7/usb1/1-4/1-4:1.0
  SysFS BusID: 1-4:1.0
  Hardware Class: unknown
  Model: "Atheros USB2.0 WLAN"
  Hotplug: USB
  Vendor: usb 0x0cf3 "Atheros Communications, Inc."
  Device: usb 0x9271 "USB2.0 WLAN"
  Revision: "1.08"
  Serial ID: "12345"
  Driver: "ath9k_hif_usb"
  Driver Modules: "ath9k_htc"
  Speed: 480 Mbps
  Module Alias: "usb:v0CF3p9271d0108dcFFdscFFdpFFicFFisc00ip00"
  Driver Info #0:
    Driver Status: ath9k_htc is active
    Driver Activation Cmd: "modprobe ath9k_htc"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #6 (Hub)
---------------------------------------------------------------------------

majo@laptop:~$ sudo modprobe iwl3945
FATAL: Error inserting iwl3945  (/lib/modules/2.6.32-38-generic/kernel/drivers/net/wireless/iwlwifi/iwl3945.ko):  Unknown symbol in module, or unknown parameter (see dmesg)

FATAL: Error inserting iwlagn (/lib/modulroot@laptop:/home/majo/airtest# lsusb 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 0b05:1712 ASUSTek Computer, Inc. BT-183 Bluetooth 2.0+EDR adapter
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 0cf3:9271 Atheros Communications, Inc. 
Bus 001 Device 004: ID 174f:a311 Syntek 1.3MPixel Web Cam - Asus A3A, A6J, A6K, A6M, A6R, A6T, A6V, A7T, A7sv, A7U
Bus 001 Device 002: ID 1e3d:2092  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

-------------------------------------------------------------------------
root@laptop:/home/majo/airtest# hwinfo --wlan
16: PCI 300.0: 0282 WLAN controller                             
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_8086_4222
  Unique ID: svHJ.voNJAxCYCzB
  Parent ID: Z7uZ.f4r+Yl3RyX5
  SysFS ID: /devices/pci0000:00/0000:00:1c.3/0000:03:00.0
  SysFS BusID: 0000:03:00.0
  Hardware Class: network
  Model: "Intel PRO/Wireless 3945ABG Network Connection"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x4222 "PRO/Wireless 3945ABG [Golan] Network Connection"
  SubVendor: pci 0x8086 "Intel Corporation"
  SubDevice: pci 0x1001 "PRO/Wireless 3945ABG Network Connection"
  Revision: 0x02
  Features: WLAN
  Memory Range: 0xfe1ff000-0xfe1fffff (rw,non-prefetchable)
  IRQ: 3 (no events)
  Module Alias: "pci:v00008086d00004222sv00008086sd00001001bc02sc80i00"
  Driver Info #0:
    Driver Status: iwl3945 is not active
    Driver Activation Cmd: "modprobe iwl3945"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #5 (PCI bridge)
----------------------------------------------------------------------
hwinfo --usb
16: USB 00.0: 0000 Unclassified device
  [Created at usb.122]
  UDI: /org/freedesktop/Hal/devices/usb_device_cf3_9271_12345_if0
  Unique ID: Uc5H.7OI4S6n4RF2
  Parent ID: k4bc.9T1GDCLyFd9
  SysFS ID: /devices/pci0000:00/0000:00:1d.7/usb1/1-4/1-4:1.0
  SysFS BusID: 1-4:1.0
  Hardware Class: unknown
  Model: "Atheros USB2.0 WLAN"
  Hotplug: USB
  Vendor: usb 0x0cf3 "Atheros Communications, Inc."
  Device: usb 0x9271 "USB2.0 WLAN"
  Revision: "1.08"
  Serial ID: "12345"
  Driver: "ath9k_hif_usb"
  Driver Modules: "ath9k_htc"
  Speed: 480 Mbps
  Module Alias: "usb:v0CF3p9271d0108dcFFdscFFdpFFicFFisc00ip00"
  Driver Info #0:
    Driver Status: ath9k_htc is active
    Driver Activation Cmd: "modprobe ath9k_htc"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #6 (Hub)
---------------------------------------------------------------------------

majo@laptop:~$ sudo modprobe iwl3945
FATAL: Error inserting iwl3945  (/lib/modules/2.6.32-38-generic/kernel/drivers/net/wireless/iwlwifi/iwl3945.ko):  Unknown symbol in module, or unknown parameter (see dmesg)

FATAL: Error inserting iwlagn  (/lib/modules/2.6.32-38-generic/kernel/drivers/net/wireless/iwlwifi/iwlagn.ko):  Unknown symbol in module, or unknown parameter (see dmesg)




es/2.6.32-38-generic/kernel/drivers/net/wireless/iwlwifi/iwlagn.ko): Unknown symbol in module, or unknown parameter (see dmesg)

---

### Post by wildmanne39 on 2012-02-18
Hi, the problem you are having at the moment is that you are trying to build the wrong driver version for the kernel you are using.> 2.6.32-38-generic> compat-wireless-2.6.38.2-2.tar.bz2see the difference?

I am not convinced building the driver is necessary, please post:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by praseodym on 2012-02-18
Hi,

install the backported kernel and the firmware:

```
sudo apt-get install linux-image-generic-lts-backport-natty linux-headers-generic-lts-backport-natty
wget http://media.cdn.ubuntu-de.org/forum/attachments/26/23/2640681-ath_htc_firmware-1-1.tar.gz
sudo tar xvf 2640681-ath_htc_firmware-1-1.tar.gz -C /lib/firmware 
```
and reboot.

---

### Post by floorripper on 2012-03-04
Here is the output, please advise....

```
majo@laptop:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.4 LTS"
Linux laptop 2.6.32-38-generic #83-Ubuntu SMP Wed Jan 4 11:13:04 UTC 2012 i686 GNU/Linux
majo@laptop:~$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 01)
    Kernel driver in use: r8169
    Kernel modules: r8169
03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)
    Kernel modules: iwl3945
04:01.0 CardBus bridge [0607]: Ricoh Co Ltd RL5c476 II [1180:0476] (rev b3)
majo@laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan1     IEEE 802.11bgn  ESSID:"blabla"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:12:B0:67:D1:C3   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=29/70  Signal level=-81 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:647   Missed beacon:0

pan0      no wireless extensions.

mon0      IEEE 802.11bgn  Mode:Monitor  Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
majo@laptop:~$ rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

---

### Post by floorripper on 2012-03-04
Hello Praseodym,

Your solution worked perfectly.THATS AMAZING. THANKS.
Now I am able to use both adapters.
But it seems to be that I have upgraded kernel, should not be that a problem for another applications already installed? Will not I get problems when getting applications from default  repositories or some dependencies issues?



> **praseodym said:**
> Hi,

install the backported kernel and the firmware:

```
sudo apt-get install linux-image-generic-lts-backport-natty linux-headers-generic-lts-backport-natty
wget http://media.cdn.ubuntu-de.org/forum/attachments/26/23/2640681-ath_htc_firmware-1-1.tar.gz
sudo tar xvf 2640681-ath_htc_firmware-1-1.tar.gz -C /lib/firmware 
```and reboot.

```

majo@laptop:~$ hwinfo --wlan
16: PCI 300.0: 0282 WLAN controller                             
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_8086_4222
  Unique ID: y9sn.xDGkhUDfcCA
  Parent ID: Z7uZ.69Og7fkiPQ2
  SysFS ID: /devices/pci0000:00/0000:00:1c.3/0000:03:00.0
  SysFS BusID: 0000:03:00.0
  Hardware Class: network
  Model: "Intel PRO/Wireless 3945ABG Network Connection"
  Vendor: pci 0x8086 "Intel Corporation"
  Device: pci 0x4222 "PRO/Wireless 3945ABG [Golan] Network Connection"
  SubVendor: pci 0x8086 "Intel Corporation"
  SubDevice: pci 0x1001 "PRO/Wireless 3945ABG Network Connection"
  Revision: 0x02
  Driver: "iwl3945"
  Driver Modules: "iwl3945"
  Device File: wlan0
  Features: WLAN
  Memory Range: 0xfe1ff000-0xfe1fffff (rw,non-prefetchable)
  IRQ: 44 (no events)
  HW Address: 00:13:02:9b:49:4e
  Link detected: no
  WLAN channels: 1 2 3 4 5 6 7 8 9 10 11 12 13
  WLAN frequencies: 2.412 2.417 2.422 2.427 2.432 2.437 2.442 2.447 2.452 2.457 2.462 2.467 2.472
  WLAN encryption modes: WEP40 WEP104 TKIP CCMP
  WLAN authentication modes: open sharedkey wpa-psk wpa-eap
  Module Alias: "pci:v00008086d00004222sv00008086sd00001001bc02sc80i00"
  Driver Info #0:
    Driver Status: iwl3945 is active
    Driver Activation Cmd: "modprobe iwl3945"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #5 (PCI bridge)
```


```
majo@laptop:~$ uname -r
2.6.38-13-generic

```

---

