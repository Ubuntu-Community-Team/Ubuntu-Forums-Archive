---
title: "No connection with Fritz!WLAN USB stick"
date: 2009-10-25
forum: Networking &amp; Wireless
---

### Post by vaessen on 2009-10-25
I have a Fritz!Box Fon WLAN 7170 as router and try to connect wireless to it with the Fritz!WLAN USB N2.4 stick using the compat-wireless software.
Without succes so far.

Software: bleeding edge tarball: compat-wireless-2.6.tar.bz2
Kernel: 2.6.28-16-generic
Firmware: ar9170.fw put in /lib/firmware

The software compiles without problem and installs the driver after reboot:

sudo lsmod | grep 9170 gives:
ar9170usb              63624  0 
led_class              12036  1 ar9170usb
ath                    17024  1 ar9170usb
mac80211              218160  1 ar9170usb
cfg80211              135240  3 ar9170usb,ath,mac80211

After inserting the usb stick, this is shown in /var/log/messages

Oct 25 15:37:00 vaessen-laptop kernel: [  301.480049] usb 1-1: new high speed USB device using ehci_hcd and address 5
Oct 25 15:37:00 vaessen-laptop kernel: [  301.643507] usb 1-1: configuration #1 chosen from 1 choice
Oct 25 15:37:00 vaessen-laptop kernel: [  301.702461] Initializing USB Mass Storage driver...
Oct 25 15:37:00 vaessen-laptop kernel: [  301.702650] scsi4 : SCSI emulation for USB Mass Storage devices
Oct 25 15:37:00 vaessen-laptop kernel: [  301.702803] usbcore: registered new interface driver usb-storage
Oct 25 15:37:00 vaessen-laptop kernel: [  301.702808] USB Mass Storage support registered.
Oct 25 15:37:05 vaessen-laptop kernel: [  306.709252] scsi 4:0:0:0: CD-ROM            FRITZ!   WLAN selfinstall 1.00 PQ: 0 ANSI: 0 CCS
Oct 25 15:37:05 vaessen-laptop kernel: [  306.722276] sr1: scsi3-mmc drive: 52x/52x cd/rw xa/form2 cdda tray
Oct 25 15:37:05 vaessen-laptop kernel: [  306.723067] sr 4:0:0:0: Attached scsi generic sg2 type 5

Oct 25 15:38:38 vaessen-laptop kernel: [  399.349605] usb 1-1: USB disconnect, address 5
Oct 25 15:38:39 vaessen-laptop kernel: [  400.608057] usb 1-1: new high speed USB device using ehci_hcd and address 6
Oct 25 15:38:39 vaessen-laptop kernel: [  400.771795] usb 1-1: configuration #1 chosen from 1 choice
Oct 25 15:38:39 vaessen-laptop kernel: [  400.888063] usb 1-1: reset high speed USB device using ehci_hcd and address 6
Oct 25 15:38:40 vaessen-laptop kernel: [  402.044043] usb 1-1: firmware: requesting ar9170.fw
Oct 25 15:38:41 vaessen-laptop kernel: [  402.465806] Registered led device: ar9170-phy1::tx
Oct 25 15:38:41 vaessen-laptop kernel: [  402.465846] Registered led device: ar9170-phy1::assoc
Oct 25 15:38:41 vaessen-laptop kernel: [  402.465851] usb 1-1: Atheros AR9170 is registered as 'phy1'
Oct 25 15:38:41 vaessen-laptop kernel: [  402.471136] udev: renamed network interface wlan0 to wlan1

It seems the firmware is installed. At least, there is no complaint about it not being found.
Command iwconfig:
 
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

wlan1     IEEE 802.11bg  Mode:Managed  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

Command sudo lshw -C network gives for the wireless this information:

  *-network:1 DISABLED
       description: Wireless interface
       physical id: 2
       bus info: usb@1:1
       logical name: wlan1
       serial: 00:1f:3f:09:2d:40
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ar9170usb driverversion=2.6.28-16-generic firmware=N/A link=yes multicast=yes wireless=IEEE 802.11bg

This 'firmware=N/A' puzzles me.
 
I used System->Administration->Network Tools but cannot ping the Fritz!Box router
The interface information says that wireless interface wlan1 is inactive.

---

