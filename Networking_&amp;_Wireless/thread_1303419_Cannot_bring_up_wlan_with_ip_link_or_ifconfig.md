---
title: "Cannot bring up wlan with ip link or ifconfig"
date: 2009-10-28
forum: Networking &amp; Wireless
---

### Post by vaessen on 2009-10-28
I have a Fritz!Box Fon WLAN 7170 as router and try to connect wireless to
it with the Fritz!WLAN USB N2.4 stick using the compat-wireless software.
Without succes so far.

Software: yesterdays bleeding edge tarball: compat-wireless-2.6.tar.bz2
Kernel: Ubuntu 9.04 2.6.28-16-generic
PC: Athec L51A10
Firmware: ar9170.fw put in /lib/firmware

The software compiles without problem and installs the driver after reboot:

sudo lsmod | grep 9170 gives:
ar9170usb 63624 0
led_class 12036 1 ar9170usb
ath 17024 1 ar9170usb
mac80211 218160 1 ar9170usb
cfg80211 135240 3 ar9170usb,ath,mac80211

After inserting the usb stick, this is shown in /var/log/messages

Oct 25 15:37:00 vaessen-laptop kernel: [ 301.480049] usb 1-1: new high
speed USB device using ehci_hcd and address 5
Oct 25 15:37:00 vaessen-laptop kernel: [ 301.643507] usb 1-1:
configuration #1 chosen from 1 choice
Oct 25 15:37:00 vaessen-laptop kernel: [ 301.702461] Initializing USB Mass
Storage driver...
Oct 25 15:37:00 vaessen-laptop kernel: [ 301.702650] scsi4 : SCSI
emulation for USB Mass Storage devices
Oct 25 15:37:00 vaessen-laptop kernel: [ 301.702803] usbcore: registered
new interface driver usb-storage
Oct 25 15:37:00 vaessen-laptop kernel: [ 301.702808] USB Mass Storage
support registered.
Oct 25 15:37:05 vaessen-laptop kernel: [ 306.709252] scsi 4:0:0:0: CD-ROM
FRITZ! WLAN selfinstall 1.00 PQ: 0 ANSI: 0 CCS
Oct 25 15:37:05 vaessen-laptop kernel: [ 306.722276] sr1: scsi3-mmc drive:
52x/52x cd/rw xa/form2 cdda tray
Oct 25 15:37:05 vaessen-laptop kernel: [ 306.723067] sr 4:0:0:0: Attached
scsi generic sg2 type 5

Oct 25 15:38:38 vaessen-laptop kernel: [ 399.349605] usb 1-1: USB
disconnect, address 5
Oct 25 15:38:39 vaessen-laptop kernel: [ 400.608057] usb 1-1: new high
speed USB device using ehci_hcd and address 6
Oct 25 15:38:39 vaessen-laptop kernel: [ 400.771795] usb 1-1:
configuration #1 chosen from 1 choice
Oct 25 15:38:39 vaessen-laptop kernel: [ 400.888063] usb 1-1: reset high
speed USB device using ehci_hcd and address 6
Oct 25 15:38:40 vaessen-laptop kernel: [ 402.044043] usb 1-1: firmware:
requesting ar9170.fw
Oct 25 15:38:41 vaessen-laptop kernel: [ 402.465806] Registered led
device: ar9170-phy1::tx
Oct 25 15:38:41 vaessen-laptop kernel: [ 402.465846] Registered led
device: ar9170-phy1::assoc
Oct 25 15:38:41 vaessen-laptop kernel: [ 402.465851] usb 1-1: Atheros
AR9170 is registered as 'phy1'
Oct 25 15:38:41 vaessen-laptop kernel: [ 402.471136] udev: renamed network
interface wlan0 to wlan1

Command iwconfig:

lo no wireless extensions.

eth0 no wireless extensions.

pan0 no wireless extensions.

wlan1 IEEE 802.11bg Mode:Managed Access Point: Not-Associated
Tx-Power=0 dBm
Retry long limit:7 RTS thrff Fragment thrff
Power Managementff

Command sudo lshw -C network gives for the wireless this information:

*-network:1 DISABLED
description: Wireless interface
physical id: 2
bus info: usb@1:1
logical name: wlan1
serial: 00:1f:3f:09:2d:40
capabilities: ethernet physical wireless
configuration: broadcast=yes driver=ar9170usb
driverversion=2.6.28-16-generic firmware=N/A link=yes multicast=yes
wireless=IEEE 802.11bg



I tried to activate wlan1 by using command:
sudo ifconfig wlan1 up
but that gives an error: 
SIOCSIFFLAGS: Operation not permitted

Another command:
sudo ip link set wlan1 up
gives an error too:
RTNETLINK answers: Operation not permitted


Can anybody help me?

---

### Post by chili555 on 2009-10-28
> firmware=N/AI wonder if this is a problem. Let's see if the kernel has any clues:```
sudo cat /var/log/messages | grep firm
dmesg | grep firm
```I'd also love to see if the permissions are correct for the firmware you added:```
ls -al /lib/firmware
```Thanks.

---

### Post by vaessen on 2009-10-28
Hello Chili555,

Here some information:


sudo cat /var/log/messages | grep firm  gives:

Oct 28 13:21:59 vaessen-laptop kernel: [ 3111.120044] usb 1-1: firmware: requesting ar9170.fw

If I rename the file ar9170.fw to something else, this message is given:

Oct 28 12:55:56 vaessen-laptop firmware.sh[4533]: Cannot find  firmware file 'ar9170.fw'

dmesg | grep firm gives:

[ 3111.120044] usb 1-1: firmware: requesting ar9170.fw

in /lib/firmware this file is present:

-rw-r--r--  1 root root  15960 2009-10-25 15:04 ar9170.fw


Ed

---

### Post by chili555 on 2009-10-28
Great! Everything looks perfect. Are you using Network Manager? If so, it may not allow command line manipulation of network interfaces.

*wlan1* is configured:> wlan1 IEEE 802.11bg Mode:Managed Access Point: Not-Associated
Tx-Power=0 dBm
Retry long limit:7 RTS thrff Fragment thrff
Power ManagementffIf you click the Network Manager icon, does it connect?

---

### Post by vaessen on 2009-10-28
Unfortunately no.
The network manager does not show any wireless network present, even though my laptop is next to the router. I can only connect by ethernet cable to that router (which I am doing now).
What I see is that a command like 

sudo ip link set wlan1 down

 gives no message, whereas 

sudo ip link set wlan1 up

gives:

RTNETLINK answers: Operation not permitted


Ed

---

### Post by chili555 on 2009-10-28
May we see:```
cat /etc/network/interfaces
```Does Network Manager show a wireless interface as available, or is it grayed out?

---

### Post by vaessen on 2009-10-28
> **chili555 said:**
> May we see:```
cat /etc/network/interfaces
```Does Network Manager show a wireless interface as available, or is it grayed out?
The icon is that of a wireless interface in gray (with these vertical bars) and a red cross or something like it.
Clicking on it shows that the wireless interface is grayed out.
One can of course create a new wireless network but I fear that my stick is simply unable to see a network as it is not driven properly yet.

iwlist wlan1 scanning gives:

wlan1     Failed to read scan data : Network is down

The command 
cat /etc/network/interfaces 
gives:

auto lo
iface lo inet loopback

---

