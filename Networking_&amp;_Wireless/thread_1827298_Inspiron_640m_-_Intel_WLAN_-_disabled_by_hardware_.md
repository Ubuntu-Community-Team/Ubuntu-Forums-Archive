---
title: "Inspiron 640m - Intel WLAN - disabled by hardware switch"
date: 2011-08-17
forum: Networking &amp; Wireless
---

### Post by _sphinx_ on 2011-08-17
Wireless doesn't glow up even after pressing the hardware switch. Following are the detail of the system:
```

$rfkill list all
0: dell-wifi: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
1: dell-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

$ lspci | grep -i wireless
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

$iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
$iwlist scan 2>&1| grep wlan0 
wlan0     Failed to read scan data : Network is down

$lsb_release -d
Description:	Ubuntu 11.04

$uname -mr
2.6.38-10-generic i686

```
lsmod/dmesg doesn't give any useful messages. The wireless was working perfectly fine before the upgrade from 10.10 to 11.04. Also I get the following message in the /var/log/syslog upon pressing the hardware switch to enable the wireless adopter.
```

Aug 18 03:33:08 soni kernel: [ 1228.062610] keyboard: can't emulate rawmode for keycode 240
Aug 18 03:33:08 soni kernel: [ 1228.062632] keyboard: can't emulate rawmode for keycode 240
Aug 18 03:33:09 soni kernel: [ 1228.544168] usb 3-1: new full speed USB device using uhci_hcd and address 6
Aug 18 03:33:09 soni bluetoothd[3727]: Bluetooth deamon 4.91
Aug 18 03:33:09 soni bluetoothd[3729]: Starting SDP server
Aug 18 03:33:09 soni bluetoothd[3729]: Listening for HCI events on hci0
Aug 18 03:33:09 soni NetworkManager[732]: <warn> bluez error getting default adapter: No such adapter
Aug 18 03:33:09 soni bluetoothd[3729]: HCI dev 0 up
Aug 18 03:33:09 soni bluetoothd[3729]: input-headset driver probe failed for device 00:1B:33:D1:38:43
Aug 18 03:33:09 soni bluetoothd[3729]: input-headset driver probe failed for device 18:86:AC:73:03:5C
Aug 18 03:33:09 soni bluetoothd[3729]: input-headset driver probe failed for device 00:25:47:97:CE:13
Aug 18 03:33:09 soni bluetoothd[3729]: input-headset driver probe failed for device D8:54:3A:64:A0:D6
Aug 18 03:33:09 soni bluetoothd[3729]: Adapter /org/bluez/3727/hci0 has been enabled
Aug 18 03:33:12 soni bluetoothd[3729]: HCI dev 0 down
Aug 18 03:33:12 soni bluetoothd[3729]: Adapter /org/bluez/3727/hci0 has been disabled
Aug 18 03:33:12 soni kernel: [ 1231.736187] usb 3-1: USB disconnect, address 6
Aug 18 03:33:12 soni kernel: [ 1231.737210] btusb_intr_complete: hci0 urb dce6f900 failed to resubmit (19)
Aug 18 03:33:12 soni kernel: [ 1231.737237] btusb_bulk_complete: hci0 urb dce6f480 failed to resubmit (19)
Aug 18 03:33:12 soni kernel: [ 1231.738211] btusb_bulk_complete: hci0 urb dce6f700 failed to resubmit (19)
Aug 18 03:33:12 soni kernel: [ 1231.738286] btusb_send_frame: hci0 urb dce6bb00 submission failed
Aug 18 03:33:12 soni bluetoothd[3729]: HCI dev 0 unregistered
Aug 18 03:33:12 soni bluetoothd[3729]: Stopping hci0 event socket
Aug 18 03:33:12 soni bluetoothd[3729]: Unregister path: /org/bluez/3727/hci0
Aug 18 03:33:12 soni NetworkManager[732]: <info> BT device 18:86:AC:73:03:5C removed
Aug 18 03:33:12 soni NetworkManager[732]: <info> BT device 00:1B:33:D1:38:43 removed
Aug 18 03:33:12 soni NetworkManager[732]: <info> BT device 00:25:47:97:CE:13 removed

```

---

### Post by _sphinx_ on 2011-08-19
bump ](*,)
help requested. wifi is not working.

---

### Post by chili555 on 2011-08-19
You might check this thread and see if you have the same issue and need the same solution: [http://ubuntuforums.org/showthread.php?t=1778094&highlight=dell-laptop](http://ubuntuforums.org/showthread.php?t=1778094&highlight=dell-laptop)

---

### Post by _sphinx_ on 2011-08-20
Thanks. It solved the problem. I did these step before also but forgot to turn on the wifi interface through ```
sudo ifconfig wlan0 up
```. Thanks very much.

---