### Post by vaessen on 2009-10-25
I have a Fritz!Box Fon WLAN 7170 as router and try to connect wireless to it with the Fritz!WLAN USB N2.4 stick using the compat-wireless software.
Without succes so far.

Software: bleeding edge tarball: compat-wireless-2.6.tar.bz2
Kernel: 2.6.28-16-generic
Firmware: ar9170.fw put in /lib/firmware

The software compiles without problem and installs the driver after reboot:

sudo lsmod | grep 9170 gives:
ar9170usb              63624  0 
led_class              12036  1 ar9170usb
ath                    17024  1 ar9170usb
mac80211              218160  1 ar9170usb
cfg80211              135240  3 ar9170usb,ath,mac80211

After inserting the usb stick, this is shown in /var/log/messages

Oct 25 15:37:00 vaessen-laptop kernel: [  301.480049] usb 1-1: new high speed USB device using ehci_hcd and address 5
Oct 25 15:37:00 vaessen-laptop kernel: [  301.643507] usb 1-1: configuration #1 chosen from 1 choice
Oct 25 15:37:00 vaessen-laptop kernel: [  301.702461] Initializing USB Mass Storage driver...
Oct 25 15:37:00 vaessen-laptop kernel: [  301.702650] scsi4 : SCSI emulation for USB Mass Storage devices
Oct 25 15:37:00 vaessen-laptop kernel: [  301.702803] usbcore: registered new interface driver usb-storage
Oct 25 15:37:00 vaessen-laptop kernel: [  301.702808] USB Mass Storage support registered.
Oct 25 15:37:05 vaessen-laptop kernel: [  306.709252] scsi 4:0:0:0: CD-ROM            FRITZ!   WLAN selfinstall 1.00 PQ: 0 ANSI: 0 CCS
Oct 25 15:37:05 vaessen-laptop kernel: [  306.722276] sr1: scsi3-mmc drive: 52x/52x cd/rw xa/form2 cdda tray
Oct 25 15:37:05 vaessen-laptop kernel: [  306.723067] sr 4:0:0:0: Attached scsi generic sg2 type 5

Oct 25 15:38:38 vaessen-laptop kernel: [  399.349605] usb 1-1: USB disconnect, address 5
Oct 25 15:38:39 vaessen-laptop kernel: [  400.608057] usb 1-1: new high speed USB device using ehci_hcd and address 6
Oct 25 15:38:39 vaessen-laptop kernel: [  400.771795] usb 1-1: configuration #1 chosen from 1 choice
Oct 25 15:38:39 vaessen-laptop kernel: [  400.888063] usb 1-1: reset high speed USB device using ehci_hcd and address 6
Oct 25 15:38:40 vaessen-laptop kernel: [  402.044043] usb 1-1: firmware: requesting ar9170.fw
Oct 25 15:38:41 vaessen-laptop kernel: [  402.465806] Registered led device: ar9170-phy1::tx
Oct 25 15:38:41 vaessen-laptop kernel: [  402.465846] Registered led device: ar9170-phy1::assoc
Oct 25 15:38:41 vaessen-laptop kernel: [  402.465851] usb 1-1: Atheros AR9170 is registered as 'phy1'
Oct 25 15:38:41 vaessen-laptop kernel: [  402.471136] udev: renamed network interface wlan0 to wlan1

It seems the firmware is installed. At least, there is no complaint about it not being found.
Command iwconfig:
 
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

wlan1     IEEE 802.11bg  Mode:Managed  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

Command sudo lshw -C network gives for the wireless this information:

  *-network:1 DISABLED
       description: Wireless interface
       physical id: 2
       bus info: usb@1:1
       logical name: wlan1
       serial: 00:1f:3f:09:2d:40
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ar9170usb driverversion=2.6.28-16-generic firmware=N/A link=yes multicast=yes wireless=IEEE 802.11bg

This 'firmware=N/A' puzzles me.
 
I used System->Administration->Network Tools but cannot ping the Fritz!Box router
The interface information says that wireless interface wlan1 is inactive.

---

### Post by PriceChild on 2009-10-25
Duplicate thread. Other here: [http://ubuntuforums.org/showthread.php?t=1300771](http://ubuntuforums.org/showthread.php?t=1300771)

---

